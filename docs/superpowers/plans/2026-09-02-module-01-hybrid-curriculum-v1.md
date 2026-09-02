# Module 01 Hybrid Curriculum v1 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use
> superpowers:subagent-driven-development (recommended) or
> superpowers:executing-plans to implement this plan task-by-task. Steps use
> checkbox - [ ] syntax for tracking. When using subagents, follow the model
> routing policy below; do not default every task to GPT-5.6 Sol or maximum
> reasoning effort.

**Goal:** Produce the complete, review-ready Module 01 hybrid curriculum with
five original units, evidence-backed exercises, async facilitation, a core lab,
and an optional advanced experiment.

**Architecture:** Keep the curriculum repository dependency-free and
Markdown-based. brief.md remains the normative contract, curriculum.md becomes
the learner entry point, focused unit files contain teaching, exercise
templates define artifact contracts, evidence packs provide bounded fallbacks,
and the lab and facilitation files compose those parts without duplicating
them. Agent Experiment Ledger supplies real historical cases at two immutable
commits.

**Tech Stack:** Markdown, Git, shell verification, Node.js 22 or newer and pnpm
10.26.1 only when validating Agent Experiment Ledger exercises.

**Spec:** docs/superpowers/specs/2026-09-02-module-01-hybrid-curriculum-design.md

## Global Constraints

- Read AGENTS.md, CHARTER.md, PROFILE.md, RUBRIC.md, ROADMAP.md, DECISIONS.md,
  the approved spec, and every active Module 01 artifact before editing.
- Keep the curriculum repository dependency-free and Markdown-based.
- Preserve unrelated .DS_Store changes and any later user changes.
- Write original teaching. MEGA supplies only its public topic progression.
- Target experienced software engineers; remove beginner material unless it
  unlocks an advanced dependency.
- Keep the core workload at 405 minutes: 45, 60, 75, 90, and 60 minutes for the
  five units plus 75 minutes for async or synchronous discussion.
- Include required reading inside each unit timebox and cap it at 15 minutes.
- Keep the core provider-neutral. No learner must have both Codex and Claude.
- Treat Unit 4 as an N=1 case study and the advanced lab as exploratory unless
  conditions are replicated.
- Never claim that one execution proves workflow improvement.
- Every live-run exercise needs a timebox, stop condition, sanitized evidence
  fallback, expected repository state, and external verification procedure.
- Store learner evidence outside code-under-test worktrees.
- Do not publish repositories, choose a license, or create a remote in this
  plan. Public distribution and sample-project release packaging require a
  separate approved plan.
- Do not author Claude's independent findings or final verdict.
- Only the learner may mark Module 01 approved.
- Use Agent Experiment Ledger exercise baseline
  bb65b5cec8c96c3ba3d89b0025473561c7c8146f.
- Use Agent Experiment Ledger verified reference revision
  2c498f616583d1fd6aeeaa381552b47acdb71ab7.

## Subagent Model Routing

Choose the route from the task shape, risk, and required quality. When multiple
routes can meet the acceptance criteria, prefer the less expensive one. Treat
these as initial assignments, not permanent labels:

| Work shape | Initial route | Escalate when |
| --- | --- | --- |
| Deterministic checks, link and path audits, metadata normalization, evidence extraction, and other bounded mechanical work | `gpt-5.6-luna`, `medium` | The work requires unresolved semantic judgment rather than a better-defined procedure |
| Contract interpretation, curriculum authoring, exercise design, facilitation design, and cross-file synthesis | `gpt-5.6-terra`, `medium` or `high` | Review finds a material correctness or reasoning gap after one focused revision |
| Independent adversarial critique, difficult conflict resolution, and quality-first final review | `gpt-5.6-sol`, `high` | A defined review criterion still fails and the failure plausibly needs deeper reasoning; try `xhigh` before `max` |

Use these task defaults:

| Plan work | Default route |
| --- | --- |
| Task 1 contract and decision alignment | Terra, `medium` |
| Task 2 source metadata and mechanical claim mapping | Luna, `medium`; Terra, `medium` for the semantic claim audit |
| Task 3 artifact and evidence-pack contracts | Terra, `medium` |
| Tasks 4-8 unit authoring | Terra, `high` |
| Task 9 core and advanced lab design | Terra, `high` |
| Task 10 async and workshop facilitation | Terra, `high` |
| Task 11 navigation, links, and file assembly | Luna, `medium`; Terra, `medium` for learner-facing synthesis |
| Task 12 deterministic validation | Luna, `medium` |
| Task 12 fresh-context learner simulation | Terra, `medium` |
| Task 12 independent curriculum critique | Sol, `high` |
| Task-scoped review | Terra, `medium`; Luna, `medium` only for a small mechanical diff with deterministic checks; Sol, `high` for subtle or high-risk cross-file judgment |
| Final whole-module review | Sol, `high` |

For every subagent dispatch:

- set `model` and `reasoning_effort` explicitly;
- use `fork_turns: "none"` and provide a self-contained prompt with the exact
  files, constraints, acceptance checks, and expected output;
- keep authoring and independent review in separate contexts;
- raise effort or move up one model tier only in response to a named task risk
  or observed quality failure;
- use a model at least one tier above the stuck implementer for fix rounds four
  and five, as required by the subagent-driven-development workflow;
- do not use Sol `max` as a first pass; reserve it for a still-failing,
  quality-first task after `high` or `xhigh` has been evaluated; and
- record the actual model, effort, selection reason, and any escalation in the
  plan's subagent progress ledger and task handoff. Summarize the routing used
  in codex-review.md during Task 12.

If a task changes shape, reroute it. Cost alone does not justify assigning a
review to a model that cannot evaluate the relevant failure modes.

## Plan Boundary

This plan implements the curriculum and validates it against the local sibling
checkout of Agent Experiment Ledger. It prepares source material and exact
baseline requirements for distribution but does not publish the sample
project. A separate release plan will select licenses, create or approve a
public remote, tag the course baseline, and test a clean external checkout.

## File Responsibility Map

### Existing files to modify

- DECISIONS.md — append the learner-approved hybrid-delivery decision.
- README.md — explain the hybrid course workflow and current distribution
  status.
- research/source-index.md — register current sources that support more than
  one module.
- ROADMAP.md — update Module 01 status only when the review handoff is ready.
- modules/01-agentic-engineering-fundamentals/brief.md — normative outcomes,
  gates, prerequisites, and required deliverables.
- modules/01-agentic-engineering-fundamentals/curriculum.md — learner start
  page, sequence, timing, MEGA coverage map, and links.
- modules/01-agentic-engineering-fundamentals/sources.md — sole source metadata
  registry and claim map.
- modules/01-agentic-engineering-fundamentals/lab.md — core artifact-chain lab.
- modules/01-agentic-engineering-fundamentals/codex-review.md — lead
  self-review, evidence, and handoff.
- modules/01-agentic-engineering-fundamentals/claude-review.md — update only the
  handoff status and requested review scope; leave findings and verdict blank
  for Claude.

### New learner files

- modules/01-agentic-engineering-fundamentals/units/01-models-loops-harnesses.md
- modules/01-agentic-engineering-fundamentals/units/02-context-engineering.md
- modules/01-agentic-engineering-fundamentals/units/03-project-knowledge.md
- modules/01-agentic-engineering-fundamentals/units/04-harness-comparison.md
- modules/01-agentic-engineering-fundamentals/units/05-reusable-workflows.md
- modules/01-agentic-engineering-fundamentals/workshop.md
- modules/01-agentic-engineering-fundamentals/facilitator-guide.md
- modules/01-agentic-engineering-fundamentals/advanced-lab.md

### New artifact templates

- modules/01-agentic-engineering-fundamentals/exercises/run-trace-template.md
- modules/01-agentic-engineering-fundamentals/exercises/context-comparison-template.md
- modules/01-agentic-engineering-fundamentals/exercises/knowledge-map-template.md
- modules/01-agentic-engineering-fundamentals/exercises/harness-case-study-template.md
- modules/01-agentic-engineering-fundamentals/exercises/workflow-template.md
- modules/01-agentic-engineering-fundamentals/exercises/team-decision-template.md

### New evidence packs

- modules/01-agentic-engineering-fundamentals/exercises/evidence/README.md
- modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-01-run-trace.md
- modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-02-context-comparison.md
- modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-03-knowledge-audit.md
- modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-04-harness-case-study.md
- modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-05-workflow-validation.md

---

### Task 1: Align the normative contract and decision log

**Files:**

- Modify: DECISIONS.md
- Modify: modules/01-agentic-engineering-fundamentals/brief.md

**Interfaces:**

- Consumes: the approved hybrid-curriculum design spec.
- Produces: the normative outcomes and deliverables every later task must
  satisfy.

- [ ] **Step 1: Re-read the governing documents and inspect repository state**

Run:

~~~bash
git status --short --branch
git log -3 --oneline --decorate
~~~

Expected: main contains the approved design commit. Existing .DS_Store changes
remain unstaged and are not included in later commits.

- [ ] **Step 2: Append decision D-006 to DECISIONS.md**

Use this exact decision:

~~~markdown
## D-006 — Adopt a free hybrid course and separate the advanced experiment

- Date: 2026-09-02
- Status: accepted
- Decider: learner
- Context: The initial Module 01 draft made a five-run controlled experiment a core requirement. The learner wants an original course that coworkers can use without a curriculum fee, with comparable coverage to MEGA's public progression and realistic participation during a busy schedule.
- Proposal or critique: Use five concise self-paced units, async-first discussion, an optional synchronous workshop, provider-neutral core exercises, evidence-backed artifacts, and an optional advanced controlled experiment.
- Decision: Adopt the hybrid delivery model in docs/superpowers/specs/2026-09-02-module-01-hybrid-curriculum-design.md. Make the five-run experiment elective. Prepare the repositories for eventual public distribution without selecting licenses or publishing them in this change.
- Reason: This retains the desired subject coverage while reducing core workload, avoiding unnecessary provider requirements, and supporting coworkers who cannot attend live sessions.
- Evidence: Learner approvals recorded during the 2026-09-02 design discussion and the independent design critique incorporated into the approved spec.
- Change made: Module 01 outcomes, curriculum, lab, exercises, workshop, facilitation, and reviews will be aligned with the approved hybrid design.
- Revisit when: A pilot shows that the timeboxes, artifact chain, provider-neutral fallbacks, or async format do not produce the intended learning.
~~~

- [ ] **Step 3: Rewrite brief.md around five core outcomes**

The outcomes must state that the learner can:

1. Trace model inference, context assembly, agent-loop decisions, tool
   execution, environment effects, authority, observations, and verification.
2. Compare bounded context configurations while separating observations,
   explanations, and confounders.
3. Design and test a repository knowledge structure with authority, freshness,
   discovery, precedence, and retirement rules.
4. Conduct an N=1 comparison of two agent-system configurations without
   generalizing beyond the observed case.
5. Write and execute a bounded workflow with decision rights, safety,
   escalation, evidence, and verification gates.

Replace the required deliverables with the five core artifacts plus one
decision record. State that advanced-lab.md is elective and cannot block core
completion.

- [ ] **Step 4: Make prerequisites provider-neutral**

Require:

- one supported coding-agent configuration or the prepared evidence packs;
- a local copy of Agent Experiment Ledger at the named commits;
- Git, Node.js 22 or newer, and pnpm 10.26.1 for live code exercises;
- an isolated worktree or equivalent disposable checkout; and
- permission to retain sanitized learning artifacts.

Do not require both Codex and Claude.

- [ ] **Step 5: Verify the old mandatory experiment contract is gone**

Run:

~~~bash
rg -n "at least five total runs|three context treatments|Compare Codex and Claude|controlled comparison report" modules/01-agentic-engineering-fundamentals/brief.md
~~~

Expected: no matches.

Run:

~~~bash
rg -n "N=1|provider-neutral|advanced-lab.md|decision record|405 minutes" modules/01-agentic-engineering-fundamentals/brief.md
~~~

Expected: every concept is present.

- [ ] **Step 6: Check the contract against the approved spec**

For every outcome, point to one required artifact and one falsifiable
acceptance condition. Confirm that no elective outcome remains in the core
gate.

- [ ] **Step 7: Check Markdown and staged scope**

Run:

~~~bash
git diff --check
git status --short
~~~

Expected: only DECISIONS.md and brief.md are staged for this task; .DS_Store
changes remain unstaged.

- [ ] **Step 8: Commit the contract**

~~~bash
git add DECISIONS.md modules/01-agentic-engineering-fundamentals/brief.md
git commit -m "docs: align Module 01 with hybrid delivery"
~~~

---

### Task 2: Refresh and map the source registry

**Files:**

- Modify: modules/01-agentic-engineering-fundamentals/sources.md
- Modify: research/source-index.md

**Interfaces:**

- Consumes: Task 1 outcomes and the source policy in RUBRIC.md.
- Produces: stable source IDs used by every unit; later units must not duplicate
  source metadata.

- [ ] **Step 1: Re-open every retained source**

Verify the exact supporting sections in:

- S01: https://developers.openai.com/blog/codex-as-a-platform
- S02: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- S03: https://www.anthropic.com/engineering/harness-design-long-running-apps
- S04: https://www.anthropic.com/engineering/managed-agents
- S05: https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents

Record the actual check date, visible publication or version date, source type,
relevance, and freshness status. If a publication date is not shown, write
"not stated" rather than inventing one.

- [ ] **Step 2: Add current first-party harness documentation**

Add:

- S06: https://code.claude.com/docs/en/how-claude-code-works
- S07: https://code.claude.com/docs/en/settings
- S08: https://code.claude.com/docs/en/permissions
- S09: https://code.claude.com/docs/en/memory
- S10: https://developers.openai.com/api/docs/guides/latest-model

Use S06-S09 only for current Claude Code behavior. Use S10 for visible model
settings, context management, tool behavior, and the need to treat model
families as versioned systems. Do not turn provider behavior into a universal
claim.

- [ ] **Step 3: Retain the MEGA reference as scope evidence**

Add local source R01:

~~~text
../../research/mega-dev-curriculum.md
~~~

State that it supports only MEGA's public agenda and format claims checked on
2026-08-26. It does not establish paid lesson depth or technical truth.

- [ ] **Step 4: Add repository evidence as a primary local source**

Add P01 for Agent Experiment Ledger:

~~~text
Repository: /Users/tmeduho/dev/learning/agent-experiment-ledger
Exercise baseline: bb65b5cec8c96c3ba3d89b0025473561c7c8146f
Reference revision: 2c498f616583d1fd6aeeaa381552b47acdb71ab7
~~~

State that Git history, source, tests, and README support the prepared cases.
The absolute path is authoring evidence, not a public distribution location.

- [ ] **Step 5: Add a unit-to-source map**

Map:

- Unit 1: S01, S06, S10, P01.
- Unit 2: S02, S06, S09, P01.
- Unit 3: S02, S09, P01.
- Unit 4: S01, S03, S07, S08, P01.
- Unit 5: S03, S04, S05, P01.

Required reading must use at most one 10-15 minute source selection per unit.
All other sources are optional or facilitator material.

- [ ] **Step 6: Expand the claim-to-source map**

Include these exact claim families:

- model output and agent-system outcome are not the same thing;
- context contains more than the user prompt;
- context and memory behavior are harness-specific and versioned;
- tools, permissions, sandboxing, and approvals are separate control surfaces;
- completion text is not environment verification;
- repository knowledge needs authority, freshness, and discovery rules;
- more context and more harness structure are not automatically better; and
- one case study cannot establish universal model or harness superiority.

Qualify each claim and identify the unit that teaches it.

- [ ] **Step 7: Register reusable sources in research/source-index.md**

Add:

- SRC-017 for OpenAI Model guidance;
- SRC-022 for How Claude Code works;
- SRC-023 for Claude Code settings;
- SRC-024 for Claude Code permissions; and
- SRC-025 for Claude Code memory.

Use the same title, publisher, URL, publication/version information, checked
date, status, and relevance as the module registry. The shared index describes
program-wide relevance; the module file retains the Unit 01 claim mapping.

- [ ] **Step 8: Verify metadata completeness and source uniqueness**

Run:

~~~bash
rg -n "S01|S02|S03|S04|S05|S06|S07|S08|S09|S10|R01|P01" modules/01-agentic-engineering-fundamentals/sources.md
~~~

Expected: every identifier appears in the registry and mapping.

Run:

~~~bash
rg -n "Date not captured|not set|not evaluated" modules/01-agentic-engineering-fundamentals/sources.md
~~~

Expected: no matches. Unknown publication dates use "not stated" with a
checked date.

- [ ] **Step 9: Commit the source registry**

~~~bash
git add research/source-index.md modules/01-agentic-engineering-fundamentals/sources.md
git commit -m "docs: refresh Module 01 source map"
~~~

---

### Task 3: Define the artifact and evidence-pack contracts

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/exercises/run-trace-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/context-comparison-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/knowledge-map-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/harness-case-study-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/workflow-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/team-decision-template.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/README.md

**Interfaces:**

- Consumes: Task 1 artifact requirements.
- Produces: exact artifact schemas consumed by Units 1-5, the lab, and the
  workshop.

- [ ] **Step 1: Create the run-trace schema**

Require:

- run identity and evidence references;
- event sequence;
- per-event labels for intent, context, inference, tool, environment,
  observation, state, authority, verification, and human decision;
- earliest preventable layer;
- three competing failure hypotheses;
- evidence for and against each hypothesis; and
- conclusion and residual uncertainty.

- [ ] **Step 2: Create the context-comparison schema**

Require:

- frozen task and acceptance;
- configuration A and B inventories;
- authority, freshness, placement, size/cost, and retrieval timing;
- predicted failure modes before results;
- observed behavior;
- wrong turns and interventions;
- confounders; and
- keep, revise, or reject decision.

- [ ] **Step 3: Create the knowledge-map schema**

Require one row per artifact with:

- purpose;
- owner;
- authority;
- consumers;
- discovery path;
- load strategy;
- freshness trigger;
- precedence;
- supersession or deletion rule; and
- observed decision value.

Add before/after discovery-probe sections with exact question, starting
context, steps, elapsed time, result, and evidence.

- [ ] **Step 4: Create the harness-case-study schema**

Require:

- frozen task, baseline, acceptance, and stop condition;
- configuration descriptions;
- permissions and environment;
- observed outcomes;
- interventions, wrong turns, wall time, and available usage data;
- acceptance and regression results;
- independent diff or evidence review;
- confounders;
- claims supported by this case; and
- claims this case cannot support.

- [ ] **Step 5: Create the workflow schema**

Require:

- intended task class;
- intent and risk framing;
- inspect-before-edit evidence;
- context selection and retrieval;
- tools, permissions, and environment;
- human decision rights;
- stop, recovery, and escalation conditions;
- progress and handoff state;
- acceptance, regression, and independent review gates;
- retained metrics; and
- validation deviations.

- [ ] **Step 6: Create the team-decision schema**

Require:

- participants or "solo";
- evidence reviewed;
- strongest supported practice;
- challenged claim;
- adopted, rejected, or further-test decision;
- dissent;
- owner and revisit trigger; and
- course feedback.

- [ ] **Step 7: Define evidence-pack rules**

In exercises/evidence/README.md state:

- packs are sanitized fallbacks, not hidden answer keys;
- every observation must be labeled actual repository evidence, prepared
  comparison material, or hypothetical counterexample;
- raw private transcripts are forbidden;
- commit and file references carry provenance;
- unavailable telemetry remains unknown;
- evidence packs let learners finish without a second paid provider; and
- prepared results cannot be presented as learner-run measurements.

- [ ] **Step 8: Verify all schemas contain evidence and uncertainty fields**

Run:

~~~bash
rg -L "Evidence|evidence" modules/01-agentic-engineering-fundamentals/exercises/*-template.md
rg -L "Uncertainty|uncertainty|Confounders|confounders" modules/01-agentic-engineering-fundamentals/exercises/*-template.md
~~~

Expected: both commands produce no filenames.

- [ ] **Step 9: Commit the artifact contracts**

~~~bash
git add modules/01-agentic-engineering-fundamentals/exercises
git commit -m "docs: define Module 01 artifact contracts"
~~~

---

### Task 4: Author Unit 1 — models, loops, and harnesses

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/units/01-models-loops-harnesses.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-01-run-trace.md

**Interfaces:**

- Consumes: S01, S06, S10, P01 and run-trace-template.md.
- Produces: the vocabulary and run trace used by every later unit.

- [ ] **Step 1: Write measurable outcomes and the 45-minute schedule**

Use:

- lesson: 12 minutes;
- required reading: 10 minutes;
- prepared-case exercise: 18 minutes;
- self-check and async post: 5 minutes.

Outcomes must require learners to distinguish model, agent loop, harness, tool,
environment, authority, state, and verifier; explain operational
nondeterminism; and diagnose false completion with competing hypotheses.

- [ ] **Step 2: Write the original lesson**

Cover:

- next-output generation and why fluent text is not environment observation;
- stochastic behavior and why repeated runs may differ;
- model-visible context versus external state;
- tool-call selection versus tool execution;
- the harness responsibilities around context, state, routing, approvals,
  retries, and termination;
- the execution environment and its permission boundary;
- independent verification; and
- why a model or provider label alone does not identify the deployed system.

Do not teach transformer mathematics or a provider catalog.

- [ ] **Step 3: Add the required reading**

Select one 10-minute section from S01. Use S06 and S10 as optional comparison
material. Explain what claim the learner should test while reading.

- [ ] **Step 4: Build the prepared run-trace case**

Base it on:

- exercise baseline bb65b5cec8c96c3ba3d89b0025473561c7c8146f;
- a successful type-check, test, and build report;
- an initial completion claim;
- an independent failure-injection review of initializeLedger;
- discovery that a pre-publication failure could leave partial state;
- the new test named "failed initialization publishes no partial ledger and
  can be retried";
- the staged-directory repair at reference revision
  2c498f616583d1fd6aeeaa381552b47acdb71ab7; and
- rerun verification.

Before describing the baseline checks as successful, execute pnpm install
--frozen-lockfile, pnpm check, pnpm test, and pnpm build in an isolated
baseline checkout and preserve the actual result. If a check fails, record the
failure in the case instead of repeating the historical completion claim as
fact.

Label the event sequence as a prepared reconstruction grounded in Git evidence,
not a verbatim private transcript.

- [ ] **Step 5: Write the exercise**

Learners copy run-trace-template.md, annotate every event, identify the earliest
layer that could have prevented false completion, and write three hypotheses:

1. acceptance criteria omitted failure atomicity;
2. the producing agent failed to consider interrupted publication; and
3. verification lacked fault injection.

They must cite evidence that supports or weakens each hypothesis rather than
selecting one by intuition.

- [ ] **Step 6: Write falsifiable acceptance checks**

A complete artifact:

- labels every event with at least one valid system layer;
- distinguishes completion narrative from repository evidence;
- identifies authority and verification transitions;
- includes three competing hypotheses;
- cites Git or prepared-case evidence for each; and
- states residual uncertainty.

- [ ] **Step 7: Add async and optional-depth sections**

Async prompt: "Which earliest intervention would have prevented the false
completion at the lowest recurring cost?"

Optional depth: compare S06 and S10 system descriptions and identify
provider-specific behavior that must not become a universal claim.

- [ ] **Step 8: Validate structure and language**

Run:

~~~bash
rg -n "^## (Engineering question|Learning outcomes|Lesson|Required reading|Worked example|Exercise|Deliverable|Acceptance checks|Async discussion|Optional depth)$" modules/01-agentic-engineering-fundamentals/units/01-models-loops-harnesses.md
~~~

Expected: ten section headings.

Run:

~~~bash
rg -n "always|guarantee|the model knows|AI decided" modules/01-agentic-engineering-fundamentals/units/01-models-loops-harnesses.md
~~~

Review every match and remove unsupported absolutes or anthropomorphic causal
claims.

- [ ] **Step 9: Commit Unit 1**

~~~bash
git add modules/01-agentic-engineering-fundamentals/units/01-models-loops-harnesses.md modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-01-run-trace.md
git commit -m "docs: author Module 01 agent-loop unit"
~~~

---

### Task 5: Author Unit 2 — context engineering

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/units/02-context-engineering.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-02-context-comparison.md

**Interfaces:**

- Consumes: S02, S06, S09, P01 and context-comparison-template.md.
- Produces: a bounded context-comparison method used in Units 3-5.

- [ ] **Step 1: Write outcomes and the 60-minute schedule**

Use:

- lesson: 12 minutes;
- required reading: 12 minutes;
- prediction and inventory: 8 minutes;
- comparison exercise: 23 minutes;
- self-check and async post: 5 minutes.

- [ ] **Step 2: Write the original lesson**

Cover:

- system, developer, repository, task, retrieved, tool, history, summary, and
  environment context;
- instruction versus evidence versus preference versus untrusted data;
- relevance, authority, freshness, placement, resolution, cost, and failure
  behavior;
- progressive disclosure;
- compaction and lossy summaries;
- skills, tool descriptions, and subagent results as model-visible inputs;
- context poisoning and conflicting precedence; and
- why more context is not a default improvement.

- [ ] **Step 3: Define the frozen read-only task**

Use this task at exercise baseline
bb65b5cec8c96c3ba3d89b0025473561c7c8146f:

~~~text
Determine whether a whole-ledger integrity check detects both an
experiment-directory symlink that escapes the ledger root and an in-root
experiment alias. Cite the exact traversal behavior, code paths, and missing
tests. Do not modify files. State uncertainty and stop after 20 minutes.
~~~

Acceptance requires identifying that traversal filtered only
Dirent.isDirectory entries, so symlink entries were skipped before realpath
containment could evaluate them.

- [ ] **Step 4: Define configuration A and B**

Configuration A receives only the frozen task, baseline commit, timebox, and
acceptance format.

Configuration B additionally receives:

- AGENTS.md;
- README sections on artifacts, privacy, and integrity;
- the design spec's integrity and filesystem-safety sections;
- an orientation note naming src/checks/check-ledger.ts and
  test/check.test.ts; and
- an instruction to retrieve raw source before concluding.

Keep model, harness, permissions, baseline, and timebox constant when a learner
runs both configurations.

- [ ] **Step 5: Build the evidence fallback**

Include:

- exact configuration packets;
- a concise prepared response for A that explores broadly and misses the
  Dirent filter;
- a concise prepared response for B that follows the pointer and finds it;
- raw pre-fix code from the relevant traversal branch;
- the reference fix and tests at 2c498f6;
- byte counts for both packets; and
- a warning that the prepared responses illustrate comparison material rather
  than measured provider performance.

- [ ] **Step 6: Write the exercise and artifact instructions**

Learners predict failure modes before opening the prepared results. They run
one or both configurations, or use the fallback, then record context inventory,
observations, wrong turns, interventions, cost proxy, and confounders.

- [ ] **Step 7: Write acceptance checks**

A complete artifact:

- freezes the task and variables;
- classifies every added context item by authority and freshness;
- records predictions before results;
- separates observed navigation behavior from causal explanation;
- accounts for configuration-size and file-pointer advantages;
- does not claim that more context is generally better; and
- makes a keep, revise, or reject decision for each added context item.

- [ ] **Step 8: Add discussion and optional depth**

Async prompt: "Which item in configuration B earned its context cost, and
which item merely restated information?"

Optional depth: contrast CLAUDE.md, auto memory, tool definitions, and compacted
state using S06 and S09 without assuming another harness behaves identically.

- [ ] **Step 9: Validate and commit Unit 2**

Run the ten-heading structural check used in Task 4 against
02-context-engineering.md. Confirm the evidence pack contains both
configuration packets, byte counts, raw evidence, and the prepared-result
label.

~~~bash
git add modules/01-agentic-engineering-fundamentals/units/02-context-engineering.md modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-02-context-comparison.md
git commit -m "docs: author Module 01 context unit"
~~~

---

### Task 6: Author Unit 3 — durable project knowledge

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/units/03-project-knowledge.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-03-knowledge-audit.md

**Interfaces:**

- Consumes: S02, S09, P01, knowledge-map-template.md, and Unit 2's context
  dimensions.
- Produces: a tested project-knowledge proposal used as context in Unit 4.

- [ ] **Step 1: Write outcomes and the 75-minute schedule**

Use:

- lesson: 12 minutes;
- required reading: 10 minutes;
- current-state map: 18 minutes;
- before/after discovery probe: 25 minutes;
- self-check and async post: 10 minutes.

- [ ] **Step 2: Write the original lesson**

Cover:

- operating policy, project orientation, decisions, task state, reference,
  evidence, and learned corrections;
- always-loaded versus discoverable versus task-local knowledge;
- authority, scope, precedence, ownership, freshness, and retirement;
- duplication and drift;
- summaries versus raw evidence;
- progressive disclosure;
- promoting repeated corrections into the narrowest durable control; and
- why repository instructions should not become chronological memory dumps.

- [ ] **Step 3: Define the Agent Experiment Ledger knowledge inventory**

Require learners to inspect:

- AGENTS.md;
- README.md;
- docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md;
- docs/superpowers/plans/2026-08-27-agent-experiment-ledger-v0.md;
- package.json;
- representative source and test files; and
- Git history at the two named commits.

- [ ] **Step 4: Define the discovery probe**

Use this question:

~~~text
Where is direct comparison eligibility decided, which facts make two
controlled runs comparable, and which checks prevent an ineligible report?
Provide the shortest evidence path from repository orientation to source and
tests.
~~~

Before the learner reads the prepared audit, named inventory, or any
result-bearing example, they copy the template and start a fresh context with
only the repository root listing. They run the exact before question, preserve
and close that context, then inspect/build the map. The proposed improvement is
a concise architecture and evidence navigation map in the learner's disposable
worktree. The after measurement starts a second fresh session with only that
map added from project orientation. Prepared learners analyze the recorded
paths and cannot claim them as their prospective measurement.

- [ ] **Step 5: Build the fallback evidence**

Include:

- a prepared current-state knowledge map;
- a recorded before path through README, design spec, source, and tests;
- a proposed navigation map that links comparison/eligibility.ts,
  checks/check-ledger.ts, reports/service.ts, and their tests;
- a recorded after path;
- a caution that prepared timings are illustrative and cannot substitute for
  the learner's own timing claim; and
- a duplication review showing which facts should remain in their existing
  source of truth.

- [ ] **Step 6: Write the exercise**

Live learners copy the template and run the root-listing-only before probe in a
fresh context before seeing the named inventory, prepared audit, or worked
results; they preserve and close it, build the map, then run the same after
probe in a second fresh context with only the proposed map added. Prepared
learners critically analyze the recorded paths without calling them their own
prospective measurement. Both paths decide whether the discovery benefit
justifies maintenance and context cost. They do not merge the exercise change
into the sample project's main branch.

- [ ] **Step 7: Write acceptance checks**

A complete artifact:

- assigns owner, authority, discovery, freshness, precedence, and retirement
  to every artifact;
- distinguishes source of truth from index;
- preserves raw evidence provenance;
- records before and after paths;
- rejects or narrows an improvement that duplicates existing material; and
- states where the change would be reviewed and maintained.

- [ ] **Step 8: Add discussion and optional depth**

Async prompt: "Which project fact should be always loaded, and which should be
discoverable only when its boundary is in scope?"

Optional depth: compare repository-controlled instructions with machine-local
memory using S09 and identify privacy, portability, and freshness tradeoffs.

- [ ] **Step 9: Validate and commit Unit 3**

Run the ten-heading structural check against 03-project-knowledge.md. Confirm
the evidence pack contains both discovery paths and labels its timing
limitations.

~~~bash
git add modules/01-agentic-engineering-fundamentals/units/03-project-knowledge.md modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-03-knowledge-audit.md
git commit -m "docs: author Module 01 knowledge unit"
~~~

---

### Task 7: Author Unit 4 — harness comparison

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/units/04-harness-comparison.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-04-harness-case-study.md

**Interfaces:**

- Consumes: S01, S03, S07, S08, P01,
  harness-case-study-template.md, and Unit 3's orientation proposal.
- Produces: an N=1 case study and an independently reviewed implementation
  artifact.

- [ ] **Step 1: Write outcomes and the 90-minute schedule**

Use:

- lesson: 12 minutes;
- required reading: 10 minutes;
- setup and prediction: 10 minutes;
- bounded run or dossier review: 35 minutes;
- verification and comparison: 18 minutes;
- async post: 5 minutes.

- [ ] **Step 2: Write the original lesson**

Cover:

- context assembly and compaction;
- tool schemas, routing, and observations;
- task and session state;
- sandbox, filesystem, network, and command authority;
- approval policy;
- interface effects;
- progress and handoff;
- retry, recovery, and termination;
- telemetry and missing measurements;
- stable interfaces versus stale scaffolding; and
- confounding model, harness, permission, context, and stochastic differences.

- [ ] **Step 3: Freeze the historical implementation task**

At baseline bb65b5cec8c96c3ba3d89b0025473561c7c8146f use:

~~~text
Make ledger initialization publish no partial ledger when execution fails
immediately before publication, remove unpublished staging, and permit a clean
retry. Preserve the existing CLI and error contracts. Add a deterministic
failure-injection test. Do not add dependencies or change unrelated lifecycle
behavior. Stop after 35 minutes or two failed implementation approaches.
~~~

Acceptance requires the test named "failed initialization publishes no partial
ledger and can be retried", no destination after injected failure, no staging
entry, a successful retry, and a blocker-free check.

- [ ] **Step 4: Define two comparable configurations**

Configuration A is the learner's available agent with the frozen task,
AGENTS.md, normal repository discovery, workspace-only writes, no network, and
approval for dependency or scope changes.

Dependency installation occurs during setup before the measured agent run. If
the package store is not already populated, record the setup network access
separately; the task run itself receives no network authority.

Configuration B changes exactly one named system dimension:

- another harness with equivalent authority;
- another model in the same harness;
- the same harness with the Unit 3 orientation map; or
- the prepared anonymous implementation dossier.

Record every unavoidable difference. Do not call the result a provider
benchmark.

- [ ] **Step 5: Build the implementation dossier**

Include two anonymous approaches:

- Approach A writes the destination incrementally and cleans up in a catch
  block, leaving interruption windows.
- Approach B constructs a hidden same-parent staging directory, validates it,
  and publishes it with one rename.

Include:

- relevant baseline source;
- the failure-injection test;
- focused test output;
- final regression output;
- sanitized diffs;
- permission and environment records;
- a review identifying why cleanup alone does not provide publication
  atomicity; and
- provenance linking Approach B to reference revision 2c498f6 without
  attributing either approach to a provider.

- [ ] **Step 6: Write learner execution and verification instructions**

The live path must:

1. create an isolated checkout at the exercise baseline;
2. run pnpm install --frozen-lockfile during setup and record whether it used
   network access;
3. run pnpm check, pnpm test, and pnpm build before mutation;
4. add the failure-injection test before implementation;
5. capture agent configuration, permissions, start time, interventions, and
   stop reason;
6. run the focused test;
7. run pnpm check, pnpm test, and pnpm build after the final mutation; and
8. obtain an independent diff review or use the prepared review.

- [ ] **Step 7: Write acceptance checks**

A complete case study:

- holds the task, baseline, acceptance, and authority constant;
- changes one named configuration dimension or uses the dossier;
- reports unavailable telemetry as unknown;
- includes external test and diff evidence;
- distinguishes observation from mechanism;
- records confounders; and
- limits conclusions to the observed task and configurations.

- [ ] **Step 8: Add discussion and optional depth**

Async prompt: "Which observed difference belongs to the harness, and what
evidence would be required to separate it from model or context effects?"

Optional depth: design a replicated experiment without running it.

- [ ] **Step 9: Validate and commit Unit 4**

Run the ten-heading structural check against 04-harness-comparison.md. Confirm
the evidence pack contains two approaches, the failure test, verification
output, diff evidence, permissions, and explicit provenance.

~~~bash
git add modules/01-agentic-engineering-fundamentals/units/04-harness-comparison.md modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-04-harness-case-study.md
git commit -m "docs: author Module 01 harness unit"
~~~

---

### Task 8: Author Unit 5 — reusable workflows

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/units/05-reusable-workflows.md
- Create: modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-05-workflow-validation.md

**Interfaces:**

- Consumes: S03, S04, S05, P01, workflow-template.md, and findings from Units
  1-4.
- Produces: workflow-v1 and an execution record consumed by the core lab and
  workshop.

- [ ] **Step 1: Write outcomes and the 60-minute schedule**

Use:

- lesson: 10 minutes;
- required reading: 10 minutes;
- workflow construction: 12 minutes;
- fresh-task execution or fallback: 20 minutes;
- validation and async post: 8 minutes.

- [ ] **Step 2: Write the original lesson**

Cover:

- task outcome and risk framing;
- inspect-before-edit behavior;
- falsifiable acceptance;
- context, tools, environment, and authority;
- human decision rights;
- stop, recovery, escalation, and handoff;
- acceptance, regression, security, and independent review;
- retained metrics;
- workflow usability and adoption cost;
- product, user, security, and business constraints; and
- promoting the smallest evidence-backed durable change.

- [ ] **Step 3: Freeze the fresh validation task**

At baseline bb65b5cec8c96c3ba3d89b0025473561c7c8146f use:

~~~text
Runtime-validate the complete report-generation request before ledger access,
runtime clock access, or output creation. Reject an invalid experiment ID,
unsupported format, blank output path, non-boolean includeGeneratedAt, and
unknown option keys through the stable invalid-record error path. Preserve
valid Markdown and CSV behavior. Do not add dependencies. Stop after 20
minutes or two failed approaches.
~~~

Acceptance includes the test named "runtime-validates the complete report
request before ledger access or output" from reference revision 2c498f6.

- [ ] **Step 4: Write workflow construction instructions**

Learners derive workflow-v1 from their prior artifacts. Every step must name:

- inputs;
- authority;
- observable output;
- stop condition;
- verifier; and
- retained evidence.

They must remove any practice supported only by preference or one unexplained
correlation.

- [ ] **Step 5: Build the validation evidence pack**

Include:

- the frozen task;
- baseline report service behavior;
- the full invalid-request table;
- an incomplete solution that guards only format and experiment ID;
- the request-schema solution from 2c498f6;
- evidence that invalid requests do not call runtime.now or create paths;
- focused and full verification output;
- a workflow execution trace; and
- deviations where the workflow was ambiguous, redundant, or skipped.

- [ ] **Step 6: Write the exercise**

Learners execute workflow-v1 on the fresh task or prepared dossier, recording
where the workflow was followed, impossible, ambiguous, or overridden. They
revise the workflow only when the evidence shows a recurring decision or risk.

- [ ] **Step 7: Write acceptance checks**

A complete artifact:

- can be followed by another engineer;
- names decision rights, stop conditions, and independent checks;
- completes or analyzes the fresh task;
- records deviations and external results;
- identifies one keep, revise, or remove decision; and
- makes no claim of general performance improvement from one execution.

- [ ] **Step 8: Add discussion and optional depth**

Async prompt: "Which workflow step prevented a plausible failure, and which
step merely moved effort from the agent to the human?"

Optional depth: define the minimum repeated evidence that would justify
automating one manual gate.

- [ ] **Step 9: Validate and commit Unit 5**

Run the ten-heading structural check against 05-reusable-workflows.md. Confirm
the evidence pack contains the invalid-request matrix, both solution
approaches, verification output, and workflow deviations.

~~~bash
git add modules/01-agentic-engineering-fundamentals/units/05-reusable-workflows.md modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-05-workflow-validation.md
git commit -m "docs: author Module 01 workflow unit"
~~~

---

### Task 9: Replace the core lab and preserve the advanced experiment

**Files:**

- Modify: modules/01-agentic-engineering-fundamentals/lab.md
- Create: modules/01-agentic-engineering-fundamentals/advanced-lab.md

**Interfaces:**

- Consumes: all five units, templates, and evidence packs.
- Produces: one core completion path and one explicitly elective advanced path.

- [ ] **Step 1: Rewrite lab.md as the core artifact-chain lab**

Include:

- module outcome;
- 405-minute budget;
- setup and privacy boundaries;
- the two immutable ledger commits;
- isolated-checkout instructions;
- evidence storage outside the code worktree;
- the five artifact sequence;
- live and prepared paths;
- async or solo decision record;
- completion rubric; and
- stop and recovery rules.

State that unit exercises are the lab stages; the core lab does not add a
sixth implementation task.

- [ ] **Step 2: Write reproducible setup commands**

Use task-specific paths:

~~~bash
export MODULE01_LEDGER_REPO="$(cd ../agent-experiment-ledger && pwd -P)"
export MODULE01_WORK_ROOT="$(mktemp -d /tmp/module-01-work.XXXXXX)"
git -C "$MODULE01_LEDGER_REPO" rev-parse bb65b5cec8c96c3ba3d89b0025473561c7c8146f
git -C "$MODULE01_LEDGER_REPO" rev-parse 2c498f616583d1fd6aeeaa381552b47acdb71ab7
~~~

State that these commands run from the curriculum repository root and require
the ledger checkout in the named sibling directory. Learners using another
layout set the same task-specific variables to their resolved absolute paths.
For the internal pilot, the facilitator distributes or grants access to the
sibling repository. Public checkout instructions belong to the later release
plan.

- [ ] **Step 3: Define core completion**

Require:

- five artifacts marked complete;
- one async, synchronous, or solo decision record;
- no open safety violation;
- external verification for Units 4 and 5; and
- explicit uncertainty and confounders.

Do not require the advanced lab.

- [ ] **Step 4: Move the original controlled experiment into advanced-lab.md**

Preserve:

- frozen task and immutable baseline;
- three context treatments under one harness/model;
- strongest treatment across two harnesses;
- fresh-task workflow validation;
- isolated worktrees;
- declared permissions, time, and spend;
- independent diff review;
- acceptance and regression checks; and
- separation of observations, explanations, confounders, and decisions.

- [ ] **Step 5: Correct the advanced-lab claims**

State:

- five conditions are not statistical replication;
- the default output is an exploratory report;
- repeat each condition with randomized order when estimating treatment
  effects;
- prior familiarity with Agent Experiment Ledger is a confounder;
- a fresh fixture is preferred for provider comparison; and
- the learner chooses whether the additional time and tool cost are justified.

- [ ] **Step 6: Verify core and advanced contracts are disjoint**

Run:

~~~bash
rg -n "optional|elective|exploratory" modules/01-agentic-engineering-fundamentals/advanced-lab.md modules/01-agentic-engineering-fundamentals/lab.md
~~~

Expected: both files explicitly label the advanced path non-core.

Run:

~~~bash
rg -n "five total runs|three context treatments" modules/01-agentic-engineering-fundamentals/lab.md
~~~

Expected: no matches.

- [ ] **Step 7: Commit the lab split**

~~~bash
git add modules/01-agentic-engineering-fundamentals/lab.md modules/01-agentic-engineering-fundamentals/advanced-lab.md
git commit -m "docs: split Module 01 core and advanced labs"
~~~

---

### Task 10: Build async collaboration and facilitation

**Files:**

- Create: modules/01-agentic-engineering-fundamentals/workshop.md
- Create: modules/01-agentic-engineering-fundamentals/facilitator-guide.md

**Interfaces:**

- Consumes: all unit artifacts, evidence packs, and team-decision-template.md.
- Produces: platform-neutral async, synchronous, and solo learning paths.

- [ ] **Step 1: Write the async-first collaboration path**

Define:

1. learner artifact summary;
2. evidence-backed challenge;
3. author response or revision;
4. facilitator synthesis; and
5. decision record.

Provide copyable Markdown for each stage. State that peer availability cannot
block completion.

- [ ] **Step 2: Write the optional 75-minute meeting**

Use:

- calibration: 10 minutes;
- paired failure diagnosis: 15 minutes;
- artifact comparison: 20 minutes;
- adversarial workflow review: 15 minutes;
- team decision: 10 minutes; and
- debrief: 5 minutes.

Define facilitator, evidence presenter, skeptic, and recorder roles.

- [ ] **Step 3: Write group-size variants**

Cover:

- solo: prepared critique plus solo decision record;
- two people: reciprocal critique;
- three to eight people: one group with rotating roles; and
- more than eight: breakout groups with one synthesis recorder per group.

- [ ] **Step 4: Write facilitator preparation**

Require:

- verify source freshness;
- verify the ledger commits exist;
- run setup and focused checks;
- review privacy rules;
- select live or prepared path;
- publish timeboxes;
- create async threads; and
- decide how course feedback will be captured.

- [ ] **Step 5: Add evaluation guidance**

For every artifact, include one strong and one weak example. The weak examples
must expose:

- unsupported causal diagnosis;
- context quantity mistaken for quality;
- duplicated project knowledge;
- provider ranking from an N=1 case; and
- workflow completion claimed without independent verification.

- [ ] **Step 6: Add recovery procedures**

Cover:

- missing provider access;
- setup or dependency failure;
- expired source link;
- live run exceeding its timebox;
- private evidence accidentally selected;
- absent peers; and
- disagreement without decisive evidence.

- [ ] **Step 7: Verify platform neutrality**

Run:

~~~bash
rg -n "must use Slack|must use Teams|must use GitHub|requires Codex|requires Claude" modules/01-agentic-engineering-fundamentals/workshop.md modules/01-agentic-engineering-fundamentals/facilitator-guide.md
~~~

Expected: no matches.

- [ ] **Step 8: Commit collaboration material**

~~~bash
git add modules/01-agentic-engineering-fundamentals/workshop.md modules/01-agentic-engineering-fundamentals/facilitator-guide.md
git commit -m "docs: add Module 01 async facilitation"
~~~

---

### Task 11: Assemble the learner entry point and repository guidance

**Files:**

- Modify: modules/01-agentic-engineering-fundamentals/curriculum.md
- Modify: README.md

**Interfaces:**

- Consumes: every completed learner-facing Module 01 file.
- Produces: a coherent start-to-finish navigation path without duplicated
  teaching.

- [ ] **Step 1: Rewrite curriculum.md as the Module 01 start page**

Include:

- who the module is for;
- what "free" means;
- prerequisites;
- setup and privacy summary;
- five-unit sequence and 405-minute budget;
- links to each unit, template, lab, workshop, facilitator guide, sources, and
  optional advanced lab;
- the teach/touch/defer MEGA coverage matrix from the approved spec;
- completion rules;
- async, synchronous, and solo paths; and
- distribution status.

Do not duplicate unit lessons or source metadata.

- [ ] **Step 2: Add a concise "How to take the course" section to README.md**

Define:

1. read the module start page;
2. complete units in order;
3. retain sanitized artifacts outside code worktrees;
4. participate asynchronously or use the solo fallback;
5. use the meeting only when useful; and
6. treat the advanced lab as elective.

State that the curriculum is being prepared for public distribution but the
sample-project release and licenses are not yet finalized.

- [ ] **Step 3: Verify every learner-facing link resolves**

Run:

~~~bash
rg -o "\]\([^)]*\.md[^)]*\)" modules/01-agentic-engineering-fundamentals/curriculum.md README.md
~~~

Open every reported relative path from the file that contains it. Fix broken
anchors or filenames.

- [ ] **Step 4: Verify the coverage matrix remains complete**

Check for all 27 public agenda labels from the approved spec. Count:

- 18 Teach rows; and
- 9 Touch rows.

No public Week 1 agenda label may disappear during condensation.

- [ ] **Step 5: Verify learner-facing status language**

Run:

~~~bash
rg -n "verified|approved|better than|equivalent to MEGA|universal winner" README.md modules/01-agentic-engineering-fundamentals/curriculum.md
~~~

Every match must avoid claiming that the unpiloted module is verified,
approved, superior, or equivalent to unreleased paid content.

- [ ] **Step 6: Commit navigation**

~~~bash
git add README.md modules/01-agentic-engineering-fundamentals/curriculum.md
git commit -m "docs: assemble Module 01 learner path"
~~~

---

### Task 12: Pilot the written instructions and complete the lead self-review

**Files:**

- Modify: modules/01-agentic-engineering-fundamentals/codex-review.md
- Modify: modules/01-agentic-engineering-fundamentals/claude-review.md
- Modify: modules/01-agentic-engineering-fundamentals/brief.md
- Modify: modules/01-agentic-engineering-fundamentals/curriculum.md
- Modify: ROADMAP.md
- Modify: any Module 01 learner or facilitator file whose validation fails

**Interfaces:**

- Consumes: the complete curriculum from Tasks 1-11.
- Produces: a reproducibly checked draft ready for Claude's independent
  adversarial review.

- [ ] **Step 1: Run the global structural checks**

Run:

~~~bash
git diff --check
rg -n -i "T[B]D|T[O]DO|F[I]XME|f[i]ll this in|l[o]rem ipsum" modules/01-agentic-engineering-fundamentals README.md
rg --files modules/01-agentic-engineering-fundamentals/units modules/01-agentic-engineering-fundamentals/exercises
~~~

Expected:

- no whitespace errors;
- no unfinished learner content;
- five unit files;
- six templates; and
- six evidence-pack files including the evidence README.

- [ ] **Step 2: Verify the ledger baselines**

In the local Agent Experiment Ledger checkout run:

~~~bash
git rev-parse bb65b5cec8c96c3ba3d89b0025473561c7c8146f
git rev-parse 2c498f616583d1fd6aeeaa381552b47acdb71ab7
pnpm install --frozen-lockfile
pnpm check
pnpm test
pnpm build
~~~

Expected:

- both commits resolve;
- the reference checkout passes type-check, full tests, and build; and
- any baseline limitation used by the exercises is reproduced from an
  isolated checkout rather than assumed from the final code.

- [ ] **Step 3: Execute every prepared path exactly as written**

For each unit:

- start with only the stated learner context;
- use the documented timebox;
- copy the artifact template;
- complete the prepared case;
- run every listed command;
- compare output with the evidence pack; and
- record unclear instructions, missing inputs, false-positive acceptance, and
  actual elapsed time.

Revise the affected unit, template, evidence pack, or lab immediately.

- [ ] **Step 4: Run one live path for Units 4 and 5**

Use disposable isolated checkouts at the exercise baseline. Demonstrate:

- the Unit 4 failure test fails before the repair and passes after the
  reference repair;
- the Unit 5 invalid-request test fails before the repair and passes after the
  reference repair;
- pnpm check, pnpm test, and pnpm build pass at the reference revision; and
- learner evidence stays outside both worktrees.

- [ ] **Step 5: Run a fresh-context learner simulation**

Dispatch a reviewer with no authoring history. Give it only:

- curriculum.md;
- one assigned unit;
- the linked template;
- the linked evidence pack;
- lab.md; and
- access to the local ledger checkout.

Ask it to follow the learner path, stop at ambiguity, and return:

- blocking instructions;
- missing prerequisites;
- estimated time;
- acceptance checks that could pass bad work; and
- unnecessary material.

Fix every blocker and major finding or record an evidence-backed rejection in
codex-review.md.

- [ ] **Step 6: Run an independent curriculum critique**

Give a second reviewer the approved spec, MEGA snapshot, brief, curriculum,
units, lab, workshop, facilitator guide, sources, and rubric. Ask for ranked
findings on coverage, correctness, teachability, workload, assessment,
provider neutrality, privacy, and maintenance.

Record an accept, reject, or defer disposition for every finding. Add a
DECISIONS.md entry only for a material disagreement or scope change.

- [ ] **Step 7: Complete the lead rubric**

Copy the worksheet structure from evals/curriculum-rubric.md into
codex-review.md and complete:

- metadata;
- subagent model, effort, selection rationale, and escalation history;
- every hard gate;
- all eight scored dimensions with evidence;
- source audit;
- lab audit;
- ten adversarial questions;
- findings and dispositions; and
- verdict.

The lead handoff requires:

- at least 32/40;
- no dimension below 3;
- technical correctness and lab validity at least 4;
- no open blocker; and
- no open major.

- [ ] **Step 8: Refresh statuses for review handoff**

Set:

- brief.md status to "in-review";
- curriculum.md status to "in-review";
- ROADMAP.md Module 01 status to "in-review";
- codex-review.md current handoff to the exact revision being submitted; and
- claude-review.md current state to "ready for independent adversarial review".

Do not fill Claude's research, scores, findings, verdict, or verification.

- [ ] **Step 9: Run final repository checks**

Run:

~~~bash
git diff --check
git status --short
git log --oneline --decorate -12
~~~

Review all learner links manually. Re-open every source whose freshness window
would expire before the planned review date.

- [ ] **Step 10: Commit the review-ready module**

~~~bash
git add README.md ROADMAP.md DECISIONS.md modules/01-agentic-engineering-fundamentals
git commit -m "docs: prepare Module 01 for adversarial review"
~~~

Verify that .DS_Store changes are not staged.

- [ ] **Step 11: Stop for Claude and learner review**

Report:

- exact commit;
- checks run and outcomes;
- pilot timings;
- accepted, rejected, and deferred review findings;
- remaining distribution prerequisites; and
- the request for Claude's independent review.

Do not mark the module verified or approved.
