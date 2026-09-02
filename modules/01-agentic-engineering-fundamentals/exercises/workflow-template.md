# workflow-v1

- Artifact status: complete | revise | not attempted
- Workflow owner and version:
- Named human decision owner and escalation recipient (learner by default for a solo prepared exercise, unless another authorized human is named):
- Intended task class:
- Validation run identity:
- Evidence location: outside the code-under-test worktree
- Unavailable telemetry or data (record as `unknown`):

## Frame the work

- Intent and expected outcome:
- Risk framing and non-goals:
- Falsifiable acceptance checks:
- Required evidence before work starts:

## Inspect and select context

- Inspect-before-edit evidence (repository state, relevant files, baseline):
- Context selected, authority, freshness, placement, and retrieval trigger:
- Evidence references and uncertainty:

## Execute within boundaries

- Permitted tools, permissions, and environment:
- Human decision rights (including required approvals):
- Agent decision rights:
- Stop conditions:
- Recovery conditions:
- Escalation conditions and recipient:
- Progress state to retain:
- Handoff state and evidence required on pause or failure:

## Per-step execution record

Record every workflow step. Status is one of `followed`, `impossible`,
`ambiguous`, or `overridden`; an override names the approving human.

| Step and status | Inputs | Authority | Observable output | Stop condition | Verifier | Retained evidence |
| --- | --- | --- | --- | --- | --- | --- |
| Frame |  |  |  |  |  |  |
| Inspect |  |  |  |  |  |  |
| Execute |  |  |  |  |  |  |
| Recover/escalate |  |  |  |  |  |  |
| Gates |  |  |  |  |  |  |
| Handoff/learn |  |  |  |  |  |  |

## Gates

| Gate | Required procedure/evidence | Result | Provenance: learner-run actual \| prepared/reference \| hypothetical | Independent reviewer or source | Uncertainty |
| --- | --- | --- | --- | --- | --- |
| Acceptance |  |  |  |  |  |
| Regression |  |  |  |  |  |
| Independent review |  |  |  |  |  |

## Metrics and validation

- Retained metrics (wall time, interventions, usage/cost when available, wrong turns, changed files, results):
- Validation deviation from this workflow:
- Validation observations and evidence type: actual repository evidence | prepared comparison material | hypothetical counterexample
- External acceptance result (not agent self-report):
- Cold-reader validation: internal-pilot default is a fresh isolated P01 checkout at `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` on the frozen report-validation task, with workspace-only/no-network authority and the 20-minute/two-failed-approaches stop rule. Withhold the evaluator's exact reference test; after the run, an independent evaluator applies the named behavior check and runs `node --import tsx --test --test-name-pattern='runtime-validates the complete report request before ledger access or output' test/report.test.ts`, then `pnpm check`, `pnpm test`, and `pnpm build`. Record reader identity, ambiguity, deviation, unsafe action, external result, and at least one discriminating failure scenario. This known-task repeat tests workflow usability, not generalization. A prepared path may design/analyze this check only and must say it did not execute it.
- Decision: keep | revise | remove
- Residual uncertainty and next validation:
