# Harness Controls and Independent Verification Case Study

- Artifact status: complete | revise | not attempted
- Case identity:
- Evidence location: outside the code-under-test worktree
- Scope limit: one bounded case; no measured configuration effect or provider ranking.

## Frozen case boundary

- Task outcome:
- Baseline repository and commit:
- Acceptance checks and expected results:
- Selected path capability: live `executed` | prepared `critically analyzed`:
- Live only — candidate documented deterministic injection seam (or `none`):
- Stop condition (time, spend, repeated failure, safety, ambiguity):
- Authority boundary:

## Case environment and provenance

- Harness/version and visible model/settings (or `unknown`):
- Repository instruction files present (`AGENTS.md` and `CLAUDE.md`):
- Instruction files actually loaded and precedence (or `unknown`):
- Known instruction-file divergence and treatment:
- Environment, worktree, runtime, and clean-baseline evidence:
- Setup package-store/network evidence, separate from measured-run authority:
- CPU, RAM, disk, concurrency, and resource-enforcement mechanism (or `unknown`):
- Infrastructure failure or exclusion rule:
- Prior exposure to the initialization solution, ambient context, and other limits:

## Ten-dimension control assessment

Complete every row. Identify whether a value is a required instruction,
configured control, observed behavior, or unknown historical behavior. A
required instruction is not proof of enforcement. Every `unknown` needs its
practical consequence; prepared source correctness cannot fill a missing
historical harness field.

| Harness dimension | Configured/observed value or `unknown` | Evidence and provenance | Uncertainty | Consequence for this task |
| --- | --- | --- | --- | --- |
| Context assembly and compaction |  |  |  |  |
| Tool schemas, routing, and observations |  |  |  |  |
| Task and session state |  |  |  |  |
| Sandbox, filesystem, network, and command authority |  |  |  |  |
| Approval policy |  |  |  |  |
| Interface effects |  |  |  |  |
| Progress and handoff |  |  |  |  |
| Retry, recovery, and termination |  |  |  |  |
| Telemetry and missing measurements |  |  |  |  |
| Stable interfaces versus stale scaffolding |  |  |  |  |

## Control decisions — analyze, do not execute these requests

| Request | Governing control | Required evidence | Permitted next action or stop/escalation |
| --- | --- | --- | --- |
| In-scope source edit in the disposable checkout |  |  |  |
| Network access to install a new dependency during the run |  |  |  |
| Completion claimed using only existing green baseline tests |  |  |  |

## Observed candidate implementation — live only

For a prepared path, write `no candidate run` rather than copying reference
results into this section. Retain incomplete live observations with their stop
reason if switching paths; they do not establish completed live acceptance.

| Outcome | Interventions | Wrong turns | Wall time | Available usage data | Evidence reference/type | Uncertainty |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |

## Reference and prepared evidence — separate from candidate observations

| Repository revision or prepared item | Supported behavior or claim | Evidence reference/type | What it cannot establish |
| --- | --- | --- | --- |
|  |  |  |  |

Evidence type is one of: `actual repository evidence`, `prepared comparison
material`, or `hypothetical counterexample`. These describe provenance, not
agent-system configurations. Do not describe prepared results as learner-run
measurements or a proposed control as observed enforcement.

## Verification and review

For a live path, name a second engineer or fresh-context agent as the
independent verifier. The verifier starts only after the producing session
stops, has no access to the producing conversation, treats no producer
conclusion as evidence, and receives the candidate checkout with the evaluator
test still withheld. The verifier may adapt the evaluator-owned test only to
the documented candidate seam and may not change production behavior. If that
channel is unavailable, use the prepared path and do not claim live
acceptance.

| Gate | Result or explicit absence | Evidence provenance: learner-run actual \| prepared/reference \| hypothetical | Independent evidence/reviewer |
| --- | --- | --- | --- |
| Live only — evaluator behavior-level acceptance (candidate seam; failure immediately before candidate publication; rejection/failure; no destination or unpublished staging; clean retry; blocker-free check) |  |  |  |
| Live only — agent-authored test review and final check/test/build |  |  |  |
| Prepared only — reference-test/invariant/seam-adaptation analysis; explicitly no candidate run, seam, evaluator post-run test, or focused candidate result in the dossier |  |  |  |
| Reference regression evidence, separately labeled |  |  |  |
| Independent diff or evidence review |  |  |  |
| Permission/safety boundary respected |  |  |  |

## Proposed configuration change — untested

- One control or enforcement mechanism to change, and the current case evidence motivating it:
- Target failure:
- Expected observation in a future test:
- Falsifier:
- Enforcement mechanism and responsible human or system:
- Held constants (task, baseline, model, authority, acceptance, stop rule, and other relevant conditions):
- Remaining confounders and next evidence needed:
- Status: `untested`; not implemented or measured in this unit.

Do not claim a measured configuration effect. If proposing a change to a gate
already required by this unit, identify the distinct enforcement mechanism
being changed; restating the requirement is not a new configuration.

## Interpretation

- Confounders and evidence-path limitations:
- Claims supported by this case:
- Claims this case cannot support:
- Seam/test-design variance and candidate-production-change check:
- Prepared-path absence statement (candidate run/seam/evaluator test/focused result):
- Residual uncertainty and next evidence needed:
