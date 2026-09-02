# Unit 4 Prepared Evidence — Harness Case Study

- **Artifact status:** prepared comparison material plus actual repository
  evidence; it is a sanitized fallback, not a learner-run measurement.
- **Repository:** Agent Experiment Ledger (P01).
- **Exercise baseline:** `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` —
  `test: close task 9 review gaps`.
- **Reference revision:** `2c498f616583d1fd6aeeaa381552b47acdb71ab7` —
  `fix: close ledger v0 final review gaps`.
- **Sanitization:** repository paths, source, test names, Git metadata, and
  command outcomes only. No private transcript, credential, proprietary prompt,
  personal path, or provider attribution is included.

## Case boundary and evidence index

The frozen task, acceptance conditions, authority, and stop condition are the
ones in [Unit 4](../../units/04-harness-comparison.md#exercise). The task is at
the baseline and ends after 35 minutes or two failed implementation approaches.
The exact reference test named `failed initialization publishes no partial
ledger and can be retried` is evidence for the reference solution at
`2c498f6` only. It records no destination after injected failure, no staging
entry, a successful retry, and a blocker-free check; it is not a universal
candidate evaluator oracle.

| Item | Consumer | Evidence type | Provenance | Supports | Remains uncertain |
| --- | --- | --- | --- | --- | --- |
| Baseline source and test | Unit 4 case study | actual repository evidence | `git show bb65b5c:src/config/service.ts`; `git show bb65b5c:test/init.test.ts` | Incremental baseline publication and absence of the named test | Whether a historical interruption occurred |
| Reference implementation and test | Unit 4 case study | actual repository evidence | `git diff bb65b5c..2c498f6 -- src/config/service.ts src/storage/staged-directory.ts test/init.test.ts` | Staging, validation, rename, and the named test | Cross-filesystem and concurrent-writer behavior |
| Command records | Unit 4 case study | actual repository evidence | Disposable checkouts at both pinned revisions; exact results below | Baseline and reference verification outcomes | Agent/model/harness behavior that produced the historical repair |
| Anonymous approaches and review | Unit 4 case study | prepared comparison material | Sanitized reconstruction from the actual source/test diff | A review exercise about publication boundaries | A timed, live second implementation run or causal attribution |

The evidence pack is outside P01 code-under-test worktrees. It can support a
local inspection and a prepared-review fallback. It cannot support a provider
benchmark, token comparison, agent ranking, or an assertion that a particular
agent followed either approach.

## Frozen configurations and controls

| Property | Configuration A | Configuration B |
| --- | --- | --- |
| Evidence source | Live learner’s available agent, if run | Prepared anonymous dossier in this file |
| Frozen task, baseline, acceptance, authority | Exact Unit 4 task; `bb65b5c`; named test and state checks; workspace-only writes/no task-run network | Same frozen case boundary; review-only, no new authority |
| Context | Task, P01 `AGENTS.md`, normal discovery | This sanitized dossier and cited source/test/diff evidence |
| Intended changed dimension | — | **Evidence source: live bounded work → prepared anonymous dossier** |
| Model/harness/settings | Record when visible; otherwise `unknown` | `unknown`; deliberately not attributed to a provider |
| Time, tool trace, interventions, usage | Record if actually observed; otherwise `unknown` | `unknown` |
| Unavoidable asymmetries | A is a live mutable checkout under a 35-minute/two-failure stop | B is an after-the-fact source/test review with no live tool, approval, or timing trace |

Configuration B is an explicitly permitted dossier fallback, not a controlled
second agent configuration. Do not compare its absent time, cost, tool count,
or model identity with A. A future live B may change **only** context treatment
by adding Unit 3’s proposed orientation map in a fresh session; it must record
that map’s file-pointer advantage, context cost, maintenance status, and every
ambient context difference.

**Prepared environment and permission record:** the actual source/test commands
ran only in detached disposable worktrees, never in P01’s main checkout. The
reference verification recorded Node `v23.7.0`, pnpm `10.26.1`, macOS `26.6.2`,
and `arm64`; the package declares Node `>=22` and pnpm `10.26.1`. Source/test
inspection was read-only. The case permits workspace-only writes during a live
implementation, denies network to that measured run, and requires human
approval for dependency or scope changes. Setup installation is a separate
authority: it may need package-store/network access and must record it before
the measured run starts. Historical agent permission mode, prompts, approvals,
and command authority are `unknown`.

## Actual repository evidence: baseline and reference

At baseline, `src/config/service.ts` calls `mkdir(paths.experiments, {
recursive: true })` and writes `config.json` in the destination directory.
The baseline `test/init.test.ts` has initialization, idempotence, invalid
directory, symlink, and atomic-file tests, but no test named `failed
initialization publishes no partial ledger and can be retried`.

The relevant reference diff is intentionally limited to:

```sh
git diff --no-ext-diff bb65b5cec8c96c3ba3d89b0025473561c7c8146f \
  2c498f616583d1fd6aeeaa381552b47acdb71ab7 -- \
  src/config/service.ts src/storage/staged-directory.ts test/init.test.ts
```

At `2c498f6`, `initializeLedger` constructs a hidden same-parent path named
`.${basename(root)}.init.staging`, creates the staged ledger, writes and reads
its config, validates the staged experiments directory, invokes the injected
pre-publish hook, then publishes with `rename(stagingDirectory, paths.root)`.
The catch path removes unpublished staging. The named test injects the failure,
asserts `access(root)` rejects, asserts no parent entry includes `.staging`,
retries initialization, then asserts `checkLedger(root).hasBlockers === false`.

**Pinned provenance:** Approach B is linked to reference revision
`2c498f616583d1fd6aeeaa381552b47acdb71ab7` (`2c498f6` short form) by the
source/test diff above. Neither approach is attributed to a model, product,
provider, or person.

## Anonymous implementation approaches and sanitized diffs

**Approach A — incremental destination plus catch cleanup** (prepared
comparison material; not a claim about historical source or an agent):

```diff
+ try {
+   await mkdir(destination, { recursive: true });
+   await mkdir(join(destination, "experiments"));
+   await writeJsonAtomic(join(destination, "config.json"), config, destination);
+ } catch (error) {
+   await rm(destination, { recursive: true, force: true });
+   throw error;
+ }
```

This cleanup runs only if the process reaches the catch block. An abrupt
termination after destination creation but before cleanup leaves a publication
window in which the public path can be empty or partial; a reader or a retry
can observe it. Cleanup also cannot make a sequence of visible writes into one
publication event.

**Approach B — hidden same-parent staging, validation, and rename** (actual
repository evidence at `2c498f6`, excerpted and formatted as a sanitized diff):

```diff
+ const stagingDirectory = join(parent, "." + basename(paths.root) + ".init.staging");
+ await createCleanStagingDirectory(parent, stagingDirectory);
+ try {
+   const stagedPaths = ledgerPaths(stagingDirectory);
+   await mkdir(stagedPaths.experiments);
+   await writeJsonAtomic(stagedPaths.config, config, stagedPaths.root);
+   await readJson(stagedPaths.config, LedgerConfigSchema, stagedPaths.root);
+   if (publicationHooks.beforePublish) await publicationHooks.beforePublish();
+   await publishStagedDirectory(stagingDirectory, paths.root);
+ } catch (error) {
+   await discardStagingDirectory(stagingDirectory).catch(() => undefined);
+   throw error;
+ }
+
+ export async function publishStagedDirectory(stagingDirectory, destination) {
+   await rename(stagingDirectory, destination);
+ }
```

The tested local publication boundary moves construction and validation out of
the destination and makes a same-parent rename the visible publication step.
That addresses the stated pre-publish failure boundary. It does **not** prove
atomic behavior for all filesystems, cross-device moves, concurrent writers,
crashes during rename, or all portability conditions. P01’s documented model
is one writer per ledger root; that model matters to the conclusion.

## Deterministic test and verification records

**Exact reference deterministic failure test** (actual repository evidence at
`2c498f6` only, not a required candidate API or universal evaluator test):

```ts
test("failed initialization publishes no partial ledger and can be retried", async () => {
  const parent = await temporaryDirectory("agent-ledger-init-publication-");
  const root = join(parent, "records");
  await assert.rejects(initializeLedger(root, fixedRuntime(), {
    beforePublish: async () => { throw new Error("injected initialization publication failure"); }
  }), /injected initialization publication failure/);
  await assert.rejects(access(root));
  assert.deepEqual((await readdir(parent)).filter((name) => name.includes(".staging")), []);
  await initializeLedger(root, fixedRuntime());
  assert.equal((await checkLedger(root)).hasBlockers, false);
});
```

Setup and measured-run boundaries are separate. A fresh baseline disposable
checkout used `pnpm install --frozen-lockfile`: it exited 0, reported
`downloaded 0`, installed 9 packages with pnpm 10.26.1, and warned that the
`esbuild` build script was ignored. The observable output did not report a
network download; it cannot prove that no transport was attempted. This is
setup evidence only, never authority for a measured agent run.

| Revision | Command | Actual repository result |
| --- | --- | --- |
| `bb65b5c` | `pnpm check` | Exit 0. |
| `bb65b5c` | `pnpm test` | Exit 0; 110 passed, 0 failed; the named initialization-publication test is absent. |
| `bb65b5c` | `pnpm build` | Exit 0. |
| `2c498f6` | `node --import tsx --test --test-name-pattern='failed initialization publishes no partial ledger and can be retried' test/init.test.ts` | Exit 0; 1 passed, 0 failed; focused result 21.598834ms. |
| `2c498f6` | `pnpm check` | Exit 0. |
| `2c498f6` | `pnpm test` | Exit 0; 121 passed, 0 failed; duration 7570.737666ms. |
| `2c498f6` | `pnpm build` | Exit 0. |
| `bb65b5c..2c498f6` | `git diff --check <baseline> <reference>` | Exit 0; no whitespace errors in the reference diff. |

The baseline install/check/test/build record and an earlier reference full
regression record are also preserved in
[Unit 1’s prepared run trace](unit-01-run-trace.md#fresh-baseline-command-record).
Those are actual repository evidence, not a transcript. This pack’s focused
reference command was executed in a disposable reference checkout. Package
setup in that checkout first attempted resolution but the sandbox reported
`ENOTFOUND`; its completed focused/full verification therefore used the same
lockfile’s already-materialized disposable dependency tree. That environment
difference is recorded here and must not be hidden in a live comparison.

## Prepared independent review and bounded conclusion

**Prepared independent review** (prepared comparison material, independent of
the anonymous implementation approaches): the source/test diff supports the
claim that A’s catch cleanup cannot provide a single publication boundary when
the process is interrupted before the catch runs. B validates off-destination
and uses a same-parent rename, so the tested destination is either absent before
publication or populated after the publication call. The named test supports
the injected failure, absent destination, removed staging entry, retry, and
blocker-free check. It does not test all interruption points, simultaneous
writers, filesystem rename guarantees, permissions failures, or every platform.

The review finds no evidence that a model, provider, harness, or context packet
caused Approach B. Those fields, along with historical elapsed time, token use,
tool calls, approvals, and private reasoning, are `unknown`. The actual source
and deterministic verification establish a bounded implementation property;
the anonymous approaches are a case-study aid.

**Prepared-path completion boundary:** this dossier can be completed only as
`critically analyzed`. It analyzes the exact reference test as evidence for
`2c498f6`, its frozen behavior invariants (failure immediately before
publication; failure result; absent destination; no unpublished staging; clean
retry; blocker-free ledger check), and how a future independent evaluator would
adapt a behavior-level test to a documented candidate seam. It contains no
candidate run, candidate-documented seam, evaluator post-run test, or focused
candidate result. Those absences are limitations, not fields a prepared learner
may fill from the reference test.

For a live path, preserve the learner/agent-authored test separately. The exact
reference test above is not preseeded into the measured task and is not applied
to the candidate. After the run, an independent verifier writes or runs a
behavior-level test through the candidate's documented deterministic injection
seam only. It injects deterministic failure immediately before candidate
publication; requires operation rejection/failure, an absent destination, no
unpublished staging entry, a clean retry, and a blocker-free ledger check; and
reviews the authored test separately. The verifier may adapt only to that
documented seam and may not change production behavior. If no observable seam
exists, acceptance fails. Seam and test-design variance are confounders, not
reasons to alter the frozen task or force `publicationHooks.beforePublish`.

**Case conclusion:** the reference test and source support a local conclusion:
for the injected pre-publication failure in this repository’s one-writer local
model, hidden same-parent staging plus validation and rename avoids publishing
the partially built destination tested here, removes unpublished staging, and
allows retry. The case does not establish universal filesystem atomicity,
concurrency safety, portability, agent performance, or a harness/provider
ranking. A useful next test is a fault matrix over staging creation, validation,
rename, cleanup, retry, and concurrent-writer conditions, with filesystem and
platform recorded.
