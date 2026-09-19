# Annotated Run Trace

- Artifact status: complete | revise | not attempted
- Run identity:
- Task and baseline/reference:
- Evidence location: outside the code-under-test worktree
- Evidence references: commit(s), file path(s), command output(s), or sanitized pack item(s)
- Telemetry unavailable or withheld (record as `unknown`):

## Event sequence

Add one row for each material event. Use only labels that apply; leave an
inapplicable label blank rather than inferring it.

| Order/time | Event | Intent | Context | Inference | Tool | Environment | Observation | State | Authority | Verification | Human decision | Evidence reference | Evidence type | Uncertainty |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Evidence type is one of: `actual repository evidence`, `prepared comparison
material`, or `hypothetical counterexample`.

## Failure analysis

- Failure or unexpected outcome:
- Earliest preventable layer: model inference | context assembly | agent loop | tool | environment | authority | verification | human decision
- Why this is the earliest preventable layer:

| Hypothesis | Evidence for | Evidence against | Current disposition | Residual uncertainty |
| --- | --- | --- | --- | --- |
| 1.  |  |  | supported; rejected; unresolved |  |
| 2.  |  |  | supported; rejected; unresolved |  |
| 3.  |  |  | supported; rejected; unresolved |  |

## Conclusion

- Conclusion supported by the evidence:
- What the trace cannot establish:
- Residual uncertainty and next evidence needed:
