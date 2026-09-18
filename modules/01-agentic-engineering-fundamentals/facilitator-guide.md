# Module 01 Facilitator Guide

This guide lets a competent software engineer facilitate the evidence review
without being an expert in every agent product. The core remains
provider-neutral, asynchronous-first, and governed by learner-owned approval. The facilitator
organizes evidence and synthesis; only the learner owns final approval,
authority expansion, and the decision to adopt a practice.

Use [workshop.md](workshop.md) for learner-facing instructions, the five unit
templates for artifact contracts, the prepared evidence packs for bounded
fallbacks, and the [team decision record](exercises/team-decision-template.md)
for the final output. Do not report this material as a pilot result: it is
course design, not evidence that a cohort has run it.

## Preparation

Before opening async review or a meeting:

1. **Verify source freshness.** Check the source registry’s checked dates and
   the freshness rules in `../../RUBRIC.md`; flag stale or unavailable claims
   as uncertain rather than refreshing them during a timed exercise.
2. **Verify ledger pins exist.** From the local Agent Experiment Ledger clone,
   resolve `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` and
   `2c498f616583d1fd6aeeaa381552b47acdb71ab7`. A missing pin means prepared
   evidence or a pause, not a substitute revision.
3. **Run setup and focused checks.** In a disposable checkout, run the unit’s
   setup and named focused checks before a live path. Retain command/result
   references outside code-under-test worktrees. Separate setup network access
   from a measured run’s authority.
4. **Review privacy and authority.** Confirm synthetic, sanitized, or approved
   data only; exclude raw transcripts, credentials, proprietary prompts,
   private source, and private absolute paths. Confirm no production,
   deployment, billing, destructive infrastructure, or unapproved authority.
   Run the focused private-path scan (`rg -n '/[U]sers/' README.md modules/01-agentic-engineering-fundamentals`) before internal-pilot handoff or release review; any tracked learner/facilitator hit blocks distribution until removed or replaced by a configured path.
5. **Confirm platform and setup boundary.** This internal pilot supports macOS
   or Linux with a POSIX shell. Treat dependency install as setup code execution,
   separate from a measured agent run. A verified non-POSIX alternative remains
   a public-release prerequisite.
6. **Use optional independent risk material narrowly.** S11, NIST AI 600-1,
   is optional facilitator/security material for risk framing and documenting
   evaluation/verification considerations. It is voluntary guidance, not a
   product-behavior source, a replacement for vendor documentation, or a
   required unit reading.
7. **Select live or prepared paths.** Choose by access, time, and safety, not
   prestige. Mark prepared evidence as prepared comparison material and retain
   unknown telemetry as `unknown`.
8. **Publish the timeboxes.** State unit limits, stop conditions, the async
   deadline, and, if used, the fixed 75-minute meeting agenda in advance.
9. **Create async threads.** Open one copyable Markdown thread per artifact
   summary/challenge pair, synthesis, and decision record; give solo learners a
   prepared critique and the solo-synthesis block at the same time.
10. **Decide feedback capture.** Name the location, owner, privacy review, and
   cadence for course feedback. Record proposed corrections with their evidence;
   do not silently change frozen tasks during a cohort.

## Cadence and facilitation moves

Run the five async stages in order: artifact summary, evidence-backed
challenge, author response or revision, facilitator synthesis, and decision
record. Peer availability cannot block completion. A facilitator can prompt for
provenance, competing hypotheses, a narrower claim, and a revisit trigger; do
not fill gaps with assumed tool behavior or approve a conclusion.

For solo work, the learner completes the same five records: artifact summary,
prepared or self-authored evidence-backed challenge, author response or
revision, solo synthesis, and decision record. The solo synthesis follows the
response and separates claims supported by cited evidence, unresolved
disagreement or uncertainty, and the material that carries into the decision
record. It is self-synthesis, not independent verification or approval.

For an optional meeting, use the exact agenda in [workshop.md](workshop.md):
10 minutes calibration, 15 paired failure diagnosis, 20 artifact comparison,
15 adversarial workflow review, 10 decision, and 5 debrief. Assign or rotate
facilitator, evidence presenter, skeptic, and recorder. Use the group variants
there exactly: solo prepared critique, solo synthesis, and solo record;
two-person reciprocal critique; one rotating-role group for 3–8; breakouts
with one synthesis recorder per group for more than 8.

## Evaluation examples

These are concise examples of evidence discipline, not model answers. Replace
the placeholder references with actual sanitized provenance in learner work.

| Artifact | Strong example | Weak example and why it fails |
| --- | --- | --- |
| Annotated run trace | “At baseline `bb65b5c`, the named suite passed; the reference adds a pre-publish fault-injection test. The earliest evidenced gap is verification. An omitted acceptance criterion remains possible, not proven.” | “The model caused the initialization bug.” No transcript or controlled evidence supports this causal diagnosis; source and verification layers remain plausible. |
| Context comparison | “Before opening results, the record predicted A and B failures with falsifiers; its per-item table keeps, revises, or rejects each B-only item by cost and follow-up evidence.” | “B had more files, so it was better context.” Quantity is treated as quality; a prediction after results or one aggregate decision omits prospective falsification, item-level value, controls, and cost. |
| Repository knowledge map | “The live before probe used only a root listing in a fresh context before named inventory or prepared results; the after probe used a second fresh context with only the map added. `README` is orientation, not the source of truth.” | “Copy every project note into a giant agent guide.” This either contaminates the before probe or duplicates project knowledge, creates competing authority, and has no retirement or freshness rule. |
| Harness-control case study | “The live or prepared evidence identifies the bounded control contract, its independent verification, unknowns, and one falsifiable next configuration change. Prepared material is `critically analyzed`; it records no candidate run, seam, or focused candidate result.” | “Provider X is best because it succeeded once.” One bounded case cannot establish a harness effect or superiority; the evidence must support only the local control decision and next test. |
| `workflow-v1` and validation record | “The independent evaluator withheld and then applied the named test artifact, recorded that an absent/unmatched artifact fails the gate, and observed the exact named TAP test with 1 pass/0 fail before regression and review.” | “The command exited 0 with pass 1, so workflow-v1 works.” Node can report a file-level pass for an unmatched pattern; completion language, exit status, or count alone is not independent verification. |
| Decision record | “Adopt the pre-edit source/test inspection for the frozen report task; evidence is the cited validation dossier and independent review. Revisit after three comparable tasks; this does not prove universal workflow improvement.” | “The group liked the workflow, so approve it.” Preference and consensus replace provenance, dissent, owner, revisit trigger, and learner approval authority. |

Mark an artifact `revise` when its conclusion exceeds evidence, when prepared
material is represented as a learner run, or when required unknowns and limits
are omitted. A clear disagreement with decisive evidence absent is a valid
`further-test` decision, not a facilitation failure.

`Artifact status: complete` means that the selected artifact contract is
complete; it never means that a learner executed a live path. During grading or
facilitation, inspect the decision record's per-unit capability/evidence table,
its provenance, and limitations. Mark the artifact `revise` when a prepared or
reference analysis is presented as execution.

## Recovery procedures

| Failure | Immediate fallback | Record the limitation |
| --- | --- | --- |
| Missing provider access | Use the relevant prepared evidence pack or evaluate the bounded case/control contract; do not require a named product. | Path selected, absent capability, evidence type, unavailable telemetry as `unknown`, and resulting scope limit. |
| Setup or dependency failure | Stop the live path; retain command, exit result, environment, and current state; use prepared evidence or return only after a human-approved setup fix. | Exact command/result, pin, runtime/package-manager version, network observation, stop reason, and next safe action. |
| Expired source link | Do not treat memory or a search snippet as evidence. Use a current registered primary source if already verified, or mark the claim unavailable and narrow the discussion. | URL, check date, failure, replacement provenance or `unavailable`, and affected claim. |
| Live run exceeds its timebox | Stop at the published limit; preserve diff and evidence, then switch to the prepared pack without widening task or authority. | Elapsed time, stop condition, approaches attempted, state/diff location, and live-versus-prepared limit. |
| Private evidence accidentally selected | Stop sharing; remove access through the available platform process, replace with sanitized evidence, and seek the appropriate human/privacy escalation before continuing. | That private material was selected (without repeating it), containment action, escalation recipient/status, replacement evidence, and residual limitation. |
| Absent peers | Use a prepared critique or strongest alternative explanation, author the solo synthesis, and complete the solo decision record. | `Participants: solo`, critique source, solo synthesis, missing peer interaction, and same evidence/uncertainty fields. |
| Disagreement without decisive evidence | Preserve both positions; choose `further-test` or no adoption; define the smallest discriminating evidence and owner. | Dissent, competing explanations, missing evidence, proposed probe, revisit trigger, and decision scope. |

## Closeout

Check that all five async stages have a record, every decision record identifies
whether it is solo or group work, and the conclusion stays local to its task,
baseline, configuration, and evidence. Capture course corrections separately
from learner decisions. Do not change publication state, select a license, or
mark the module approved.
