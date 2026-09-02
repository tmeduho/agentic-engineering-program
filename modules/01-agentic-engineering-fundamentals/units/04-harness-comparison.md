# Unit 4 — Harness Comparison as an N=1 Case Study

**Core timebox:** 90 minutes: lesson 12 minutes; required reading 10 minutes;
setup and prediction 10 minutes; bounded run or dossier review 35 minutes;
verification and comparison 18 minutes; async post 5 minutes.

**Source map:** [S08](../sources.md#technical-sources) is the sole required
reading. S01, S03, and S07 are optional supporting material. P01 supplies the
prepared case at exercise baseline `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`
and reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7`.

## Engineering question

When two agent-system configurations differ, which observed difference is
actually useful for an engineering decision, and which explanation would be
premature?

## Learning outcomes

By the end of this unit, you can:

- inventory the harness surfaces that assemble context, route tools, carry
  state, constrain authority, expose progress, and determine recovery;
- run or review one bounded comparison while preserving a frozen task,
  baseline, acceptance conditions, and authority boundary;
- distinguish repository evidence from a prepared dossier, observations from
  mechanisms, and unavailable telemetry from measured data; and
- make a local keep, revise, or further-test decision without calling an N=1
  result a model, harness, or provider benchmark.

## Lesson

A harness is the execution system surrounding a model call. It decides what
the model sees, what action shapes are available, where actions run, what
persists between turns, when a person must decide, and what counts as finished.
The model is therefore one variable in the delivered outcome, not a complete
explanation of it. S01’s [“The reusable part is the agent loop”](https://developers.openai.com/blog/codex-as-a-platform#the-reusable-part-is-the-agent-loop)
describes this division for Codex. Its details are product-specific and must
not be assumed for another harness.

Use this inventory before comparing configurations:

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

Comparison needs a causal discipline. Hold the task, repository revision,
acceptance conditions, authority, and stop rule constant. Name exactly one
intended changed dimension. Then record unavoidable differences: model/version
and stochastic sampling, harness/version, permission and approval policy,
context and session history, filesystem and tool environment, setup state,
interface, human intervention, and available telemetry. An observation is
“the focused test passed” or “the agent requested an approval.” “The
orientation map caused the result” is a mechanism hypothesis; it needs
counterfactual or replicated evidence. An N=1 comparison can justify a local
workflow choice for this task. It cannot isolate model from harness or
establish provider superiority.

## Required reading

Read S08, [“Permission system”](https://code.claude.com/docs/en/permissions#permission-system)
through [“How permissions interact with sandboxing”](https://code.claude.com/docs/en/permissions#how-permissions-interact-with-sandboxing), for 10 minutes.
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

The pack deliberately uses **Configuration B: prepared anonymous dossier**.
That is a permitted solo fallback, not an agent run and not a provider
benchmark. It lets the learner audit two implementation strategies without
inventing a second paid-provider trace. The intended changed dimension is the
evidence source: live bounded implementation work in A versus prepared,
sanitized implementation material in B. This is not a controlled performance
comparison. B lacks a model identity, harness version, wall time, tool trace,
and intervention record; all are `unknown`. Those asymmetries are recorded,
not normalized away.

Unit 3’s proposed orientation map remains a candidate context input, not an
approved P01 artifact. A future comparison may instead change only **context
treatment** by providing that map in a fresh session. It must preserve the
same frozen task and authority, disclose the map’s orientation advantage and
maintenance cost, and never merge the exercise map into P01.

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

**Configuration A — live, bounded run.** Use one available coding agent with
the frozen task, P01 `AGENTS.md`, normal repository discovery, workspace-only
writes, no network authority during the measured run, and approval required
for a dependency or scope change. Before starting the measured run:

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
5. Record agent/harness and visible model/settings, context sources,
   permissions, approval policy, start time, interventions, each failed
   approach, and stop reason. Mark unavailable telemetry `unknown`.
6. After the measured run, an independent verifier writes or runs an
   evaluator-owned behavior-level test through the candidate's documented
   deterministic injection seam. It must inject failure immediately before
   candidate publication; assert rejection/failure, absent destination, no
   unpublished staging entry, clean retry, and blocker-free `checkLedger`.
   The verifier may adapt only to that seam and must not change production
   behavior. If no observable seam exists, mark acceptance failed. Record seam
   and test-design variance as confounders, review the agent-authored test
   separately, then run `pnpm check`, `pnpm test`, and `pnpm build` and inspect
   scope, cleanup, publication boundary, and unrelated changes.

**Configuration B — prepared dossier fallback.** Review the linked prepared
case study instead of claiming a live second run. It changes only the named
evidence source to a prepared anonymous dossier. Copy its actual repository
evidence, its prepared review, and its unknown telemetry into the template.
Do not supply a model, provider, prompt, elapsed time, token count, or tool
trace that the dossier does not contain.

For either path, use the baseline source/test and reference diff as external
evidence. Do not execute against P01’s main checkout, do not publish a
repository, and do not retain raw transcripts, credentials, proprietary
prompts, or absolute private paths in the shared artifact.

## Deliverable

A completed N=1 case study using
[harness-case-study-template.md](../exercises/harness-case-study-template.md).
It must name the frozen task, baseline, acceptance checks, held constants, one
changed dimension, configuration inventory, permissions, setup/network record,
observed outcomes, external test/diff evidence, independent review, stop
reason, confounders, and uncertainty. Mark whether it contains a live learner
run, prepared comparison material, or both.

Use `unknown` for unavailable telemetry. Keep the observation/mechanism split
visible: “the named test passed at the reference” is an observation; “staging
plus rename caused all future interruptions to be safe” overstates the test.
Retain a raw evidence reference for every material claim.

## Acceptance checks

The artifact is complete only if it:

- holds the exact task, baseline, acceptance conditions, and authority boundary
  constant for the stated comparison;
- names one intended changed dimension, or explicitly uses the prepared dossier
  and records every unavoidable live-versus-prepared difference;
- records setup separately from the measured run, including package-store and
  network observations, and gives the measured task no network authority;
- includes the evaluator-owned behavior-level post-run test, its documented
  candidate seam and focused result, final `pnpm check`, `pnpm test`, and
  `pnpm build` evidence, destination/staging inspection, agent-authored test
  review, and an external diff or source review;
- identifies the independent reviewer or clearly labels the prepared review,
  and records permissions, approval events, interventions, stop reason, CPU,
  RAM, disk, concurrency, resource-enforcement, and infrastructure
  failure/exclusion data as observed or `unknown`;
- marks unavailable model, tool, cost, time, or token telemetry as `unknown`
  rather than estimating it;
- separates observations from mechanism hypotheses, records confounders and
  disconfirming evidence, and limits conclusions to this task and recorded
  configurations; and
- does not call the result a provider benchmark, a universal harness result, or
  evidence that one execution improved a workflow.

Mark it `revise` if it changes task, baseline, acceptance, or authority while
calling the comparison controlled; treats a prepared dossier as a learner-run
measurement; omits setup-network evidence; or attributes a result to the
harness without separating model, context, permissions, and stochastic effects.
Mark it `revise` if it forces the reference `publicationHooks.beforePublish`
API onto a candidate, changes production behavior to create a seam, or accepts
a candidate with no observable deterministic publication seam.

## Async discussion

Post one observed difference, the evidence type, one mechanism hypothesis,
the strongest confounder, and the next evidence needed. Then answer:
**Which observed difference belongs to the harness, and what evidence would be
required to separate it from model or context effects?** Challenge one peer’s
claim; working solo, write the strongest alternative explanation.

## Optional depth

Design, but do not run, a replicated experiment. Specify at least three fresh
repetitions per configuration, fixed model/version where visible, fixed task
and baseline, fixed authority and network state, fresh isolated worktrees,
randomized run order, recorded context/session state, declared telemetry
schema, a stopping and exclusion rule, independent diff review, and a
predeclared decision rule. State which remaining differences cannot be
controlled and why a replicated result would still be local to the selected
task, filesystem, harness/version, and model configuration.
