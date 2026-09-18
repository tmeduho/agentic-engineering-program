# Module 01 Brief — Agentic Engineering Fundamentals

- Status: in-review
- Lead: Codex
- Adversarial reviewer and final verifier: Claude
- Source freshness metadata: [sources.md](sources.md) is the sole registry
- Target learner: `../../PROFILE.md`

## Purpose

Develop a rigorous, provider-neutral mental model of agentic engineering and use it to build a bounded, evidence-backed workflow for real software work.

The module should replace vague ideas such as “the model did well” with explicit reasoning about the model, context, agent loop, harness, tools, environment, authority, observations, and verification.

## Primary question

Which parts of an agentic engineering result come from the model, which come from the surrounding harness and context, and how can we change those layers deliberately without adding unjustified machinery?

## Outcomes

By the end of the module, the learner can:

1. Trace model inference, context assembly, agent-loop decisions, tool execution, environment effects, authority, observations, and verification.
2. Compare bounded context configurations while separating observations, explanations, and confounders.
3. Design and test a repository knowledge structure with authority, freshness, discovery, precedence, and retirement rules.
4. Evaluate a bounded run or prepared dossier against an explicit
   harness-control and independent-verification contract, and propose one
   falsifiable configuration change without claiming a measured configuration
   effect. Label live execution `executed` and prepared analysis
   `critically analyzed`.
5. Execute a bounded workflow with decision rights, safety, escalation,
   evidence, and verification gates, or critically analyze its prepared
   validation dossier without claiming execution skill.

## Prerequisites

- One supported coding-agent configuration or the prepared evidence packs.
- A local copy of Agent Experiment Ledger at exercise baseline `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` and verified reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7`.
- Git, Node.js 22 or newer, and pnpm 10.26.1 for live code exercises.
- An isolated worktree or equivalent disposable checkout.
- Permission to retain sanitized learning artifacts outside code-under-test worktrees.

## Non-goals

- General LLM history or beginner prompting advice.
- Training or fine-tuning a model.
- Building a production orchestration platform.
- Declaring one model or harness universally superior.
- Exhaustive coverage of tool design, MCP, multi-agent coordination, or autonomous operations; later modules own those subjects.

## Five units

1. Model, agent loop, and harness boundaries.
2. Context engineering as allocation of a finite resource.
3. Durable project knowledge and progressive disclosure.
4. Harness controls and independent verification.
5. Reusable workflows with verification and feedback.

The five unit allocations (45, 60, 75, 90, and 60 minutes) and the 75-minute
discussion are planned learner-work caps, not empirically established human
completion estimates. Environment provisioning, facilitator preparation,
dependency download, and peer waiting are outside the 405-minute cap; required
in-task setup observation and configuration capture remain inside where named.
A timed human/cohort pilot is required before learner approval or public release.

## Required deliverables

- An annotated run trace and competing failure hypotheses.
- A bounded context inventory and comparison.
- A repository knowledge map and before/after discovery evidence.
- A harness-control case study with independent verification and one untested,
  falsifiable proposed configuration change.
- `workflow-v1` and its validation record.
- One decision record from async, synchronous, or solo review.

`advanced-lab.md` is elective and exploratory unless replication conditions are met. Its controlled experiment may extend the core artifacts, but it cannot block core completion or add a core outcome.

## Acceptance criteria

Every core artifact is either complete, revise, or not attempted. File
existence alone is not complete. The mapping below defines the required
artifact and a falsifiable acceptance condition for each outcome.

| Outcome | Required artifact | Falsifiable acceptance condition |
| --- | --- | --- |
| Trace the agent system | Annotated run trace and competing failure hypotheses | The trace labels model inference, context assembly, agent-loop decision, tool execution, environment effect, authority, observation, and verification where they occur; for one failure it records competing hypotheses and evidence that rejects or leaves each unresolved. |
| Compare bounded context | Bounded context inventory and comparison | The comparison records configurations and held-constant conditions, then separates observations, explanations, and confounders; it fails if it treats an explanation as an observation or omits a material uncontrolled variable. |
| Design and test project knowledge | Repository knowledge map and before/after discovery evidence | The map assigns authority, freshness trigger, discovery path, precedence, and retirement rule to every listed knowledge artifact, and the evidence shows whether the proposed structure changed a specified discovery task. |
| Evaluate harness controls and independent verification | Harness-control case study and untested configuration-change proposal | Both paths preserve the frozen task, baseline, acceptance checks, and authority boundary; assess all ten harness dimensions with configured/observed values, evidence, uncertainty, and consequences; and distinguish instructions from enforcement. Live acceptance requires independent candidate evaluation; prepared analysis records missing candidate evidence. The proposal names a target failure, expected observation, falsifier, enforcement mechanism, and held constants without claiming a measured effect. |
| Execute or critically analyze a bounded workflow | `workflow-v1` and validation record | A live validation records external acceptance independent of the producing agent. A prepared validation is labeled `critically analyzed` and cannot evidence execution skill. |

The decision record states an evidence-backed practice to adopt, test further,
or reject. It supports the artifact chain but does not add another core outcome.

All time-sensitive claims must meet `../../RUBRIC.md` freshness rules at
verification time. The module must pass the shared rubric and Claude must
verify the final revision. Only the learner may mark Module 01 approved.

## Known risks

- Agent-system configurations can expose different telemetry and permission models, limiting strict equivalence.
- A single case can support a bounded control or verification decision, not a
  measured configuration effect or a general provider or harness ranking.
- Prepared evidence packs may omit telemetry; record unavailable values as unknown rather than inventing estimates.
- A task that is too easy will hide context and harness differences; a task that is too broad will introduce uncontrolled variance.

Document these limitations rather than hiding them.
