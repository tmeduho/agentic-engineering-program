# Claude Review Record — Module 01

## Role

Claude is the adversarial reviewer and final verifier for Module 01. Claude must not rewrite the curriculum during the first review.

## Current state

- Status: adversarial review complete; module returned for revision
- Review date: 2026-09-04
- Revision or commit: content revision `9bb82901a0b2ec4184239e1b3f4f939301e3b874`, reviewed from handoff `a0adcbf50888e42cdf202bce0c8396ef3a1b9408`
- Verdict: `revise`

`git diff --name-status 9bb8290 a0adcbf` changes only `claude-review.md` and
`codex-review.md`, so the curriculum content at the handoff is identical to the
submitted revision. The working tree was clean at review start.

## Independent research pass

Recorded before reading `sources.md` in detail and before reading
`codex-review.md` at all. Raw candidate list retained during the session.

**Sources independently selected (checked 2026-09-04):**

- MCP specification, revision `2026-07-28` — <https://modelcontextprotocol.io/specification/2026-07-28>
- Anthropic, *Effective context engineering for AI agents* — matches S02
- Anthropic, *Harness design for long-running application development* — matches S03
- Anthropic, *Scaling Managed Agents* — matches S04
- Anthropic, *Effective harnesses for long-running agents* — matches S05
- Anthropic, *Building Effective AI Agents*, *Writing effective tools for AI agents*, *Code execution with MCP*, *Equipping agents for the real world with Agent Skills*, *Demystifying evals for AI agents*
- Claude Code docs: `how-claude-code-works`, `settings`, `permissions`, `memory`, `hooks`, `sub-agents`, `skills` — overlaps S06–S09
- OpenAI Codex docs: `concepts/sandboxing`, `agent-approvals-security`, `config-reference`, `permissions`, `cli/features`
- <https://agents.md/> — AGENTS.md open format, Agentic AI Foundation (Linux Foundation)
- arXiv 2606.25447, *The Interplay of Harness Design and Post-Training in LLM Agents* (2026-06-24)

**Sources the lead missed:** `agents.md` and arXiv 2606.25447. See C-010.

**Sources that contradict or narrow the draft:** none contradict the module's
teaching. arXiv 2606.25447 narrows Unit 4's framing slightly by reporting that
harness design and post-training *interact* rather than compose additively,
which supports the unit's refusal to attribute an N=1 outcome to either layer.

**Sources rejected and why:** the MCP `2026-07-28` revision is current and
relevant to the program, but `brief.md` places MCP in Module 01's non-goals and
assigns it to a later module; adding it here would be scope creep. Secondary
"context rot" explainers were rejected in favour of S02, which states the
finite-resource claim first-party.

**Independent verification performed against the source registry.** Confirmed
by direct fetch on 2026-09-04: S02 published 2025-09-29 with the cited section
present; S03 published 2026-03-24 with "Why naive implementations fall short"
present; S04 published 2026-04-08 with the session/harness/sandbox quotes
present; S05 published 2025-11-26 with the false-completion failure mode
present; S06 present with the agentic-loop, context-window, and permission
sections cited; S08 present with both cited anchors (`Permission system` at
line 11, `How permissions interact with sandboxing` at line 554 of the fetched
page); S09 present with `CLAUDE.md vs auto memory`, `How CLAUDE.md files load`,
and `AGENTS.md` all present. Two entries did not verify — see C-002 and C-006.

## Adversarial review

Worksheet from `../../evals/curriculum-rubric.md`, completed here.

### Reproducible checks run by the reviewer

All checks were run on 2026-09-04 against the local P01 clone in detached
`git worktree` checkouts under the session scratchpad, never in P01's main
checkout. Both worktrees were removed and `git worktree prune` was run
afterwards; P01's main checkout is clean and unchanged.

| # | Check | Result |
| --- | --- | --- |
| 1 | `git rev-parse` both pins; baseline is an ancestor of the reference | Both resolve; `bb65b5c..2c498f6` is exactly one commit |
| 2 | Unit 2's decisive citation `src/checks/check-ledger.ts:404-407` at baseline | Exact. Lines 404–407 are the `readdir(..., { withFileTypes: true })` / `.filter((entry) => entry.isDirectory())` / `.map` / `.sort` chain, with `assertExistingPathContained` first called at line 415 |
| 3 | Unit 1's baseline incremental-publication claim | Confirmed: baseline `initializeLedger` `mkdir`s the root, and a non-empty root without `config.json` throws `INVALID_TRANSITION` "Refusing to initialize over a non-ledger directory" |
| 4 | Unit 1's "the baseline did type-check, test, and build" claim | Confirmed: `pnpm check` exit 0, `pnpm test` 110/110 pass, `pnpm build` exit 0 — green while still carrying the defect |
| 5 | Reference suite | 121/121 pass; +11 tests over baseline |
| 6 | Named tests cited by Units 1, 2, 5 | All present and passing at `2c498f6`: `failed initialization publishes no partial ledger and can be retried`; `whole-ledger check reports an experiment symlink that escapes the ledger`; `whole-ledger check rejects an in-root experiment alias without double-counting`; `runtime-validates the complete report request before ledger access or output` |
| 7 | **Unit 5 negative control, unmatched pattern** | **Claim confirmed.** `node --import tsx --test --test-name-pattern='<no-such-name>' test/report.test.ts` exits **0** and prints `✔ test/report.test.ts` with `tests 1 / pass 1 / fail 0` — a file-level pass indistinguishable from a real pass by exit code or counts |
| 8 | **Unit 5 negative control, artifact absent** | **Claim confirmed.** The same focused command at the *baseline*, where the named test does not exist, also exits 0 with `✔ test/report.test.ts`, `pass 1` |
| 9 | Unit 4's `publicationHooks.beforePublish` reference seam | Real at `2c498f6` in `src/storage/staged-directory.ts` and three services — it is production API surface, which substantiates the unit's rule that an evaluator may not force it onto a candidate |
| 10 | `lab.md#setup-isolation-and-privacy` commands run verbatim on macOS | All succeed, including `mktemp -d /tmp/module-01-work.XXXXXX` and `git worktree add --detach` |
| 11 | Unit 3's inspected paths at both pins | All ten cited paths exist at both revisions |
| 12 | Curriculum MEGA matrix counts ("18 Teach rows and 9 Touch rows") | Exact: 18 Teach, 9 Touch, 27 rows |
| 13 | Timebox arithmetic (45+60+75+90+60+75) | Exactly 405; each unit's internal breakdown also sums to its stated cap |
| 14 | P01 root instruction files | **`AGENTS.md` and `CLAUDE.md` both exist at both pins and differ** — see C-003 |

Check 7 is the most consequential. Unit 5 and the facilitator guide claim that
Node reports a file-level pass for an unmatched `--test-name-pattern`, and both
build a gate around it. The claim is correct, it is not obvious, and the gate
Unit 5 specifies (require the exact test *name* in TAP output, not exit status
or `pass 1`) is the right discriminator. This is the strongest single piece of
evidence for the module's verification design.

### Hard-gate result

- Result: **fail** — 4 of 13 gates fail
- Failed gates: outcome coverage; unaccepted majors; source freshness; lab exercises the stated skills

| Gate | Result | Evidence or required change |
| --- | --- | --- |
| Outcomes are measurable and fully covered. | fail | C-001. Outcome 4 is "Execute an N=1 comparison of two agent-system configurations, or critically analyze the explicitly labeled prepared case." No path compares two agent-system configurations: Configuration A is one live run and Configuration B is a document. |
| Technical correctness has no known material error. | pass | Checks 2–9 reproduced every substantive technical claim exactly, including the non-obvious Node false-green. C-002 and C-003 are source-metadata and configuration-description defects, not errors in what the module teaches. |
| No open blocker findings remain. | pass | Nothing found is unsafe, materially incorrect in its teaching, or unverifiable. |
| No unaccepted major findings remain. | fail | Five open majors: C-001 through C-005. None is covered by D-006, D-007, or D-008. |
| Fast-moving claims satisfy the source-freshness policy. | fail | C-002. S10 is a rolling `latest-model` URL; its content changed between the lead's 2026-09-02 check and this 2026-09-04 review, and `sources.md`'s verification note is already inaccurate. |
| Important claims use primary sources when available. | pass | S01–S10 are first-party; P01 is primary local repository evidence. Anchors verified for S02, S03, S04, S05, S06, S08, S09. |
| The lab exercises the stated skills rather than adjacent skills. | fail | C-001. Unit 4 teaches a ten-row harness-comparison inventory that no required exercise applies to a second harness or second configuration. |
| The lab has a baseline and reproducible procedure. | pass | Check 10: setup runs verbatim on the stated platform. Check 1, 11: pins resolve and all cited paths exist at both. |
| Acceptance checks can falsify a bad outcome. | pass | Checks 7–8 show the Unit 5 gate is load-bearing: it rejects a state that exit code and pass counts accept. Unit 4's behaviour invariants reject observable bad states. |
| Verification includes a channel independent of the producing agent. | pass | Evaluator-owned post-run test, withheld artifact, negative control, diff review. C-009 records that Unit 4 leaves the solo-path verifier undefined where Unit 5 defines it. |
| Production risks and decision rights are addressed where applicable. | pass | Authority boundaries, no-network measured runs, setup/measured separation, evidence containment outside code worktrees, stop/recovery/escalation/handoff, learner-owned approval. |
| Beginner material is absent or explicitly justified. | pass | Units open on engineering questions; `brief.md` non-goals exclude LLM history and prompting advice. Consistent with `PROFILE.md`. |
| Every prior finding has a recorded disposition. | pass | `codex-review.md` records 32 findings, each with a disposition. This is Claude's first review, so no prior Claude findings exist. |

### Scores

| Dimension | Score | Evidence | Highest-value improvement |
| --- | ---: | --- | --- |
| Technical correctness | 4 | Checks 2–9. Line-exact citation at `check-ledger.ts:404-407`; baseline green at 110/110 while defective; reference 121/121; all four named tests present and passing; `publicationHooks.beforePublish` real; the Node file-level-pass claim independently reproduced in both the unmatched-pattern and absent-test cases. Deductions are C-002, C-003, C-006 — all metadata or configuration description, not taught content. | Fix S10 and the P01 instruction-file description; neither touches the teaching. |
| Technical depth | 5 | Failure atomicity via stage-validate-rename, publication boundaries, observation-versus-mechanism discipline, lossy compaction, precedence and context poisoning, candidate seam versus universal oracle, and a negative control against a false-green test gate. Unit 5's gate design is above what most senior curricula reach. | Keep Modules 02–04 from re-teaching these mechanisms. |
| Production relevance | 5 | Workspace-only authority, no network during measured runs, setup separated from the measured boundary, evidence kept outside code-under-test worktrees, stop/recovery/escalation/handoff contracts, named decision owner, private-path scan in facilitator preparation. | Confirm operational burden in the timed pilot. |
| Source quality and currency | 3 | Seven of eleven registry entries verified exactly (dates and anchors). Two failed at review time: S10's page now documents GPT-6 Astra rather than the recorded GPT-5.6 guidance and does not carry the benchmarking guidance attributed to it (C-002); S01's recorded `2026-08-19` publication date appears nowhere on the article, its `.md` rendering, or the blog index, while every other undated entry is correctly marked `not stated` (C-006). Two defective entries in a registry declared "the sole registry" is a real drop, but the remainder is first-party, correctly anchored, and correctly qualified, so this stays at 3. | Replace the rolling S10 URL with a version-pinned model page and correct the S01 date to `not stated`. |
| Lab validity | 4 | Pins resolve, setup runs verbatim, the pedagogical premise holds under test (green suite plus real defect), acceptance checks are falsifiable, and the Unit 5 gate defeats a false-green that exit status and pass counts accept. Four of five stages are strong. Deductions are C-001 (Unit 4's comparison structure), C-003 (an unrecorded instruction-file divergence inside a stated held-constant), and C-005 (a required reading that consumes the measured budget). | Give Unit 4 a real second configuration; the module already names the zero-cost one. |
| Verification quality | 4 | Evaluator-owned behaviour-level test through a documented candidate seam, withheld artifact, required negative control, exact TAP name match, full check/test/build, independent diff review. Check 7 confirms the negative control is necessary rather than ceremonial. | Define Unit 4's solo-path independent verifier as Unit 5 already does (C-009). |
| Personal relevance | 5 | Matches `PROFILE.md`: begins with the engineering question, no beginner scaffolding, primary sources first, a real repository as the laboratory, falsifiable acceptance criteria, explicit uncertainty marking, and five reusable artifacts. | Confirm the time cost against the learner's weekly budget. |
| Coherence and efficiency | 4 | The chain is genuinely cumulative — Unit 3's map becomes a candidate Unit 4 context input, Units 1–4 feed `workflow-v1`. Counts and arithmetic verified (checks 12, 13). Deductions are C-005 (one unit's required reading is a fourfold outlier while another allocates 10 minutes to a ~250-word section), C-007, C-008. | Rebalance the five required-reading spans against their allocations. |
| **Total / 40** | **34** | `4 + 5 + 5 + 3 + 4 + 4 + 5 + 4 = 34`. Meets the 32 threshold; no dimension below 3; technical correctness and lab validity both at least 4. Gates still fail on open majors and outcome coverage. | Close C-001 through C-005. |

The single point of difference from the lead's 35/40 is source quality and
currency, lowered from 4 to 3 on the two verifiable registry defects above.
Every other dimension is scored identically to the lead's self-assessment, on
independently gathered evidence.

### Source audit

| Claim | Source ID or URL | Primary? | Fresh? | Supports claim? | Notes |
| --- | --- | --- | --- | --- | --- |
| Model output and agent-system outcome are not the same thing. | S01, S06, P01 | yes | yes | yes | S01's "The reusable part is the agent loop" assigns conversation state, streaming, tool use, sandbox/approval enforcement, and cross-turn carry to the harness. S06 states Claude Code "serves as the **agentic harness** around Claude." |
| Context contains more than the user prompt. | S02, S06, S09 | yes | yes | yes | S02: "Context, therefore, must be treated as a finite resource with diminishing marginal returns." Section anchors verified. |
| Context and memory behavior are harness-specific and versioned. | S09, S10, S04 | partly | **no** | partly | S09 and S04 support it exactly; S09 states "Claude treats them as context, not enforced configuration," which Unit 3 cites correctly. **S10 fails**: see C-002. |
| Tools, permissions, sandboxing, and approvals are separate control surfaces. | S01, S08 | yes | yes | yes | S08's `Permission system` and `How permissions interact with sandboxing` sections both verified present. |
| Completion text is not environment verification. | S01, S05, P01 | yes | yes | yes | S05 documents the false-completion mode verbatim: "a later agent instance would look around, see that progress had been made, and declare the job done." Reproduced independently at P01 (checks 4, 7, 8). |
| Repository knowledge needs authority, freshness, and discovery rules. | S09, S02, P01 | yes | yes | yes | Supported, but the exercise omits P01's own `CLAUDE.md` — see C-004. |
| More context and more harness structure are not automatically better. | S02, S03, S04, S10 | yes | partly | yes, minus S10 | S03 and S04 carry this fully ("those assumptions need to be frequently questioned because they can go stale as models improve"). S10 adds nothing; see C-002. |
| One case study cannot establish universal model or harness superiority. | S03, S04, P01 | yes | yes | yes | Unit 4 records confounders and keeps conclusions local throughout. |
| Baseline/reference fault and validation boundaries exist as described. | P01 `bb65b5c..2c498f6` | yes | yes | yes | Independently reproduced: checks 1–9. |

Independent source candidates the lead did not select:

| Candidate | Why it might improve or contradict the module | Disposition |
| --- | --- | --- |
| [agents.md](https://agents.md/), Agentic AI Foundation (Linux Foundation) | A genuinely non-vendor, cross-tool primary source on Unit 3's exact subject, including nearest-file-in-the-tree precedence and cross-tool adoption. It is a better answer to the open D-008 question than S11, which is optional facilitator risk framing rather than subject-matter reading. | Recommend to the lead as the bounded non-vendor required reading candidate for D-008. Reviewer does not add it. |
| [arXiv 2606.25447](https://arxiv.org/abs/2606.25447), *The Interplay of Harness Design and Post-Training in LLM Agents* (2026-06-24) | Bears directly on Unit 4's primary question; reports that harness design and post-training interact rather than compose, and that without careful harness design post-training shows "a drastic performance drop" under tool-environment shift. | Optional depth for Unit 4 only. Limitation: ALFWorld, not coding agents, and it does not test cross-model transfer. Not a required reading. |
| Anthropic, *Demystifying evals for AI agents* | Candidate optional depth for Unit 5's separation of acceptance, regression, security, and independent-review gates. | Note only. |

### Lab audit

- **Stated skill under test:** bounded, evidence-backed decisions across model, context, knowledge, harness, and workflow layers.
- **Baseline/control:** P01 `bb65b5c` in isolated detached worktrees. Verified reproducible; verified green (110/110) while carrying the defect the module teaches.
- **Independent variables:** Unit 2 context packets (a genuine two-configuration comparison); Unit 4 evidence source (**not** a two-configuration comparison — C-001); Unit 5 workflow use.
- **Controlled variables:** frozen task text, baseline commit, acceptance conditions, authority, stop rule, response format. One stated held-constant is wrong in practice: "P01 `AGENTS.md`" (C-003).
- **Observable outcomes:** deterministic focused tests, `pnpm check`/`test`/`build`, destination and staging state inspection, diff review, TAP name matching.
- **Confounders:** the module records model/harness settings, ambient context, telemetry gaps, package-store and network state, seam and test-design variance, prior P01 familiarity, and live-versus-prepared asymmetry. It does **not** record the instruction-file divergence (C-003).
- **Failure and recovery path:** explicit stop conditions, evidence retention, fresh-checkout rollback, named escalation recipient. Complete.
- **Permission and data boundary:** workspace-local writes, no network during measured runs, approval for expansion, sanitized data, evidence outside code worktrees. Complete.
- **Independent verifier:** defined precisely for Unit 5 including a solo default; under-specified for a solo learner on Unit 4's live path (C-009).
- **Can the checks pass while the real outcome is bad?** Yes, in three ways. (a) Unit 4's prepared path can be completed in full without ever comparing two configurations, so outcome 4 is satisfied by an artifact contract rather than by the skill (C-001). (b) A Claude Code learner can record "P01 `AGENTS.md`" as held constant while actually loading `CLAUDE.md`, which carries an extra instruction to verify repository state independently rather than accept the producing agent's summary — the very behaviour Unit 4 grades (C-003). (c) Templates default the evidence-type cell to `actual repository evidence`, so a prepared-path learner who leaves defaults produces a mislabelled artifact (C-007). The module's own acceptance checks would catch (c) but not (a) or (b).

### Adversarial questions

1. **Strongest claim that could be false?** That the artifact chain teaches harness comparison. Unit 4's ten-row inventory is the module's densest teaching, and no required exercise applies it to two configurations.
2. **What would disprove it?** A learner completing Unit 4's prepared path in full and then being unable to name what they held constant *between two agent systems* — because they never had two.
3. **Which mechanism or production failure mode is missing?** Instruction-file resolution across harnesses. The module teaches precedence and ambient-context control but never has the learner check *which* instruction file their own harness loaded, despite P01 shipping two divergent ones.
4. **What content assumes older model, harness, SDK, or protocol behaviour?** S10 only, and it has already drifted (C-002). Everything else is correctly scoped to a checked date and a named product.
5. **What could an experienced engineer skip?** Optional depth, the advanced lab, and roughly 80% of Unit 4's required S08 span, which is permission-rule reference material rather than the approval-versus-sandbox distinction the task needs (C-005).
6. **What advanced prerequisite is assumed but not established?** A working coding-agent configuration and local P01 access. Both are documented, with prepared fallbacks and a recorded release prerequisite.
7. **Does the lab test the outcome or merely generate an artifact?** Units 1, 2, 3, and 5 test the outcome. Unit 4 generates an artifact that its acceptance checks accept without the stated comparison occurring.
8. **What simpler workflow might achieve the same result?** For Unit 4: one agent, one frozen task, two context treatments — with and without Unit 3's orientation map, in fresh sessions. The module already describes this in Unit 4's worked example and in the Unit 4 evidence pack as "a future live B." It costs no second provider and no additional spend, and it is a real two-configuration comparison.
9. **Where would multiple agents add coordination cost without benefit?** Nowhere in the core; the solo path is complete without peers. Correct.
10. **What result would cause us to revise the curriculum itself?** A timed pilot showing Unit 4's live path cannot finish inside 90 minutes once the S08 reading is counted honestly, or a cold-reader run where the learner records `AGENTS.md` as held constant while their harness loaded `CLAUDE.md`.

### Findings

| ID | Severity | Artifact/section | Finding | Evidence | Required change | Status |
| --- | --- | --- | --- | --- | --- | --- |
| C-001 | major | `brief.md` outcome 4; `units/04-harness-comparison.md` exercise; `lab.md` stage 4 | No path exercises the stated comparison of **two agent-system configurations**. Configuration A is one live run; Configuration B is a prepared document. The unit says so plainly — "Configuration B is an explicitly permitted dossier fallback, not a controlled second agent configuration" and "the intended changed dimension is the evidence source" — so the ten-row harness inventory, the unit's core teaching, is never applied to a second configuration by any required exercise. The brief's "or critically analyze the explicitly labeled prepared case" narrows the outcome to fit the exercise rather than covering it. This is not disposed by D-007, which concerns `executed` versus `critically analyzed` labelling, not comparison structure. | `units/04-harness-comparison.md`, "Worked example" and "Exercise"; `brief.md` outcome 4 and its acceptance row; `exercises/evidence/unit-04-harness-case-study.md` "Frozen configurations and controls". | Make the default second configuration a real one. The module already names the zero-cost option in Unit 4's worked example and in the evidence pack: same agent, same frozen task, same authority, changing **only** context treatment by supplying Unit 3's orientation map in a fresh session. Keep the prepared dossier as the no-access fallback, and if it remains a permitted completion path, say in the brief that outcome 4 is then evidenced by analysis rather than by comparison. | open |
| C-002 | major | `sources.md` S10 row, unit-to-source map, claim map, verification notes; `units/01-models-loops-harnesses.md` lines 103 and 207 | S10 cites `https://developers.openai.com/api/docs/guides/latest-model` — a rolling URL that always shows the newest family. Fetched 2026-09-04, it documents **GPT-6 Astra** ("GPT-6 Astra is more intelligent and capable than prior models like GPT-5.6 Sol"), which OpenAI announced as rolling out within the last few days. `sources.md`'s verification note that "S10 was opened at its GPT-5.6 model guidance" is therefore already inaccurate two days after the recorded check, and Unit 1 line 103 tells learners S10 "documents current OpenAI model-family context and tool settings" while line 207 asks them to compare S06 and S10. Separately, the registry attributes to S10 "guidance to benchmark configuration changes on representative work"; the only related sentence on the current page is "If you currently use `none` or `minimal`, start with `low` and compare results," which does not support that description. | Direct fetch 2026-09-04 of the S10 URL and its `.md` rendering; `sources.md` lines 20, 54, 58, 70–73; `units/01-models-loops-harnesses.md` lines 103, 207. Contrast: the claim-map entry it supports is fully carried by S02, S03, and S04. | Cite a version-pinned model page instead of the rolling guide, or keep the rolling URL and label it explicitly as a moving page whose content is expected to change between checks. Correct the relevance cell and the verification note, and drop the unsupported "benchmark ... on representative work" attribution unless a page stating it is cited. `RUBRIC.md`'s source policy requires citing "the exact page supporting the claim." | open |
| C-003 | major | `units/04-harness-comparison.md` Configuration A; `exercises/evidence/unit-04-harness-case-study.md` configuration table; `units/02-context-engineering.md` step 2 | P01 ships **both** `AGENTS.md` (626 bytes) and `CLAUDE.md` (768 bytes) at both pins, and they differ by exactly one line present only in `CLAUDE.md`: "When reviewing Codex-authored work, verify behavior and repository state independently rather than accepting the producing agent's summary." Unit 4 fixes the context as "the frozen task, P01 `AGENTS.md`, normal repository discovery," and the dossier records "Context \| Task, P01 `AGENTS.md`, normal discovery." But S09 — the module's own required Unit 3 reading — states "Claude Code reads `CLAUDE.md`, not `AGENTS.md`." A Claude Code learner therefore records a held-constant that is not what loaded, and the divergent line instructs exactly the independent-verification behaviour Unit 4's acceptance gates assess. Unit 2 step 2 compounds this by naming only "automatic `AGENTS.md` or other ambient context" as the collapse risk. | `git show 2c498f6:CLAUDE.md` vs `:AGENTS.md` (single-line diff, reproduced check 14); `git ls-tree` at both pins shows both files; S09 fetched 2026-09-04, section "AGENTS.md". | State in Unit 4 and in the dossier's configuration table that P01 carries both instruction files with a known one-line divergence, and require the learner to record which file their harness actually loaded rather than assuming `AGENTS.md`. Either equalise the two files in P01 or name the divergence as a recorded uncontrolled difference. Add `CLAUDE.md` to Unit 2 step 2's ambient-context list. | open |
| C-004 | major | `units/03-project-knowledge.md` exercise step 3 and acceptance checks | The knowledge-map artifact list enumerates `AGENTS.md`, `README.md`, the two `docs/superpowers/` files, and `package.json`, and omits `CLAUDE.md` — a root-level instruction file present at both pins. The acceptance check requires "one row for every listed knowledge artifact," so a learner can produce a complete, passing repository knowledge map that omits one of the repository's two instruction files. The omission also discards the unit's best available example: the `AGENTS.md`/`CLAUDE.md` pair is a live instance of exactly the failure the lesson describes — "It consumes context when every copy is loaded, and it drifts when only one copy changes." | `units/03-project-knowledge.md` step 3; `git ls-tree --name-only 2c498f6` root listing; the single-line divergence from C-003. | Add `CLAUDE.md` to the inspected artifact list, and require the map to assign precedence between the two instruction files and record the observed divergence and its retirement rule. | open |
| C-005 | major | `units/04-harness-comparison.md` required reading | The required S08 span, `Permission system` through `How permissions interact with sandboxing`, measures **7,875 words across 571 lines and 18 headings** on the fetched page — including the full permission-rule syntax, wildcard, and per-tool reference sections. At 200 wpm that is roughly 39 minutes of plain reading, before the required note-taking, against a stated allocation of **10 minutes**. The other four units are not comparable: Unit 2 allots 12 minutes to ~2,850 words, Unit 5 allots 10 minutes to ~1,100 words, and Unit 3 allots 10 minutes to a ~250-word section. Unit 4 is a fourfold outlier in the module's largest and most demanding unit, and the overrun comes out of the 35-minute measured run or the 18-minute verification. This is distinct from the acknowledged "planned cap" caveat, which covers learner-work estimates rather than a mis-scoped citation span. | Word and line counts measured directly on the fetched S08 page; per-unit spans measured on S02, S03, S09; `units/*.md` "Core timebox" lines. | Narrow the required span to the two sections the task actually needs — `Permission system` and `How permissions interact with sandboxing` — and move rule syntax, wildcards, and tool-specific rules to optional depth; or raise the allocation and the unit cap accordingly. Rebalance Unit 3's over-generous 10 minutes at the same time. | open |
| C-006 | minor | `sources.md` S01 row | S01's recorded publication date `2026-08-19` is not verifiable on the source. Fetched 2026-09-04, neither the article, its `.md` rendering, nor the OpenAI blog index displays any publication date. The registry correctly records `not stated` for every other undated entry (S06–S10), so the practice is inconsistent here, and `AGENTS.md` requires that publication dates never be invented. | Direct fetch of `https://developers.openai.com/blog/codex-as-a-platform`, its `.md` variant, and `https://developers.openai.com/blog` on 2026-09-04; `sources.md` line 11. | Record `not stated`, or cite in the verification notes where the date is observable (a dated changelog or feed entry). Freshness is unaffected either way, since the policy windows run from the checked date. | open |
| C-007 | minor | `exercises/run-trace-template.md`, `exercises/context-comparison-template.md`, `exercises/harness-case-study-template.md` | All three templates pre-fill the evidence-type cell with `actual repository evidence` — the one label a prepared-path learner must not use — while their own notes state the value is one of three and that "Prepared comparison material is not a learner-run measurement." Under D-006 and D-007 the prepared path is the default no-cost route, so the default value is wrong for the most common case, in the artifacts whose whole purpose is honest provenance labelling. | The three template files; contrast `exercises/knowledge-map-template.md`, which correctly writes the menu inline: "Evidence reference and type: actual repository evidence \| prepared comparison material \| hypothetical counterexample". | Leave the cell blank or write the three-value menu inline, matching the knowledge-map template. | open |
| C-008 | minor | `exercises/evidence/README.md` | `curriculum.md` routes learners to "the matching sanitized [evidence pack index](exercises/evidence/README.md)" as the entry point for the prepared path, but the file's "Minimum pack index" is an empty template table and the file contains no links to the five packs sitting beside it. The prepared path is the module's default no-cost route, so its index is the wrong place to be empty. | `curriculum.md` "Core path" section and "Reference material"; `exercises/evidence/README.md`; the five `unit-0*.md` packs in the same directory. | List the five packs with their consuming unit and evidence type, or relabel the section as the schema learners fill in and link the packs explicitly. | open |
| C-009 | minor | `units/04-harness-comparison.md` live path; `lab.md` completion rubric | Unit 5 defines a concrete solo verification fixture — "an independent engineer or fresh-context agent starts a new isolated P01 checkout" with the evaluator test withheld until after the producer run. Unit 4 requires "an independent verifier writes or runs an evaluator-owned behavior-level test" but never says who qualifies for a solo learner, and its acceptance check asks only that the artifact "identifies the independent reviewer." The workshop states the solo synthesis "is neither independent verification nor approval," so a solo learner on Unit 4's live path has no defined independent channel, while `lab.md`'s rubric requires one for Units 4 and 5. | `units/04-harness-comparison.md` Configuration A step 6 and acceptance checks; `units/05-reusable-workflows.md` cold-reader fixture; `workshop.md` solo synthesis; `lab.md` completion rubric. | Give Unit 4 the same solo default Unit 5 has: a fresh-context agent or second engineer writing the evaluator test without access to the producing session. | open |
| C-010 | note | `sources.md`; D-008 | Two independent candidates the lead did not select. `agents.md` (Agentic AI Foundation, Linux Foundation) is a non-vendor, cross-tool primary source on Unit 3's exact subject — including nearest-file precedence in the directory tree — and is a better candidate for D-008's open "bounded non-vendor required reading" question than S11, which is optional facilitator risk framing rather than subject-matter reading. arXiv 2606.25447 (2026-06-24) bears on Unit 4's model-versus-harness question and reports that the two interact rather than compose, which supports the unit's refusal to attribute an N=1 result to either layer; its limitation is that it evaluates ALFWorld, not coding agents. | Fetched 2026-09-04: `https://agents.md/`, `https://arxiv.org/abs/2606.25447`. | No change required. Offered to the lead as input to D-008, which remains learner-pending. | open |

Finding IDs use `C-001`, `C-002`, and so on. Use only the severities defined in `../../RUBRIC.md`.

### Verdict

- Recommendation: **revise**
- Open blockers: none
- Open majors: C-001, C-002, C-003, C-004, C-005
- Concise rationale: the module's technical core holds up under independent
  testing. Every substantive claim I could execute reproduced exactly, including
  the line-exact `check-ledger.ts:404-407` citation, the green-but-defective
  baseline, all four named regression tests, and — most notably — the
  non-obvious Node false-green that Unit 5 builds its acceptance gate around.
  The lab setup runs verbatim, the pins are immutable and correctly ordered, and
  the epistemic discipline around observations, mechanisms, confounders, and
  prepared-versus-live capability is genuinely strong. It scores 34/40 with no
  dimension below 3 and both gated dimensions at 4.

  It cannot move to `verified` yet. Five majors are open and none is covered by
  an existing decision. The most important, C-001, is structural: Unit 4 teaches
  a harness-comparison framework that no required exercise applies to a second
  configuration, so outcome 4 is satisfied by an artifact contract rather than by
  the skill. The module already names the zero-cost fix in its own worked
  example. C-003 and C-004 share one root cause — the module describes P01 as
  carrying `AGENTS.md` when it carries two divergent instruction files — and that
  divergence lands inside a stated held-constant and favours the behaviour Unit 4
  grades. C-002 shows a rolling source URL drifting inside the review window, and
  C-005 is a required reading roughly four times its allocation.

  I did not lower any score to appear adversarial: seven of eight dimensions
  match the lead's self-assessment on independently gathered evidence, and the
  one difference is tied to two specific registry entries that failed direct
  verification on 2026-09-04.

## Final verification

Complete this section only after Codex records dispositions and revises the module.

- Revision or commit verified:
- Source freshness rechecked:
- Each accepted finding verified:
- Rejected/deferred findings and decision IDs reviewed:
- Reproducible checks rerun:
- New findings:
- Final recommendation: pass | revise | reject
- Quality-gate result:

Claude may recommend `pass`; only the learner may mark the module `approved`.
