# Module 01 Curriculum — Agentic Engineering Fundamentals

Status: draft for adversarial review.

Estimated effort: 12–18 focused hours, dominated by the lab. This is an initial estimate, not a deadline.

Use source IDs from `sources.md`. Treat tool behavior as versioned and empirical.

## Unit 1 — Model, agent loop, and harness

### Engineering question

When an agent succeeds or fails, which layer deserves credit or blame?

### Working model

```text
intent and constraints
        ↓
harness assembles context and authority
        ↓
model selects a response or tool call
        ↓
tool executes inside an environment
        ↓
observation returns to the harness
        ↓
context/state update, approval, retry, recovery, or termination
        ↓
independent verification of the outcome
```

A model produces decisions from context. A harness maintains the loop around it: task state, context, tool routing, execution boundaries, approvals, progress, failures, and result delivery. The deployed agent is the combined system, not the model alone. See S01, S02, and S03.

### Advanced focus

- Hidden coupling between model capabilities and harness assumptions.
- State represented in messages, files, an append-only session, external stores, or environment state.
- The difference between reasoning about a task and observing the actual environment.
- Termination conditions, false completion, and the gap between a plausible report and a correct outcome.
- Why model upgrades can turn formerly useful scaffolding into dead weight.

### Exercise

Take one completed coding-agent run and annotate each meaningful event with:

`intent`, `context`, `inference`, `tool`, `environment`, `observation`, `state`, `authority`, `verification`, or `human decision`.

For every wrong turn, identify the earliest layer where a different design could have prevented it. Do not label every failure “the prompt.”

### Exit evidence

- An agent-loop trace another engineer can follow.
- At least three competing root-cause hypotheses for one failure and the evidence that separates them.

## Unit 2 — Context engineering

### Engineering question

What is the smallest high-signal context that reliably produces the desired behavior?

Context includes more than the user prompt: system and repository instructions, tool descriptions, selected files, retrieved documents, prior messages, summaries, durable notes, current environment observations, and model-visible state. Context engineering is the repeated selection and maintenance of those inputs, not a one-time wording exercise. See S02.

### Design dimensions

- **Relevance:** Does the information change a decision in this task?
- **Authority:** Is it an instruction, evidence, preference, or untrusted data?
- **Freshness:** Could the fact have changed since it was recorded?
- **Placement:** Should it be always loaded, discovered, retrieved on demand, or exposed through a tool?
- **Resolution:** Is the agent seeing raw evidence, a lossy summary, or a conclusion?
- **Cost:** What token, latency, privacy, and maintenance cost does it impose?
- **Failure behavior:** What happens when the context is missing, contradictory, stale, or too large?

### Three treatments for the lab

1. **Task-only:** concise task, constraints, and acceptance criteria; normal repository discovery.
2. **Repository-guided:** task plus well-scoped `AGENTS.md`/`CLAUDE.md` and project documentation.
3. **Curated progressive disclosure:** a small initial brief with explicit links or tools for task-local evidence, decisions, and deeper material.

The hypothesis is not that more context wins. Each treatment should state why every additional token earns its place.

### Exit evidence

- A context inventory classified by authority, freshness, placement, and cost.
- A prediction of how each treatment will fail before observing the results.

## Unit 3 — Durable project knowledge

### Engineering question

How should knowledge persist without turning repository instructions into an unmaintainable context dump?

### Knowledge layers

| Layer | Examples | Loading strategy |
| --- | --- | --- |
| Operating policy | Safety boundaries, review rules, non-negotiable commands | Small, always available where the harness supports it. |
| Project orientation | Architecture map, ownership, entry points | Discover early; concise and link-rich. |
| Decisions | ADRs, rejected alternatives, constraints | Retrieve when the affected boundary is in scope. |
| Task state | Brief, plan, acceptance checks, open questions | Task-local and current. |
| Reference | APIs, library docs, research, runbooks | Search or retrieve on demand. |
| Evidence | Logs, test output, measurements, traces | Inject at the decision point; preserve raw provenance. |
| Learned corrections | Repeated failure and its prevention | Promote into the narrowest durable instruction, test, tool, or design change. |

### Failure modes

- Instruction files become a chronological dumping ground.
- Summaries replace evidence and hide uncertainty.
- Conflicting rules lack precedence.
- Old product behavior remains presented as current.
- Retrieval returns semantically similar but operationally irrelevant material.
- The same fact is copied into several files and drifts.

### Exercise

Design a knowledge map for the lab repository. For each artifact, specify owner, authority, discovery path, refresh trigger, and deletion/supersession rule. Remove any artifact whose expected decision value does not justify its maintenance and context cost.

### Exit evidence

- A project knowledge map with explicit precedence and freshness rules.
- One example of progressive disclosure from orientation to raw evidence.

## Unit 4 — Harness engineering and controlled comparison

### Engineering question

Which surrounding mechanisms materially improve outcomes, and which encode stale assumptions about the model?

### Harness responsibilities to inspect

- context assembly and compaction;
- tool schemas, routing, and observations;
- session and task state;
- sandbox and filesystem boundaries;
- permission and approval policy;
- concurrency and isolation;
- progress visibility and handoff artifacts;
- retry, recovery, and termination;
- output structure and integration with the system of record;
- telemetry needed to evaluate the complete system.

S01 describes the current open Codex harness as the layer managing context, tools, conversation state, sandboxing, approvals, and work across turns. S03 and S04 show that harness components should be stress-tested as models improve rather than preserved as folklore.

### Comparison rule

Do not ask “Which agent is better?” Ask narrower questions such as:

- Which context treatment reduces unnecessary exploration without hiding important constraints?
- Which harness exposes enough evidence to diagnose failure?
- Which approval model matches the task's risk?
- Which system reaches verified completion with fewer human decisions?
- Which apparent advantage disappears when the baseline, model version, or tools change?

### Exercise

Execute the controlled comparison in `lab.md`. Capture the task, baseline revision, harness/model versions, context treatment, tools, permissions, outcomes, interventions, wall time, cost/token data when available, diff characteristics, automated checks, and independent review findings.

### Exit evidence

- A comparison report that separates observations from explanations.
- At least one harness or context hypothesis rejected by the data.

## Unit 5 — Workflows, gates, and durable improvement

### Engineering question

How do we turn a successful run into a repeatable system without freezing accidental details?

### Workflow skeleton

```text
frame intent and risk
        ↓
inspect current state
        ↓
define falsifiable acceptance
        ↓
select context, tools, environment, and authority
        ↓
plan and execute within boundaries
        ↓
observe, steer, recover, or escalate
        ↓
run independent acceptance checks
        ↓
review the system diff and outcome
        ↓
capture the smallest durable improvement
```

### Required design decisions

- What the agent may decide without approval.
- Which actions require approval and who grants it.
- Stop conditions for ambiguity, risk, repeated failure, budget, and time.
- What evidence must exist before implementation and before completion.
- What checks are synthetic, independent, or human.
- How a partial or failed run hands off state without claiming success.
- Which metric would show that the workflow is getting worse.

### Exercise

Turn the lab's strongest treatment into `workflow-v1`: a concise specification another agent can execute. Apply it once to a fresh but comparable task. Compare the second run with the original baseline and record whether the durable change improved outcome quality or merely moved effort elsewhere.

### Exit evidence

- A reusable workflow with explicit interfaces and decision rights.
- Before/after evidence for one durable change.
- A decision to keep, revise, or remove that change.

## Module completion review

Before requesting adversarial review:

- Map each outcome in `brief.md` to a curriculum section and lab artifact.
- Refresh time-sensitive sources.
- Remove claims that outrun their evidence.
- Remove beginner material that does not unlock an advanced mechanism.
- State confounders and negative results.
- Complete the lead self-review in `codex-review.md`.

