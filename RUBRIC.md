# Curriculum Quality Rubric

This file is normative. `evals/curriculum-rubric.md` is the worksheet used to apply it.

## Scored dimensions

Score each dimension from 1 to 5. A score must cite evidence.

| Dimension | A score of 5 means |
| --- | --- |
| Technical correctness | Claims are accurate, qualified where necessary, and consistent with current primary sources and observed behavior. |
| Technical depth | The material reaches architecture, mechanisms, tradeoffs, and failure modes appropriate for a senior engineer. |
| Production relevance | The module addresses permissions, security, reliability, observability, cost, recovery, and human decision rights where applicable. |
| Source quality and currency | Important claims use strong primary sources; fast-moving sources meet the freshness policy below. |
| Lab validity | The lab exercises the stated skills under realistic constraints and has falsifiable acceptance criteria. |
| Verification quality | Success depends on observable outcomes and an independent check, not an agent's claim or polished output. |
| Personal relevance | The module respects `PROFILE.md`, avoids unjustified basics, and produces reusable value for the learner. |
| Coherence and efficiency | Outcomes, material, sources, and lab align without avoidable duplication or low-value work. |

Maximum score: 40.

## Hard quality gates

A module may move to `verified` only when all of these are true:

- Total score is at least 32/40.
- No dimension scores below 3/5.
- Technical correctness and lab validity each score at least 4/5.
- No open `blocker` findings remain.
- No open `major` findings remain unless the learner accepts a documented exception in `DECISIONS.md`.
- Every stated outcome is exercised by the curriculum and checked by the lab or an explicitly named alternative.
- The lab defines a baseline, reproducible procedure, captured evidence, acceptance checks, and an independent verification step.
- Every time-sensitive factual claim has a current source or is labeled uncertain/stale.
- Beginner material is either removed or justified by a specific prerequisite dependency.
- The lead has responded to every reviewer finding.
- The reviewer has checked the revision rather than only the original draft.

Only the learner may move a verified module to `approved`.

## Finding severity

| Severity | Meaning |
| --- | --- |
| `blocker` | Unsafe, materially incorrect, unverifiable, or incapable of teaching a required outcome. |
| `major` | Significant gap, weak evidence, invalid exercise, outdated assumption, or poor fit that materially reduces value. |
| `minor` | Useful improvement that does not invalidate the module. |
| `note` | Non-blocking observation or possible future enhancement. |

## Adversarial review criteria

The reviewer must actively test the module for:

1. Technical errors and ambiguous claims.
2. Claims that changed after their cited source was published.
3. Weak secondary sources where primary sources exist.
4. Missing primary sources or relevant competing evidence.
5. Assumptions tied to obsolete models, SDKs, protocols, or product behavior.
6. Beginner material that does not earn its place.
7. Missing advanced mechanisms, tradeoffs, or production failure modes.
8. Material that is interesting but not practically useful.
9. Labs that reward completion without demonstrating the stated skill.
10. Acceptance checks that can pass despite a bad real-world outcome.
11. Redundancy with other modules.
12. Better free, cheaper, or more current resources.
13. Unsupported claims or citations that do not support the claim made.
14. Overconfidence, hidden uncertainty, and untested generalization.
15. Work unlikely to justify the learner's time, cost, or operational risk.

Agreement without additional analysis is a review failure.

## Source policy and freshness

Every source entry must include its URL, publisher/author, publication or version date when available, date checked, source type, relevance, and status.

Use these maximum ages at the time a module is verified:

| Material | Maximum time since last check | Rule |
| --- | ---: | --- |
| Product behavior, model capabilities, SDK/API details, protocol versions, pricing, security guidance | 30 days | Use a primary source. Reproduce behavior when practical. |
| Active engineering practices, benchmarks, and ecosystem comparisons | 90 days | Seek a newer primary source or label the limitation. |
| Foundational papers, specifications, and stable concepts | 12 months | The source may be older; recheck that it remains relevant and has not been superseded. |

An older source may remain as historical background. It may not support a claim about the current state unless the module labels that limitation explicitly.

Primary sources include official documentation and specifications, source repositories, release notes, papers, and first-party engineering reports. Videos and practitioner reports can add implementation context but should not be the sole support for consequential claims when a primary source exists.

