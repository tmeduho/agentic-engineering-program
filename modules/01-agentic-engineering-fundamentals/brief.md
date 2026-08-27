# Module 01 Brief — Agentic Engineering Fundamentals

- Status: draft
- Lead: Codex
- Adversarial reviewer and final verifier: Claude
- Last source check: 2026-08-26
- Target learner: `../../PROFILE.md`

## Purpose

Develop a rigorous, tool-independent mental model of agentic engineering and use it to build a measured workflow for real software work.

The module should replace vague ideas such as “the model did well” with explicit reasoning about the model, context, agent loop, harness, tools, environment, authority, observations, and verification.

## Primary question

Which parts of an agentic engineering result come from the model, which come from the surrounding harness and context, and how can we change those layers deliberately without adding unjustified machinery?

## Outcomes

By the end of the module, the learner can:

1. Trace a coding-agent run through context assembly, inference, tool use, environment changes, observations, approvals, and termination.
2. Diagnose failures at the correct layer instead of defaulting to prompt changes.
3. Design a context strategy with explicit inclusion, exclusion, freshness, and progressive-disclosure rules.
4. Build a repository knowledge structure that supports discovery without dumping the entire project into context.
5. Compare Codex and Claude on a controlled engineering task using observable outcome, intervention, cost, latency, and review data.
6. Turn the experiment into a reusable engineering workflow with decision rights, safety boundaries, quality gates, recovery, and escalation.

## Prerequisites

- A non-sensitive software repository with deterministic checks and a representative bounded task.
- Working access to Codex and Claude Code, or learner approval to substitute another pair of harnesses.
- Ability to create isolated branches or worktrees.
- Permission to record aggregate run metrics and sanitized observations.

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
4. Harness engineering, authority, and empirical comparison.
5. Reusable workflows with verification and feedback.

## Required deliverables

- An annotated agent-loop trace from a real run.
- A context and repository-knowledge design for the selected project.
- A controlled comparison report covering at least two harnesses and three context treatments.
- A reusable workflow specification with safety, escalation, and verification gates.
- One durable project improvement justified by experiment evidence.

## Acceptance criteria

- Every outcome maps to curriculum material and lab evidence.
- All time-sensitive claims meet `../../RUBRIC.md` freshness rules at verification time.
- The comparison uses the same baseline, task, acceptance checks, and controlled variables where technically possible.
- The report distinguishes observed facts, plausible explanations, confounders, and opinions.
- Success is verified through repository state and checks, not agent self-report.
- The module passes the shared rubric and Claude verifies the final revision.

## Known risks

- Model updates during the experiment can invalidate comparisons.
- Harnesses expose different telemetry and permission models, limiting strict equivalence.
- Repeated runs can contaminate later prompts or allow task-specific memorization.
- Token and cost data may be incomplete or calculated differently.
- A task that is too easy will hide context and harness differences; a task that is too broad will introduce uncontrolled variance.

Document these limitations rather than hiding them.

