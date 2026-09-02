# Unit 3 — Durable Project Knowledge

**Core timebox:** 75 minutes: lesson 12 minutes; required reading 10 minutes;
current-state map 18 minutes; before/after discovery probe 25 minutes;
self-check and async post 10 minutes.

**Source map:** [S09](../sources.md#technical-sources) is the sole required
reading. S02 is optional context-engineering depth. P01 supplies the prepared
repository evidence at exercise baseline
`bb65b5cec8c96c3ba3d89b0025473561c7c8146f` and reference revision
`2c498f616583d1fd6aeeaa381552b47acdb71ab7`.

## Engineering question

How should project knowledge persist and be found without turning repository
instructions into an unmaintainable context dump?

## Learning outcomes

By the end of this unit, you can:

- classify a project knowledge artifact by authority, scope, owner, freshness,
  precedence, discovery path, and retirement rule;
- distinguish an index from the source of truth, and a useful summary from raw
  evidence with preserved provenance;
- design and test one small progressive-disclosure improvement without claiming
  a speed result that was not measured; and
- decide whether a knowledge artifact earns its maintenance and context cost,
  including the decision to narrow or reject it.

## Lesson

Project knowledge has different jobs and therefore should not have one loading
strategy. **Operating policy** states non-negotiable safety, review, and command
rules. **Project orientation** gives a short architecture map and entry points.
**Decisions** preserve approved constraints and rejected alternatives.
**Task state** holds the current brief, plan, acceptance, and open questions.
**Reference** material supplies APIs, runbooks, and research. **Evidence** is
the raw test output, trace, log, diff, or measurement that can support or
contradict a claim. **Learned corrections** are repeated failures and their
specific prevention.

Place operating policy in the smallest always-loaded control that is actually
needed across work. Make orientation discoverable early and link-rich. Keep
decisions, raw evidence, and detailed reference material discoverable only
when their boundary is in scope. Keep task state task-local, current, and
retirable. This is progressive disclosure: start with a trustworthy route to
the next decision, then retrieve the source material instead of front-loading
the repository into every session.

Each artifact needs an explicit contract. Its **authority** says whether it is
binding instruction, approved product intent, a plan, derived output, or
evidence. Its **scope** says which work it governs. Its **owner** maintains it.
Its **freshness trigger** says when it must be rechecked. Its **precedence**
resolves conflicts. Its **retirement rule** says when it is superseded,
regenerated, archived, or deleted. Without these fields, copied guidance
slowly becomes contradictory folklore.

An index is not a second source of truth. A project-orientation map may name a
path, its purpose, and the decision it unlocks; it must point to the approved
specification, source, or raw test result for the fact itself. Summaries are
useful for routing and handoff, but they are lossy: retain the raw evidence
path, revision, command/output reference, and uncertainty when a conclusion
matters. Do not replace a failed check or a source file with a prose summary of
what it supposedly showed.

Duplication has two costs. It consumes context when every copy is loaded, and
it drifts when only one copy changes. Prefer one authoritative source plus
narrow indexes and links. A repeated correction should become the narrowest
durable control that can prevent it: a test for a behavioral regression, a
path-scoped instruction for local process, a validation tool for a mechanical
rule, or a design decision for an architectural constraint. Do not promote it
automatically into a root instruction file.

Repository instructions become harmful chronological memory dumps when they
record every past task, investigation, and temporary workaround. Such a file
is expensive to load, obscures precedence, and makes stale facts look current.
Keep only stable, cross-cutting policy and orientation there. Link to task
records, decisions, and evidence that have narrower scope and explicit
retirement.

## Required reading

Read S09, [“CLAUDE.md vs auto memory”](https://code.claude.com/docs/en/memory#claudemd-vs-auto-memory), for 10 minutes. Identify the documented writer,
scope, and load behavior for `CLAUDE.md` and auto memory, then compare those
mechanisms with the authority and retirement rules in this unit.

S09 documents **Claude Code** behavior, not a portable repository-memory
standard: its loading, auto-memory storage, precedence, size limits, and
configuration can change with the installed product and settings. In
particular, context-loaded instructions are not an enforcement mechanism. Do
not infer the same behavior for Codex or another harness.

## Worked example

Use the prepared audit in
[unit-03-knowledge-audit.md](../exercises/evidence/unit-03-knowledge-audit.md).
It begins at the Agent Experiment Ledger root and asks one concrete question:
where direct-comparison eligibility is decided, which facts make two controlled
runs comparable, and which checks prevent an ineligible report.

The reference design establishes the inward dependency boundary: comparison
eligibility is a domain rule, `checkLedger` evaluates integrity and comparison
state, and report generation refuses output when the checker finds blockers.
The shortest defensible answer still needs source and test evidence. The
proposed navigation map routes to those files; it does not duplicate their
rules or become a new authority.

## Exercise

Work in an isolated, disposable checkout of P01. Do not add the proposed map
to the Agent Experiment Ledger main branch.

1. Copy [knowledge-map-template.md](../exercises/knowledge-map-template.md)
   outside the code-under-test worktree. Record whether you use the prepared
   material or a live discovery probe.
2. At both pinned revisions, inspect `AGENTS.md`, `README.md`,
   `docs/superpowers/specs/2026-08-27-agent-experiment-ledger-design.md`,
   `docs/superpowers/plans/2026-08-27-agent-experiment-ledger-v0.md`, and
   `package.json`. Inspect the representative source files
   `src/comparison/eligibility.ts`, `src/checks/check-ledger.ts`, and
   `src/reports/service.ts`, plus `test/check.test.ts` and
   `test/report.test.ts`. Inspect Git history at baseline
   `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` and reference
   `2c498f616583d1fd6aeeaa381552b47acdb71ab7`; record the paths and commands
   used.
3. Fill one map row per artifact. Give every row an owner, authority,
   discovery path, load strategy, freshness trigger, precedence, and
   supersession/deletion rule. Mark an index as an index and link it to its
   source of truth; preserve revision and raw-evidence provenance.
4. Run the before probe from **only** a repository root listing. Use this exact
   question:

   ```text
   Where is direct comparison eligibility decided, which facts make two
   controlled runs comparable, and which checks prevent an ineligible report?
   Provide the shortest evidence path from repository orientation to source and
   tests.
   ```

   Record the actual path, result, start/end evidence, and unavailable
   telemetry. Do not add ambient context after the root listing and call it a
   before result.
5. In the disposable checkout, propose the smallest architecture and evidence
   navigation map and link it from project orientation. Start a **fresh
   session** for the after probe with that concise map available from the
   orientation link. Run or inspect the after path, preserving the same
   question and recording the path rather than inferring a timing improvement.
6. Review duplication and source-of-truth boundaries. Keep, narrow, or reject
   the map based on whether its discovery benefit justifies its maintenance and
   context cost. A rejected or narrowed proposal is a valid result. Leave the
   proposed map as disposable exercise material; do not merge it into P01's
   main branch.

## Deliverable

A completed repository knowledge map and before/after discovery record using
the shared template. Store the artifact outside the P01 code-under-test
worktree. Include the pinned revision, exact paths, command/output references,
raw-evidence provenance, and a keep, revise, or reject decision. The concise
orientation map, if retained for a later controlled comparison, becomes a
candidate Unit 4 context input only after its ownership and maintenance cost
are accepted; this exercise does not approve or merge it.

## Acceptance checks

The artifact is complete only if it:

- has one row for every listed knowledge artifact, assigning owner, authority,
  discovery, freshness, precedence, and retirement;
- distinguishes every index from its source of truth and keeps the source path,
  commit, and raw-evidence provenance for material claims;
- records the exact before and after discovery paths, with the before starting
  from a root listing and the after starting in a fresh session from an
  orientation-linked map;
- identifies duplication and drift risk, retains existing sources of truth,
  and narrows or rejects a proposal that merely copies material;
- states where the proposed map would be reviewed and maintained if adopted;
- labels prepared material as prepared and unavailable timing/telemetry as
  `unknown`; and
- makes a bounded keep, revise, or reject decision about discovery benefit
  versus maintenance and context cost.

Mark it `revise` if it calls an index authoritative, replaces source/tests with
a summary, claims a timing gain without a learner measurement, or merges the
exercise proposal into P01.

## Async discussion

Post the artifact you would always load, the artifact you would retrieve only
on demand, and the authority/freshness rule behind each choice. Then answer:
**Which project fact should be always loaded, and which should be discoverable
only when its boundary is in scope?** Challenge one proposed always-loaded
fact for duplication or maintenance cost; working solo, write that challenge
yourself.

## Optional depth

Read S02, [“Context retrieval and agentic search”](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents#context-retrieval-and-agentic-search), after completing the core work. Compare its
just-in-time retrieval and progressive-disclosure discussion with S09's
repository-controlled instructions and machine-local auto memory. Record the
privacy, portability, and freshness tradeoffs: repository material can be
reviewed and shared but may expose project data; machine-local memory may be
personal and less portable; both can become stale. Treat the S09 product
details as Claude Code-specific and configuration-dependent.
