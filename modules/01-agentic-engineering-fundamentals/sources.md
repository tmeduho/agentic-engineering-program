# Module 01 Sources

- Last broadly checked: 2026-09-02; S01 and S10 rechecked: 2026-09-18
- Freshness policy: `../../RUBRIC.md`
- Status: current registry for all five units. Unit files reference these stable IDs and do not repeat source metadata.

## Technical sources

| ID | Source | Publisher | Type | Published/version | Checked | Relevance | Status and freshness |
| --- | --- | --- | --- | --- | --- | --- | --- |
| S01 | [Codex as a platform: build on the open agent harness](https://developers.openai.com/blog/codex-as-a-platform) | OpenAI | First-party engineering article | 2026-08-19 | 2026-09-18 | Describes the agent loop and a Codex harness's context, tools, sandbox, approval, state, and integration responsibilities. | core; current product/harness article checked inside the 30-day window. |
| S02 | [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Anthropic | First-party engineering article | 2025-09-29 | 2026-09-02 | Defines context as model-visible tokens beyond prompts and discusses finite-context curation, compaction, note-taking, and multi-agent context. | core; older engineering guidance rechecked within the 90-day window; do not treat provider examples as universal behavior. |
| S03 | [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) | Anthropic | First-party engineering report | 2026-03-24 | 2026-09-02 | Provides a case study of structured handoffs, context resets, planner/generator/evaluator roles, and measured harness iteration. | core; current engineering report checked within the 90-day window; its observed tactics are case-specific. |
| S04 | [Scaling Managed Agents: Decoupling the brain from the hands](https://www.anthropic.com/engineering/managed-agents) | Anthropic | First-party engineering article | 2026-04-08 | 2026-09-02 | Separates session, harness, and sandbox interfaces and explains why model-specific harness assumptions can become stale. | supporting; current engineering article checked within the 90-day window. |
| S05 | [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | Anthropic | First-party engineering report | 2025-11-26 | 2026-09-02 | Documents incremental progress, durable handoffs, session boundaries, and a false-completion failure mode in one long-running-agent setup. | supporting; older report rechecked within the 90-day window; compare it with newer evidence rather than generalizing its tactics. |
| S06 | [How Claude Code works](https://code.claude.com/docs/en/how-claude-code-works) | Anthropic | First-party product documentation | not stated | 2026-09-02 | Current Claude Code architecture, agent loop, tool use, context, and working-directory behavior. | core; current product behavior checked inside the 30-day window; applies only to the documented Claude Code version/configuration. |
| S07 | [Claude Code settings](https://code.claude.com/docs/en/settings) | Anthropic | First-party product documentation | not stated | 2026-09-02 | Current configuration scopes, precedence, environment settings, and extensibility controls in Claude Code. | supporting; current product behavior checked inside the 30-day window; settings depend on the installed version and configured scopes. |
| S08 | [Configure permissions](https://code.claude.com/docs/en/permissions) | Anthropic | First-party product documentation | not stated | 2026-09-02 | Current Claude Code permission rules, modes, sandboxing, and approval boundaries. | core; current product behavior checked inside the 30-day window; permissions, sandboxing, and approvals are documented control surfaces, not universal equivalents. |
| S09 | [How Claude remembers your project](https://code.claude.com/docs/en/memory) | Anthropic | First-party product documentation | not stated | 2026-09-02 | Current Claude Code memory files, scopes, imports, discovery, and project instruction behavior. | core; current product behavior checked inside the 30-day window; memory behavior is Claude Code-specific and configuration-dependent. |
| S10 | [Model guidance](https://developers.openai.com/api/docs/guides/latest-model) | OpenAI | First-party product documentation | not stated | 2026-09-18 | Rolling current-model guide for visible model-family settings, reasoning/context management, and tool behavior. | core; rolling product page checked inside the 30-day window; its family, names, defaults, settings, and tool support can change between checks. |
| S11 | [NIST AI 600-1: Generative AI Profile](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence) | NIST | Official technical publication | 2024-07-26 | 2026-09-02 | Optional facilitator/security material for scoped risk framing, documented governance, and evaluation/verification considerations. | optional; NIST says AI RMF 1.0 is being revised, so use this as voluntary risk-management guidance, not as a current product-behavior source or mandatory unit reading. |

## Scope and local evidence

| ID | Source | Publisher/author | Type | Published/version | Checked | Status | Use and constraint |
| --- | --- | --- | --- | --- | --- | --- | --- |
| R01 | [`../../research/mega-dev-curriculum.md`](../../research/mega-dev-curriculum.md) | not stated | Local research snapshot | not stated | 2026-08-26 | supporting | Supports only MEGA's public agenda and format snapshot. It does not establish paid lesson depth, technical truth, or parity. |
| P01 | Agent Experiment Ledger — internal-pilot sibling repository, configured by `MODULE01_LEDGER_REPO` | not stated | Primary local repository evidence | reference revision `2c498f616583d1fd6aeeaa381552b47acdb71ab7`; exercise baseline `bb65b5cec8c96c3ba3d89b0025473561c7c8146f` | 2026-09-02 | core | Git history, source, tests, and README support the prepared cases, their lifecycle/evidence boundaries, and their deterministic checks. Public repository location/access is a deferred release prerequisite. |

## Unit-to-source map

Each unit has one required 10–15 minute source selection. Every other source in
its row is optional or facilitator material; P01 supplies the shared prepared
case rather than a required reading.

| Unit | Stable source IDs | Required 10–15 minute selection | Optional or facilitator material |
| --- | --- | --- | --- |
| 1. Models, loops, and harnesses | S01, S06, S10, P01 | S01 | S06, S10, P01 |
| 2. Context engineering | S02, S06, S09, P01 | S02 | S06, S09, P01 |
| 3. Project knowledge | S02, S09, P01 | S09 | S02, P01 |
| 4. Harness comparison | S01, S03, S07, S08, P01 | S08 | S01, S03, S07, P01 |
| 5. Reusable workflows | S03, S04, S05, S11, P01 | S03 | S04, S05, S11, P01 |

R01 maps to the program's public-agenda/format provenance only. It is not a
unit reading or technical authority, so it is intentionally absent from the
five unit source lists.

## Claim-to-source map

| Claim family | Support | Taught in | Qualification |
| --- | --- | --- | --- |
| Model output and agent-system outcome are not the same thing. | S01, S06, P01 | Unit 1 | A model response is one event inside a configured loop; the observed outcome also depends on context assembly, tool execution, environment, authority, and verification. |
| Context contains more than the user prompt. | S02, S06, S09 | Unit 2 | The exact model-visible inputs and their ordering are harness-specific; the examples are not a universal context schema. |
| Context and memory behavior are harness-specific and versioned. | S09, S04 | Units 2 and 3 | Claude Code memory behavior is provider documentation; recheck the installed harness and distinguish its mechanism from a general context or memory claim. |
| Tools, permissions, sandboxing, and approvals are separate control surfaces. | S01, S08 | Unit 4 | These controls can interact in a product, but neither source establishes that every harness exposes or enforces them in the same way. |
| Completion text is not environment verification. | S01, S05, P01 | Units 1 and 5 | Completion text is an agent claim; the module requires external acceptance results, state inspection, and deterministic checks for the prepared case. |
| Repository knowledge needs authority, freshness, and discovery rules. | S09, S02, P01 | Unit 3 | The rules are a maintainability design for the learner's repository, not a claim that a provider's memory mechanism is sufficient. |
| More context and more harness structure are not automatically better. | S02, S03, S04 | Units 2 and 4 | These sources support bounded, representative comparisons; benefits and costs depend on the task, model family, and configuration. |
| One case study cannot establish universal model or harness superiority. | S03, S04, P01 | Unit 4 | Unit 4 is an N=1 comparison with recorded confounders; it can support a local workflow decision only. |

## Verification notes

- S01 was rechecked on 2026-09-18 at its “The reusable part is the agent loop”
  section; the official article visibly displays its publication date as
  `Aug 19, 2026`. S02 was opened at “Context engineering vs. prompt
  engineering”; S03 at “Why naive implementations fall short”; S04 at its
  session/harness/sandbox interface discussion; and S05 at “The long-running
  agent problem.”
- S06–S09 were opened at their current architecture, settings, permissions,
  and memory documentation respectively. No visible publication or version
  date was supplied on those pages, so this registry records `not stated`.
- S10 was rechecked on 2026-09-18 at its rolling GPT-6 Astra model guidance,
  including model-family naming, reasoning effort, persisted reasoning/context,
  and tool calling. It gives a condition-specific instruction to compare
  reasoning-effort results; it does not establish representative-workload
  comparison guidance. No visible publication or version date was supplied, so
  this registry records `not stated`.
