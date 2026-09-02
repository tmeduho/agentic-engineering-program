# Unit 3 Prepared Evidence — Project-Knowledge Audit

- **Evidence type:** prepared comparison material plus actual repository
  evidence. It is a fallback for the Unit 3 exercise, not a learner-run timing
  result or an approved P01 change.
- **Repository:** Agent Experiment Ledger (P01).
- **Exercise baseline:** `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` —
  `test: close task 9 review gaps`.
- **Reference revision:** `2c498f616583d1fd6aeeaa381552b47acdb71ab7` —
  `fix: close ledger v0 final review gaps`.
- **Sanitization:** reviewed as repository paths, commit metadata, source, and
  test names only. No transcript, credential, private prompt, or local
  experiment record is included.

## Question and evidence boundary

Use this exact discovery question:

```text
Where is direct comparison eligibility decided, which facts make two
controlled runs comparable, and which checks prevent an ineligible report?
Provide the shortest evidence path from repository orientation to source and
tests.
```

All paths below are references to P01 at the stated revision. They support a
repository-navigation exercise, not a claim that an agent or learner completed
the exercise. No elapsed time was measured for these prepared paths. Their hop
count and order are illustrative navigation evidence only and cannot substitute
for the learner's own timed before/after claim.

**Live-ordering boundary:** a live learner must copy the template and complete
the root-listing-only before question in a fresh context before opening this
prepared audit, the required inventory, or any worked result. They preserve and
close that context, then inspect/build the map, and run the after question in a
second fresh context with only the proposed map added. A prepared learner may
critically analyze the recorded routes below, but cannot label them as their
own prospective measurement.

## Prepared current-state knowledge map

The map distinguishes sources of truth from indexes. “Ledger maintainers” is
the owner role recorded by the prepared case; a learner must name the actual
owner if their local project differs.

| Artifact | Purpose and source-of-truth status | Owner | Authority and scope | Discovery and load strategy | Freshness trigger | Precedence | Retirement / review and maintenance |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `AGENTS.md` | Operating policy; source of truth for repository contributor instructions. | Ledger maintainers | Binding repository instruction; cross-cutting contributor scope. | Root listing -> `AGENTS.md`; always load only where the active harness supports it. | Change to workflow, validation, or safety boundary. | Subordinate to applicable system/human policy; directs readers to the approved design. | Revise in the same review as a cross-cutting rule; remove a rule once its narrower control supersedes it. |
| `README.md` | Project orientation and operator entry point; source of truth for public operator guidance, not for domain rules. | Ledger maintainers | Explanatory repository documentation; whole-project scope. | Root listing -> `README.md`; discover early. | CLI workflow, data layout, or operator guarantee changes. | `AGENTS.md` governs contributor procedure; approved design governs product intent; source/tests settle implementation behavior. | Review with public-interface changes; remove stale walkthroughs rather than retaining chronology. |
| `docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md` | Approved product contract and architecture decisions; source of truth for the version-zero design. | Product/design owner with ledger maintainers | Approved design; version-zero product boundary. | `AGENTS.md` or README -> specification; retrieve when a product boundary is in scope. | Approved design revision or explicit superseding decision. | Overrides implementation plans on product intent; does not override higher-level policy. | Supersede with a new approved decision/specification; review through product/design review. |
| `docs/superpowers/plans/2026-08-27-agent-experiment-ledger-v0.md` | Historical implementation plan; source of truth for planned task sequencing, not final behavior. | Plan author and ledger maintainers | Implementation-plan scope. | Specification or docs directory -> plan; retrieve for implementation provenance. | Task plan amendment or completed-plan archival decision. | Subordinate to approved specification and verified source/tests. | Archive or mark superseded when a new plan replaces it; review in implementation planning. |
| `package.json` | Runtime, package-manager, and verification-command declaration; source of truth for package scripts and tool versions. | Ledger maintainers | Executable package configuration; repository scope. | Root listing -> `package.json`; discover before local validation. | Dependency, Node, or script change. | Beats copied command snippets when they conflict; policy may constrain which command is required. | Update with the dependency/script change; review in code/dependency review. |
| `src/comparison/eligibility.ts` | Pairwise direct-comparison decision rules; source of truth for eligibility implementation. | Domain maintainers | Domain implementation; direct-comparison boundary. | Proposed orientation index -> path; task-local retrieval for comparison behavior. | Any change to comparison rules, run schema, or verification semantics. | Approved design defines intent; this source and tests establish implemented behavior. | Change with a behavioral test and domain review; delete only if the boundary is replaced. |
| `src/checks/check-ledger.ts` | Ledger integrity and eligibility checks; source of truth for checker behavior. | Ledger integrity maintainers | Application/checking boundary. | Proposed orientation index -> path; retrieve when inspecting integrity or report gating. | Schema, lifecycle, artifact, path-containment, or eligibility change. | Approved design defines intent; source/tests settle runtime behavior. | Change with focused checks and review; retire only with a replacement checker boundary. |
| `src/reports/service.ts` | Report request validation, checker gate, and output behavior; source of truth for report-service behavior. | Reporting maintainers | Reporting/application boundary. | Proposed orientation index -> path; retrieve when a report or output rule is in scope. | Report request, integrity-gate, or destination behavior change. | Checker result blocks report output; source/tests settle runtime behavior. | Change with report tests and review; retire only with a replacement service boundary. |
| `test/check.test.ts` | Raw executable evidence for checker and eligibility behavior; source of truth for the tested cases, not the entire product contract. | Test owner / ledger maintainers | Test evidence for check and comparison behavior. | Source import or proposed index -> test; retrieve with `check-ledger.ts` and `eligibility.ts`. | Behavior, schema, or defect change. | Contradicts unsupported prose about observed behavior; does not replace the approved design. | Update with the behavior change; retain regression cases while the behavior remains supported. |
| `test/report.test.ts` | Raw executable evidence for report-service behavior; source of truth for its tested cases, not the entire product contract. | Test owner / ledger maintainers | Test evidence for report generation and integrity gating. | Source import or proposed index -> test; retrieve with `reports/service.ts`. | Report behavior, output containment, or defect change. | Contradicts unsupported prose about observed behavior; does not replace the approved design. | Update with the behavior change; retain regression cases while the behavior remains supported. |
| Proposed `docs/architecture-and-evidence-navigation.md` | **Index only**: concise orientation route to existing authoritative docs, source, and tests. It must not restate eligibility rules. | Proposed owner: ledger maintainers, only if adopted | Non-binding navigation aid; disposable exercise material. | Linked from `README.md` only in the learner's disposable worktree; discover early, not always loaded. | Any target path, ownership, or architecture boundary changes. | Never overrides `AGENTS.md`, approved design, source, or tests. | Review in documentation and affected-boundary code review; reject/delete if it duplicates the sources or fails the cost-benefit decision. |

## Required P01 inspection record

Inspect these artifacts at **both** pinned commits before making the learner
map. The reference revision is the prepared source/test navigation basis;
baseline-to-reference history supplies change provenance.

| Required artifact | What the prepared inspection establishes | Provenance |
| --- | --- | --- |
| `AGENTS.md` | The approved design is the product contract; `pnpm check`, `pnpm test`, and `pnpm build` are completion checks. | `git show <commit>:AGENTS.md` at both commits. |
| `README.md` | The project is a local evidence ledger; reports display direct-comparison eligibility and do not calculate a universal winner. | `git show <commit>:README.md` at both commits. |
| Design specification | The five-boundary architecture puts comparison eligibility in domain rules; `check` evaluates integrity and direct-comparison eligibility; reports are deterministic views. | `git show <commit>:docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md`. |
| Implementation plan | `src/comparison/eligibility.ts`, `src/checks/check-ledger.ts`, and `src/reports/service.ts` are named responsibilities. | `git show <commit>:docs/superpowers/plans/2026-08-27-agent-experiment-ledger-v0.md`. |
| `package.json` | Node, pnpm, and the `check`, `test`, and `build` commands are declared package facts. | `git show <commit>:package.json`. |
| Representative source | Eligibility compares experiment, controlled source type, frozen plan hash, known shared baseline, invalidation, finished state, and complete verification; checker imports it; report generation calls the checker before output. | `git show <commit>:src/comparison/eligibility.ts`, `src/checks/check-ledger.ts`, and `src/reports/service.ts`. |
| Representative tests | Check tests cover same-frozen-baseline eligibility and blocks for retrospective, mismatch, invalidation, and incomplete verification; report tests cover integrity-gated output and contained destinations. | `git show <commit>:test/check.test.ts` and `test/report.test.ts`. |
| Git history | Baseline is `test: close task 9 review gaps`; reference is `fix: close ledger v0 final review gaps`. The reference diff changes README, checker/report behavior, and their tests among other files. | `git show --no-patch --format=fuller <commit>` and `git diff --name-status <baseline> <reference>`. |

Replace `<commit>` with each pinned SHA. Preserve the full command and the
result location in the learner artifact; this table is a prepared route, not a
substitute for that evidence.

## Recorded before discovery path

**Starting context:** only the P01 repository-root listing at reference
revision. Do not pre-open instructions, README, specification, plan, source,
or tests.

**Prepared route:**

1. `git ls-tree --name-only 2c498f616583d1fd6aeeaa381552b47acdb71ab7`
   reveals `README.md`, `AGENTS.md`, `docs`, `src`, and `test`.
2. `README.md` identifies direct-comparison eligibility as report content but
   does not name the implementation file.
3. `docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md`
   names comparison eligibility as a domain rule and says `check` evaluates it
   before reports describe it.
4. `src/comparison/eligibility.ts` answers where eligibility is decided and
   lists the blocking facts: same experiment, controlled runs, known matching
   frozen-plan hash and baseline, non-invalidated finished runs, and complete
   independent verification.
5. `src/checks/check-ledger.ts` imports `assessDirectComparison` and records
   its blockers and confounders while checking ledger integrity.
6. `test/check.test.ts` supplies executable cases for eligible same-baseline
   controlled runs and ineligible retrospective, mismatched, invalidated, or
   unverified runs.
7. `src/reports/service.ts` calls `checkLedger` before rendering or writing;
   it throws on blockers. `test/report.test.ts` verifies the integrity gate and
   contained-output behavior.

**Prepared result:** direct comparison is decided in
`src/comparison/eligibility.ts`; controlled pairs require the same experiment,
known same frozen-plan hash, and known same baseline, and are blocked when a
run is retrospective, invalidated, unfinished, or not completely independently
verified. `checkLedger` exposes that assessment, while `generateReport` refuses
output when `checkLedger` has blockers.

**Timing limitation:** no elapsed time or token count was captured. This is an
illustrative seven-step prepared route, not a measured before result. A learner
must record their own start/end evidence and may report `unknown` timing.

## Proposed disposable navigation map and after path

Create this map only in the learner's disposable P01 worktree and add one
concise link to it from the README/project orientation. Do not merge it into
the Agent Experiment Ledger main branch.

```markdown
## Architecture and evidence navigation (disposable exercise map)

For the direct-comparison question, read the approved design's Architecture
and Check integrity sections, then inspect:

1. `src/comparison/eligibility.ts` — direct-comparison blockers and
   confounders.
2. `src/checks/check-ledger.ts` — integrity scan and eligibility assessment.
3. `src/reports/service.ts` — report gate before rendering or writing.
4. `test/check.test.ts` and `test/report.test.ts` — executable evidence for
   eligibility, checker, report-gate, and destination behavior.

This map is an index. The specification, source, and tests remain authoritative.
```

**After starting context:** a fresh session starts at `README.md` and follows
the concise orientation link to the disposable map. It does not inherit the
before session's conversational summary.

**Prepared route:** `README.md` -> disposable map ->
`src/comparison/eligibility.ts` -> `src/checks/check-ledger.ts` ->
`test/check.test.ts` -> `src/reports/service.ts` -> `test/report.test.ts`.
Use the design specification when resolving product-intent questions; the map
links to it rather than duplicating it.

**Prepared result:** the proposed map removes the ambiguity of locating three
implementation boundaries and their executable evidence, but it does not
prove a faster discovery time or a better agent outcome. Its cost is a
maintained orientation link that can drift whenever paths, boundaries, or
authority change.

**Timing limitation:** no after timing was measured. This path is illustrative
prepared comparison material only; hop count is not a time claim and cannot
substitute for a learner's measurement in a fresh session.

## Duplication and source-of-truth review

| Fact needed by the probe | Keep as source of truth | What the map may say | What it must not duplicate |
| --- | --- | --- | --- |
| Eligibility rule and confounders | `src/comparison/eligibility.ts` with `test/check.test.ts` evidence | Path and one-line purpose. | A copied list of conditions that can drift from source. |
| Ledger-wide integrity behavior | `src/checks/check-ledger.ts` with `test/check.test.ts` evidence | Path and relation to eligibility assessment. | A prose claim that the checker passed without raw test/command provenance. |
| Report output gate | `src/reports/service.ts` with `test/report.test.ts` evidence | Path and relation to `checkLedger`. | A second report contract or duplicated output rules. |
| Product intent and architecture | Approved design specification | Link to the relevant sections. | Repeated architecture narrative that competes with the approved contract. |
| Operator orientation | `README.md` | One link to the navigation map. | Full source/test explanation in the README. |

Keep the proposal only if a learner's path evidence shows that the index
meaningfully improves the stated discovery task and its owner accepts the
review/maintenance burden. Narrow it to links and purposes if a draft repeats
rules; reject and delete it if it adds no decision value.

## Learner acceptance record

Use this checklist after completing the live or prepared path:

- [ ] Every map row has owner, authority, discovery path, freshness trigger,
  precedence, and retirement; indexes are labeled and sources of truth named.
- [ ] The artifact records baseline/reference commits, exact P01 paths, and
  raw-evidence provenance rather than only conclusions.
- [ ] Live path: the before route used only a repository-root listing in a
  fresh context before this prepared audit, the named inventory, or a
  result-bearing example; that context was preserved and closed. The after
  route used a second fresh context with only the project-orientation map
  added. Prepared path: both recorded paths are labeled prepared analysis, not
  prospective learner measurement.
- [ ] Prepared timings are labeled illustrative or `unknown`; no time claim is
  based on hop count or this pack.
- [ ] One package/dependency item and one source-registry claim record
  authority, provenance, freshness/corroboration, and retirement/recheck; an
  unsupported or stale conclusion is marked `revise`.
- [ ] The proposed map links all three source boundaries and both test files,
  but does not duplicate their rules.
- [ ] The decision says keep, revise, or reject, and states who would review
  and maintain the map if adopted.
- [ ] No exercise map was merged into P01's main branch.
