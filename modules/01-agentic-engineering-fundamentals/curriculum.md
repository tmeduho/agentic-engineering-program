# Module 01 — Agentic Engineering Fundamentals

- Status: verified

**Design policy:** verified internal-pilot curriculum prepared for eventual
public distribution; approval and release prerequisites remain separate from
this verified status.

This text-first module is for experienced software engineers who want to make
agentic engineering choices with bounded authority and evidence, rather than
learn a catalog of products or prompt patterns. It is a self-paced, async-first
course with an optional meeting and a solo completion path.

## Before you start

**Free** means the curriculum is shared at no participation cost. It is not a
license claim. A learner-selected agent subscription, API usage, or other tool
may still cost money.

You need one supported coding-agent configuration **or** the prepared evidence
packs; Git; Node.js 22 or newer and pnpm 10.26.1 for live code exercises; a
disposable checkout or isolated worktree; and permission to retain sanitized
learning artifacts. The core does not require both Codex and Claude.

For the internal pilot, the facilitator provides access to the sibling Agent
Experiment Ledger repository described in [the lab](lab.md). Its public release
location and access method are not finalized. The curriculum license and the
sample-project license are also not finalized.

Use synthetic, sanitized, or approved data. Keep artifacts, command output,
and evidence outside code-under-test worktrees; do not share credentials, raw
private transcripts, proprietary prompts, private source, or private absolute
paths. The setup, authority limits, pinned revisions, stop rules, and recovery
path are in [the lab](lab.md#setup-isolation-and-privacy).

## Core path — planned 405-minute learner-work cap

Complete these in order. The timeboxes include required reading and the
decision-record activity.

| Order | Time | What to complete |
| --- | ---: | --- |
| 1 | 45 min | [Unit 1 — Models, loops, and harnesses](units/01-models-loops-harnesses.md) and an [annotated run trace](exercises/run-trace-template.md) |
| 2 | 60 min | [Unit 2 — Context engineering](units/02-context-engineering.md) and a [context comparison](exercises/context-comparison-template.md) |
| 3 | 75 min | [Unit 3 — Project knowledge](units/03-project-knowledge.md) and a [repository knowledge map](exercises/knowledge-map-template.md) |
| 4 | 90 min | [Unit 4 — Harness Controls and Independent Verification](units/04-harness-comparison.md) and a [harness-control case study](exercises/harness-case-study-template.md) |
| 5 | 60 min | [Unit 5 — Reusable workflows](units/05-reusable-workflows.md) and [`workflow-v1`](exercises/workflow-template.md) |
| Decision | 75 min | [Workshop](workshop.md) and a [team decision record](exercises/team-decision-template.md) |

These allocations are planned learner-work caps, not evidence that a typical
human finishes in 405 minutes. Environment provisioning, facilitator
preparation, dependency download, and peer waiting are outside the cap; setup
observation/configuration capture stays inside where a unit says so. A timed
human/cohort pilot is required before learner approval or public release.

The [core lab](lab.md) connects these five artifacts into one artifact chain;
it adds no sixth implementation task. If live access, time, or safety prevents
a run, use the matching sanitized [evidence pack index](exercises/evidence/README.md)
and complete the same analysis honestly as prepared comparison material. The
final decision record labels capability **per unit/artifact**: `executed` only
for the relevant live path and `critically analyzed` for a prepared path. A
mixed chain must preserve both labels and neither may imply the other.

## Collaboration and completion

Async is the default: post an artifact summary, receive or author an
evidence-backed challenge, respond or revise, synthesize, and complete the
decision record. Follow [the workshop](workshop.md) for the exact path. When a
meeting is useful, use its optional 75-minute agenda; attendance never replaces
the async path. If peers are unavailable, use the solo fallback and label the
decision record `solo`.

Only the learner exercises learner-owned approval for a decision or authority
expansion. Facilitators and
peers can challenge and synthesize evidence, but cannot approve work for the
learner. [The facilitator guide](facilitator-guide.md) covers preparation,
evaluation, and recovery.

Core completion follows [the lab rubric](lab.md#completion-rubric):

- all five artifacts are `complete` under their selected contracts, not merely
  present; `complete` never by itself means `executed`;
- one async, synchronous, or solo decision record is complete;
- no open safety violation occurred, including unapproved authority expansion,
  retained sensitive material, production use, or evidence in a code worktree;
- Units 4 and 5 include external acceptance and regression evidence plus an
  independent source or diff review, not producing-agent self-report;
- every artifact records material uncertainty and confounders, including
  live-versus-prepared limits where applicable; and
- every conclusion stays within its recorded task, baseline, configuration,
  and evidence boundary.

The [advanced lab](advanced-lab.md) is optional and elective. It does not gate
core completion.

## MEGA Week 1 public-agenda coverage

This is a coverage and format provenance map based on the public snapshot in
[sources](sources.md#scope-and-local-evidence). It is not evidence of paid
content depth or equivalence. Module 01 uses original teaching and assessment;
the public labels below neither reproduce nor characterize unreleased lessons.

**Teach** means the topic is explained, exercised, and assessed here. **Touch**
means it is introduced operationally and connected to an exercise; later
modules own deeper treatment. This matrix has 18 Teach rows and 9 Touch rows.

| MEGA Week 1 public agenda | Coverage | Module 01 connection |
| --- | --- | --- |
| Introduction | Touch | Orientation and the model, agent, harness, workflow distinction |
| Model mechanics | Teach | Unit 1 |
| Limitations | Teach | Unit 1 |
| Providers | Touch | Provider-neutral core setup |
| Interactions | Teach | Unit 1 |
| Steering | Teach | Unit 2 |
| Settings | Teach | Units 1 and 4 |
| Context | Teach | Unit 2 |
| Processing | Teach | Unit 2 |
| Skills | Touch | Reusable instruction context; deeper construction later |
| Tools | Touch | Tool execution and observations; deeper design later |
| Subagents | Touch | Delegated output as context; coordination later |
| Files | Teach | Unit 3 |
| Style guides | Teach | Unit 3 |
| Specifications | Teach | Units 3 and 5 |
| Tasks | Teach | Units 1 and 5 |
| Libraries | Teach | Unit 3 |
| Research | Teach | Unit 3 |
| Harnesses | Teach | Unit 4 |
| Interfaces | Teach | Unit 4 |
| Workflows | Teach | Unit 5 |
| Teamwork | Touch | Workshop evidence review and decision record |
| Product | Touch | Outcome framing and decision rights; deeper judgment later |
| Quality | Teach | Units 4 and 5 |
| User experience and UI | Touch | Workflow usability and human interaction cost; deeper treatment later |
| Security | Teach | Lab and Units 4–5 |
| Business | Touch | Time, cost, risk, and adoption constraints; deeper treatment later |

## Reference material

- [Module brief](brief.md) defines outcomes, prerequisites, and the normative
  artifact contract.
- [Sources](sources.md) is the sole source metadata and claim registry.
- [Evidence packs](exercises/evidence/README.md) provide bounded prepared
  fallbacks for Units 1–5.
- [Core lab](lab.md) defines the integration exercise, setup, and completion
  rubric.
- [Workshop](workshop.md) and [facilitator guide](facilitator-guide.md) define
  async, meeting, and solo participation.
- [Advanced lab](advanced-lab.md) contains the elective controlled experiment.
