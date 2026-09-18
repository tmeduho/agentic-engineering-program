# Evidence Packs

Evidence packs are sanitized fallbacks for a timeboxed exercise. They let a
learner finish without a second paid provider; they are not hidden answer keys
and do not replace judgment, artifact completion, or the stated acceptance
checks.

## Boundaries

- Every observation is labeled `actual repository evidence`, `prepared
  comparison material`, or `hypothetical counterexample`.
- Raw private transcripts are forbidden. Do not include credentials, private
  source, proprietary prompts, or unsanitized conversation exports.
- Commit and file references carry provenance: repository identifier, exact
  commit or baseline, path, and command/output reference where applicable.
- Unavailable telemetry remains `unknown`; do not estimate it or borrow it
  from another harness.
- Prepared results cannot be presented as learner-run measurements or execution
  capability. They can evidence `critically analyzed` work when the learner
  completes the stated analysis and provenance record.
- Store packs and learner evidence outside code-under-test worktrees.

## Minimum pack index

For each item, record:

| Item | Exercise/artifact consumer | Evidence type | Provenance | Sanitization review | What it can support | What remains uncertain |
| --- | --- | --- | --- | --- | --- | --- |
| [Unit 1 run trace](unit-01-run-trace.md) | Unit 1 annotated run trace | prepared comparison material | P01 baseline/reference pins named in the pack; pack also cites actual repository evidence | Sanitized pack; no private transcript or credential | Initialization publication boundary and baseline/reference command evidence | No learner-run trace or provider/harness attribution |
| [Unit 2 context comparison](unit-02-context-comparison.md) | Unit 2 context comparison | prepared comparison material | P01 baseline/reference pins named in the pack; pack also cites actual repository evidence | Sanitized packets and source evidence | Context-treatment comparison and raw traversal evidence | No learner-run measurement; ambient instruction loading may be unknown |
| [Unit 3 knowledge audit](unit-03-knowledge-audit.md) | Unit 3 repository knowledge map | prepared comparison material | P01 baseline/reference pins named in the pack; pack also cites actual repository evidence | Sanitized map and discovery records | Source-of-truth, precedence, and discovery analysis | No learner-run before/after probe or timing claim |
| [Unit 4 harness case study](unit-04-harness-case-study.md) | Unit 4 N=1 harness case study | prepared comparison material | P01 baseline/reference pins named in the pack; pack also cites actual repository evidence | Sanitized implementation evidence and review | Publication-boundary invariants and evaluator-seam analysis | No live candidate run, candidate seam, or provider/harness attribution |
| [Unit 5 workflow validation](unit-05-workflow-validation.md) | Unit 5 workflow validation record | prepared comparison material | P01 baseline/reference pins named in the pack; pack also cites actual repository evidence | Sanitized validation dossier and command evidence | Workflow acceptance, negative-control, and regression-gate analysis | No learner-run cold-reader validation or general workflow claim |

## Learner use

Record whether the artifact uses a live learner run or prepared comparison
material. Cite the pack item in the artifact, preserve the stated uncertainty,
and make a keep, revise, reject, or further-test decision only within what the
evidence can support.
