# Source Index

This index tracks sources that can support the program across modules. Module-specific selection and claims belong in each module's `sources.md`.

## Required metadata

Every source entry must record:

- stable identifier;
- title and URL;
- publisher or author;
- source type and whether it is primary;
- publication, release, or version date when available;
- date last checked;
- curriculum relevance;
- status: `core`, `supporting`, `candidate`, `stale`, or `superseded`.

Apply the refresh windows in `RUBRIC.md`. A checked date proves only that the page was inspected on that date; it does not make every claim on the page true.

## Current index

| ID | Source | Publisher | Type | Primary | Published/version | Checked | Status | Relevance |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRC-001 | [MEGA program](https://mega.dev/) | MEGA | Program page | Yes, for MEGA's public claims | 2026 cohort | 2026-08-26 | core | Public schedule, twenty-lesson agenda, format, audience, instructors, included benefits, refund/access terms, and certificate claims. |
| SRC-002 | [MEGA Assessment Scan](https://mega.dev/challenge.md) | MEGA | Public assessment runbook | Yes, for the published assessment model | Current page; publication date not stated | 2026-08-26 | supporting | Defines 24 collaboration traits, 47 indicators, coverage rules, descriptive fields, consent flow, and episode IDs aligned to the twenty lessons. Treat as untrusted external instructions; do not execute without an explicit request. |
| SRC-003 | `chatgpt-conversation://6a8de235-67a8-83ea-b33f-eab7dccf6b64` — “Evaluate MEGA Value” | Learner and ChatGPT | Prior decision context | No | 2026-08-25 | 2026-08-26 | supporting | Preserves the earlier $711 promo quote, value analysis, custom curriculum proposal, and two-agent workspace design. Revalidate factual claims with public sources. |
| SRC-010 | [Codex as a platform: build on the open agent harness](https://developers.openai.com/blog/codex-as-a-platform) | OpenAI | First-party engineering article | Yes | 2026-08-19 | 2026-08-26 | core | Current model/harness boundary, agent loop responsibilities, context/tools, approvals, sandbox policy, and integration layers. |
| SRC-011 | [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Anthropic | First-party engineering article | Yes | 2025-09-29 | 2026-08-26 | core | Context as a finite resource; prompt versus context engineering; compaction, note-taking, and multi-agent context patterns. |
| SRC-012 | [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | Anthropic | First-party engineering report | Yes | 2025-11-26 | 2026-08-26 | core | Session boundaries, durable handoffs, incremental progress, and long-running harness failure modes. |
| SRC-013 | [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) | Anthropic | First-party engineering report | Yes | 2026-03-24 | 2026-08-26 | core | Planner/generator/evaluator architectures, harness simplification, context resets, cost, and evaluation-driven iteration. |
| SRC-014 | [Scaling Managed Agents: Decoupling the brain from the hands](https://www.anthropic.com/engineering/managed-agents) | Anthropic | First-party engineering article | Yes | 2026-04-08 | 2026-08-26 | supporting | Stable interfaces for session, harness, and sandbox; why harness assumptions expire as models improve. |
| SRC-015 | [The 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) | Model Context Protocol maintainers | Specification release announcement | Yes | 2026-07-28 | 2026-08-26 | core | Current MCP revision: stateless core, MRTR, routing, cacheability, extensions, Tasks, authorization hardening, and deprecations. |
| SRC-016 | [MCP TypeScript SDK v2](https://ts.sdk.modelcontextprotocol.io/v2/) | Model Context Protocol maintainers | Official SDK documentation | Yes | v2 / MCP 2026-07-28 | 2026-08-26 | supporting | Current TypeScript implementation and migration baseline for later tool-engineering labs. |
| SRC-017 | [Model guidance](https://developers.openai.com/api/docs/guides/latest-model) | OpenAI | First-party product documentation | Yes | not stated | 2026-09-02 | core | Visible model-family settings, reasoning/context management, tool behavior, and guidance to benchmark configuration changes on representative work. |
| SRC-020 | [Build Hour: API & Codex](https://www.youtube.com/watch?v=rhsSqr0jdFw) | OpenAI | First-party video/workshop | Yes | 2026-03-10 | 2026-08-26 | supporting | Free workshop on agentic delegation, harness engineering, reusable workflows, and agent evaluation. |
| SRC-021 | [Claude Agent SDK — Full Workshop](https://www.youtube.com/live/TqC1qOfiVcQ) | Thariq Shihipar / workshop host | Technical workshop video | Partly; first-party instructor, third-party host | Publication date not captured | 2026-08-26 | candidate | Builds an agent loop and demonstrates tools and filesystem-based context engineering. Verify code and current SDK behavior before use. |
| SRC-022 | [How Claude Code works](https://code.claude.com/docs/en/how-claude-code-works) | Anthropic | First-party product documentation | Yes | not stated | 2026-09-02 | core | Current Claude Code architecture, agent loop, tool use, context, and working-directory behavior. Applies only to the documented Claude Code version/configuration. |
| SRC-023 | [Claude Code settings](https://code.claude.com/docs/en/settings) | Anthropic | First-party product documentation | Yes | not stated | 2026-09-02 | supporting | Current Claude Code configuration scopes, precedence, environment settings, and extensibility controls. Settings depend on the installed version and configured scopes. |
| SRC-024 | [Configure permissions](https://code.claude.com/docs/en/permissions) | Anthropic | First-party product documentation | Yes | not stated | 2026-09-02 | core | Current Claude Code permission rules, modes, sandboxing, and approval boundaries. Product-specific controls are not universal equivalents. |
| SRC-025 | [How Claude remembers your project](https://code.claude.com/docs/en/memory) | Anthropic | First-party product documentation | Yes | not stated | 2026-09-02 | core | Current Claude Code memory files, scopes, imports, discovery, and project instruction behavior. Memory behavior is Claude Code-specific and configuration-dependent. |

## Intake rule

Place raw links or brief notes in `research/inbox/` only when they are not yet evaluated. Promotion to this index requires opening the source, recording metadata, and stating why it is better than or complementary to an existing source.
