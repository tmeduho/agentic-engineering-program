# Unit 1 Prepared Run Trace — Ledger Initialization

- Artifact status: prepared comparison material
- Case: Agent Experiment Ledger initialization publication boundary
- Baseline: `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`
- Reference: `2c498f616583d1fd6aeeaa381552b47acdb71ab7`
- Repository evidence: Agent Experiment Ledger local repository; paths cited
  below are relative to its root.
- Evidence location: this sanitized pack is outside the ledger code-under-test
  worktree.
- Telemetry: producing-agent identity, prompt, model settings, token use,
  exact wall time, and private transcript are `unknown` or intentionally
  withheld.

This is a **prepared reconstruction grounded in Git evidence and a fresh
disposable-checkout verification**, not a verbatim private transcript. It does
not present its event ordering as observed hidden reasoning. “Initial
completion claim” is a reconstruction of the release posture that green
baseline checks could support, not an attributed quotation.

## Evidence-pack index

| Item | Consumer | Evidence type | Provenance | Sanitization review | Supports | Remains uncertain |
| --- | --- | --- | --- | --- | --- | --- |
| Baseline command record | Unit 1 run trace | actual repository evidence | Disposable checkout of `bb65b5c`, commands below | No transcript, credentials, or private source | Baseline commands and their results | Any earlier agent’s configuration or reasoning |
| Initialization source and test diff | Unit 1 run trace | actual repository evidence | `git diff bb65b5c..2c498f6 -- src/config/service.ts test/init.test.ts src/storage/staged-directory.ts` | Source paths and commits only | The pre-repair publication structure, repair, and regression test | Whether a historical production run hit this path |
| Event table and hypotheses | Unit 1 run trace | prepared comparison material | Reconstruction from the two items above | No private transcript or prompt | A bounded failure-analysis exercise | A single causal explanation for false completion |

## Fresh baseline command record

The author created `/private/tmp/unit-01-ledger.MWudTE` as a disposable,
isolated clone, detached it at the baseline, and removed it after preparing
this pack. The ledger’s main checkout was not modified.

`pnpm install --frozen-lockfile` exited 0. It reported “Lockfile is up to date,
resolution step is skipped” and `downloaded 0`; on that observable basis, the
install used the local store and did not report a network download. The command
output cannot prove that the package manager made no transport attempt beyond
what it reported. It installed 9 packages and completed in 564ms using pnpm
10.26.1; it also warned that the `esbuild` build script was ignored.

| Command | Observed result |
| --- | --- |
| `pnpm check` | Exit 0; `tsc -p tsconfig.json --noEmit` |
| `pnpm test` | Exit 0; 110 tests passed, 0 failed, duration 6266.323459ms |
| `pnpm build` | Exit 0; `tsc -p tsconfig.build.json` |

These commands establish only the baseline’s checked behavior. They do not
establish that its test suite covered an interrupted initialization publication.

## Shared-template field mapping

This pack uses the shared run-trace vocabulary without changing its schema.
When copying `run-trace-template.md`, use `Inference` for an observed **model
inference** or tool-call selection; `Context` for model-visible inputs and
**context assembly** by the harness; `Intent` plus `State` for an **agent-loop
decision** and state transition; and `Context`, `Tool`, `Authority`, `State`,
or `Verification` for an observed **harness responsibility**. In `Tool`,
record the distinction between a selected call and its routed execution or
result. Mark each unavailable layer `unknown` rather than inventing it.

## Prepared event sequence

| Order | Event | Shared template fields (mapped layers) | Evidence type | Evidence and interpretation | Uncertainty |
| ---: | --- | --- | --- | --- | --- |
| 1 | The exercise fixes the target at baseline `bb65b5c` and reference `2c498f6`. | `Context` (context assembly); `Authority`; `Human decision` | prepared comparison material | The module brief and `sources.md` pin both revisions. | The original task framing and agent-visible context are unavailable. |
| 2 | A disposable checkout is created and detached at `bb65b5c`. | `Tool` (routed clone); `Environment`; `Authority`; `State` | actual repository evidence | `git clone --no-hardlinks` and detached checkout completed in `/private/tmp/unit-01-ledger.MWudTE`. Isolation bounds filesystem effects to the disposable clone. | It does not reproduce the historical producing environment. |
| 3 | Baseline installation, type-check, test, and build complete successfully. | `Tool` (execution result); `Environment`; `Observation`; `Verification` | actual repository evidence | Fresh command record above: install exit 0, check exit 0, 110/110 tests, build exit 0. | The suite’s coverage is bounded by its assertions. |
| 4 | A completion narrative could treat those green checks as sufficient evidence. | `Inference` (unknown; no transcript); `Intent` (agent-loop termination); `State` | prepared comparison material | The task requires an “initial completion claim”; no private completion message is included. This event labels a claim, not a verified repository fact. | No transcript identifies who made the claim or why. |
| 5 | An independent review inspects baseline `initializeLedger`. | `Context` (review assembly); `Verification`; `Human decision` | actual repository evidence | Baseline `src/config/service.ts` creates the destination root and `experiments/` before writing `config.json`. `test/init.test.ts` lacks an initialization-publication failure/retry test. | The review’s exact tool sequence is unknown. |
| 6 | The review identifies a pre-publication interruption that could leave partial state. | `Tool`; `Environment`; `State`; `Verification` | prepared comparison material | If failure occurs after the root or `experiments/` directory exists but before a valid `config.json`, a later call sees a non-empty directory without `config.json` and rejects it as non-ledger. This follows the baseline control flow. | This pack does not claim an observed historical crash at that point. |
| 7 | The reference revision stages initialization in a hidden same-parent directory, validates it, and publishes by rename. | `Tool` (application publication); `State`; `Verification`; harness responsibility `unknown` | actual repository evidence | `2c498f6:src/config/service.ts` uses `createCleanStagingDirectory`, validates staged paths, and calls `publishStagedDirectory`; `src/storage/staged-directory.ts` implements rename publication. | Rename atomicity and filesystem semantics depend on the environment; the case concerns the tested local behavior. |
| 8 | Reference revision adds `failed initialization publishes no partial ledger and can be retried`. | `Verification`; `Tool` (test execution); `Environment`; `State` | actual repository evidence | `2c498f6:test/init.test.ts` injects a pre-publish failure, asserts that the destination is absent and no staging directory remains, retries initialization, then checks for no blockers. | The test covers its injected boundary, not every interruption point or concurrency scenario. |
| 9 | The repaired reference is rerun in the same disposable checkout. | `Tool` (execution result); `Environment`; `Observation`; `Verification` | actual repository evidence | At `2c498f6`, `pnpm check` and `pnpm build` exited 0; `pnpm test` exited 0 with 121 passed, 0 failed, duration 7422.822917ms. | A local rerun does not prove behavior across platforms, filesystems, or concurrent writers. |

## Failure analysis

- Failure or unexpected outcome: a plausible initial completion state based on
  successful baseline checks did not establish that ledger initialization was
  failure-atomic or retryable after an interrupted publication.
- Earliest preventable layer: **verification**.
- Why: the baseline already had type-check, test, and build evidence. A
  targeted, local fault-injection test would have directly exercised the
  missing invariant without requiring a claim about unobserved model reasoning.
  A stronger acceptance criterion could also have driven that test; the record
  does not establish which omission occurred first.

| Hypothesis | Evidence for | Evidence against or that weakens it | Current disposition | Residual uncertainty |
| --- | --- | --- | --- | --- |
| 1. Acceptance criteria omitted failure atomicity. | Baseline `test/init.test.ts` tests valid initialization, existing non-ledger directories, idempotence, and path integrity, but not failed initialization plus retry. The reference adds a named failure-atomicity test. | No frozen historical acceptance-criteria document or review checklist is in this pack; a criterion may have existed but been implemented inadequately. | supported, not proven | The original acceptance wording and review decisions are unknown. |
| 2. The producing agent failed to consider interrupted publication. | Baseline `initializeLedger` publishes incrementally; the reference changes it to staging plus rename and adds the missing regression test. That is consistent with the interruption scenario not receiving sufficient design attention. | Source diff does not reveal the producing agent’s reasoning, alternatives considered, or whether a human constrained the implementation. | unresolved | A sanitized design note or review record could distinguish an unconsidered scenario from an accepted tradeoff. |
| 3. Verification lacked fault injection. | Baseline test output is green at 110 tests, while baseline `test/init.test.ts` has no initialization fault-injection/retry test. The reference test injects `beforePublish` failure and passes in the 121-test rerun. | The baseline does include an atomic file-replacement fault-injection test, `an injected pre-rename failure preserves the prior valid file`; verification was not absent, but it did not cover directory-level initialization publication. | supported, narrowed | The pack cannot show whether another independent review procedure inspected this boundary before reference revision. |

## Conclusion

The evidence supports a bounded conclusion: passing baseline type, test, and
build checks did not cover directory-level initialization failure atomicity;
the reference revision adds a staged-directory repair and a targeted retry test
that passes in a fresh local rerun. It does not support attributing the earlier
gap to a particular model, provider, harness, or individual.

The next useful evidence would be a deliberately recorded fault matrix for
directory creation, validation, publish rename, cleanup, retry, and concurrent
writer behavior, with platform and filesystem details. Until then, portability
and concurrency behavior remain uncertain.
