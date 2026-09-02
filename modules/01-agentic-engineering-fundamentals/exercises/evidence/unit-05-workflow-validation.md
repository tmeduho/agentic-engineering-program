# Unit 5 Prepared Evidence — Workflow Validation

- **Artifact status:** prepared comparison material plus actual repository
  evidence and fresh disposable-checkout verification. This is a sanitized
  fallback, not a learner-run implementation measurement.
- **Repository:** Agent Experiment Ledger (P01).
- **Exercise baseline:** `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` —
  `test: close task 9 review gaps`.
- **Reference revision:** `2c498f616583d1fd6aeeaa381552b47acdb71ab7` —
  `fix: close ledger v0 final review gaps`.
- **Sanitization:** source paths, commit IDs, test names, command outcomes, and
  prepared approach excerpts only. No private transcript, credential,
  proprietary prompt, provider attribution, or private path is retained.

## Evidence-pack index

| Item | Consumer | Evidence type | Provenance | Supports | Remains uncertain |
| --- | --- | --- | --- | --- | --- |
| Frozen task and matrix | Unit 5 workflow record | prepared comparison material | Unit 5 contract plus pinned source/test review | A bounded validation target and required cases | A learner’s live task trace |
| Baseline/report diff | Unit 5 source inspection | actual repository evidence | `git show` and `git diff bb65b5c..2c498f6 -- src/reports/service.ts test/report.test.ts` | Baseline boundary and reference request-schema repair | Why a historical producer chose either approach |
| Reference test records | Unit 5 acceptance gate | actual repository evidence | Fresh detached disposable clone at `2c498f6`; commands below | Named test and full reference verification | Baseline fail-before behavior; agent/harness telemetry |
| Approach and trace | Unit 5 workflow review | prepared comparison material | Sanitized reconstruction constrained by the pinned diff and test | Analysis of incomplete versus complete validation and workflow deviations | A timed implementation run or causal performance claim |

## Frozen task and acceptance boundary

At baseline `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`, use this task exactly:

```text
Runtime-validate the complete report-generation request before ledger access,
runtime clock access, or output creation. Reject an invalid experiment ID,
unsupported format, blank output path, non-boolean includeGeneratedAt, and
unknown option keys through the stable invalid-record error path. Preserve
valid Markdown and CSV behavior. Do not add dependencies. Stop after 20
minutes or two failed approaches.
```

Acceptance includes the reference test named
`runtime-validates the complete report request before ledger access or output`.
It also includes the existing deterministic Markdown/CSV tests and the full
`pnpm check`, `pnpm test`, and `pnpm build` gates. A valid request must retain
the reference’s Markdown and CSV behavior; an invalid request must take the
stable `LedgerError` path with code `INVALID_RECORD` and message `Report request
failed validation` before ledger, clock, or output work.

## Actual baseline report behavior

At `bb65b5c`, `src/reports/service.ts` accepts separate TypeScript parameters.
It first rejects a non-`markdown`/`csv` format as `USAGE`, then parses only the
experiment ID as `Experiment ID`, constructs ledger paths, calls `checkLedger`,
loads the experiment/runs, conditionally calls `runtime.now()`, renders, and
only then resolves/writes an optional output. Its type annotation says
`includeGeneratedAt: boolean` and `output?: string`, but the function has no
runtime schema for the complete request and the options object is not strict.

The baseline source does not establish an observed baseline test failure for
this task. In particular, it has no test named
`runtime-validates the complete report request before ledger access or output`.
Do not turn that absence into a fabricated fail-before command result. The
existing baseline tests do establish valid Markdown/CSV rendering, deterministic
repeated output, integrity gating, contained output, and unsupported-format CLI
behavior; they do not make malformed direct service input safe.

| Invalid request | Baseline source behavior | Required reference behavior | Evidence boundary |
| --- | --- | --- | --- |
| Invalid experiment ID, such as `../invalid` | Reaches the separate experiment-ID parse after the format branch; its error is scoped to `Experiment ID`, not the complete request. | `INVALID_RECORD`, `Report request failed validation`, before ledger access. | Reference named test includes `../invalid` with a missing root. |
| Unsupported format, such as `html` | Throws `USAGE`, `Unsupported report format: html`, before experiment-ID parse. | Same stable invalid-record path as every invalid request. | Reference named test includes `html` with a missing root. |
| Blank output path, such as `   ` | No substantive-string validation; for an otherwise valid ledger it can proceed through ledger/report work before destination handling. | Stable invalid-record path before ledger access or output creation. | Reference named test includes blank output with a missing root. |
| Non-boolean `includeGeneratedAt`, such as string `false` | No runtime boolean validation; a truthy value can reach the conditional clock call after ledger work. | Stable invalid-record path; no clock call and no output creation. | Reference named test instruments `runtime.now`. |
| Unknown option key, such as `extra: true` | The plain options object ignores unknown keys. | Stable invalid-record path before ledger access. | Reference named test includes a strict-object violation with a missing root. |

The baseline column is source inspection, not a claim that all five malformed
requests were run against the baseline. Its purpose is to identify the
unprotected boundary for the exercise without inventing a baseline failure.

## Two validation approaches

**Approach A — guard only format and experiment ID** is prepared comparison
material, not historical source or an attributed agent implementation:

```ts
if (format !== "markdown" && format !== "csv") {
  throw new LedgerError("USAGE", "Unsupported report format: " + format);
}
const parsedExperimentId = parseValue(experimentId, ExperimentIdSchema, "Experiment ID");
```

It leaves root, output, `includeGeneratedAt`, and unknown option keys outside
the request boundary. It can reject two bad fields while still reaching ledger
access, clock access, or destination processing for other malformed input. It
therefore cannot satisfy the frozen task.

**Approach B — validate the complete request** is actual repository evidence
at `2c498f6` (formatted excerpt from `src/reports/service.ts`):

```ts
export const ReportRequestSchema = z.object({
  root: SubstantiveStringSchema,
  experimentId: ExperimentIdSchema,
  format: z.enum(["markdown", "csv"]),
  options: z.object({
    output: SubstantiveStringSchema.optional(),
    includeGeneratedAt: z.boolean()
  }).strict()
}).strict();

const request = parseValue(
  { root, experimentId, format, options },
  ReportRequestSchema,
  "Report request"
);
const paths = ledgerPaths(request.root);
```

The pinned diff moves all five stated validation concerns into one strict
schema. The source order places `parseValue` before `ledgerPaths`,
`checkLedger`, `runtime.now`, output resolution, and `writeTextAtomic`. It does
not claim that schema validation alone protects every later filesystem or
integrity failure; those are separate report-service gates.

## Invalid-request gate evidence

At `2c498f6`, `test/report.test.ts` adds the named test. It constructs a valid
fixture/output path and a runtime whose `now()` increments `nowCalls`; passing
`includeGeneratedAt: "false"` rejects with `INVALID_RECORD` and `Report request
failed validation`, then asserts `nowCalls === 0` and that the output path does
not exist. This is direct evidence that the non-boolean case does not call the
clock or create that output.

The same test sends four more requests with a deliberately missing root:

```ts
{ root: missingRoot, experimentId: "../invalid", format: "csv", options: { includeGeneratedAt: false } }
{ root: missingRoot, experimentId: "valid-id", format: "html", options: { includeGeneratedAt: false } }
{ root: missingRoot, experimentId: "valid-id", format: "csv", options: { output: "   ", includeGeneratedAt: false } }
{ root: missingRoot, experimentId: "valid-id", format: "csv", options: { includeGeneratedAt: false, extra: true } }
```

Each must reject through the same stable invalid-record path, and the test then
asserts `access(missingRoot)` rejects. Together with the reference source order,
this supports the narrow conclusion that the complete invalid matrix is
validated before ledger path creation, and that the seeded invalid cases create
neither the output path nor the missing-root path. The explicit `nowCalls ===
0` assertion is for the non-boolean case; the other four use
`includeGeneratedAt: false` and are also rejected before the source could reach
the clock branch. This is test-plus-source evidence, not a claim about every
possible malformed object.

## Focused and full verification records

All commands below ran in a fresh detached disposable clone of P01 at full
reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7`. The clone was
created under `/private/tmp`, not in P01’s main checkout. Its final Git status
was clean. Setup was outside any learner’s measured 20-minute implementation
window:

| Stage | Command | Observed result |
| --- | --- | --- |
| Setup | `pnpm install --offline --frozen-lockfile` | Exit 0; lockfile current; reused 9 packages, downloaded 0; pnpm warned that `esbuild` build scripts were ignored. This setup result does not describe a learner’s agent authority. |
| Focused acceptance | `node --import tsx --test --test-name-pattern='runtime-validates the complete report request before ledger access or output' test/report.test.ts` | Exit 0; 1 passed, 0 failed; `duration_ms 660.105167`. |
| Type check | `pnpm check` | Exit 0; `tsc -p tsconfig.json --noEmit`. |
| Full regression | `pnpm test` | Exit 0; 121 passed, 0 failed; `duration_ms 7120.104333`. |
| Build | `pnpm build` | Exit 0; `tsc -p tsconfig.build.json`. |
| Reference diff hygiene | `git diff --check bb65b5cec8c96c3ba3d89b0025473561c7c8146f 2c498f616583d1fd6aeeaa381552b47acdb71ab7` | Exit 0; no output. |

The disposable environment reported Node `v23.7.0` and pnpm `10.26.1`. The
package declares Node `>=22` and pnpm `10.26.1`. These are actual reference
verification results; they do not prove a learner’s elapsed time, model,
harness, token use, approval history, or an equivalent result on another host.

## Prepared workflow execution trace and deviations

This is a trace for constructing the dossier, not a prepared claim that a
learner or historical agent executed a live repair.

| Workflow step | Status | Inputs and authority | Observable output / verifier / retained evidence |
| --- | --- | --- | --- |
| Frame risk and acceptance | followed | Frozen task, Unit 5 contract; curriculum author may define the prepared exercise only. | Complete invalid matrix and named acceptance test; verifier is the pinned test/source; retained task text and pin pair. |
| Inspect before edit | followed | P01 `AGENTS.md`, baseline/reference `service.ts` and `report.test.ts`; source/test authority for observed behavior. | Pinned baseline/reference diff; verifier is direct `git show`/diff inspection; retained paths and matrix. |
| Set authority and stop | followed | Task constraints; no dependency, P01-main mutation, network, or scope authority. | Disposable reference clone only; verifier is clone revision/status; retained environment and setup boundary. |
| Compare approaches | followed | Prepared A and actual B source; author may label, not attribute, the comparison. | A fails the complete-boundary analysis; B has strict schema; verifier is source order and named test; retained excerpts. |
| Run gates | followed | Reference checkout and declared commands. | Focused test, check, full suite, build, and diff hygiene all exit 0; retained command outcomes. |
| Independent review | followed | Source/test evidence independent of completion language. | Boundary review checks parse order, output absence, and regression results; retained limitation statements. |
| Handoff and learning | followed | This dossier and workflow template. | Learner can record followed/impossible/ambiguous/overridden steps and make a local decision; verifier is the Unit 5 acceptance checklist. |

| Deviation | What happened | Required record and effect |
| --- | --- | --- |
| Ambiguous | The baseline lacks the named focused test, so a “fail-before/pass-after” demonstration is not available from that test name. | Record source/test absence instead of inventing a baseline failure; use the prepared fallback or write a new test only within a live task’s authority/timebox. |
| Redundant | Earlier evidence packs contain historical full-suite records, but this dossier reran the named reference test and full reference verification in its own disposable clone. | Retain this fresh command provenance; do not use duplicated command logs as evidence that a learner ran them. |
| Skipped | No live agent implementation, dependency change, or P01 mutation was performed while creating the dossier. | Mark model, harness, prompts, elapsed implementation time, interventions, and failed approaches `unknown`; a learner may not infer them from this pack. |

## Learner use and acceptance record

## Compact prepared-prior-artifact summary

This is a bounded substitute for completed Unit 1–4 learner artifacts on the
prepared path. It is **prepared/reference** evidence, not learner execution,
and it cannot establish that a learner or provider performed the prior work.
Use it directly for the Unit 5 workflow record; consult the linked full packs
only when you need deeper source detail.

| Prior unit/artifact | Bounded input and provenance | Candidate workflow implication | Evidence type | Limitation |
| --- | --- | --- | --- | --- |
| Unit 1 / run trace | [Initialization reconstruction](unit-01-run-trace.md) at `bb65b5c..2c498f6`: green baseline tests lacked directory-publication fault injection. | Require an independent behavior-level failure boundary before accepting completion. | prepared/reference | No producer transcript or live learner trace. |
| Unit 2 / context comparison | [Symlink comparison](unit-02-context-comparison.md) at `bb65b5c..2c498f6`: A/B packets and raw traversal/diff evidence. | Capture ambient context and treatment differences; mark unbounded A/B evidence non-comparable. | prepared/reference | Prepared responses are not causal provider measurements. |
| Unit 3 / knowledge map | [Knowledge audit](unit-03-knowledge-audit.md) at the pinned revisions: source/tests outrank navigation indexes. | Inspect authoritative source/tests; record freshness, provenance, and recheck/retirement rules. | prepared/reference | Prepared routes do not measure learner discovery speed. |
| Unit 4 / harness case study | [Harness dossier](unit-04-harness-case-study.md) at `bb65b5c..2c498f6`: staged publication and reference test evidence. | Freeze task/authority, preserve test-design variance, and obtain independent behavior-level verification after the run. | prepared/reference | Reference test is evidence for `2c498f6`, not a universal evaluator oracle. |

The selected Unit 5 prepared capability is `critically analyzed`. Record each
row's use in the workflow template and do not relabel this summary as a
learner-run artifact.

Copy `workflow-template.md` outside the code-under-test worktree. Completed
Units 1–4 artifacts are normal input; a prepared path uses only their named
packs or a concise prepared-prior-artifact summary with provenance. Use the
live path only in a disposable checkout at the frozen baseline, or use this
dossier as prepared comparison material and label the capability `critically
analyzed`, never executed. For every workflow step, record followed,
impossible, ambiguous, or overridden, with inputs, authority, observable
output, stop condition, verifier, retained evidence, and authority for any
deviation. Preserve command outputs and review evidence; do
not retain raw private transcripts, credentials, or proprietary prompts.

For internal-pilot live cold-reader validation, use a fresh isolated P01
checkout at `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`, the frozen
report-validation task, workspace-only/no-network authority, and the
20-minute/two-failed-approaches stop rule. Withhold the evaluator's exact
reference test from the reader. After the run, an independent evaluator derives
and applies the evaluator-owned test artifact from `2c498f6`. First retain a
negative control: with that artifact absent or an unmatched test name, the
focused command is a failed gate even if Node exits 0 with a file-level pass.
Then verify the candidate checkout contains the exact named
`runtime-validates the complete report request before ledger access or output`
test, run `node --import tsx --test --test-name-pattern='runtime-validates the
complete report request before ledger access or output' test/report.test.ts`,
and require TAP output naming the test with exactly 1 pass and 0 fail before
running `pnpm check`, `pnpm test`, and `pnpm build`. Exit 0 or `pass 1` alone is
insufficient. Retain evaluator evidence outside learner self-report. Record the
independent reader,
one discriminating failure scenario, ambiguity/deviation/unsafe-action
observations, and the external results. This repeat of a known task tests
workflow usability, not generalization. This prepared dossier may support only
a design or critical analysis of that check; it did not execute a cold-reader
run and may not be presented as execution.

The validation record is complete only if it:

- freezes the exact task, baseline, stop rule, authority, and named acceptance
  test;
- records all five invalid request cases, the stable error contract, source/test
  evidence that invalid input precedes ledger/clock/output work, and valid
  Markdown/CSV preservation;
- distinguishes the prepared incomplete approach from the actual reference
  request-schema solution;
- includes focused and full external verification output, an independent source
  or diff review, and every workflow deviation;
- makes one keep, revise, or remove decision only when the record identifies a
  recurring decision or risk; and
- does not describe this prepared trace or one learner execution as evidence of
  general workflow, provider, or agent performance improvement.

**Prepared-dossier decision:** keep the complete-request validation gate for
this report-service task. Its value is bounded by a named behavior, source
order, and deterministic test. Revalidate before exporting it as a general
workflow rule; the dossier alone does not show recurrence across task classes.
