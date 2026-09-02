# Decision Log

This is an append-only record of material curriculum decisions and agent disagreements. Correct factual errors in place; otherwise supersede an old decision with a new entry rather than erasing the history.

## Entry format

```markdown
## D-XXX — Short title

- Date: YYYY-MM-DD
- Status: proposed | accepted | rejected | deferred | superseded
- Decider: learner | Codex | Claude | joint
- Context:
- Proposal or critique:
- Decision:
- Reason:
- Evidence:
- Change made:
- Revisit when:
```

## D-001 — Start with a manual, document-based workflow

- Date: 2026-08-26
- Status: accepted
- Decider: learner
- Context: Codex and Claude need shared state, provenance, and repeatable review without building infrastructure prematurely.
- Proposal or critique: Begin with repository instructions, module artifacts, reviews, and Git history; add orchestration only after observing the manual process.
- Decision: No dependencies, hooks, CLI wrapper, scheduled jobs, or automatic model handoffs in the initial scaffold.
- Reason: The manual cycle can prove whether independent review improves curriculum quality before automation cost is incurred.
- Evidence: The initial design discussion and approved scaffold.
- Change made: The repository contains Markdown artifacts only.
- Revisit when: At least two complete lead/reviewer cycles expose repetitive, stable handoff work.

## D-002 — Alternate lead ownership by module

- Date: 2026-08-26
- Status: accepted
- Decider: learner
- Context: Fixing one model as author and the other as critic would confound model capability with assigned role.
- Proposal or critique: Codex leads odd-numbered modules; Claude leads even-numbered modules. The non-lead performs adversarial review and final verification.
- Decision: Adopt the alternating protocol.
- Reason: Each model must demonstrate authorship and review skill, and alternating reduces role anchoring.
- Evidence: The approved collaboration design.
- Change made: Ownership is recorded in `README.md` and `ROADMAP.md`.
- Revisit when: Review quality or tool access creates a persistent asymmetry.

## D-003 — Treat source freshness as a quality gate

- Date: 2026-08-26
- Status: accepted
- Decider: learner
- Context: Models, coding agents, SDKs, MCP, and operating guidance can change faster than a static course.
- Proposal or critique: Require checked dates and bounded freshness windows for time-sensitive claims.
- Decision: Apply the source policy in `RUBRIC.md` to every module.
- Reason: A current, custom curriculum is a core advantage over a fixed course.
- Evidence: MCP's July 2026 protocol revision is a concrete example of older tutorials becoming materially inaccurate.
- Change made: Source metadata and freshness checks are mandatory.
- Revisit when: A source class needs a different refresh interval.

## D-004 — Preserve MEGA as a reference, not a template

- Date: 2026-08-26
- Status: accepted
- Decider: learner
- Context: The custom program originated as an alternative to purchasing MEGA and should retain the evidence used in that comparison.
- Proposal or critique: Capture MEGA's public curriculum, format, promises, and evaluation notes in a dated research snapshot.
- Decision: Keep `research/mega-dev-curriculum.md`, distinguish public facts from user-provided pricing and our own inference, and recheck it before purchase decisions.
- Reason: This preserves provenance while preventing the paid course from becoming an unquestioned syllabus.
- Evidence: MEGA's public site, its public assessment artifact, and the referenced ChatGPT conversation.
- Change made: Added the dedicated research snapshot and source-index entries.
- Revisit when: MEGA publishes lesson materials, outcomes, a new cohort, or material curriculum changes.

## D-005 — Use four major modules and twenty units

- Date: 2026-08-26
- Status: accepted
- Decider: learner
- Context: The requested first module is `01-agentic-engineering-fundamentals`, while the reference curriculum uses four weeks and twenty daily lessons.
- Proposal or critique: Represent each major theme as one module with five units rather than creating twenty module directories upfront.
- Decision: Start with four modules and scaffold only Module 01.
- Reason: This retains the useful progression while keeping the repository minimal and allowing later units to change before they are built.
- Evidence: The approved minimal-scaffold design and MEGA curriculum structure.
- Change made: `ROADMAP.md` defines four modules; only Module 01 exists.
- Revisit when: A module becomes too large to review or execute coherently.

## D-006 — Adopt a free hybrid course and separate the advanced experiment

- Date: 2026-09-02
- Status: accepted
- Decider: learner
- Context: The initial Module 01 draft made a five-run controlled experiment a core requirement. The learner wants an original course that coworkers can use without a curriculum fee, with comparable coverage to MEGA's public progression and realistic participation during a busy schedule.
- Proposal or critique: Use five concise self-paced units, async-first discussion, an optional synchronous workshop, provider-neutral core exercises, evidence-backed artifacts, and an optional advanced controlled experiment.
- Decision: Adopt the hybrid delivery model in docs/superpowers/specs/2026-09-02-module-01-hybrid-curriculum-design.md. Make the five-run experiment elective. Prepare the repositories for eventual public distribution without selecting licenses or publishing them in this change.
- Reason: This retains the desired subject coverage while reducing core workload, avoiding unnecessary provider requirements, and supporting coworkers who cannot attend live sessions.
- Evidence: Learner approvals recorded during the 2026-09-02 design discussion and the independent design critique incorporated into the approved spec.
- Change made: Module 01 outcomes, curriculum, lab, exercises, workshop, facilitation, and reviews will be aligned with the approved hybrid design.
- Revisit when: A pilot shows that the timeboxes, artifact chain, provider-neutral fallbacks, or async format do not produce the intended learning.
