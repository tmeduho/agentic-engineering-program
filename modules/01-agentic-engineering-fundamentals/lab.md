# Module 01 Lab — Context and Harness Experiment

- Status: designed, not run
- Lead: Codex
- Independent reviewer: Claude
- Estimated effort: 8–12 hours across setup, five runs, verification, and synthesis

## Objective

Measure how context design and harness choice affect a real engineering outcome, then convert the strongest observed practice into a reusable workflow and validate it on a fresh task.

This is not a model benchmark. It is a controlled, local experiment intended to improve the learner's own engineering system.

## Required evidence

When the lab is run, create:

```text
runs/YYYY-MM-DD-<task-slug>/
├── experiment-plan.md
├── run-metrics.csv
├── observations.md
├── verification.md
├── experiment-report.md
└── workflow-v1.md
```

The `runs/` directory is deliberately absent from the initial scaffold. Create it only when a real experiment exists. Do not commit raw transcripts, secrets, proprietary code, or sensitive prompts without an explicit data review.

## Safety boundary

- Use a non-production repository or an isolated copy of a representative repository.
- Start each run from the same immutable baseline commit in a separate branch or worktree.
- Use test credentials and synthetic or approved data only.
- Disable deployment, release, billing, account administration, destructive infrastructure actions, and access to unrelated directories.
- Keep network access off unless the task requires a named endpoint; record every allowed endpoint and why it is needed.
- Require human approval for dependency changes, data migrations, destructive commands, scope changes, and access expansion.
- Define a time and spend ceiling before the first run.

Stop the lab if equivalent isolation cannot be established.

## Step 1 — Select the task

Choose one task that:

- represents 45–120 minutes of experienced human engineering work;
- requires repository discovery and at least one nontrivial decision;
- changes several related code paths but fits in one coherent review;
- has deterministic automated checks and observable behavioral acceptance;
- does not depend on production credentials or unstable external services;
- is unfamiliar enough that memorized task-specific solutions are unlikely.

Good candidates include a bounded feature across API and UI boundaries, a defect requiring root-cause analysis, or a small reliability improvement with measurable behavior.

Avoid greenfield toy apps, mechanical renames, dependency-only updates, or open-ended rewrites.

## Step 2 — Freeze the experiment plan

Write `experiment-plan.md` before any agent sees the task:

```markdown
# Experiment Plan

## Task outcome
<observable user or system outcome>

## Baseline
- Repository:
- Commit:
- Environment:

## Constraints and non-goals
- ...

## Acceptance checks
- Command or observable check:
- Expected result:

## Human approval boundaries
- ...

## Stop conditions
- Time ceiling:
- Spend ceiling:
- Repeated-failure threshold:
- Safety or ambiguity conditions:

## Predicted failure modes
- Treatment A:
- Treatment B:
- Treatment C:
```

The task outcome, constraints, acceptance checks, time budget, and safety boundary must remain constant across comparison runs.

## Step 3 — Prepare three context treatments

Use the same initial harness and model version for these runs.

### Treatment A — Task-only

Provide the frozen task outcome, constraints, and acceptance checks. Allow normal repository discovery. Do not add special project instructions for the experiment.

### Treatment B — Repository-guided

Provide Treatment A plus concise repository-level instructions and an architecture/orientation document. Include only rules expected to recur across tasks.

### Treatment C — Curated progressive disclosure

Provide Treatment A plus a small task packet that links to relevant decisions, entry points, raw evidence, and deeper documentation. The initial packet should explain when to retrieve each item rather than loading all content upfront.

Record exact context artifacts and byte/token counts when the harness exposes them. Never silently repair a treatment after seeing a prior result.

## Step 4 — Run the context comparison

Before starting, choose and record the run order to reduce convenience bias. For every run:

1. Create a fresh isolated worktree at the baseline commit.
2. Start a fresh agent session with no generated output from another treatment.
3. Record harness, model, model settings, tool versions, permissions, network access, and start time.
4. Apply the assigned context treatment.
5. Let the agent work within the frozen boundaries. Record every human intervention and why it occurred.
6. Stop at the predefined limit or when the agent claims completion.
7. Preserve the final diff and sanitized event summary for verification.
8. Run the same acceptance and regression checks.
9. Have a human inspect the diff without seeing which treatment produced it when practical.

Do not allow the producing agent to grade its own outcome as the only verifier.

## Step 5 — Compare harnesses

Select the strongest context treatment based on verified outcome quality, not speed alone.

Run that treatment from the same baseline in both Codex and Claude Code. Keep the task, acceptance checks, authority, time budget, and available external systems equivalent. Record unavoidable differences in tools, sandboxing, telemetry, and model settings as confounders.

Do not generalize beyond the tested harness/model/version/task combination.

## Step 6 — Capture measurements

Use one row per run in `run-metrics.csv`.

| Field | Definition |
| --- | --- |
| `run_id` | Stable identifier without model or treatment leakage for blinded review. |
| `baseline_commit` | Exact starting revision. |
| `harness_version` | Product and version. |
| `model` | Exact model identifier and reasoning setting when visible. |
| `context_treatment` | A, B, or C. |
| `context_size` | Bytes or tokens supplied initially and retrieved later. |
| `permissions` | Filesystem, network, command, and approval policy. |
| `wall_minutes` | Start to stop. |
| `reported_tokens` | Input/output/cached tokens when available; otherwise blank. |
| `reported_cost` | Provider-reported or explicitly calculated cost; otherwise blank. |
| `human_interventions` | Count of decisions, corrections, approvals, and restarts. |
| `wrong_turns` | Evidence-backed abandoned approaches, not stylistic disagreement. |
| `files_changed` | Final changed-file count. |
| `diff_lines` | Added plus removed lines, with generated files identified separately. |
| `acceptance_result` | Pass/fail for each frozen acceptance check. |
| `regression_result` | Pass/fail for the full relevant test suite. |
| `review_findings` | Blocker/major/minor counts from independent diff review. |
| `verified_outcome` | Yes only when behavior and repository state satisfy acceptance. |

Record missing telemetry as missing. Do not estimate it from another harness.

## Step 7 — Verify independently

`verification.md` must include:

1. Exact commands or procedures and their outputs/results.
2. Behavioral acceptance evidence outside the producing agent's narrative.
3. Relevant regression checks.
4. Human diff review findings.
5. Security, permission, and dependency-change review.
6. Whether the implementation solves the stated outcome rather than only passing tests.
7. Any evidence contamination, harness asymmetry, or other confounder.

If an acceptance check was corrected after a run exposed a gap, rerun every treatment affected by the change or clearly invalidate the comparison.

## Step 8 — Synthesize without overclaiming

In `experiment-report.md`, separate:

- **Observations:** directly measured results.
- **Explanations:** plausible mechanisms supported by evidence.
- **Confounders:** uncontrolled differences and missing telemetry.
- **Decisions:** practices to adopt, reject, or test again.
- **Scope:** the exact situations to which each conclusion applies.

At least one result should be allowed to challenge the original hypothesis. A report in which every preferred practice wins needs extra scrutiny for confirmation bias.

## Step 9 — Build and validate `workflow-v1`

Write a concise workflow containing:

- task framing and falsifiable acceptance;
- inspect-before-edit behavior;
- context selection and retrieval rules;
- tool, environment, and permission boundaries;
- human decision rights and escalation;
- progress and handoff state;
- verification and review gates;
- stop conditions and recovery;
- metrics retained for later comparison.

Apply `workflow-v1` to a fresh, comparable task. Capture the same metrics. Keep the workflow only if the validation run improves a stated outcome or reduces risk without moving disproportionate work to the human.

## Lab acceptance criteria

- Three context treatments were run under one fixed harness/model baseline.
- The strongest treatment was compared across Codex and Claude from the same repository baseline.
- `workflow-v1` was validated on a fresh task, for at least five total runs.
- Every run stayed within the declared safety, time, and spend boundaries.
- Acceptance and regression checks were executed after each final change.
- A human or independent agent reviewed each final diff; human review remains required for product and risk judgment.
- Observations, explanations, and confounders are separated.
- At least one hypothesis was rejected, narrowed, or left unresolved.
- One durable improvement was adopted with before/after evidence, or the report explains why no change earned adoption.

## Optional extension

Build a minimal agent loop with one safe read tool and one reversible write tool. Add structured event logging, explicit approval, a stop condition, and an external outcome check. Compare the loop with the same model called without tools. This is a mechanism probe, not a production agent platform.

