# Module 01 Workshop — Evidence Review and Decision

- Duration: 75 minutes, completed asynchronously by default or in an optional meeting
- Output: one completed [team decision record](exercises/team-decision-template.md)
- Inputs: the five completed unit artifacts and their cited evidence packs or live evidence

This workshop turns the five core artifacts into one bounded practice decision.
It is not a vote on a provider, a claim of workflow improvement, or a substitute
for the acceptance and independent-review gates in the units. A learner may use
live evidence, prepared comparison material, or both, but must label the type
and preserve its limits.

Shared material must be sanitized: no raw transcripts, credentials, proprietary
prompts, private source, or private absolute paths. Keep learner artifacts and
command evidence outside code-under-test worktrees. The learner retains
learner-owned approval authority; a facilitator can summarize evidence but cannot approve a
decision for the learner.

## Async-first path

Post the following in any asynchronous medium that can carry Markdown. A
discussion board, review comment, email, or plain Markdown file all work; no
particular collaboration product is required. Peer availability cannot block
completion. If nobody is available, use the prepared critique in the solo path
below and complete the same class of decision record, marked `solo`.

### 1. Learner artifact summary

Post a short summary for one artifact, preferably the claim most likely to
change a workflow decision.

```markdown
## Artifact summary — <artifact and date>

- Path: live | prepared | mixed
- Per-unit capability/evidence record: complete the decision template table;
  do not collapse a mixed chain to one label.
- What I attempted or analyzed:
- Observation: <directly evidenced result>
- Evidence and provenance: <commit, command/result, sanitized pack item, or review>
- Current conclusion: <bounded to task/configuration>
- Uncertainty and confounders:
- One claim I invite a challenge on:
```

Do not replace an observation with a mechanism. Record unavailable telemetry as
`unknown`.

### 2. Evidence-backed challenge

Challenge one conclusion, not the author. Cite counterevidence, an omitted
control, or a prepared failure scenario. A polished assertion without evidence
is not a challenge.

```markdown
## Challenge — <artifact and claim>

- Claim challenged:
- Alternative explanation or failure scenario:
- Evidence or prepared scenario and provenance:
- What this evidence can and cannot establish:
- Narrower conclusion I think the record supports:
- Evidence needed to resolve the disagreement:
```

### 3. Author response or revision

The author may defend a conclusion with new evidence, narrow it, revise the
artifact, or record an unresolved disagreement. Do not silently alter a frozen
task, baseline, acceptance condition, or authority boundary.

```markdown
## Author response — <artifact and claim>

- Challenge addressed:
- Evidence considered:
- Response: retained | revised | unresolved
- Revised conclusion or reason it remains bounded:
- Artifact/evidence change, if any:
- Remaining uncertainty and next safe evidence:
```

### 4. Facilitator synthesis

The facilitator identifies recurring evidence patterns and gaps. This is a
synthesis, not an approval or a substitute for independent verification.

```markdown
## Facilitator synthesis — <cohort/date>

- Recurring supported observation:
- Repeated unsupported inference or missing control:
- Evidence types represented and gaps:
- Candidate decision state: adopted | rejected | further-test
- Limits that remain after discussion:
- Follow-up evidence or course correction to capture:
```

For a solo path, the learner authors this fourth-stage synthesis after the
prepared or self-authored critique and the author response. It must distinguish
claims supported by cited evidence, unresolved disagreement or uncertainty, and
what carries into the decision record:

```markdown
## Solo synthesis — <artifact and date>

- Claims supported by cited evidence:
- Unresolved disagreement, uncertainty, or missing evidence:
- Evidence types represented and limits:
- What carries into the decision record:
```

This self-synthesis is neither independent verification nor approval.

### 5. Decision record

Copy [the shared decision-record template](exercises/team-decision-template.md)
and complete it. The record must name evidence provenance, uncertainty,
dissent, owner, revisit trigger, and what the decision does not establish.
Choose only `adopted`, `rejected`, or `further-test`. A solo learner uses the
same template, identifies the prepared critique as the challenge source,
authors the solo synthesis, and sets `Participants: solo`.

## Solo and group variants

| Group size | Path |
| --- | --- |
| Solo | Select a prepared evidence-pack counterexample or write the strongest alternative explanation; respond to it; author the solo synthesis; complete a solo decision record. |
| Two people | Exchange reciprocal critiques: each person challenges the other’s artifact, then each responds before one shared or two linked decision records. |
| Three to eight people | Work as one group. Rotate facilitator, evidence presenter, skeptic, and recorder through the review; record dissent rather than forcing consensus. |
| More than eight people | Use breakout groups. Each group has one synthesis recorder, produces a bounded synthesis, and sends it to the whole cohort for a final decision record or explicitly scoped records. |

## Optional 75-minute meeting

Use this meeting only when it is useful; it does not replace the async path or
make attendance a completion requirement. The agenda totals exactly 75 minutes.

| Time | Activity | Output |
| ---: | --- | --- |
| 10 min | Calibration | Agree on evidence labels, scope limits, privacy boundary, and one claim worth testing. |
| 15 min | Paired failure diagnosis | Identify the earliest preventable layer and competing hypotheses for one run trace or workflow failure. |
| 20 min | Artifact comparison | Compare context, knowledge, or harness artifacts; separate observations, explanations, and confounders. |
| 15 min | Adversarial workflow review | Challenge authority, stop, recovery, and independent-verification gates in `workflow-v1`. |
| 10 min | Team decision | Complete the decision record with a bounded `adopted`, `rejected`, or `further-test` result. |
| 5 min | Debrief | Capture unresolved evidence and course-feedback candidates. |

Rotate these roles when the group size permits:

- **Facilitator:** protects timeboxes, evidence and privacy boundaries, and the learner’s approval authority; synthesizes without deciding for the learner.
- **Evidence presenter:** points the group to the exact artifact, provenance, and scope limit.
- **Skeptic:** supplies alternative explanations, failure scenarios, missing controls, or disconfirming evidence.
- **Recorder:** completes the shared synthesis and decision record, including dissent and unknowns.

Consensus is formative. It never replaces the unit’s external acceptance,
regression, or independent-review evidence.

## Completion and recovery

Completion requires the same [decision record](exercises/team-decision-template.md)
in async, meeting, or solo form. It does not authorize publication, a license
choice, a change in module status, or an approval claim. See
[facilitator-guide.md](facilitator-guide.md) for preparation, evaluation, and
recovery procedures.
