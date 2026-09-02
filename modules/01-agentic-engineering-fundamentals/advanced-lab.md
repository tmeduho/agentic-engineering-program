# Module 01 Advanced Lab — Controlled Context and Harness Experiment

- Status: optional, elective, and non-core
- Prerequisite: complete or clearly understand the five core artifacts in
  [lab.md](lab.md)
- Output: an exploratory report by default

This advanced lab preserves the former controlled experiment for a learner who
judges the additional time and tool cost worthwhile. It does not block core
completion, establish provider superiority, or license publication, approval,
or production use.

## Objective and scope

Use one frozen engineering task to explore how context design and harness
choice affect a locally observed outcome, then validate a candidate workflow
on a fresh task. This is an exploratory, local engineering experiment, not a
model benchmark. Its conclusions apply only to the recorded task, baseline,
harness/model versions, permissions, environment, and evidence.

The five conditions in this design are **not statistical replication**. Their
default output is an exploratory report. When estimating treatment effects,
repeat each condition with randomized run order and predeclare the replication,
stopping, exclusion, and analysis rules. Prior familiarity with Agent
Experiment Ledger is a material confounder. Prefer a fresh fixture when the
aim is provider comparison, while retaining the same discipline about frozen
tasks, baseline, authority, and verification.

## Safety and evidence boundary

Use a non-production repository or an isolated representative checkout. Before
the first run, declare and record permissions, network state, time ceiling,
tool spend ceiling, CPU, RAM, disk, concurrency limit, resource-enforcement
mechanism, and infrastructure-failure/exclusion rule. Use synthetic or approved data; do not retain raw
private transcripts, credentials, proprietary prompts, private source, or
absolute private paths. Disable deployment, release, billing, account
administration, destructive infrastructure actions, and access to unrelated
directories. Require human approval for dependency changes, data migrations,
destructive commands, scope changes, and authority expansion.

Use a fresh isolated worktree at the immutable baseline for every run. Store
the experiment plan, metrics, sanitized event summaries, verification records,
and report outside code-under-test worktrees. Stop the experiment if equivalent
isolation cannot be established.

## 1. Freeze the task and baseline

Before any agent sees the task, write an experiment plan that fixes:

```markdown
# Experiment Plan

## Task outcome
<observable user or system outcome>

## Baseline
- Repository:
- Immutable commit:
- Environment:

## Constraints and non-goals
- ...

## Acceptance checks
- Command or observable check:
- Expected result:

## Permissions and human approval boundaries
- ...

## Limits and stop conditions
- Time ceiling:
- Tool spend ceiling:
- Repeated-failure threshold:
- Safety or ambiguity conditions:

## Predicted failure modes
- Treatment A:
- Treatment B:
- Treatment C:
```

The outcome, constraints, baseline, acceptance checks, permission boundary,
and limits remain fixed during the context comparison. A changed task or
acceptance rule invalidates the affected comparison rather than becoming an
unrecorded treatment adjustment.

Choose a task that represents bounded experienced engineering work, requires
repository discovery and a nontrivial decision, has deterministic checks and
observable behavior, and fits coherent review. Avoid production dependencies,
open-ended rewrites, mechanical renames, and familiar solutions. A fresh,
unfamiliar fixture is preferable if comparison across providers is the actual
question.

## 2. Context treatments under one harness/model

Keep the initial harness and model version the same for these three context
treatments. Start every run in a fresh session and a separate isolated worktree
at the baseline; never repair one treatment with knowledge from another.

| Treatment | Context | Required record |
| --- | --- | --- |
| A — task-only | Frozen outcome, constraints, and acceptance; normal repository discovery. | Exact task packet and any unavoidable ambient context. |
| B — repository-guided | A plus concise recurring repository instructions and orientation. | Included files, authority, freshness, and cost. |
| C — curated progressive disclosure | A plus a small packet that points to task-local decisions, entry points, raw evidence, and deeper material. | Initial packet, retrieval triggers, later retrieval, and cost. |

Record exact context artifacts and byte/token counts only where the harness
exposes them. Do not silently revise a treatment after observing a result.
Missing telemetry remains `unknown`.

For every treatment run:

1. Record the immutable baseline, worktree path, clean Git state, harness,
   model/settings when visible, tools, permissions, network state, time/spend
   limits, CPU/RAM/disk/concurrency limits, resource enforcement,
   infrastructure failures/exclusions, and start time. Record unavailable
   values as `unknown`.
2. Apply the assigned context, let the agent work only within the frozen
   boundary, and record every human intervention and why it occurred.
3. Stop at the declared limit or an agent completion claim; preserve the final
   diff and a sanitized event summary.
4. Run the same acceptance and regression checks and obtain an independent
   diff review. When practical, hide the treatment identity from the reviewer.

The producing agent's completion claim is not the sole verifier.

## 3. Cross-harness comparison

Select the strongest treatment by verified outcome quality, not speed alone.
Run that treatment from the same immutable baseline across two harnesses. Keep
the frozen task, acceptance, authority, time/spend limits, and available
external systems equivalent as far as possible. Record unavoidable differences
in model/version, tools, sandboxing, telemetry, interface, session state, and
approval policy as confounders.

This comparison does not isolate a provider, model, or harness from those
remaining differences. Do not call it a provider ranking or generalize beyond
the recorded systems and task.

## 4. Measurements and independent verification

Use one metrics row per run:

| Field | Record |
| --- | --- |
| `run_id` | Stable identifier that does not reveal treatment to a blinded reviewer. |
| `baseline_commit` | Exact immutable starting revision. |
| `harness_version`, `model` | Visible product/version/settings, or `unknown`. |
| `context_treatment` | A, B, C, or selected-treatment cross-harness run. |
| `context_size` | Initially supplied and later retrieved bytes/tokens, where observed. |
| `permissions` | Filesystem, network, command, and approval policy. |
| `resources`, `enforcement`, `infrastructure_exclusion` | CPU, RAM, disk, concurrency, enforcement mechanism, and excluded/failed infrastructure condition; use `unknown` where unavailable. |
| `wall_minutes`, `reported_tokens`, `reported_cost` | Observed values; record `unknown` when unavailable. |
| `human_interventions`, `wrong_turns` | Evidence-backed count and explanation. |
| `files_changed`, `diff_lines` | Final scope, noting generated files separately. |
| `acceptance_result`, `regression_result` | Result for every frozen check. |
| `review_findings`, `verified_outcome` | Independent review counts and whether external evidence supports acceptance. |

`verification.md` must retain exact commands or procedures, results outside
the producing agent's narrative, behavioral acceptance evidence, regression
results, independent diff-review findings, and a permission/dependency safety
review. If an acceptance check changes, rerun affected conditions or invalidate
the comparison. Do not use agent self-report as external verification.

For an initialization-publication task modeled on Unit 4, the independent
verifier owns a behavior-level post-run test, not a reference-solution API.
Use only the candidate's documented deterministic seam to inject failure
immediately before candidate publication; require rejection/failure, no
destination, no unpublished staging entry, a clean retry, and a blocker-free
ledger check. Review the agent-authored test separately, record seam/test-design
variance as a confounder, and fail acceptance if no observable seam exists.
Do not change production behavior to create a seam or require
`publicationHooks.beforePublish`; that exact reference test remains evidence
only for its reference revision.

## 5. Synthesize and validate a workflow

In `experiment-report.md`, keep these categories separate:

- **Observations:** directly measured results.
- **Explanations:** plausible mechanisms and their supporting evidence.
- **Confounders:** uncontrolled differences, familiarity, missing telemetry,
  and evidence contamination.
- **Decisions:** practices to adopt, reject, or test further.
- **Scope:** the exact case to which each conclusion applies.

Allow negative, narrowed, and unresolved results. A preferred practice that
wins every condition needs extra scrutiny for confirmation bias.

Then write `workflow-v1` with task framing, falsifiable acceptance,
inspect-before-edit behavior, context selection and retrieval rules,
tools/environment/permission boundaries, decision rights, progress and
handoff state, verification/review gates, stop/recovery rules, and retained
metrics. Apply it to a fresh comparable task in another isolated worktree.
Declare the task's permissions, time, and tool spend before starting. Use an
independent diff review plus acceptance and regression checks. Keep the
workflow only when the validation evidence supports a stated outcome or risk
reduction without disproportionally transferring work to the human.

## Advanced-lab acceptance

An exploratory advanced report is complete when it contains:

- a frozen task and immutable baseline before exposure to agents;
- three context treatments under one stated harness/model;
- the strongest treatment tested across two harnesses;
- isolated worktrees and declared permissions, time, and tool spend for every
  run;
- independent diff review, acceptance checks, and regression checks;
- a fresh-task `workflow-v1` validation with the same verification discipline;
- observations, explanations, confounders, and decisions as separate sections;
  and
- explicit limits: five conditions are not replication, prior ledger
  familiarity confounds results, and provider comparison prefers a fresh
  fixture.

Decide for yourself whether this elective additional time and tool cost is
justified. If it is not, finish the core artifact chain; no advanced work is
required.
