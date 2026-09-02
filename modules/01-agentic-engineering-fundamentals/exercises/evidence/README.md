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
- Prepared results cannot be presented as learner-run measurements.
- Store packs and learner evidence outside code-under-test worktrees.

## Minimum pack index

For each item, record:

| Item | Exercise/artifact consumer | Evidence type | Provenance | Sanitization review | What it can support | What remains uncertain |
| --- | --- | --- | --- | --- | --- | --- |
|  |  | prepared comparison material |  |  |  |  |

## Learner use

Record whether the artifact uses a live learner run or prepared comparison
material. Cite the pack item in the artifact, preserve the stated uncertainty,
and make a keep, revise, reject, or further-test decision only within what the
evidence can support.
