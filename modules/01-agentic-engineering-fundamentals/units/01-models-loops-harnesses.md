# Unit 1 — Models, Loops, and Harnesses

**Core timebox:** 45 minutes: lesson 12 minutes; required reading 10 minutes;
prepared-case exercise 18 minutes; self-check and async post 5 minutes.

**Source map:** [S01](../sources.md#technical-sources) is required. S06 and
S10 are optional product-specific comparisons. P01 supplies the prepared case.

## Engineering question

When an agent reports success, what happened in the deployed system, and what
evidence would justify accepting that report?

## Learning outcomes

By the end of this unit, you can:

- distinguish a model, agent loop, harness, tool, execution environment,
  authority boundary, state, and independent verifier in a concrete run;
- explain why operational nondeterminism means two runs with the same apparent
  task can take different paths or yield different results;
- separate a fluent completion narrative from observations of repository or
  environment state; and
- diagnose a false-completion case with competing hypotheses, evidence for and
  against each, and an explicit residual uncertainty.

## Lesson

A coding model produces its next output from the context made visible to it. An
output can be useful: a proposed edit, a command, an explanation, or a tool
call. It is not itself an observation that the command ran, the edit persisted,
or the requested behavior now holds. The distinction matters most when a
response sounds complete: fluency is evidence of neither repository state nor
external effect.

An **agent loop** repeats a decision cycle: establish or update the task,
assemble model-visible context, obtain a model output, route a selected tool,
receive an observation, update state, and either continue, request approval,
recover, or stop. A loop may stop because a model emits completion language, a
budget expires, a policy blocks an action, a human intervenes, or an external
check accepts the outcome. Those are different termination events and should
not be collapsed into “done.”

The **harness** is the surrounding execution system that runs this loop. It
decides which instructions, files, tool results, summaries, and task state
become model-visible context; routes tool calls; preserves or compacts state;
enforces approval and retry rules; records progress; and decides how a turn or
session terminates. Its configuration can change the delivered result without a
change to the model identifier. S01 describes these responsibilities for the
Codex harness; use that as an implementation example, not as a universal
architecture.

Separate a selected tool call from tool execution. The model can select
`pnpm test`; the harness can reject it, request approval, fail to start it, or
run it in a different directory. A process may then exit unsuccessfully,
produce stale output, or modify a different checkout than the one a reviewer
inspects. The **execution environment** is where permitted tools actually run:
filesystem view, working directory, credentials, network, runtime versions,
and sandbox or host controls. Its permission boundary limits what a tool can
attempt; it does not turn a tool selection into a verified outcome.

**State** exists both inside and outside the model-visible context. A harness
may keep conversation history, a task record, a queue, or a summary. The
environment holds Git state, files, processes, service data, and tool side
effects. The model only receives the subset the harness provides. Treat a
statement about a file as a claim until a permitted observation, such as a
read, diff, test result, or service probe, supports it.

Operational nondeterminism is broader than token sampling. Sampling can cause
different outputs for the same inputs. A real agent run also varies with
context selection and truncation, tool outputs, filesystem and Git state,
timing, retries, approval decisions, network availability, and human
intervention. A repeated run is evidence about that configured system under
those conditions; it does not isolate one cause by itself.

An **independent verifier** runs acceptance checks or inspects state outside
the producing agent’s completion narrative. Independence here is functional,
not ceremonial: the verifier needs access to evidence capable of contradicting
the claim. In a repository task, that commonly means a fresh checkout, a
deterministic command, a targeted fault injection, and a diff review. The
verifier can find a failure after a model and harness have both reported
success.

For this reason, “provider X with model Y” does not identify a deployed agent
system. The model family is one component. To reproduce or compare a run, also
record the harness and version when visible, context sources, tool set,
environment, permissions and approvals, relevant state, termination rule, and
verification procedure. Record unavailable telemetry as `unknown`; do not
fill gaps with a provider-level assumption.

## Required reading

Read S01, [“The reusable part is the agent loop”](https://developers.openai.com/blog/codex-as-a-platform#the-reusable-part-is-the-agent-loop), through the following “An open harness” discussion (10 minutes).

While reading, test this claim: **a capable coding agent is a configured loop
and environment around a model response, so a model name cannot account for a
result without the surrounding context, tools, authority, state, and
verification.** Mark which responsibilities S01 assigns to the Codex harness.
Then mark which of those are specific to that documented product and which are
provider-neutral roles this unit uses as analytical labels.

For comparison, S06 describes Claude Code’s current loop, terminal access, and
contexts; S10 documents current OpenAI model-family context and tool settings.
They are optional because their named settings and behavior are product- and
version-specific. Do not infer an equivalent control surface in another
harness.

## Worked example

Use the prepared reconstruction in
[unit-01-run-trace.md](../exercises/evidence/unit-01-run-trace.md). It traces
the Agent Experiment Ledger initialization repair from exercise baseline
`bb65b5cec8c96c3ba3d89b0025473561c7c8146f` to reference revision
`2c498f616583d1fd6aeeaa381552b47acdb71ab7`.

The key error is to accept a green baseline suite and completion narrative as
proof that initialization is failure-atomic. The baseline did type-check, test,
and build in the prepared checkout, but its `initializeLedger` path published
the destination incrementally. The review’s counterfactual interruption falls
between creating the destination and completing its valid structure; a retry
then encounters a non-empty directory without `config.json`. The repair stages
the complete ledger in a hidden same-parent directory, validates it, then
publishes it by rename. The reference revision adds the regression test
`failed initialization publishes no partial ledger and can be retried` and
reruns the checks.

The reconstruction supports a narrow conclusion: the reference change covers
this injected initialization-publication boundary. It does not identify a
single cause of the earlier false completion or establish that another harness
or model would have found the defect.

## Exercise

Spend 18 minutes producing your own annotated trace.

1. Copy [run-trace-template.md](../exercises/run-trace-template.md) outside the
   code-under-test worktree. Start from the prepared pack if you do not have a
   suitable sanitized live run.
2. Use the template fields without changing its schema. Map the required layers
   to concrete fields as follows:

   | Required layer | Template field or fields | What to record |
   | --- | --- | --- |
   | Model inference | `Inference` | The observed response or tool-call selection; write `unknown` when no such observation is available. |
   | Context assembly | `Context` | The model-visible instructions, files, tool results, or summaries, and which harness action assembled them. |
   | Agent-loop decision | `Intent` and `State` | The next-loop transition—continue, request approval, retry, recover, or terminate—and any resulting session or task-state update. |
   | Harness responsibility | `Context`, `Tool`, `Authority`, `State`, and `Verification` | Its applicable action: context assembly, tool routing/execution result, approval enforcement, state update/retry/termination, or verification gate. |

   In `Tool`, distinguish a model-selected call from its routed execution and
   result. A harness responsibility is an annotation in these existing fields,
   not a new template column.
3. Annotate every material event with one or more applicable layers: model
   inference, context assembly, agent loop, tool, environment, authority,
   state, verification, or human decision. Leave a label blank when it did not
   occur; do not infer hidden reasoning or unavailable telemetry.
4. Mark the transition from the initial completion narrative to independent
   evidence, and name the earliest layer that could have prevented false
   completion. Explain why an earlier layer is unsupported or more expensive.
5. Analyze all three hypotheses below. For each, cite Git or prepared-case
   evidence that supports it and evidence that weakens it. Do not select one by
   intuition:

   - acceptance criteria omitted failure atomicity;
   - the producing agent failed to consider interrupted publication; and
   - verification lacked fault injection.

6. State what evidence is missing and what next observation would reduce that
   uncertainty. Keep the conclusion narrower than the evidence.

## Deliverable

An annotated Markdown run trace using the shared template. Store it outside
the code-under-test worktree and identify whether it uses a live learner run or
prepared comparison material. Use the mapping above: `Inference` for model
output, `Context` for context assembly, `Intent` plus `State` for agent-loop
decisions, and the existing `Context`, `Tool`, `Authority`, `State`, and
`Verification` fields for harness responsibility. Cite the baseline/reference
commits, relevant paths, and check output summaries. Raw private transcripts,
credentials, private source, and proprietary prompts do not belong in the
artifact.

## Acceptance checks

The artifact is complete only if it:

- labels every material event with at least one valid system layer;
- distinguishes the completion narrative from repository or environment
  evidence;
- identifies authority and verification transitions;
- records all three competing hypotheses, with evidence for and against each;
- cites Git or prepared-case evidence for each hypothesis; and
- states residual uncertainty and the next evidence needed.

Mark it `revise` if it attributes the outcome to a model or provider label
without showing the harness, environment, and verification boundary.

## Async discussion

Post one concise claim, its supporting evidence, and its residual uncertainty.
Then answer: **Which earliest intervention would have prevented the false
completion at the lowest recurring cost?** Challenge one peer’s layer
assignment or, working solo, challenge your own assignment with a plausible
alternative.

## Optional depth

Compare S06 and S10. Identify one behavior each source documents about its own
system, then write the provider-specific qualifier that prevents it becoming a
universal claim. For example, distinguish a documented product’s context or
permission behavior from the generic analytical roles of context, authority,
and environment. Record the page’s checked date from [sources.md](../sources.md)
and recheck before relying on a current-product detail.
