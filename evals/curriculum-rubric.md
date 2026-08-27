# Curriculum Review Worksheet

Use this worksheet for every lead self-review, adversarial review, and final verification. Record the completed evaluation in the reviewing agent's module review file; do not overwrite this template.

The scoring definitions and gates in `../RUBRIC.md` are normative.

## Review metadata

- Module:
- Revision or commit:
- Review type: lead self-review | adversarial review | final verification
- Reviewer:
- Review date:
- Source freshness cutoff date:
- Artifacts reviewed:

## Hard-gate check

Mark each item `pass`, `fail`, or `not-applicable`; explain every non-pass.

| Gate | Result | Evidence or required change |
| --- | --- | --- |
| Outcomes are measurable and fully covered. |  |  |
| Technical correctness has no known material error. |  |  |
| No open blocker findings remain. |  |  |
| No unaccepted major findings remain. |  |  |
| Fast-moving claims satisfy the source-freshness policy. |  |  |
| Important claims use primary sources when available. |  |  |
| The lab exercises the stated skills rather than adjacent skills. |  |  |
| The lab has a baseline and reproducible procedure. |  |  |
| Acceptance checks can falsify a bad outcome. |  |  |
| Verification includes a channel independent of the producing agent. |  |  |
| Production risks and decision rights are addressed where applicable. |  |  |
| Beginner material is absent or explicitly justified. |  |  |
| Every prior finding has a recorded disposition. |  |  |

## Scores

Use integers from 1 to 5. Cite a source, artifact section, or observed check for every score.

| Dimension | Score | Evidence | Highest-value improvement |
| --- | ---: | --- | --- |
| Technical correctness |  |  |  |
| Technical depth |  |  |  |
| Production relevance |  |  |  |
| Source quality and currency |  |  |  |
| Lab validity |  |  |  |
| Verification quality |  |  |  |
| Personal relevance |  |  |  |
| Coherence and efficiency |  |  |  |
| **Total / 40** |  |  |  |

## Source audit

For each material claim, verify that the cited source supports the exact claim and remains current.

| Claim | Source ID or URL | Primary? | Fresh? | Supports claim? | Notes |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

Record at least one independent source candidate that the lead did not select:

| Candidate | Why it might improve or contradict the module | Disposition |
| --- | --- | --- |
|  |  |  |

## Lab audit

- Stated skill under test:
- Baseline/control:
- Independent variables:
- Controlled variables:
- Observable outcomes:
- Confounders:
- Failure and recovery path:
- Permission and data boundary:
- Independent verifier:
- Can the checks pass while the real outcome is bad? If yes, how?

## Adversarial questions

Answer directly:

1. What is the strongest claim that could be false?
2. What source or experiment would disprove it?
3. Which mechanism or production failure mode is missing?
4. What content assumes older model, harness, SDK, or protocol behavior?
5. What could an experienced engineer skip without losing the outcome?
6. What advanced prerequisite has been assumed but not established?
7. Does the lab test the module's outcome or merely generate an artifact?
8. What simpler workflow might achieve the same result?
9. Where would multiple agents add coordination cost without enough benefit?
10. What result would cause us to revise the curriculum itself?

## Findings

| ID | Severity | Artifact/section | Finding | Evidence | Required change | Status |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  | open |

## Verdict

- Recommendation: pass | revise | reject
- Open blockers:
- Open majors:
- Accepted exceptions and decision IDs:
- Verification performed:
- Concise rationale:

