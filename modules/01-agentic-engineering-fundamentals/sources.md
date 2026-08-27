# Module 01 Sources

- Last checked: 2026-08-26
- Freshness policy: `../../RUBRIC.md`
- Status: initial source set; Claude must add an independent candidate during adversarial review.

## Core technical sources

| ID | Source | Type | Published/version | Checked | Module use | Freshness note |
| --- | --- | --- | --- | --- | --- | --- |
| S01 | [Codex as a platform: build on the open agent harness](https://developers.openai.com/blog/codex-as-a-platform) — OpenAI | Primary engineering article | 2026-08-19 | 2026-08-26 | Model/harness boundary; agent loop; context, tools, state, sandbox, approvals, and integration layers. | Current inside 30-day window. |
| S02 | [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — Anthropic | Primary engineering article | 2025-09-29 | 2026-08-26 | Finite context, prompt versus context engineering, compaction, note-taking, and multi-agent context strategy. | Older than 90 days but foundational; relevance rechecked. Recheck for superseding guidance before verification. |
| S03 | [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) — Anthropic | Primary engineering report | 2026-03-24 | 2026-08-26 | Planner/generator/evaluator design, measurable criteria, long-running execution, context resets, cost, and harness simplification. | Recheck within 90 days at module verification. |
| S04 | [Scaling Managed Agents: Decoupling the brain from the hands](https://www.anthropic.com/engineering/managed-agents) — Anthropic | Primary engineering article | 2026-04-08 | 2026-08-26 | Session/harness/sandbox separation and the expiration of model-specific harness assumptions. | Recheck within 90 days at module verification. |
| S05 | [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) — Anthropic | Primary engineering report | 2025-11-26 | 2026-08-26 | Durable handoffs, incremental progress, session boundaries, and limits of compaction. | Foundational historical baseline; compare with S03/S04 rather than treating every tactic as current. |

## Free workshops and demonstrations

| ID | Source | Type | Published | Checked | Use | Caveat |
| --- | --- | --- | --- | --- | --- | --- |
| V01 | [Build Hour: API & Codex](https://www.youtube.com/watch?v=rhsSqr0jdFw) — OpenAI | First-party workshop video | 2026-03-10 | 2026-08-26 | Agentic delegation, harness engineering, reusable workflows, and evaluation. | Product/API details must still be checked against current official documentation. |
| V02 | [Claude Agent SDK — Full Workshop](https://www.youtube.com/live/TqC1qOfiVcQ) — Thariq Shihipar | Technical workshop video | Date not captured | 2026-08-26 | Builds an agent loop and demonstrates tools and filesystem-based context engineering. | Supporting source; verify current SDK behavior before following code. |

## Curriculum reference

| ID | Source | Use | Constraint |
| --- | --- | --- | --- |
| R01 | [`../../research/mega-dev-curriculum.md`](../../research/mega-dev-curriculum.md) | Comparison baseline for MEGA Week 1 topics and value proposition. | Does not establish technical truth or require parity. |

## Claim-to-source map

| Claim | Support | Qualification |
| --- | --- | --- |
| An agent's behavior depends on a surrounding harness, not only the model and prompt. | S01, S03, S04 | Harness boundaries differ by product; inspect the version actually used. |
| Context engineering includes instructions, tools, retrieved data, history, and evolving state. | S02 | Exact context assembly is harness-specific and may be partly hidden. |
| Long-running work benefits from durable state/handoff artifacts and explicit progress. | S03, S05 | Specific tactics such as forced context resets may become obsolete with newer models. |
| More harness structure is not automatically better. | S03, S04 | Validate components through controlled removal or comparison. |
| Agent completion text is not proof of the environment outcome. | S01 plus the lab's verification design | This is a system-design conclusion; the module must demonstrate it empirically. |

## Source gaps for review

- Current first-party Claude Code documentation for repository instructions, permissions, and observable run metadata.
- A strong independent source that challenges or limits the context-engineering claims above.
- A practical source on experimental design for nondeterministic coding-agent comparisons.
- Exact telemetry available from the learner's installed Codex and Claude versions.

Claude should fill at least one gap before scoring source quality.

