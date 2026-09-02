# Unit 2 — Context Engineering

**Core timebox:** 60 minutes: lesson 12 minutes; required reading 12 minutes;
prediction and inventory 8 minutes; comparison exercise 23 minutes; self-check
and async post 5 minutes.

**Source map:** [S02](../sources.md#technical-sources) is required. S06 and
S09 are optional product-specific comparisons. P01 supplies the prepared case.

## Engineering question

How do model-visible inputs change a bounded engineering investigation, and
which inputs earn their cost without turning a case study into a provider claim?

## Learning outcomes

By the end of this unit, you can:

- inventory model-visible inputs, distinguish their authority, freshness,
  placement, and retrieval trigger, and identify whether each is an
  instruction, evidence, preference, or untrusted data;
- compare two fixed context configurations while holding task, baseline, model,
  harness, permissions, and timebox constant;
- separate observations from causal explanations, then record confounders, cost
  proxies, and uncertainty; and
- decide whether each added item should be kept, revised, or rejected for this
  task rather than treating a larger packet as generally better.

## Lesson

**Context** is every model-visible input used for an inference, not just the
user prompt. The actual packet is harness-specific, but an engineering
inventory usually has these classes: system and developer instructions;
repository instructions and files; the task; retrieved source; tool
descriptions and tool results; history; summaries; and environment facts such
as working directory, Git state, permissions, available runtimes, or command
output. Skills and their descriptions, as well as a subagent’s returned
summary, are also model-visible inputs when the harness includes them. They are
not neutral plumbing: each can change what the next inference treats as salient.

Classify each item before deciding whether to include it. An **instruction**
defines an expected action or boundary; **evidence** supports or weakens a
claim; a **preference** selects among otherwise valid choices; and **untrusted
data** may be useful but must not replace higher-authority instructions. A
README sentence about privacy may be authoritative repository guidance for this
task. A copied issue comment may be evidence or untrusted data, depending on
provenance. A tool result is an observation with a command, time, environment,
and failure mode; it is not automatically a durable rule.

Evaluate a candidate context item along seven dimensions. **Relevance** asks
whether it changes the immediate decision. **Authority** asks who can set the
rule and what it may override. **Freshness** records a checked date, exact
revision, or trigger for re-reading it. **Placement** asks when and where it
appears; an early system instruction and a retrieved file are not equivalent.
**Resolution** asks how the agent can find, interpret, and reconcile the item.
**Cost** includes packet bytes or tokens, retrieval time, attention, and
maintenance. **Failure behavior** asks what happens when the item is stale,
missing, contradictory, over-broad, or ignored. Context engineering is the
allocation of that finite budget, not an instruction to maximize it.

Use **progressive disclosure** when a stable pointer is enough to begin:
provide the relevant path or search target, then retrieve raw source only when
the next decision needs it. A pointer can be both cheaper and more useful than
a pasted file because it preserves navigable structure and gives the task a
concrete retrieval path. It also has failure modes: it costs a tool call, can
be missed, and gives an agent with poor search behavior less immediate support.
Compare those effects rather than crediting the pointer with every observed
difference.

State is often compacted. A summary can preserve decisions, file pointers, and
unresolved questions while discarding raw tool output. That makes compaction
**lossy**: a conclusion may omit the exact command, qualification, or failed
branch needed later. Treat a summary as a new, lower-fidelity context artifact
with a freshness and provenance record. Retrieve the primary file, command
output, or Git revision before making a claim the summary cannot support.

Precedence errors are context-poisoning failures. A prompt embedded in an issue
or README can ask the agent to ignore repository or system rules; a stale
summary can conflict with the checked-out code; a copied tool result can belong
to another worktree. Keep authority explicit, label untrusted text, and resolve
conflicts by the actual hierarchy and current evidence—not by recency, length,
or a confident tone. More context can dilute the task, introduce conflicting
instructions, consume attention, or hide the one file that matters. The right
default is the smallest high-signal packet sufficient for the next decision,
followed by measured retrieval.

[S02](../sources.md#technical-sources), “Context engineering vs. prompt
engineering,” defines context as information beyond prompts; its “Context
retrieval and agentic search” section describes just-in-time retrieval and
progressive disclosure; and “Compaction” describes summarization tradeoffs.
Those are first-party Anthropic engineering guidance, not a universal account
of every harness. S02’s Claude Code examples must be rechecked against the
installed product and configuration.

## Required reading

Read [S02](../sources.md#technical-sources), [“Context engineering vs. prompt
engineering”](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents#context-engineering-vs-prompt-engineering), through [“Context retrieval and agentic
search”](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents#context-retrieval-and-agentic-search), including its progressive-disclosure discussion (12 minutes).
Then skim [“Compaction”](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents#context-engineering-for-long-horizon-tasks).

While reading, identify one input that should be present at task start and one
that should be retrieved only after a concrete question arises. Explain the
failure mode of including each at the other time. Do not convert S02’s examples
into an assumption about another provider or local harness.

For optional, version-specific depth, [S06](../sources.md#technical-sources)
currently documents “The context window” and “Manage context with skills and
subagents”; [S09](../sources.md#technical-sources) documents “CLAUDE.md vs auto
memory,” “How CLAUDE.md files load,” and “AGENTS.md.” Those pages describe
Claude Code behavior as checked in `sources.md`; they do not establish that
AGENTS files, memory, compaction, deferred tool descriptions, or subagent
summaries behave identically in another harness.

## Worked example

The prepared comparison in
[unit-02-context-comparison.md](../exercises/evidence/unit-02-context-comparison.md)
uses the Agent Experiment Ledger at frozen baseline
`bb65b5cec8c96c3ba3d89b0025473561c7c8146f`. The read-only task asks whether a
whole-ledger check detects an escaping experiment-directory symlink and an
in-root experiment alias. Both configurations receive the same task, baseline,
20-minute stop, and response format. Configuration B adds only bounded
repository guidance and a pointer to the likely traversal and test files.

The decisive raw baseline evidence is
`src/checks/check-ledger.ts:404-407`: the whole-ledger branch filters
`readdir(..., { withFileTypes: true })` entries with `entry.isDirectory()`
before `assertExistingPathContained` is called. A symlink does not pass that
prefilter, so containment never evaluates an escaping symlink or an in-root
alias. Reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7` changes
the traversal to include symbolic links, then rejects aliases after containment
and adds two whole-ledger tests.

The prepared A and B responses are illustrative comparison material, not live
runs, provider measurements, or evidence that the extra packet caused the
result. The packet-size difference and B’s file-pointer advantage are both
confounders: B is larger, but it is also better oriented. The artifact asks for
a local decision about every added item, not a winner.

## Exercise

Spend 23 minutes on a bounded comparison. Work in an isolated, read-only
checkout at the exact baseline, or use the prepared fallback. Do not modify
files. Stop at 20 minutes if running an agent, preserve what was observed, and
record unavailable telemetry as `unknown`.

1. Before reading the prepared responses, use
   [context-comparison-template.md](../exercises/context-comparison-template.md)
   to predict one failure mode for A and B. State what evidence would falsify
   each prediction.
2. Copy the exact A and B packets from the prepared comparison. Run one or both
   with the same model, harness, permissions, baseline, timebox, and acceptance
   format. Do not silently add a browser, memory, instructions, or retrieved
   source to A. If an implementation cannot suppress an ambient context source,
   record it as an uncontrolled difference rather than calling the comparison
   controlled.
3. Build the configuration inventory. For every B-only item, record provenance,
   authority, freshness/checked date, placement, byte cost, retrieval trigger,
   and failure behavior. Mark tools, permissions, environment, and unavailable
   telemetry explicitly.
4. Record observations separately from explanations. Navigation behavior such
   as “opened `src/checks/check-ledger.ts` first” is an observation. “The
   orientation note caused that behavior” is a hypothesis requiring support and
   competing explanations. Record wrong turns, human interventions, and a cost
   proxy such as packet bytes, elapsed minutes, tool calls, or `unknown`.
5. Compare the result against the raw baseline and the bounded reference repair
   in the prepared pack. Identify the missing `Dirent.isDirectory()` prefilter
   test without claiming that a live agent must reproduce either prepared path.
6. Make a keep, revise, or reject decision for **each** B-only item. Explain
   whether the item earned its context cost for this task, what would falsify
   that decision, and what follow-up evidence would be needed for a broader
   claim.

## Deliverable

A completed copy of
[context-comparison-template.md](../exercises/context-comparison-template.md),
stored outside the code-under-test worktree. Mark whether it contains a live
learner run, prepared comparison material, or both. Include the frozen task,
baseline, response format, held constants, configuration inventory, predictions
made before results, evidence links, observations, explanations, wrong turns,
interventions, cost proxy, confounders, uncertainty, and per-item decisions.

Do not include raw private transcripts, credentials, proprietary prompts, or
private source. A completion narrative or an invented token count is not a
measurement. The prepared pack is a fallback and does not replace reasoning.

## Acceptance checks

The artifact is complete only if it:

- freezes the task, exact baseline, 20-minute stop, acceptance format, and all
  held-constant variables;
- classifies every B-only item by provenance, authority, freshness, placement,
  retrieval trigger, cost, and failure behavior;
- records predictions before opening prepared responses or live results;
- distinguishes observed navigation or findings from causal explanations and
  records competing explanations, uncertainty, wrong turns, and interventions;
- records packet byte counts and explicitly treats both packet size and B’s
  file-pointer/orientation advantage as confounders rather than proof that more
  context helped;
- cites raw baseline traversal and bounded reference-repair evidence, while
  labeling prepared responses as illustrative rather than measured provider
  performance; and
- makes a falsifiable keep, revise, or reject decision for every B-only item
  without generalizing the result to another task, model, or harness.

Mark it `revise` if it says configuration B is better merely because it found
the filter, attributes an explanation as an observation, hides ambient context,
or treats bytes as a token count.

## Async discussion

Post one observed difference, one competing explanation, its strongest
confounder, and one per-item decision. Then answer: **Which item in
configuration B earned its context cost, and which item merely restated
information?** Challenge one peer’s causal claim or, working solo, write the
best alternative explanation before finalizing your decision.

## Optional depth

Compare S06’s current documentation of context, skills, tools, and subagents
with S09’s documentation of `CLAUDE.md`, auto memory, load order, and
`AGENTS.md` interoperability. Then contrast both with your harness’s actual
behavior. For each statement, record the provider, version/configuration when
available, checked date from [sources.md](../sources.md), and the qualifier
that prevents it becoming a universal claim. Treat compacted history and a
subagent result as potentially lossy context artifacts; retrieve raw evidence
when their summaries are insufficient.
