# Module 01 Hybrid Curriculum Design

- Date: 2026-09-02
- Status: approved by the learner on 2026-09-02
- Scope: Module 01 and the reusable delivery pattern for later modules
- Audience: experienced software engineers
- Shared project: Agent Experiment Ledger

## Summary

Module 01 will become a free, text-first, hybrid course that coworkers can
complete asynchronously and discuss together. It will cover the same public
Week 1 progression advertised by MEGA:

1. models;
2. context;
3. knowledge;
4. harnesses; and
5. workflows.

The course will use original explanations, current primary sources, practical
work in Agent Experiment Ledger, evidence-backed assessment, and optional team
discussion. It will not copy MEGA's paid material or attempt to prove that this
course is superior.

Free means that the curriculum itself is shared without charge. Agent
subscriptions, API usage, and other learner-selected tools may still cost
money. The provider-neutral core and prepared evidence fallbacks prevent a
particular paid product from becoming mandatory.

The core path will take approximately 6-8 hours. The existing five-run
controlled experiment will become an optional advanced lab rather than a core
completion requirement.

## Goals

Module 01 must:

1. Teach the operational concepts in MEGA's public Week 1 agenda at a depth
   appropriate for an experienced engineer.
2. Stand on its own as original written instruction rather than a link list.
3. Connect every unit to a real, reusable software project.
4. Work for individual, asynchronous, and facilitated cohort participation.
5. Permit different coding-agent products without making a particular paid
   provider a core prerequisite.
6. Produce artifacts that demonstrate engineering judgment and remain useful
   after the course.
7. Be safe to distribute publicly after explicit licensing and repository
   packaging decisions are completed.
8. Remain maintainable as models, harnesses, and source material change.

## Non-goals

Module 01 will not:

- reproduce or paraphrase unreleased MEGA lesson material;
- provide a beginner introduction to software engineering, Git, or testing;
- certify universal superiority of one model, harness, or context strategy;
- require every learner to perform a research-grade benchmark;
- require live meeting attendance;
- require both Codex and Claude;
- require learners to share raw transcripts, credentials, private source, or
  proprietary prompts;
- make video production a prerequisite for the first release; or
- cover agent-system construction, multi-agent orchestration, or product
  delivery at the depth reserved for later modules.

## Relationship to MEGA

MEGA's public curriculum is a coverage reference, not the source of the course
material. The custom course will retain its four-module, five-unit progression
while using original teaching, current primary sources, and a shared project.
The mapping below uses the public snapshot recorded in
research/mega-dev-curriculum.md and checked on 2026-08-26. Public agenda labels
do not establish the depth or exact contents of MEGA's unreleased paid lessons;
the mapping is our operational interpretation and must be refreshed before a
future parity claim.

The coverage vocabulary is:

- **Teach:** explain, exercise, and assess in Module 01.
- **Touch:** introduce operationally and connect to an exercise, but leave
  deeper treatment to a later module.
- **Defer:** identify the later module that owns the topic.

| MEGA Week 1 public agenda | Coverage | Module 01 treatment |
| --- | --- | --- |
| Introduction | Touch | Course orientation and the distinction between model, agent, harness, and workflow |
| Model mechanics | Teach | Operational inference, context windows, stochastic behavior, and model-visible inputs |
| Limitations | Teach | Nondeterminism, incomplete observation, false completion, stale knowledge, and tool boundaries |
| Providers | Touch | Provider/model/harness distinctions without a product ranking |
| Interactions | Teach | Responses, tool calls, observations, approvals, retries, and termination |
| Steering | Teach | Context selection, instructions, evidence, constraints, and feedback |
| Settings | Teach | Visible model and harness settings, their limits, and reproducibility |
| Context | Teach | Context contents, authority, freshness, placement, cost, and failure behavior |
| Processing | Teach | How the system assembles, transforms, compacts, and updates model-visible state |
| Skills | Touch | Skills as reusable instructions and context; deeper construction belongs to Module 02 |
| Tools | Touch | Tool schemas, execution, and observations; deeper tool design belongs to Module 02 |
| Subagents | Touch | Subagent output as delegated work and context; coordination belongs to Module 02 |
| Files | Teach | Repository instructions, orientation, task state, evidence, and references |
| Style guides | Teach | Narrow durable guidance, scope, precedence, and maintenance |
| Specifications | Teach | Intent, constraints, acceptance, and decision provenance |
| Tasks | Teach | Current state, progress, stop conditions, and handoff |
| Libraries | Teach | Discoverable reference material and dependency knowledge |
| Research | Teach | Primary sources, provenance, freshness, and uncertainty |
| Harnesses | Teach | Agent loops, state, tools, sandbox, permissions, approvals, recovery, and telemetry |
| Interfaces | Teach | CLI, editor, chat, and automation interfaces as parts of system behavior |
| Workflows | Teach | Repeatable task framing, execution, verification, review, and learning |
| Teamwork | Touch | Async evidence review and team decision records; deeper delegation belongs to Module 02 |
| Product | Touch | Outcome framing and decision rights; deeper product judgment belongs to Module 03 |
| Quality | Teach | Falsifiable acceptance, regression checks, diff review, and independent evidence |
| User experience and UI | Touch | Workflow usability and human interaction costs; deeper treatment belongs to Module 03 |
| Security | Teach | Permissions, isolation, privacy, destructive actions, and approval boundaries |
| Business | Touch | Cost, time, risk, and adoption constraints; deeper treatment belongs to Module 03 |

## Delivery model

The core module contains five self-paced units and one async-first team
workshop. A synchronous 75-minute meeting is optional. The full controlled
experiment is an elective advanced lab.

| Unit | Core timebox | Learner activity | Required artifact |
| --- | ---: | --- | --- |
| 1. Models, loops, and harnesses | 45 minutes | Trace a real agent run and diagnose a failure at the correct layer | Annotated run trace and competing failure hypotheses |
| 2. Context engineering | 60 minutes | Compare bounded context configurations and inspect their effects | Context inventory and comparison |
| 3. Project knowledge | 75 minutes | Audit project knowledge and test one proposed improvement | Knowledge map and before/after discovery evidence |
| 4. Harnesses | 90 minutes | Compare two agent-system configurations on a bounded case | N=1 comparative case study |
| 5. Workflows | 60 minutes | Build and execute a reusable workflow | workflow-v1 and validation record |
| Async or synchronous workshop | 75 minutes | Challenge findings and make one decision | Decision record, team-authored when peers are available |

The total target is 405 minutes, or 6 hours and 45 minutes. Timeboxes include
required reading. Learners stop live execution at the timebox and use a
prepared evidence pack when needed.

## Learner-facing material

Each unit will contain:

1. An engineering question.
2. Measurable learning outcomes.
3. A 10-15 minute original lesson.
4. One required primary-source selection targeted at 10-15 minutes.
5. Optional deeper readings, documentation, and talks.
6. A worked example from Agent Experiment Ledger.
7. A hands-on exercise with a hard timebox.
8. A reusable artifact template.
9. Acceptance and self-review checks.
10. Async discussion prompts.
11. Optional advanced material.

The original lesson must be sufficient to understand the core concept. External
sources provide evidence, currency, competing views, and depth; they do not
replace teaching.

Provider-specific commands or screenshots belong in versioned appendices or
callouts. The core explanation and assessment remain provider-neutral.

## Module structure

~~~text
modules/01-agentic-engineering-fundamentals/
├── curriculum.md
├── units/
│   ├── 01-models-loops-harnesses.md
│   ├── 02-context-engineering.md
│   ├── 03-project-knowledge.md
│   ├── 04-harness-comparison.md
│   └── 05-reusable-workflows.md
├── exercises/
│   ├── run-trace-template.md
│   ├── context-comparison-template.md
│   ├── knowledge-map-template.md
│   ├── harness-case-study-template.md
│   ├── workflow-template.md
│   └── team-decision-template.md
├── workshop.md
├── facilitator-guide.md
├── lab.md
├── advanced-lab.md
├── sources.md
├── brief.md
├── codex-review.md
└── claude-review.md
~~~

Source-of-truth boundaries are:

- brief.md defines normative outcomes, gates, and deliverables.
- curriculum.md is the learner entry point, sequence, timing index, and
  coverage map.
- Unit files contain teaching.
- Exercise templates define artifact structure but do not duplicate lessons.
- lab.md defines the core integration exercise.
- advanced-lab.md defines the optional controlled experiment.
- sources.md is the only module-level source metadata registry.
- facilitator-guide.md contains facilitation guidance, misconceptions,
  evaluation examples, and contingencies that do not belong in learner text.
- Codex and Claude review files remain internal governance records, not learner
  prerequisites.

## Artifact chain and assessment

The five core artifacts form one connected chain:

1. The run trace establishes what the agent system actually did.
2. The context comparison tests how model-visible inputs changed behavior.
3. The knowledge map turns useful context into maintainable project structure.
4. The harness case study compares system configurations and their
   observability, authority, and outcomes.
5. workflow-v1 combines the strongest supported practices into an executable
   process.

Artifacts are evaluated as:

- **complete:** evidence-backed and satisfies every acceptance check;
- **revise:** incomplete evidence, unsupported causal claims, internal
  inconsistency, or failure to demonstrate the intended judgment; or
- **not attempted:** no assessable artifact.

File existence is never sufficient. Exercises require raw-evidence references,
observed behavior, competing hypotheses where causality is discussed,
disconfirming evidence, confounders, and explicit uncertainty.

Unit 4 is an N=1 comparative case study. It may reveal useful differences but
cannot isolate model, harness, and stochastic effects or establish universal
superiority.

Unit 5 validates that workflow-v1 is understandable, executable, bounded, and
capable of producing the required evidence. One execution does not prove that
the workflow improves performance.

## Core lab and advanced lab

The core lab connects the five unit artifacts around bounded, seeded work in
Agent Experiment Ledger. Exercises use exact starting revisions, deterministic
checks, safe permissions, and prepared evidence fallbacks.

Agent Experiment Ledger has two roles:

1. the shared codebase learners inspect and modify; and
2. an optional evidence store for structured run records.

It does not run agents, execute verification commands, parse transcripts,
scrub sensitive material, or select a winner. Learner instructions must state
those boundaries explicitly. Ledger records remain outside code-under-test
worktrees.

Before a pilot, the sample project must have an accessible reproducible
checkout, a tagged module baseline, installation instructions, seeded
exercises, sanitized evidence, JSON examples, and exact external verification
commands.

The advanced lab contains the three context treatments, cross-harness
comparison, and workflow validation from the original lab. It is labeled
exploratory unless conditions are replicated. Prior agent familiarity with the
ledger is a stated confounder; a fresh fixture is preferred when the advanced
lab aims to compare providers.

## Provider neutrality and fallbacks

The core requires two agent-system configurations, not two named commercial
products. Valid comparisons include:

- two different harnesses;
- two models in one harness;
- one model/harness with two permission or context configurations; or
- a learner run compared with a prepared evidence dossier.

Codex and Claude remain useful examples and retain their curriculum governance
roles. Learners do not need access to both.

Every live-run exercise includes:

- an execution timebox;
- a safe stop condition;
- a sanitized evidence pack;
- expected repository state and verification output; and
- instructions for recording unavailable telemetry as unknown.

## Async-first collaboration

Async participation is the default:

1. A learner posts a short artifact summary stating what was attempted, what
   happened, the evidence, the current conclusion, and uncertainty.
2. Another learner challenges one conclusion or applies a prepared failure
   scenario.
3. The author responds with evidence, revises the conclusion, or records the
   disagreement.
4. The facilitator synthesizes recurring findings.
5. The group records one practice to adopt, test further, or reject.

Templates must work in GitHub Discussions, pull-request comments, Slack,
Teams, email, or Markdown. No collaboration platform is required.

Peer participation improves the experience but cannot block completion. A
prepared critique and evidence pack provide the solo fallback; the learner then
writes the same decision record independently and labels it as a solo result.

If the group meets synchronously, the 75-minute agenda is:

1. calibration, 10 minutes;
2. paired failure diagnosis, 15 minutes;
3. artifact comparison, 20 minutes;
4. adversarial workflow review, 15 minutes;
5. team decision, 10 minutes; and
6. debrief, 5 minutes.

Roles rotate among facilitator, evidence presenter, skeptic, and recorder.
Peer consensus remains formative and is not independent verification.

## Facilitation

The facilitator guide will provide:

- preparation and setup checks;
- suggested cadence;
- unit and workshop timing;
- discussion prompts;
- expected evidence;
- example strong and weak answers;
- common misconceptions;
- group-size variants;
- async and solo fallbacks;
- recovery guidance for tool or setup failures; and
- a procedure for proposing course corrections.

The guide must let a competent software engineer facilitate the module without
being an expert in every agent product.

## Safety and privacy

Learners use isolated clones or worktrees and synthetic or approved data. The
course will not require production credentials, deployment, destructive
infrastructure changes, broad filesystem authority, or unrestricted network
access.

Personal transcripts, private source, credentials, and proprietary prompts do
not belong in the shared curriculum or sample-project repositories. Learners
share sanitized artifacts or summaries. Prepared evidence packs contain no
private data.

## Distribution and maintenance

The repositories will be public-ready even if the first rollout is internal.
That requires:

- original teaching and exercises;
- attribution to MEGA only for its public progression and claims;
- no dependency on company-private systems or data;
- explicit curriculum and sample-code licenses before external distribution;
- an accessible tagged sample-project baseline;
- deterministic setup and verification;
- module version and source-check dates;
- compatibility notes for time-sensitive tools;
- a changelog for material course changes; and
- frozen module versions during an active cohort.

The exact licenses are a learner decision. Before public distribution, the
implementation plan must present suitable documentation and code-license
options using official license terms. Internal sharing may begin only after the
organization's distribution rules are confirmed.

Fast-moving product, model, SDK, and security claims follow the freshness
policy in RUBRIC.md. Provider-specific material must be easy to replace without
rewriting provider-neutral lessons.

## Review and quality gates

Development uses five review layers:

1. **Author self-review:** check outcomes, correctness, evidence, workload,
   duplication, safety, and source freshness.
2. **Fresh-context learner simulation:** a sub-agent or reviewer follows the
   learner instructions without relying on author context.
3. **Independent curriculum critique:** a reviewer challenges coverage,
   teachability, workload, assessment validity, and unnecessary ceremony.
4. **Reproducible exercise run:** execute every required command and acceptance
   path exactly as written.
5. **Formal adversarial verification:** Claude applies the repository rubric,
   Codex responds to every finding, and Claude verifies the revision.

Findings use the shared blocker, major, minor, and note severities. Codex records
an accept, reject, or defer disposition with evidence. Material scope changes
and disagreements go into DECISIONS.md. Only the learner may mark the module
approved.

## Acceptance criteria

The Module 01 redesign is ready for learner approval when:

- the brief, curriculum, core lab, and advanced lab agree about required work;
- every MEGA Week 1 public agenda item is marked teach, touch, or defer;
- all five units contain original lessons, selected sources, exercises,
  artifacts, acceptance checks, and async prompts;
- core work fits the published timeboxes in a clean pilot;
- the core does not require two named providers;
- every live-run exercise has a prepared fallback;
- artifact checks can reject polished but unsupported work;
- the sample project is reproducibly accessible from a tagged baseline;
- the workshop works asynchronously, synchronously, and solo;
- safety and privacy boundaries are explicit;
- distribution prerequisites and versioning are documented;
- the lead self-review has no open blocker or major finding;
- Claude has reviewed and verified the final revision; and
- the learner has approved the module.

## Risks and mitigations

| Risk | Mitigation |
| --- | --- |
| The course becomes a link list | Require original self-contained lessons |
| Topic parity becomes shallow checkbox coverage | Require teach/touch/defer rationale plus artifacts |
| Exercises exceed the time budget | Seed bounded tasks and provide evidence-pack fallbacks |
| Polished artifacts hide weak reasoning | Require provenance, disconfirming evidence, and explicit uncertainty |
| Provider access differs across coworkers | Compare configurations and provide prepared dossiers |
| Prior project familiarity biases comparison | Label the core a case study and prefer a fresh advanced fixture |
| Async discussion stalls | Provide challenge templates, facilitator synthesis, and solo critiques |
| Source behavior changes | Track checked dates and isolate provider-specific material |
| Course and sample project drift apart | Tag baselines and freeze versions during cohorts |
| Public sharing creates licensing or privacy problems | Resolve licenses and remove private dependencies before distribution |

## Implementation boundary

The next implementation plan may redesign Module 01 artifacts and add the
supporting unit, exercise, workshop, facilitator, and advanced-lab files. It may
prepare public-ready packaging requirements for Agent Experiment Ledger.
Curriculum implementation remains Markdown-based and dependency-free unless
the learner approves a later change.

It may not publish repositories, select a license on the learner's behalf,
change later-module outcomes, add orchestration infrastructure, or claim that
the redesigned module has been successfully taught before a pilot provides
that evidence.
