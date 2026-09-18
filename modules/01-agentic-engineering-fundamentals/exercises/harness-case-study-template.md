# N=1 Harness Case Study

- Artifact status: complete | revise | not attempted
- Case identity:
- Evidence location: outside the code-under-test worktree
- Scope limit: conclusions apply only to the recorded case and configurations.

## Frozen case boundary

- Task outcome:
- Baseline repository and commit:
- Acceptance checks and expected results:
- Path capability: live `executed` | prepared `critically analyzed`:
- Live only — candidate documented deterministic injection seam (or `none`):
- Stop condition (time, spend, repeated failure, safety, ambiguity):
- Conditions held constant:

## Configurations and controls

| Property | Configuration A | Configuration B |
| --- | --- | --- |
| Harness and version |  |  |
| Model/settings when visible |  |  |
| Context treatment |  |  |
| Repository instruction files present |  |  |
| Instruction files actually loaded and precedence |  |  |
| Known instruction-file divergence and treatment |  |  |
| Authority and approval policy |  |  |
| Permissions |  |  |
| Environment, worktree, and network |  |  |
| CPU, RAM, disk, and concurrency limits |  |  |
| Resource-enforcement mechanism |  |  |
| Infrastructure failure or exclusion rule |  |  |
| Known unavailable telemetry | unknown | unknown |

## Observed outcomes

| Configuration | Outcome | Interventions | Wrong turns | Wall time | Available usage data | Evidence reference | Evidence type | Uncertainty |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A |  |  |  |  |  |  |  |  |
| B |  |  |  |  |  |  |  |  |

Evidence type is one of: `actual repository evidence`, `prepared comparison
material`, or `hypothetical counterexample`. Do not describe prepared results
as learner-run measurements.

## Verification and review

For a live path, name a second engineer or fresh-context agent as the
independent verifier. The verifier starts only after the producing session
stops, has no access to the producing conversation, treats no producer
conclusion as evidence, and receives the candidate checkout with the evaluator
test still withheld. The verifier may adapt the evaluator-owned test only to
the documented candidate seam and may not change production behavior. If that
channel is unavailable, use the prepared path and do not claim live
acceptance.

| Gate | Configuration A | Configuration B | Evidence provenance: learner-run actual \| prepared/reference \| hypothetical | Independent evidence/reviewer |
| --- | --- | --- | --- | --- |
| Live only — evaluator behavior-level acceptance (candidate seam; failure immediately before candidate publication; rejection/failure; no destination or unpublished staging; clean retry; blocker-free check) |  |  |  |  |
| Prepared only — reference-test/invariant/seam-adaptation analysis; explicitly no candidate run, seam, evaluator post-run test, or focused candidate result | n/a unless live |  |  |  |
| Regression result |  |  |  |  |
| Independent diff or evidence review |  |  |  |  |
| Permission/safety boundary respected |  |  |  |  |

## Interpretation

- Confounders and asymmetries:
- Claims supported by this case:
- Claims this case cannot support:
- Seam/test-design variance and candidate-production-change check:
- Prepared-path absence statement (candidate run/seam/evaluator test/focused result):
- Residual uncertainty and next evidence needed:
