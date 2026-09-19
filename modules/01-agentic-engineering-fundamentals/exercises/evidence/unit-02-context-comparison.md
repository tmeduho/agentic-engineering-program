# Unit 2 prepared context comparison

- Evidence type: **prepared comparison material** plus **actual repository evidence**.
- Repository: Agent Experiment Ledger (P01).
- Exercise baseline: `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`.
- Reference revision: `2c498f616583d1fd6aeeaa381552b47acdb71ab7`.
- Scope: one read-only, 20-minute investigation; no files may be modified.

This is a sanitized fallback, not a hidden answer key or benchmark. The
prepared responses are illustrative comparison material. They are not live
runs, measured provider performance, token telemetry, or proof that either
configuration caused a result. Use the raw Git evidence to test the claims.
Before a live A/B run, capture automatic repository instructions, memory,
system/developer context, tool descriptions, inherited session state, and other
ambient model-visible inputs. If these collapse or obscure the intended packet
difference, mark the result non-comparable and use an isolatable configuration
or this prepared analysis without a causal treatment claim.

P01 contains both root instruction files, `AGENTS.md` and `CLAUDE.md`, at the
baseline and reference pins. They differ by one review-verification line in
`CLAUDE.md`. The bounded Configuration B packet below explicitly supplies the
`AGENTS.md` text; it does not silently supply `CLAUDE.md`. Before treating A/B
as comparable, record which file(s) the selected harness actually loads, their
precedence, and whether the divergence is present. If that load behavior is
not observable, record it as `unknown` and treat it as an uncontrolled
difference rather than assuming `AGENTS.md` was the only ambient instruction.

## Prediction gate — stop before prepared results

Before reading any later section, copy
[the context-comparison template](../context-comparison-template.md) and
record a prospective A and B failure prediction plus a falsifier for each.
Preserve that record when you read this pack. This requirement applies on the
prepared path too: the pack is result-bearing comparison material, so a
prediction made after opening it is not prospective.

## Frozen task and held constants

For both configurations, hold model, harness, permissions, baseline,
working-tree state, timebox, task text, and acceptance format constant. If a
learner cannot suppress an ambient context source, record it as an uncontrolled
difference. Stop a live run at 20 minutes, do not write files, and record
unavailable telemetry as `unknown`.

The acceptance format is: report (1) whether the check detects each symlink
case, (2) the exact traversal behavior and code paths, (3) the missing tests,
and (4) uncertainty. A complete answer identifies that the whole-ledger
traversal filters only `Dirent.isDirectory()` entries, which skips symlinks
before realpath containment can evaluate either an escape or an in-root alias.

## Exact configuration packets and byte counts

Each packet is the UTF-8 contents of its fenced `text` block, including its
final newline but excluding the fence and marker comments. Reproduce a count
from this file by changing `configuration-a` to `configuration-b`:

```sh
LC_ALL=C awk '
  $0 == "<!-- packet:start configuration-a -->" { state = 1; next }
  state == 1 && $0 == "```text" { state = 2; next }
  state == 2 && $0 == "```" { exit }
  state == 2 { print }
' modules/01-agentic-engineering-fundamentals/exercises/evidence/unit-02-context-comparison.md | wc -c
```

The command counts encoded bytes, not tokens. It produces **578** bytes for
Configuration A and **5162** bytes for Configuration B.

### Configuration A — frozen task only

<!-- packet:start configuration-a -->
```text
Exercise baseline: bb65b5cec8c96c3ba3d89b0025473561c7c8146f

Task:
Determine whether a whole-ledger integrity check detects both an
experiment-directory symlink that escapes the ledger root and an in-root
experiment alias. Cite the exact traversal behavior, code paths, and missing
tests. Do not modify files. State uncertainty and stop after 20 minutes.

Timebox: Stop after 20 minutes. Do not modify files.

Acceptance format:
Report (1) whether the check detects each symlink case, (2) the exact traversal
behavior and code paths, (3) the missing tests, and (4) uncertainty.
```
<!-- packet:end configuration-a -->

### Configuration B — frozen task plus bounded orientation

<!-- packet:start configuration-b -->
```text
Exercise baseline: bb65b5cec8c96c3ba3d89b0025473561c7c8146f

Task:
Determine whether a whole-ledger integrity check detects both an
experiment-directory symlink that escapes the ledger root and an in-root
experiment alias. Cite the exact traversal behavior, code paths, and missing
tests. Do not modify files. State uncertainty and stop after 20 minutes.

Timebox: Stop after 20 minutes. Do not modify files.

Acceptance format:
Report (1) whether the check detects each symlink case, (2) the exact traversal
behavior and code paths, (3) the missing tests, and (4) uncertainty.

Additional repository context:

AGENTS.md:
# Repository Instructions

- Treat docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md as the product contract.
- Use pnpm. Do not add runtime dependencies without explicit approval.
- Follow test-driven development: demonstrate a failing behavioral test before implementation.
- Run pnpm check, pnpm test, and pnpm build before claiming completion.
- Keep the CLI non-interactive and preserve stable JSON envelopes and exit codes.
- Never infer missing experiment data, copy artifacts implicitly, execute recorded commands, or delete evidence.
- Keep domain rules independent of process and filesystem state.

README.md — Artifacts, privacy, and source freshness:
The ledger stores a hash and sensitivity label for every attached artifact. The default is a reference to the source file; --copy creates a ledger-contained snapshot under the run's evidence/ directory. No artifact is copied implicitly.
If a source is outside the selected ledger root or the caller's current working directory, the operator must pass --allow-external. This is an acknowledgement, not a privacy guarantee. normal, sensitive, and restricted are metadata labels; the ledger does not redact, encrypt, upload, or scrub transcripts, credentials, or model output. Review paths and contents before attaching them.
Referenced artifacts remain dependent on their original absolute path and can disappear or change. Copied artifacts are stable snapshots, but their contents can still be sensitive. check verifies that every registered artifact still exists and matches its recorded hash; it reports a blocker when it does not.
The ledger is a single-writer store. Serialize mutating commands (init, experiment transitions, run transitions, attachment, retrospective registration, and report writes) for a given root. Atomic writes protect an existing file from a failed replacement, but they do not coordinate concurrent writers. check and report generation are read-oriented, yet reports should not be generated concurrently with mutations if a consistent snapshot matters.
On a failed command, inspect the JSON error envelope and rerun check. Do not delete a partial run or evidence to make a check pass. Controlled lifecycle writes are replacement writes; retrospective source-registration failures preserve the new run as invalidated and retain successfully registered evidence. Correct the source or record and preserve the original evidence trail.

Design spec — Integrity and comparison rules:
1. A controlled run cannot start before its experiment is frozen.
2. Frozen experiment inputs cannot be updated in place.
3. Changed frozen files produce an integrity error; the tool does not silently refresh hashes.
4. Every controlled run retains the exact frozen-plan hash it used; a retrospective run may record that value as unknown.
5. A direct comparison requires the same experiment identifier, plan hash, and baseline commit.
6. Controlled and retrospective runs are not pooled by default.
7. Invalidated runs remain visible but are excluded from direct comparison.
8. Reports distinguish verified successful outcomes, verified failed outcomes, and unverified claims.
9. Differences in harness, model, treatment, permissions, environment, and available telemetry are shown explicitly.
10. Missing data remains unknown and is never estimated from another run or provider.

Design spec — Filesystem safety and error handling:
- Every record is fully validated before writing.
- Writes use a temporary file in the destination directory followed by atomic replacement.
- A failed write preserves the previous valid record.
- Existing files are never silently repaired, truncated, or replaced with defaults.
- Paths used for ledger records and copied artifacts are normalized and confined to the configured ledger root.
- An artifact referenced outside the ledger root requires explicit acknowledgement, is never copied by default, and is not assumed to remain available later.
- Symlink traversal outside the permitted root is rejected for copied artifacts.
- Version zero has no delete command. Invalidating a run retains its evidence and adds a reason and timestamp.
- Commands report actionable errors without including artifact contents or likely secrets.
- One writer at a time per ledger root is required. Coordinating concurrent writers is explicitly outside version-zero guarantees.

Orientation: inspect src/checks/check-ledger.ts and test/check.test.ts.
Before concluding, retrieve raw source from the stated baseline and cite it.
```
<!-- packet:end configuration-b -->

## Context inventory for configuration B

These are the only B-only additions. The frozen task, baseline, timebox, and
acceptance format remain A’s content, not B-only context.

| Added item | Provenance and authority | Freshness | Placement and trigger | Cost / failure behavior | Decision prompt |
| --- | --- | --- | --- | --- | --- |
| `AGENTS.md` | Baseline `AGENTS.md`; repository instruction, authoritative for repository work but subordinate to harness/system rules | Exact baseline commit | Included at packet start; read before source exploration | Adds broad workflow rules; can be over-broad for a read-only task or stale on another revision | Did its constraints change this investigation? |
| `CLAUDE.md` | Baseline `CLAUDE.md`; a second root instruction file with one additional review-verification line; actual loading is harness-specific | Exact baseline commit | Not included in the fenced B packet; inspect automatic loading and precedence before calling A/B comparable | The extra line can change independent-review behavior; if loading is unobservable, retain `unknown` | Which file(s) loaded, in what precedence, and did the divergence remain uncontrolled? |
| README artifacts/privacy/integrity excerpt | Baseline `README.md`; repository documentation and evidence boundary, not a replacement for source behavior | Exact baseline commit | Included before exploration | Adds provenance and read-only framing; can restate the task without locating traversal | Did it prevent an invalid action or merely repeat a boundary? |
| Design integrity section | Baseline design specification; stated product contract via `AGENTS.md` | Exact baseline commit | Included before exploration | Explains invariants; can bias the agent toward intended design instead of current behavior | Did it identify a testable invariant? |
| Design filesystem-safety section | Baseline design specification; stated product contract via `AGENTS.md` | Exact baseline commit | Included before exploration | Narrows symlink concern; could make a learner assume code conforms | Did it generate a falsifiable raw-source question? |
| Orientation note | Exercise-authored navigation hint; lower authority than repository instructions and source | Frozen with this evidence pack | Included before exploration; names both likely files | Small packet cost and a file-pointer advantage; can reduce exploration but bias search | Did it save time without supplying the conclusion? |
| Retrieve-raw-source instruction | Exercise-authored evidence rule; subordinate to higher authority | Frozen with this evidence pack | Included after orientation; trigger is before concluding | Adds a verification step; costs time but guards against summary/design drift | Did it replace an unsupported inference with a cited observation? |

Packet size and the orientation pointer are separate confounders. Do not infer
that a larger packet is beneficial, or attribute a result to any one row, from
this prepared comparison.

## Prepared responses — illustrative, not measurements

### Prepared A response

> I inspected the integrity check and its path-containment helper. The check
> resolves experiment paths with `assertExistingPathContained`, so an
> experiment-directory symlink escaping the root should produce
> `EXPERIMENT_DIRECTORY_INVALID`. An alias inside the root may be resolved to
> the same real directory and then fail an identity check, although I did not
> find a dedicated whole-ledger alias test. Existing tests cover malformed
> experiment records and run symlink escapes. I am uncertain about the exact
> enumeration path because the timebox ended while I was tracing related run
> handling.

This response plausibly explores containment and adjacent tests but misses the
whole-ledger `Dirent.isDirectory()` prefilter. It is prepared comparison
material, not an observation from a provider or learner run.

### Prepared B response

> At baseline `bb65b5c`, `checkLedger` reads `experiments/` in
> `src/checks/check-ledger.ts:404` and immediately applies
> `.filter((entry) => entry.isDirectory())` at line 405. Directory symlinks do
> not reach the loop at line 410, so `assertExistingPathContained` at lines
> 413–418 never evaluates either the escaping symlink or an in-root alias.
> `test/check.test.ts` has run-symlink coverage but no whole-ledger
> experiment-symlink test at this baseline. Therefore the check detects neither
> requested experiment-directory symlink case through this traversal. I would
> add tests for an escaping experiment symlink and an in-root alias, and retain
> uncertainty about platform-specific Dirent behavior only if the Node runtime
> differs from the prepared baseline.

This response follows the orientation pointer and retrieves raw source. It is
prepared comparison material, not a live-run measurement or proof that B
caused the result.

## Actual repository evidence: baseline, repair, and tests

The following was inspected directly with:

```sh
git -C "$MODULE01_LEDGER_REPO" show \
  bb65b5cec8c96c3ba3d89b0025473561c7c8146f:src/checks/check-ledger.ts
git -C "$MODULE01_LEDGER_REPO" diff \
  bb65b5cec8c96c3ba3d89b0025473561c7c8146f \
  2c498f616583d1fd6aeeaa381552b47acdb71ab7 -- \
  src/checks/check-ledger.ts test/check.test.ts
```

At baseline, the raw whole-ledger traversal branch is:

```ts
let experimentDirectories: string[];
if (experimentId !== undefined) {
  if (!ExperimentIdSchema.safeParse(experimentId).success) {
    findings.push(finding("blocker", "INVALID_EXPERIMENT_ID", "Requested experiment ID is invalid", experimentId));
    const orderedFindings = sortFindings(findings);
    return { experimentsChecked, runsChecked, findings: orderedFindings, hasBlockers: true };
  }
  experimentDirectories = [experimentId];
} else {
  experimentDirectories = (await readdir(experimentsDirectory, { withFileTypes: true }))
    .filter((entry) => entry.isDirectory())
    .map((entry) => entry.name)
    .sort();
}

for (const directoryName of experimentDirectories) {
  const experimentDirectoryPath = join(experimentsDirectory, directoryName);
  let experimentDirectory: string;
  try {
    experimentDirectory = await assertExistingPathContained(paths.root, experimentDirectoryPath);
  } catch (error) {
    addExpectedError(findings, error, "EXPERIMENT_DIRECTORY_INVALID", "Experiment directory is missing or escapes the ledger", experimentDirectoryPath);
    continue;
  }
```

The prefilter is the failure mechanism: symbolic-link entries are omitted before
the `realpath`-based containment helper can execute. This is actual repository
evidence for this baseline, not a claim about all filesystems or Node releases.

Reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7` changes the
whole-ledger branch to enumerate `entry.isDirectory() || entry.isSymbolicLink()`,
records whether an entry is a symlink, still calls containment, then reports a
blocker and skips processing if it is an alias:

```ts
experimentDirectories = (await readdir(experimentsDirectory, { withFileTypes: true }))
  .filter((entry) => (
    (entry.isDirectory() || entry.isSymbolicLink())
    && !isStagingExperimentDirectory(entry.name)
  ))
  .map((entry) => ({
    name: entry.name,
    isSymbolicLink: entry.isSymbolicLink()
  }))
  .sort((left, right) => left.name.localeCompare(right.name));

// After assertExistingPathContained succeeds:
if (candidate.isSymbolicLink) {
  findings.push(finding(
    "blocker",
    "EXPERIMENT_DIRECTORY_INVALID",
    "Experiment directory symlink aliases are not valid record identities",
    experimentDirectoryPath
  ));
  continue;
}
```

The same revision adds these bounded tests in `test/check.test.ts`:

```ts
test("whole-ledger check reports an experiment symlink that escapes the ledger", async () => {
  const fixture = await createFinishedRun({ idSeed: 185 });
  const outside = join(fixture.workspace, "outside-experiment");
  await mkdir(outside);
  await symlink(outside, join(fixture.root, "experiments", "escaped-experiment"));

  const result = await checkLedger(fixture.root);

  assert.equal(result.hasBlockers, true);
  assert.equal(result.findings.some((item) => item.code === "EXPERIMENT_DIRECTORY_INVALID"), true);
});

test("whole-ledger check rejects an in-root experiment alias without double-counting", async () => {
  const fixture = await createFinishedRun({ idSeed: 186 });
  const experimentDirectory = join(fixture.root, "experiments", fixture.run.experimentId);
  await symlink(experimentDirectory, join(fixture.root, "experiments", "aliased-experiment"));

  const result = await checkLedger(fixture.root);

  assert.equal(result.experimentsChecked, 1);
  assert.equal(result.runsChecked, 1);
  assert.equal(result.findings.some((item) => item.code === "EXPERIMENT_DIRECTORY_INVALID"), true);
});
```

The reference repair and tests support the narrow conclusion that the stated
baseline had the enumeration gap and this revision covers both seeded symlink
cases. They do not measure an agent system, establish universal filesystem
semantics, or prove why a live learner would navigate differently.

## Learner use and acceptance

Before opening prepared responses, copy
[context-comparison-template.md](../context-comparison-template.md) outside the
code-under-test worktree and enter predictions for both configurations. Run one
or both packets, or use the prepared responses. In every case record:

- the configuration inventory, including authority/freshness for every B-only
  item;
- observations separately from causal explanations, with evidence type;
- wrong turns, human interventions, unavailable telemetry, and a cost proxy;
- packet-size and file-pointer/orientation advantages as confounders; and
- a keep, revise, or reject decision for every B-only item, its rationale,
  context cost, falsifying evidence, follow-up evidence, and residual
  uncertainty.

The artifact is complete only if it preserves frozen variables, makes
predictions before results, cites raw traversal and reference tests, labels
prepared material correctly, and avoids a general claim that more context is
better. It is `revise` if it treats illustrative responses as provider
measurements, invents tokens or costs, or assigns causality without accounting
for different packet sizes and B’s file-pointer advantage.
