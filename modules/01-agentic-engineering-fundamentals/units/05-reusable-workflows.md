# Unit 5 — Reusable Workflows

**Core timebox:** 60 minutes: lesson 10 minutes; required reading 10 minutes;
workflow construction 12 minutes; fresh-task execution or prepared fallback 20
minutes; validation and async post 8 minutes.

**Source map:** [S03](../sources.md#technical-sources) is the sole required
reading. S04 and S05 are optional, case-specific depth; P01 supplies the
frozen validation case at exercise baseline
`bb65b5cec8c96c3ba3d89b0025473561c7c8146f` and reference revision
`2c498f616583d1fd6aeeaa381552b47acdb71ab7`.

## Engineering question

What is the smallest workflow that another engineer can follow to deliver a
bounded change safely, retain evidence, and improve only when that evidence
justifies the added process?

## Learning outcomes

By the end of this unit, you can:

- turn the strongest supported practices from Units 1–4 into a bounded
  `workflow-v1`, with named decision rights, authority, stops, evidence, and
  independent gates;
- execute or analyze that workflow on a frozen report-validation task without
  treating agent completion text as acceptance evidence;
- distinguish a workflow step that prevents a recurring decision or risk from
  a preference, an unexplained correlation, or an adoption burden; and
- make one local keep, revise, or remove decision without claiming that one
  execution improved workflow or agent performance in general.

## Lesson

A workflow is a repeatable decision system, not a long prompt or a chronological
record of commands. Start with an outcome, its non-goals, and the loss if it is
wrong: a false report can inspect the wrong ledger, write an output where none
belongs, or make a nondeterministic result appear valid. Convert that risk into
falsifiable acceptance: named behavior, prohibited side effects, and a command
or state inspection that can contradict completion. A task that only says
“validate inputs” has no testable boundary; the frozen case below does.

Inspect before editing. Capture the repository revision and status, the
governing instructions, the task-relevant source and tests, the baseline
behavior, and the verification commands. Select context by authority and the
next decision rather than pasting every prior artifact: Unit 1 supplies the
model/loop/environment distinction, Unit 2 the context inventory and
observation-versus-explanation split, Unit 3 the source-of-truth and freshness
rules, and Unit 4 the authority and independent-review boundary. Record tools,
working directory, runtime, permissions, network state, and any unavailable
telemetry. A tool request is not evidence that the tool executed in the intended
environment.

Decision rights are part of the workflow. The human owns task framing, risk
tolerance, dependency or scope changes, destructive actions, and the final
acceptance decision. The agent may inspect and make workspace-local edits
within the declared task, but it cannot widen authority by interpreting
ambiguity in its favor. Name a stop condition before work begins. On a stop,
retain the current diff, command results, failed approaches, and unresolved
question; recover only through a defined rollback or fresh checkout; escalate
an ambiguity, failed acceptance, missing prerequisite, or requested authority
to the named human. A handoff must state the current state, evidence locations,
next safe action, and why work stopped.

Verification has separate gates. Acceptance checks the requested behavior;
regression checks the relevant suite and valid Markdown/CSV behavior; security
checks authority, input validation before filesystem access, contained output,
and privacy of retained evidence; independent review inspects the diff and can
reject the producing agent’s conclusion. Retain wall time, interventions,
failed approaches, changed files, command exit/results, environment, and
usage/cost only when observed. `unknown` is better evidence than a guessed
token count or a borrowed trace.

Usability is a production constraint. A workflow with too many manual gates
may merely move hidden work from an agent to a human, while a shortcut can hide
security or product risk. Evaluate each step against product outcome, user
impact, security boundary, and business constraints such as time, cost,
maintenance, review capacity, and adoption friction. Keep the smallest
evidence-backed durable change: a targeted test for a behavior, a narrow
instruction for a repeated process failure, an index for a proven discovery
problem, or a decision record for an approved constraint. Do not preserve a
step because it feels careful, because it appeared once in a successful run, or
because one unexplained correlation made it look useful.

## Required reading

Read S03, [“Why naive implementations fall short”](https://www.anthropic.com/engineering/harness-design-long-running-apps#why-naive-implementations-fall-short), through the section’s discussion of context resets and evaluator separation (10 minutes). Mark the observed failure modes, the added harness components, and the costs the article reports. Treat them as one Anthropic case study, not a universal workflow prescription.

S04 is optional when deciding whether a session, harness, and sandbox need
separate durable interfaces or recovery boundaries. S05 is optional when a
task crosses sessions and needs a clean-state or handoff practice. Neither is
required for this unit and neither proves that its patterns apply to the
learner’s agent, model, task, or environment.

## Worked example

The prepared [Unit 5 validation dossier](../exercises/evidence/unit-05-workflow-validation.md)
uses P01’s report service. At the frozen baseline, `generateReport` checks
format and experiment ID individually, then enters ledger/report work without
runtime validation of the complete request. The reference adds a strict
`ReportRequestSchema` and parses `{ root, experimentId, format, options }`
before `ledgerPaths`, `checkLedger`, `runtime.now`, or output resolution.

The reference test named `runtime-validates the complete report request before
ledger access or output` covers a non-boolean `includeGeneratedAt`, invalid
experiment ID, unsupported format, blank output path, and unknown option key.
Its evidence is narrower than a benchmark: it proves a request-validation
property for this repository and the seeded cases. The dossier records the
actual source/test provenance, a focused reference run, and the full reference
suite. It does not attribute the repair to an agent or provider, and it does
not claim a baseline test failure that was never run.

## Exercise

Create a copy of [workflow-template.md](../exercises/workflow-template.md)
outside the P01 code-under-test worktree. Derive `workflow-v1` from evidence in
your artifacts from Units 1–4, not from preferences alone. For **every** step,
state all six fields: inputs; authority; observable output; stop condition;
verifier; and retained evidence. Remove a step if its only support is personal
preference or one unexplained correlation. The remaining steps must still
cover framing, inspection, execution, recovery/escalation, gates, handoff, and
learning.

Choose one path. A live path uses a disposable, isolated P01 checkout at
`bb65b5cec8c96c3ba3d89b0025473561c7c8146f`; a prepared path analyzes the
linked dossier. Do not use P01’s main checkout. Store the workflow and its
evidence outside the code-under-test worktree. In either path, use this frozen
task without edits:

```text
Runtime-validate the complete report-generation request before ledger access,
runtime clock access, or output creation. Reject an invalid experiment ID,
unsupported format, blank output path, non-boolean includeGeneratedAt, and
unknown option keys through the stable invalid-record error path. Preserve
valid Markdown and CSV behavior. Do not add dependencies. Stop after 20
minutes or two failed approaches.
```

The live path permits only workspace-local edits and ordinary inspection and
verification commands. It denies network authority during the measured task;
setup is separate and any dependency or scope change requires human approval.
Inspect `AGENTS.md`, `src/reports/service.ts`, and `test/report.test.ts` at
both pins before changing code. Add or identify the acceptance test named
`runtime-validates the complete report request before ledger access or output`;
then run it, `pnpm check`, `pnpm test`, and `pnpm build`. Stop at 20 minutes or
after two failed approaches, preserve the evidence, and use the dossier rather
than extending the run.

For either path, record each workflow step as **followed**, **impossible**,
**ambiguous**, or **overridden**, with the evidence and authority behind that
status. A status is data, not a reason to silently rewrite the workflow. Revise
`workflow-v1` only when the record shows a recurring decision or risk; one
awkward step, missing tool, or isolated result is evidence to investigate, not
enough to add durable machinery.

## Deliverable

A completed `workflow-v1` using the shared template and a validation record
outside the P01 worktree. It must include the frozen task, exact baseline and
reference, selected context and authority, tools/environment/permissions,
human and agent decision rights, stop/recovery/escalation/handoff rules,
step-status record, retained metrics, external acceptance results, and one
keep, revise, or remove decision. Cite the prepared dossier when used and mark
all unavailable telemetry `unknown`.

## Acceptance checks

The artifact is complete only if it:

- can be followed by another engineer because every workflow step names inputs,
  authority, observable output, stop condition, verifier, and retained
  evidence;
- names human decision rights, agent boundaries, stop/recovery/escalation and
  handoff conditions, and an independent check;
- completes the frozen task or analyzes the prepared dossier, including the
  complete invalid-request matrix and preservation of valid Markdown and CSV;
- records external acceptance and regression results, the independent review
  result, deviations, unavailable telemetry, and any prepared-versus-live
  limitation;
- identifies one keep, revise, or remove decision that is proportional to the
  evidence and adoption cost; and
- makes no general performance, provider, or workflow-improvement claim from
  one execution.

Mark it `revise` if it accepts a completion narrative instead of external
evidence, widens authority without approval, omits a stop or verifier, presents
prepared material as a live run, or promotes a preference/unexplained
correlation to a durable workflow rule.

## Async discussion

Post the one workflow step you would keep, its evidence, and its recurring cost
or risk. Then answer: **Which workflow step prevented a plausible failure, and
which step merely moved effort from the agent to the human?** Challenge one
peer’s evidence or, working solo, write the strongest alternative explanation.

## Optional depth

Define the minimum repeated evidence that would justify automating one manual
gate. State the task class, stable preconditions, number of independent
executions, failure threshold, safety/rollback boundary, retained telemetry,
independent verification, and decision owner. Explain why that threshold would
support automation for this local workflow without proving it is safe or useful
elsewhere.
