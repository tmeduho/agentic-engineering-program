# Learner Profile

## Confirmed profile

- Software architect/developer with more than 10 years of professional experience.
- Wants advanced agentic-engineering capability, not general AI literacy.
- Prefers concise, direct material and minimal beginner explanation.
- Values production-ready guidance, concrete tradeoffs, failure modes, and real exercises.
- Wants Codex and Claude to collaborate while independently critiquing each other's work.
- Prefers free or lower-cost primary material, talks, videos, documentation, and open-source repositories where they match paid-course value.

## Curriculum calibration

Assume fluency with:

- software architecture and system design;
- version control and code review;
- APIs, automated testing, CI/CD, and production operations;
- common security and reliability concerns;
- reading source code, technical specifications, and research papers.

Do not spend time teaching those subjects at an introductory level. Teach the agent-specific implications: how models and harnesses change design choices, failure modes, verification strategy, authority, and operational risk.

## Learning preferences

- Begin with the hard engineering question, not terminology.
- Use primary sources first; use secondary sources for critique, implementation experience, or explanation.
- Favor labs against a real or representative production codebase.
- Require measurable acceptance criteria and independent verification.
- Compare competing approaches and identify when each fails.
- Mark assumptions and time-sensitive claims explicitly.
- Convert each module into reusable artifacts that can improve future work.

## Exercise standard

A useful exercise should require several of these:

- a meaningful architectural or product decision;
- constrained tool access or explicit approval boundaries;
- context selection rather than indiscriminate context loading;
- a real failure, ambiguity, or recovery path;
- instrumented comparison of two approaches;
- tests or observable state that can falsify success;
- a post-run review that changes a durable artifact.

Toy chatbots, prompt collections, and one-shot API wrappers do not meet this standard unless used as isolated probes inside a more demanding experiment.

## Unknowns to resolve when they affect a module

- Preferred implementation language and runtime for course projects.
- Which active project should serve as the main laboratory.
- Weekly time budget and desired completion cadence.
- Available model subscriptions and acceptable API spend.
- Organizational constraints on source code, credentials, telemetry, and external services.

Do not guess these. A module lead should ask only when the answer changes the design.

