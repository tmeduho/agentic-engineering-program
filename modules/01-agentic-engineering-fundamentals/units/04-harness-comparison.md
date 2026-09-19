# Unit 4 — Harness Controls and Independent Verification

**Core timebox:** 90 minutes: lesson 12 minutes; required reading 10 minutes;
setup and control inventory 10 minutes; bounded run or dossier review 35
minutes; verification, control assessment, and proposal 18 minutes; async post
5 minutes.

**Source map:** [S08](../sources.md#technical-sources) is the sole required
reading. S01, S03, and S07 are optional supporting material. P01 supplies the
prepared case at exercise baseline `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`
and reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7`.

## Engineering question

Which harness controls bound this engineering task, what evidence establishes
completion, and which configuration change is worth testing next?

## Learning outcomes

By the end of this unit, you can:

- inventory the harness surfaces that assemble context, route tools, carry
  state, constrain authority, expose progress, and determine recovery;
- evaluate a bounded run or prepared dossier against an explicit
  harness-control and independent-verification contract while preserving a
  frozen task, baseline, acceptance conditions, and authority boundary;
- distinguish repository evidence from a prepared dossier, observations from
  mechanisms, and unavailable telemetry from measured data; and
- propose one falsifiable configuration change, explicitly untested, without
  claiming a measured configuration effect or a provider benchmark.

## Lesson

A harness is the execution system surrounding a model call. It decides what
the model sees, what action shapes are available, where actions run, what
persists between turns, when a person must decide, and what counts as finished.
The model is therefore one variable in the delivered outcome, not a complete
explanation of it. S01’s [“The reusable part is the agent loop”](https://developers.openai.com/blog/codex-as-a-platform#the-reusable-part-is-the-agent-loop)
describes this division for Codex. Its details are product-specific and must
not be assumed for another harness.

Use this inventory to assess the controls for the selected evidence path:

| Harness dimension | Engineering question | Failure mode if omitted |
| --- | --- | --- |
| Context assembly and compaction | Which task text, repository facts, summaries, and tool results enter the next turn; what is compacted or dropped? | A stale summary, hidden ambient instruction, or lossy compaction changes the effective task. |
| Tool schemas, routing, and observations | What arguments can the model request; which implementation receives them; what result or error returns? | A model-visible tool name does not prove that the routed command had the expected authority or result. |
| Task and session state | What survives retries, context resets, handoff, or a new session? | A fresh session may lose the plan, while a resumed one may inherit stale state. |
| Sandbox, filesystem, network, and command authority | Which paths, commands, credentials, processes, and domains can execute? | “The agent can edit” hides whether it can install, publish, read outside the worktree, or reach a service. |
| Approval policy | Which requests pause for a human, and who can widen scope or dependencies? | An intervention becomes an unrecorded configuration change. |
| Interface effects | Does the agent work through a CLI, editor, chat, API, queue, or automation surface? | The interface can change discovery, visibility, interruption, and review ergonomics without changing the model. |
| Progress and handoff | What status, evidence, and unresolved work become visible to a person or successor? | A fluent completion message substitutes for state inspection or a handoff omits the reason to stop. |
| Retry, recovery, and termination | Which failures retry, what state is retained, and what time, attempt, safety, or ambiguity condition stops work? | Retrying can repeat an unsafe mutation; cleanup may not run after abrupt termination. |
| Telemetry and missing measurements | What records wall time, tool calls, approvals, cost, failures, and environment? | Missing token or cost data gets silently estimated, or a trace from another configuration is borrowed. |
| Stable interfaces versus stale scaffolding | Which controls are contractually stable and which encode an old model limitation? | Added structure persists after its load-bearing assumption has changed. |

S03’s [“Why naive implementations fall short”](https://www.anthropic.com/engineering/harness-design-long-running-apps#why-naive-implementations-fall-short)
is a case study, not a general performance claim. Its later “Iterating on the
harness” section argues for removing one component at a time because harness
assumptions can become stale as models change. That supports a bounded,
representative comparison; it does not establish that more scaffolding wins.

For each of the ten dimensions, record the configured or observed value, its
evidence, uncertainty, and consequence for this task. Distinguish a written
instruction from a configured enforcement mechanism and from observed
enforcement. “No network” in a task prompt specifies authority; it does not
prove a sandbox blocked transport. A missing historical control is `unknown`,
not permission to infer it from correct source code.

Preserve the task, repository revision, acceptance conditions, authority, and
stop rule. Record model/version and stochastic sampling, harness/version,
context and session history, filesystem and tool environment, setup state,
interface, human intervention, and available telemetry as limits on the case.
An observation is “the focused test passed” or “the agent requested an
approval.” “This approval policy improved correctness” is a mechanism
hypothesis requiring a separate comparison. This unit evaluates one case; its
live and prepared paths are alternative evidence paths, not configurations in
an experiment. A correct implementation does not establish which harness
control caused it.

## Required reading

For 10 minutes, read two discrete S08 excerpts: [“Permission
system”](https://code.claude.com/docs/en/permissions#permission-system),
stopping before “Manage permissions,” and [“How permissions interact with
sandboxing”](https://code.claude.com/docs/en/permissions#how-permissions-interact-with-sandboxing).
For the second excerpt, stop at the next heading of the same or higher level.
Do not read the intervening or following reference material as part of the
required span.
Record one control that is an approval rule and one that is a sandbox boundary;
say what evidence would show that they interact.

S08 is current **Claude Code** documentation, checked in `sources.md`. It
documents product-specific modes, permission rules, working directories, and
sandbox interactions. It does not establish that another agent product has the
same rule language, precedence, prompts, filesystem boundary, or network
behavior. For optional comparison, S07’s [“Settings precedence”](https://code.claude.com/docs/en/settings#settings-precedence)
documents configuration precedence for that product only.

## Worked example

The prepared [Unit 4 case study](../exercises/evidence/unit-04-harness-case-study.md)
uses the same initialization-publication boundary introduced in Unit 1. At the
P01 baseline, `initializeLedger` creates the destination and `experiments/`
incrementally. The reference adds hidden same-parent staging, validates the
staged ledger, then renames it into publication. Its deterministic test injects
a failure immediately before publication, asserts that neither destination nor
staging remains, retries, and checks that the retry is blocker-free.

The **prepared path** lets a learner audit two implementation strategies and
the evidence needed for acceptance without inventing a historical agent run.
The dossier has no model identity, harness version, wall time, tool trace, or
intervention record; those values are `unknown`. Its source/test evidence
supports a publication property, not an effect of a harness configuration.

For example, a learner might propose a completion gate that requires an
independent evaluator result before recording success. The target failure is
accepting existing green tests as evidence for the new publication behavior.
The expected observation is a completion decision withheld when that result
is absent; a success decision without it falsifies the gate's enforcement
claim. The proposal must name who or what enforces the gate and hold task,
baseline, model, authority, and stop rule constant in a future test. This is
an **untested proposal**, not evidence that the historical repair used the
gate or that the change improves outcomes. Select your own supported change;
do not claim an existing required gate is a new treatment unless you define
the distinct mechanism you would change.

## Exercise

Use [harness-case-study-template.md](../exercises/harness-case-study-template.md)
and store your completed artifact outside the P01 code-under-test worktree.
Choose one path. Stop after the 35-minute task limit or after two failed
implementation approaches, whichever comes first; retain the state and write
the stop reason rather than extending the run.

**Frozen task, baseline, and acceptance.** Create an isolated, disposable
checkout at `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`. Use this text without
editing it:

```text
Make ledger initialization publish no partial ledger when execution fails
immediately before publication, remove unpublished staging, and permit a clean
retry. Preserve the existing CLI and error contracts. Add a deterministic
failure-injection test. Do not add dependencies or change unrelated lifecycle
behavior. Stop after 35 minutes or two failed implementation approaches.
```

Live acceptance is behavior-level, not a fixed reference-test API: the
evaluator-owned post-run test must inject deterministic failure immediately
before **candidate publication** through the candidate's documented test seam,
observe rejection/failure, observe an absent destination and no unpublished
staging entry, retry cleanly, and observe a blocker-free ledger check. The
candidate's agent-authored test is reviewed separately. The evaluator may adapt
only to the documented deterministic injection seam and may not change
production behavior. If the candidate exposes no observable seam, acceptance
fails. Preserve seam/test-design variance as a confounder.

**Live path — one bounded run.** Use one available coding agent with
the frozen task, P01's `AGENTS.md` and `CLAUDE.md` under the selected harness's
normal repository discovery, workspace-only writes, no network authority
during the measured run, and approval required for a dependency or scope
change. The two instruction files exist at both P01 pins and differ by one
review-verification instruction in `CLAUDE.md`. Record which file or files the
harness actually loaded, their precedence when observable, and whether that
known divergence is an uncontrolled difference; use `unknown` rather than
assuming a load rule. Before starting the measured run:

1. Create the isolated checkout and record its absolute path, baseline SHA,
   OS/runtime, Node version, pnpm version, and clean Git status.
2. Run `pnpm install --frozen-lockfile` during **setup**, before timing the
   agent. Record package-store output and whether it reports downloads or a
   network attempt. If the store is cold and setup needs network access, record
   that separately; do not grant network to the measured task.
3. Run `pnpm check`, `pnpm test`, and `pnpm build` before mutation. Preserve
   command, exit code, and result location.
4. Do **not** preseed the evaluator-owned named acceptance test before the
   measured agent run. The frozen task makes test design part of the learner or
   agent work. Preserve the agent-authored test(s) and test-design rationale as
   an outcome; different tests are a recorded confounder, not grounds to alter
   the task.
5. Record agent/harness and visible model/settings, context sources including
   actual instruction-file loading and precedence, permissions, approval
   policy, start time, interventions, each failed approach, and stop reason.
   Mark unavailable telemetry `unknown`.
6. After the producing session stops, an independent verifier writes or runs
   an evaluator-owned behavior-level test through the candidate's documented
   deterministic injection seam. The verifier is a second engineer or a
   fresh-context agent without access to the producing conversation; the
   producer's conclusion is not evidence. The evaluator test remains withheld
   until this post-run phase. It must inject failure immediately before
   candidate publication; assert rejection/failure, absent destination, no
   unpublished staging entry, clean retry, and blocker-free `checkLedger`.
   The verifier may inspect the candidate checkout and documented seam, may
   adapt only to that seam, and must not change production behavior. If no
   independent verifier is available, switch to the prepared path and record
   that live acceptance was not completed. If no observable seam exists, mark
   acceptance failed. Record seam and test-design variance as confounders,
   review the agent-authored test separately, then run `pnpm check`,
   `pnpm test`, and `pnpm build` and inspect scope, cleanup, publication
   boundary, and unrelated changes.

**Prepared path — dossier analysis.** Review the linked prepared case study.
Retain its actual repository evidence, its prepared review, and its unknown
telemetry in the template.
Do not supply a model, provider, prompt, elapsed time, token count, or tool
trace that the dossier does not contain. Its completion contract is critical
analysis: analyze the exact reference test as evidence for `2c498f6`, the
frozen behavior invariants, and how an independent evaluator would adapt a
post-run test to a documented candidate seam. Explicitly record that the
dossier contains no candidate run, candidate seam, evaluator post-run test,
or focused candidate result. Keep any abandoned live attempt separately
labeled; it does not supply the dossier's missing evidence. Do not call this
path `executed`.

**Control assessment and proposal — both paths.** Complete the ten-dimension
inventory in the template within the existing setup/review and verification
allocations. For each dimension, cite the configured or observed value and
evidence, or write `unknown`; explain the uncertainty and its consequence.
For a prepared path, separate the unit's required controls from the unknown
historical configuration. Assess these three requests without executing them:

1. An agent requests an in-scope source edit in the disposable checkout.
2. An agent requests network access to install a new dependency during the run.
3. An agent claims completion using only the existing green baseline tests.

For each, name the governing control, required evidence, and permitted next
action or stop/escalation. Then propose one configuration change naming its
target failure, expected observation, falsifier, enforcement mechanism, and
held constants. Mark it `untested`; do not implement or measure it in this
unit. Keep candidate observations, reference evidence, and the proposal in
separate sections. Unit 3's disposable map may inform a proposal only if its
relevance to initialization is justified; its discovery result does not prove
an implementation benefit or approve the map for P01.

For either path, use the baseline source/test and reference diff as external
evidence. Do not execute against P01’s main checkout, do not publish a
repository, and do not retain raw transcripts, credentials, proprietary
prompts, or absolute private paths in the shared artifact.

## Deliverable

A completed harness-control case study using
[harness-case-study-template.md](../exercises/harness-case-study-template.md).
It must name the frozen task, baseline, acceptance checks, ten-dimension
control assessment, permissions, setup/network record, observed outcomes,
external test/diff evidence, independent review, stop reason, confounders,
uncertainty, three request decisions, and one untested configuration-change
proposal. Mark the selected path `executed` or `critically analyzed` and label
each evidence item's provenance; retained partial live work does not make
prepared completion executed.

Use `unknown` for unavailable telemetry. Keep the observation/mechanism split
visible: “the named test passed at the reference” is an observation; “staging
plus rename caused all future interruptions to be safe” overstates the test.
Retain a raw evidence reference for every material claim.

## Acceptance checks

The artifact is complete only if it:

- preserves the exact task, baseline, acceptance conditions, authority boundary,
  and stop rule for the selected path;
- records both P01 instruction files, which file or files the harness actually
  loaded, their precedence when observable, and the known one-line divergence
  as controlled, uncontrolled, or `unknown`;
- assesses all ten harness dimensions with configured/observed value, evidence,
  uncertainty, and consequence, distinguishing instructions from enforcement
  and historical unknowns from the unit's required controls;
- answers all three request scenarios with a governing control, evidence
  requirement, and next action or escalation; network/dependency expansion
  requires stopping for human authorization, and baseline green tests alone
  cannot establish the new behavior;
- separates candidate observations, reference evidence, and one explicitly
  untested configuration-change proposal naming its target failure, expected
  observation, falsifier, enforcement mechanism, and held constants;
- records setup separately from the measured run, including package-store and
  network observations, and gives the measured task no network authority;
- for a live path, includes the evaluator-owned behavior-level post-run test,
  its documented candidate seam and focused result, final `pnpm check`,
  `pnpm test`, and `pnpm build` evidence, destination/staging inspection,
  agent-authored test review, and an external diff or source review;
- for a prepared path, critically analyzes the reference test, frozen behavior
  invariants, and evaluator adaptation to a documented candidate seam, and
  explicitly records that the dossier contains no candidate run, seam,
  evaluator test, or focused candidate result; it may cite prepared/reference
  full verification but does not substitute it for live acceptance;
- identifies the independent reviewer as a second engineer or fresh-context
  agent without the producing conversation, or clearly labels the prepared
  review; for live work, records that the evaluator test was withheld until
  after the producer stopped; and records permissions, approval events,
  interventions, stop reason, CPU, RAM, disk, concurrency,
  resource-enforcement, and infrastructure failure/exclusion data as observed
  or `unknown`;
- marks unavailable model, tool, cost, time, or token telemetry as `unknown`
  rather than estimating it;
- separates observations from mechanism hypotheses, records confounders and
  disconfirming evidence, and limits conclusions to this task and recorded
  configuration and evidence path; and
- does not call the result a provider benchmark, a universal harness result, or
  evidence that one execution improved a workflow.

Mark it `revise` if it changes the frozen task, baseline, acceptance, or
authority; treats a prepared dossier as a learner-run
measurement; omits setup-network evidence; or attributes a result to the
harness without separating model, context, permissions, and stochastic effects.
Mark it `revise` if it forces the reference `publicationHooks.beforePublish`
API onto a candidate, changes production behavior to create a seam, or accepts
a live candidate with no observable deterministic publication seam. Mark a
prepared artifact `revise` if it claims a candidate seam, evaluator result, or
execution that the dossier does not contain. Mark either path `revise` if it
treats the two evidence paths as measured configurations, claims a measured
effect for the proposal, or infers historical harness enforcement from the
reference implementation's correctness.

## Async discussion

Post one control assessment, its evidence type and strongest uncertainty,
and the falsifier for your untested proposal. Then answer: **What evidence
would show that this control is enforced, and what additional evidence would
be needed to claim it changes outcomes?** Challenge one peer's claim; working
solo, write the strongest alternative explanation.

## Optional depth

Read S08's permission-rule syntax, wildcards, tool-specific rules, hooks, and
working-directory material. Map each relevant product control to the inventory
above without assuming that another harness implements the same rule language
or enforcement boundary.

Design, but do not run, a replicated experiment. Specify at least three fresh
repetitions per configuration, fixed model/version where visible, fixed task
and baseline, fixed authority and network state, fresh isolated worktrees,
randomized run order, recorded context/session state, declared telemetry
schema, a stopping and exclusion rule, independent diff review, and a
predeclared decision rule. State which remaining differences cannot be
controlled and why a replicated result would still be local to the selected
task, filesystem, harness/version, and model configuration.
