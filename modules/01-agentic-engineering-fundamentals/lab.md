# Module 01 Lab — Core Artifact Chain

- Status: designed, not run
- Core timebox: planned 405-minute learner-work cap (6 hours 45 minutes)
- Advanced experiment: [optional and elective, not a core requirement](advanced-lab.md)

## Module outcome

Build an evidence-backed, provider-neutral workflow for bounded engineering
work. The completed chain distinguishes the model, context, harness, tools,
environment, authority, observations, and verification; then turns the
strongest locally supported practice into a bounded workflow decision.

The five unit exercises **are the five stages of this lab**. The core lab adds
no sixth implementation task. It accepts a live execution, prepared evidence,
or the documented combination permitted by each unit; a prepared path still
requires the learner's analysis and completed artifact.

## Time budget and sequence

| Stage | Time | Artifact and unit | Live path | Prepared path |
| --- | ---: | --- | --- | --- |
| 1 | 45 min | [Annotated run trace](exercises/run-trace-template.md), [Unit 1](units/01-models-loops-harnesses.md) | Trace a sanitized run in a disposable checkout. | Analyze [the initialization reconstruction](exercises/evidence/unit-01-run-trace.md). |
| 2 | 60 min | [Context comparison](exercises/context-comparison-template.md), [Unit 2](units/02-context-engineering.md) | Run the frozen read-only packets under the stated controls. | Analyze [the prepared packet comparison](exercises/evidence/unit-02-context-comparison.md). |
| 3 | 75 min | [Knowledge map](exercises/knowledge-map-template.md), [Unit 3](units/03-project-knowledge.md) | Run the before/after discovery probe in a disposable checkout. | Analyze [the prepared knowledge audit](exercises/evidence/unit-03-knowledge-audit.md). |
| 4 | 90 min | [Harness-control case study](exercises/harness-case-study-template.md), [Unit 4](units/04-harness-comparison.md) | Perform and independently verify one bounded task; assess controls and propose one untested configuration change. | Analyze [the prepared dossier](exercises/evidence/unit-04-harness-case-study.md), its control/evidence limits, and one untested configuration change. |
| 5 | 60 min | [`workflow-v1`](exercises/workflow-template.md), [Unit 5](units/05-reusable-workflows.md) | Validate the workflow on the frozen report task in a fresh isolated checkout. | Analyze [the prepared validation dossier](exercises/evidence/unit-05-workflow-validation.md). |
| Decision record | 75 min | [Team decision record](exercises/team-decision-template.md) | Use the async, synchronous, or solo path. | Use the same path with prepared evidence clearly labeled. |

The total is exactly 405 planned learner-work minutes, not an empirical human
completion estimate. Environment provisioning, facilitator preparation,
dependency download, and peer waiting are outside the cap; unit-specified setup
observation/configuration capture stays inside. Stop live work at the unit's
limit and use its prepared pack rather than extending the task, widening
authority, or presenting a partial run as a complete one. A timed human/cohort
pilot is required before learner approval or public release.

## Setup, isolation, and privacy

Run these commands **from the curriculum repository root** on the supported
internal-pilot platform: macOS or Linux with a POSIX shell. They execute local
code and dependency setup, so treat dependency installation as a separate
setup code-execution boundary. They assume the internal-pilot Agent Experiment
Ledger checkout is the sibling directory `../agent-experiment-ledger`:

```bash
export MODULE01_LEDGER_REPO="$(cd ../agent-experiment-ledger && pwd -P)"
export MODULE01_WORK_ROOT="$(mktemp -d /tmp/module-01-work.XXXXXX)"
git -C "$MODULE01_LEDGER_REPO" rev-parse bb65b5cec8c96c3ba3d89b0025473561c7c8146f
git -C "$MODULE01_LEDGER_REPO" rev-parse 2c498f616583d1fd6aeeaa381552b47acdb71ab7
```

The two command results must resolve to these immutable commits:

- Exercise baseline: `bb65b5cec8c96c3ba3d89b0025473561c7c8146f`
- Verified reference: `2c498f616583d1fd6aeeaa381552b47acdb71ab7`

For another directory layout, set these same task-specific variables to their
resolved paths before continuing. During the internal pilot, the facilitator
distributes or grants access to the sibling repository. A verified PowerShell or
other cross-platform setup is a public-release prerequisite, not an implied
supported path.

Create a disposable baseline checkout and an evidence directory outside it:

```bash
mkdir -p "$MODULE01_WORK_ROOT/evidence"
git -C "$MODULE01_LEDGER_REPO" worktree add --detach \
  "$MODULE01_WORK_ROOT/ledger-baseline" \
  bb65b5cec8c96c3ba3d89b0025473561c7c8146f
```

`$MODULE01_WORK_ROOT/ledger-baseline` is code under test. Store each completed
template, command output reference, review record, and sanitized evidence in
`$MODULE01_WORK_ROOT/evidence` or another approved location outside every code
worktree. Units 4 and 5 require their own fresh disposable checkouts at the
baseline; do not reuse a mutated checkout or the ledger's main checkout.

Use only synthetic, sanitized, or approved data. Do not retain raw private
transcripts, credentials, proprietary prompts, private source, or absolute
private paths. Do not enable deployment, release, billing, account
administration, destructive infrastructure, or unrelated-directory access.
Measured live work has no network authority unless the unit explicitly records
an approved named endpoint; setup access, if needed, is separate from the
measured run. Dependency changes, scope changes, destructive commands, and
authority expansion require a human decision before they occur.

## Stage contract

For every stage, keep the unit's frozen task, baseline, acceptance, authority,
and stop rule. Record the selected path and label evidence as actual repository
evidence, prepared comparison material, or a hypothetical counterexample.
Write unavailable telemetry as `unknown`; do not estimate it from another
harness, provider, or evidence pack.

1. Unit 1 produces an annotated run trace with competing hypotheses. It
   separates completion language from external repository or environment
   evidence.
2. Unit 2 produces a bounded context inventory and comparison. It keeps
   observations separate from explanations, records packet cost and orientation
   advantages as confounders, records A/B predictions and falsifiers before any
   result-bearing prepared or live material, and decides per added item whether
   it earns its cost.
3. Unit 3 produces a knowledge map plus before/after discovery evidence. It
   distinguishes an index from a source of truth: live work completes the
   root-listing-only before probe in a fresh context before named inventory or
   prepared results, then uses a second fresh context with only the proposed
   map for after. It does not merge the disposable exercise map into the ledger.
4. Unit 4 evaluates one bounded run or prepared dossier against an explicit
   harness-control and independent-verification contract. A live path evidences
   `executed`; its prepared fallback evidences `critically analyzed` only:
   it analyzes the reference test, frozen behavior invariants, and evaluator seam adaptation
   while explicitly recording that the dossier contains no candidate run, seam,
   evaluator post-run test, or focused candidate result. The frozen task owns
   test design; after the producing session stops, a second engineer or
   fresh-context agent without access to that conversation acts as the
   independent verifier. The evaluator-owned test remains withheld until this
   post-run phase, and the producer's conclusion is not evidence. The verifier
   uses the candidate's documented deterministic seam for a behavior-level
   acceptance test: inject failure immediately before candidate publication;
   require rejection/failure, no destination, no unpublished staging, a clean
   retry, and a blocker-free ledger check. The verifier separately reviews the
   agent-authored test, records seam/test design variance as a confounder, and
   fails acceptance when no observable seam exists. It preserves the frozen
   initialization task and obtains external source, test, and diff evidence.
   Both paths assess all ten harness dimensions with configured/observed value,
   evidence, uncertainty, and consequence, separating instructions from
   enforcement and unknown historical controls from the unit contract. They
   decide the unit's three control scenarios and propose one explicitly
   untested configuration change with a target failure, expected observation,
   falsifier, enforcement mechanism, and held constants. Candidate observations,
   reference evidence, and proposed changes remain separate. The two paths are
   not two measured configurations and establish no configuration effect.
5. Unit 5 produces `workflow-v1` and a validation record for the frozen
   report-request task. It records each workflow step, deviations, external
   acceptance, cold-reader validation or prepared analysis, and the local keep,
   revise, or remove decision. A live cold-reader gate withholds an
   evaluator-owned test until after the producer run, records an
   absent/unmatched-test negative control, then requires the exact named TAP
   test with 1 pass/0 fail before check/test/build. A prepared dossier evidences
   `critically analyzed`, not `executed` workflow skill.

Use the async discussion when peers are available, the synchronous discussion
when scheduled, or the solo challenge path when neither is available. Complete
one [decision record](exercises/team-decision-template.md) in any of those
paths. Peer availability cannot block core completion.

## Completion rubric

Core completion requires all of the following:

- all five unit artifacts are marked `complete` under their selected contracts,
  not merely present; `complete` does not by itself mean `executed`. The
  decision record provides a per-unit/artifact `executed` or `critically
  analyzed` evidence table for live, prepared, or mixed chains;
- one decision record is complete through the async, synchronous, or solo
  path;
- no open safety violation, including unapproved authority expansion, retained
  sensitive material, production use, or evidence kept in a code worktree;
- Units 4 and 5 include external verification: acceptance and regression
  evidence plus an independent source or diff review, rather than producing
  agent self-report. For live Unit 4 work, the verifier is a second engineer or
  fresh-context agent without the producing conversation and receives the
  evaluator test only after the producing session stops;
- Unit 4's case study assesses all ten control dimensions, answers its three
  request scenarios, and specifies one falsifiable configuration change as
  untested; reference correctness cannot stand in for historical harness
  enforcement or candidate acceptance;
- every artifact records material uncertainty and confounders, including
  live-versus-prepared limits where applicable; and
- every conclusion stays within its recorded task, baseline, configuration,
  and evidence boundary.

The optional advanced lab is never required for core completion and does not
add a core outcome.

## Stop, recovery, and handoff

Stop immediately for a safety or privacy boundary, missing immutable commit,
wrong checkout, failed prerequisite, ambiguous authority, failed acceptance,
timebox expiry, spend ceiling, or the unit's repeated-failure limit. Preserve
the current diff, exact command/result references, stop reason, failed
approaches, and unresolved question outside the code worktree. Do not delete
evidence to make a check pass.

Recover only by returning to the pinned baseline in a new disposable checkout,
switching to the unit's prepared pack, or obtaining the required human
decision. A handoff names the checkout and commit, retained evidence location,
authority already used, last external result, next safe action, and why work
stopped. A recovery must not silently change the frozen task, acceptance
criteria, baseline, or authority boundary.
