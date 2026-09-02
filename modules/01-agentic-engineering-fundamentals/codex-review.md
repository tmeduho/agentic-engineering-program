# Codex Review Record — Module 01

This is the lead self-review. It records readiness for Claude's independent
adversarial review; it is not independent verification and does not make the
module verified, approved, published, or public-ready.

## Current handoff

- Status: ready for Claude independent adversarial review
- Validated content revision reviewed/submitted:
  `6380db1837654b2d812ed404bcb49dbf1a31b5f2`
- Review-record commit: intentionally not named here; this record cannot review
  the commit that contains it.
- Provisional decisions: D-007 and D-008 remain proposed with learner decision
  pending.
- Remaining prerequisites: timed human/cohort and live cold-reader pilot;
  public P01 access/release; curriculum and P01 licenses; verified non-POSIX
  instructions; bounded required non-vendor reading decision; and the recorded
  network/package-store setup limitation.

## Review metadata

- Module: 01 — Agentic Engineering Fundamentals
- Revision or commit: `6380db1837654b2d812ed404bcb49dbf1a31b5f2`
- Review type: lead self-review
- Reviewer: Codex (`gpt-5.6-terra`, high)
- Review date: 2026-09-02
- Source freshness cutoff date: 2026-09-02
- Artifacts reviewed: brief, curriculum, five units, six templates, six
  evidence-pack files, lab, advanced lab, workshop, facilitator guide, sources,
  DECISIONS, ROADMAP, RUBRIC, P01 evidence, Task 12 pilot reports, and the SDD
  dispatch/review ledger.
- Model/effort routing and escalation history: Tasks 1–2 and 10–11 used Terra
  medium for bounded semantic/document work; Tasks 4 and 8 used Terra high for
  evidence-grounded technical teaching; Task 12 used Terra high for the pilot
  and synthesis. Fresh-learner re-reviews used Terra medium; whole-curriculum
  critiques used Sol high. Escalations resolved the Task 2 P01-source support,
  Task 4 command/cleanup evidence, Task 8 focused reference evidence, the
  Unit 4 evaluator-oracle boundary, and the D-007/D-008 authority errors.

## Hard-gate check

| Gate | Result | Evidence or required change |
| --- | --- | --- |
| Outcomes are measurable and fully covered. | pass | `brief.md` has five outcome/artifact acceptance mappings; `curriculum.md` and `lab.md` connect all five artifacts plus the decision record. |
| Technical correctness has no known material error. | pass | P01 pins resolve; phase 1 reproduced baseline 110/110 and reference 121/121, plus the named Unit 4 and Unit 5 focused tests. Current content keeps claims local and qualified. |
| No open blocker findings remain. | pass | Final fix-round re-review found none. Release prerequisites are not internal blockers for independent review. |
| No unaccepted major findings remain. | pass | Fresh-learner, critic, mixed-path, oracle, D-007, D-008, compact-summary, and cold-reader findings have recorded dispositions and re-review evidence. |
| Fast-moving claims satisfy the source-freshness policy. | pass | `sources.md` is the sole registry; current product/engineering sources were checked 2026-09-02, the cutoff date. |
| Important claims use primary sources when available. | pass | S01–S10 are first-party product/engineering sources; P01 is primary local repository evidence; S11 is optional official NIST material. |
| The lab exercises the stated skills rather than adjacent skills. | pass | Units 1–5 respectively exercise trace, context, knowledge, harness, and workflow decisions; prepared paths label analysis rather than execution. |
| The lab has a baseline and reproducible procedure. | pass | `lab.md` and unit instructions freeze P01 `bb65b5c`; packs retain reference `2c498f6`, commands, authority, and evidence location. |
| Acceptance checks can falsify a bad outcome. | pass | Unit 4 behavior invariants and Unit 5 complete-request validation reject observable bad states; independent checks include focused test, full suite, check, build, and review. |
| Verification includes a channel independent of the producing agent. | pass | Evaluator/independent reviewer checks, source/diff review, and fresh-context review are required; prepared evidence is provenance-labeled. |
| Production risks and decision rights are addressed where applicable. | pass | Units 4–5 and lab specify authority, no-network measured runs, escalation, recovery, privacy, output containment, and decision owner. |
| Beginner material is absent or explicitly justified. | pass | `brief.md` targets experienced engineers; non-goals exclude general LLM history and beginner prompting. |
| Every prior finding has a recorded disposition. | pass | Findings table below covers Tasks 1/2/4/8/10/11 and all Task 12 pilot/re-review findings. |

## Scores

| Dimension | Score | Evidence | Highest-value improvement |
| --- | ---: | --- | --- |
| Technical correctness | 4 | Qualified source map, pinned P01 evidence, reproducible focused/full checks, and final oracle boundary. | Recheck product pages and P01 commands after the next material dependency change. |
| Technical depth | 5 | Failure atomicity, authority, context comparability, source retirement, runtime validation, confounders, and workflow recovery are taught through artifacts. | Keep later modules from duplicating these mechanisms. |
| Production relevance | 5 | Permission, safety, privacy, network, rollback, review, and decision-right boundaries are explicit in the core lab. | Validate operational burden with the human pilot. |
| Source quality and currency | 4 | Current first-party registry and P01 primary evidence are strong; S11 is scoped optional. | Decide whether a bounded non-vendor learner reading earns required status. |
| Lab validity | 4 | Frozen baseline, falsifiable checks, independent channels, prepared/live separation, and a concrete cold-reader default support the stated skills. | Run the timed human/cohort and live cold-reader pilot. |
| Verification quality | 4 | Focused acceptance, full gates, state inspection, source/diff review, and external evaluator requirements reduce self-report risk. | Collect live candidate-seam variability evidence for Unit 4. |
| Personal relevance | 5 | The course is free to participate in, provider-neutral, async-first, senior-oriented, and produces reusable evidence artifacts. | Confirm the time cost with the learner/cohort. |
| Coherence and efficiency | 4 | Five cumulative artifacts, compact prepared substitute, per-unit capability table, and elective advanced lab avoid a sixth core implementation task. | Use pilot evidence to remove any step that only transfers work to a human. |
| **Total / 40** | **35** | `4 + 5 + 5 + 4 + 4 + 4 + 5 + 4 = 35`; the prior 37/40 claim was arithmetic error. | Preserve the 32/40 threshold and reassess after live pilot evidence. |

## Source audit

| Claim | Source ID or URL | Primary? | Fresh? | Supports claim? | Notes |
| --- | --- | --- | --- | --- | --- |
| Agent outcome depends on more than the model. | S01, S06, P01 | yes | yes | yes | Product/harness claims remain qualified by configuration. |
| Context includes more than the prompt and is finite. | S02, S06, S09 | yes | yes | yes | Unit 2 does not claim a universal context schema. |
| Harness/session/sandbox boundaries and recovery matter. | S03, S04, S05 | yes | yes | yes | Case-study guidance, not a provider ranking. |
| Permissions, sandboxing, and approvals are distinct controls. | S01, S08 | yes | yes | yes | Product-specific behavior is not generalized to every harness. |
| P01 has the named local fault/validation boundaries. | P01 at `bb65b5c..2c498f6` | yes | yes | yes | Phase 1 reproduced reference 121/121 and focused tests 1/1. |
| N=1 does not establish universal model or harness superiority. | S03, S04, P01 | yes | yes | yes | Unit 4 records confounders and local scope. |
| Governance/risk framing can support facilitator review. | S11 | yes | current registry | yes, scoped | Optional NIST material only; not product behavior or required reading. |

| Candidate | Why it might improve or contradict the module | Disposition |
| --- | --- | --- |
| [Mytkowicz et al., “Producing Wrong Data Without Doing Anything Obviously Wrong!”](https://research.ibm.com/publications/producing-wrong-data-without-doing-anything-obviously-wrong) (ASPLOS 2009) | Independent systems evidence that seemingly innocuous setup variation can bias experimental conclusions; it would reinforce infrastructure-noise controls in the advanced experiment. | Defer from required reading and registry expansion. It is a useful candidate for a bounded future advanced-lab source selection, but it is older systems-performance evidence and does not establish current agent-product behavior. |

## Lab audit

- Stated skill under test: make bounded evidence-backed decisions about model,
  context, knowledge, harness, and workflow layers.
- Baseline/control: P01 `bb65b5c` in isolated disposable worktrees; prepared
  packs map the exact baseline/reference evidence without presenting it as a
  learner run.
- Independent variables: Unit 2 context packets; Unit 4 configuration/harness
  choice; Unit 5 workflow use. The advanced lab controls these more strictly.
- Controlled variables: frozen task, baseline, acceptance, authority, stop
  rules, and environment recording where a live comparison is attempted.
- Observable outcomes: deterministic focused acceptance, check/test/build,
  destination/staging state, source/diff review, artifact contracts, and
  provenance-labeled decision record.
- Confounders: model/harness settings, ambient context, telemetry gaps, setup
  network/store condition, test-design/seam variation, prior familiarity, and
  prepared-versus-live differences.
- Failure and recovery path: explicit stop, evidence retention, rollback/fresh
  checkout, escalation to a named human, and Unit 4/5 invalid-outcome checks.
- Permission and data boundary: workspace-local authority, no network during
  measured paths, approval for expansion, synthetic/sanitized data, evidence
  outside code-under-test worktrees, and no private transcripts/credentials.
- Independent verifier: evaluator-owned behavior-level check where applicable,
  independent source/diff review, and Claude's upcoming adversarial review.
- Can the checks pass while the real outcome is bad? Yes: a known-task
  cold-reader run can show workflow usability but not generalization; prepared
  artifacts can satisfy analysis contracts but not execution skill. Both limits
  are explicit and require future pilot evidence before learner approval/release.

## Adversarial questions

1. What is the strongest claim that could be false? The planned 405-minute cap
   may not fit experienced human learners in a real environment.
2. What source or experiment would disprove it? Timed human/cohort runs with
   recorded setup, path, intervention, and stop reasons.
3. Which mechanism or production failure mode is missing? Unit 4 cannot yet
   show how often real candidates expose usable deterministic seams.
4. What content assumes older model, harness, SDK, or protocol behavior?
   Provider documentation and product controls; `sources.md` requires refresh
   and scopes claims to the documented configuration.
5. What could an experienced engineer skip without losing the outcome? Optional
   depth and the elective advanced lab; core artifacts retain the required
   decisions and verification.
6. What advanced prerequisite has been assumed but not established? A supported
   coding-agent setup and local P01 access for live paths; prepared packs are
   the documented fallback.
7. Does the lab test the module's outcome or merely generate an artifact? It
   tests observable artifacts with acceptance/regression/review gates, but live
   workflow generalization remains unproven pending the pilot.
8. What simpler workflow might achieve the same result? Inspect source/tests,
   state authority and acceptance, make the smallest change, run independent
   checks, and retain a concise decision record; the template must not grow
   beyond evidence-supported steps.
9. Where would multiple agents add coordination cost without enough benefit?
   A core live run does not require multiple agents; async/solo paths preserve
   completion when peers are unavailable.
10. What result would cause us to revise the curriculum itself? Repeated pilot
    ambiguity, unsafe authority expansion, non-comparable A/B runs, failures of
    the evaluator procedure, or human timing beyond the stated caps.

## Findings

| ID | Severity | Artifact/section | Finding | Evidence | Required change | Status |
| --- | --- | --- | --- | --- | --- | --- |
| T1-001 | major | Brief | Evidence location, learner-only approval, and elective-lab scope were omitted. | Task 1 review ledger. | Add all three normative boundaries. | accepted and fixed in `0e2e036`. |
| T2-001 | major | Sources | R01/P01 metadata was incomplete; P01 support needed confirmation. | Task 2 review and controller pin inspection. | Complete metadata and substantiate pins. | accepted and fixed in `85d72f8`. |
| T4-001 | major | Unit 1/template | Trace lacked falsifiable agent-loop/harness mapping. | Task 4 review. | Add shared layer mapping and prepared example. | accepted and fixed in `85b5fc9`. |
| T4-002 | major | P01 evidence | Reported commands/cleanup required independent substantiation. | Fresh detached run: baseline 110/110, reference 121/121, check/build. | Bound install claim to reporter output and retain exact evidence. | accepted and resolved. |
| T8-001 | minor | Unit 5/template | Six-field record and `remove` vocabulary were not shared by the template. | Task 8 review, phase-1 audit. | Add mandatory table and canonical `keep | revise | remove`. | deferred to Task 12, then accepted and fixed. |
| T10-001 | major | Workshop/solo | Solo path omitted facilitator synthesis; decision vocabulary drifted. | Task 10 review. | Add the missing stage and align terms. | accepted and fixed in `5f08288`. |
| T11-001 | blocker | Curriculum entry | Start page weakened the six-condition completion contract. | Task 11 review. | Restore safety, live/prepared, and evidence-boundary clauses. | accepted and fixed in `7b5a253`. |
| T12-L1 | blocker | Unit 5 prepared path | Fresh learner stopped at 1m56: no prepared substitute, step schema, result provenance, or `remove` mapping. | Fresh learner simulation. | Add prepared substitute, table, provenance, and vocabulary. | accepted and fixed; later re-reviewed. |
| I-001 | blocker for public distribution | Paths/release | Personal paths and unresolved P01 access/licenses blocked public distribution. | Independent critique. | Remove personal paths; retain release prerequisites. | accepted/partly remediated; release deferred. |
| I-002 | major | Outcomes/assessment | Prepared work could overstate execution capability. | Independent critique. | Separate `executed` from `critically analyzed`. | accepted and fixed. |
| I-003 | major | Unit 4 | Reference test ownership could preseed assessed test design. | Independent critique. | Preserve candidate test design and independent post-run evaluation. | accepted and refined by oracle fix. |
| I-004 | major | Timeboxes | 405 looked like an empirical estimate without human evidence. | Independent critique. | Label planned caps and require human/cohort pilot. | partly accepted; unsupported implausibility claim rejected. |
| I-005 | major | Unit 5 | Cold-reader validation was absent. | Independent critique. | Require live validation or prepared analysis boundary. | accepted and later made turnkey. |
| I-006 | major | Unit 2 | Ambient/model-visible context could collapse A/B treatment. | Independent critique. | Record ambient context and mark non-comparable when unbounded. | accepted and fixed. |
| I-007 | minor | Harness records | Resource/enforcement/infrastructure fields were missing. | Independent critique. | Add fields with `unknown` valid. | accepted and fixed. |
| I-008 | minor | Sources | Independent official material was missing. | Independent critique. | Add optional S11; decide required reading separately. | accepted; D-008 remains proposed/pending. |
| I-009 | minor | Platform/setup | Supported shell/platform and install boundary were unclear. | Independent critique. | State POSIX pilot support and setup execution boundary. | accepted and fixed; release platform work deferred. |
| I-010 | minor | Status/freshness | Approval wording and duplicate freshness metadata drifted. | Independent critique. | Use learner-owned authority; sole registry. | accepted and fixed. |
| I-011 | minor | Unit 3 | Research/Libraries assessment was insufficient. | Independent critique. | Add bounded authority/provenance/freshness/retirement check. | accepted and fixed. |
| R1-001 | major | Unit 5 | Compact prior-artifact substitute was promised but absent. | Fresh re-review completed in 2m30. | Ship direct provenance-labeled summary. | accepted and fixed in `987c5a3`; final fresh completion 2m09. |
| R1-002 | minor | Facilitation | `complete` could be read as `executed`. | Fresh re-review. | Require evaluator inspection of per-unit capability/provenance. | accepted and fixed. |
| R1-003 | major | Decision record | A chain-wide binary label could not represent mixed paths. | Curriculum re-review. | Use per-unit capability/evidence table. | accepted and fixed. |
| R1-004 | major | Unit 4 evaluator | Exact reference hook was not a universal candidate oracle. | Curriculum re-review. | Freeze behavior invariants; adapt only to candidate seam. | accepted and fixed. |
| R1-005 | major | D-007 | Record invented learner assent. | Curriculum re-review. | Make controller proposal, learner pending. | accepted and fixed; D-007 proposed. |
| R2-001 | major | D-008 | Record stated controller deferral as learner-pending decision. | Fix-round re-review. | Make controller proposal with pending learner decision. | accepted and fixed; D-008 proposed. |
| R2-002 | minor | Unit 5 cold reader | Live validation lacked fixture/selection rule and external command. | Fresh re-review. | Add P01 default, withheld evaluator test, and exact gates. | accepted and fixed in `6380db`. |

## Verdict

- Recommendation: pass to independent adversarial review
- Open blockers: none within adversarial-review readiness.
- Open majors: none within adversarial-review readiness.
- Accepted exceptions and decision IDs: D-006 is accepted design policy;
  D-007 and D-008 are proposed, learner-pending decisions rather than accepted
  exceptions. Public P01 access/release, both licenses, verified non-POSIX
  setup, timed human/cohort and live cold-reader validation, bounded required
  non-vendor reading, and the network/store setup limit remain deferred
  prerequisites for learner approval or public release.
- Verification performed: Task 12 phase-1 structural checks; five prepared
  template/pack comparisons; isolated P01 baseline/reference and focused test
  evidence; fresh learner simulations; independent curriculum critiques;
  fix-round link/anchor, count, matrix, authority, oracle, and cold-reader
  contract checks.
- Concise rationale: `35/40` meets the review-readiness threshold, no dimension
  is below 3, technical correctness and lab validity are at least 4, and no
  internal blocker/major remains. Claude must independently challenge this
  conclusion; no approval or public-release claim follows from this handoff.
