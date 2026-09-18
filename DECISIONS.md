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

## D-007 — Proposed capability evidence and Unit 4 evaluation contract

- Date: 2026-09-02
- Status: proposed
- Decider: learner (pending)
- Context: The internal pilot needs a no-cost prepared path without allowing a prepared dossier to masquerade as live implementation/workflow execution. Unit 4 also needs deterministic evaluation without preloading the agent's test-design task with the evaluator-owned test.
- Proposal or critique: The Task 12 controller proposes per-unit `executed` or `critically analyzed` evidence labels, with either satisfying its selected artifact contract. The frozen Unit 4 task keeps test design with the learner or agent. After a measured run, an independent evaluator uses only the candidate's documented deterministic seam for a behavior-level test; the exact `2c498f6` reference test remains reference evidence, not a candidate API or universal oracle.
- Decision: Pending learner decision. The implementation is provisional for review and requires the learner's explicit decision before it is treated as an approved curriculum decision.
- Reason: The proposal preserves no-cost prepared participation without overstating execution and evaluates the intended publication behavior without exposing or forcing a reference-only seam.
- Evidence: Task 12 fresh-learner and independent-review findings I-002, I-003, and I-005; Task 12 controller disposition for fix round 1; the prepared dossier distinguishes repository evidence from a live agent trace.
- Change made: Provisional updates to Module 01 outcome/completion language, Unit 4/5 instructions and templates, lab, workshop, and prepared packs.
- Revisit when: The learner explicitly decides this proposal and a timed human/cohort pilot establishes whether the labels and post-run evaluation procedure are understandable and usable without author assistance.

## D-008 — Proposed boundary for required non-vendor reading selection

- Date: 2026-09-02
- Status: proposed
- Decider: learner (pending)
- Context: S11 is an optional official non-vendor facilitator/security source, while product documentation remains qualified for product behavior.
- Proposal or critique: The Task 12 controller proposes keeping S11 optional and not making a non-vendor source a required learner reading until a bounded learner-facing selection and its purpose are designed.
- Decision: Pending learner decision. The provisional implementation leaves S11 optional and keeps vendor documentation qualified to its product behavior; it does not record a learner deferral or decision.
- Reason: An optional facilitator source does not by itself establish a focused required-reading experience.
- Evidence: Task 12 independent-review finding I-008 and controller disposition for fix round 1.
- Change made: Provisional documentation only; no required reading was added.
- Revisit when: A bounded learner-facing source selection is proposed for the learner's explicit decision.

## D-009 — Proposed contraction of the Unit 4 comparison outcome

- Date: 2026-09-18
- Status: proposed
- Decider: learner (pending)
- Context: Claude finding C-001 correctly observes that Unit 4's live run and prepared dossier are two evidence paths, not two agent-system configurations. The approved brief and roadmap still promise a two-configuration comparison, while the unit has a fixed 90-minute cap and a provider-neutral, no-cost prepared route.
- Proposal or critique: An independent redesign review recommends contracting Unit 4 to one bounded run or prepared implementation dossier assessed against an explicit harness-control and independent-verification contract, followed by one falsifiable proposed configuration change. Preserving the existing comparison outcome would instead require a genuinely paired dossier or two live runs, verified tool controls, and a larger or revalidated time budget.
- Decision: Pending learner decision. Do not silently treat the existing dossier as a second configuration, shorten two implementation runs without evidence, or claim C-001 is closed.
- Reason: The contraction is the smallest rigorous 90-minute, provider-neutral design, but it changes an approved outcome and therefore requires learner authority under the roadmap change rule.
- Evidence: Claude review C-001; independent Unit 4 redesign audit dated 2026-09-18; current Unit 4 arithmetic of `12 + 10 + 10 + 35 + 18 + 5 = 90` minutes.
- Change made: No outcome or comparison-structure change pending the learner's decision. Other review findings may be remediated independently.
- Revisit when: The learner chooses the single-case contraction or authorizes the additional paired evidence and time-budget redesign needed to retain a true two-configuration comparison.

## D-010 — Retain S01's visible publication date

- Date: 2026-09-18
- Status: rejected
- Decider: Codex
- Context: Claude finding C-006 reported that S01's `2026-08-19` publication date was not visible on 2026-09-04 and proposed changing it to `not stated`.
- Proposal or critique: Remove the recorded date unless a visible first-party source supports it.
- Decision: Reject the requested metadata change and retain `2026-08-19`.
- Reason: On 2026-09-18 the cited first-party article visibly displays “Aug 19, 2026.” The reviewer's earlier observation remains a valid time-bounded observation, but it no longer describes the current page.
- Evidence: OpenAI, “Codex as a platform,” `https://developers.openai.com/blog/codex-as-a-platform`, checked 2026-09-18; `research/module-01-review-source-validation-2026-09-18.md`.
- Change made: Preserve S01's publication date and record the recheck in the source registry.
- Revisit when: The visible source metadata changes or a stable first-party archive supersedes the rolling page.
