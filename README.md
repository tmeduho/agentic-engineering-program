# Agentic Engineering Program

A living, Git-based curriculum for learning advanced agentic engineering through research, production-oriented labs, and adversarial review by Codex and Claude.

The repository starts manually. It contains no orchestration code, dependencies, hooks, or scheduled automation. We will automate only after the manual protocol proves useful.

## Start here

Read these files in order:

1. `CHARTER.md` — the capability target and program boundaries.
2. `PROFILE.md` — the learner's background and how material should be calibrated.
3. `ROADMAP.md` — the four-module progression and current ownership.
4. `RUBRIC.md` — the normative quality gates.
5. `DECISIONS.md` — accepted, rejected, and deferred curriculum decisions.
6. The active module's `brief.md`, `sources.md`, `curriculum.md`, and `lab.md`.

`research/mega-dev-curriculum.md` preserves the public MEGA curriculum and the earlier evaluation that led to this program. It is a reference and comparison baseline, not an authority.

## Alternating lead and reviewer

Ownership alternates by module:

| Module | Lead | Adversarial reviewer | Final verifier |
| --- | --- | --- | --- |
| Odd-numbered | Codex | Claude | Claude |
| Even-numbered | Claude | Codex | Codex |

The reviewer does not optimize for agreement. The reviewer tries to disprove the module's claims, expose weak exercises, find better sources, and identify material that does not justify the learner's time.

## Module workflow

1. **Brief** — the lead drafts measurable outcomes, prerequisites, non-goals, constraints, and deliverables. The learner approves material scope changes.
2. **Independent research** — the lead and reviewer identify primary sources independently. Each source receives a publication date, checked date, relevance note, and freshness status.
3. **Draft** — the lead writes the curriculum and lab, then records a self-review in its agent review file.
4. **Adversarial review** — the reviewer scores the module with `evals/curriculum-rubric.md` and records evidence-backed findings in its review file. The reviewer does not rewrite the module during this step.
5. **Revision and rebuttal** — the lead accepts, rejects, or defers every finding; updates the module; and logs material decisions in `DECISIONS.md`.
6. **Verification** — the reviewer checks the final artifacts and reruns any reproducible checks. New problems reopen review.
7. **Learner decision** — the learner approves the module, accepts a documented exception, or sends it back.

## Status lifecycle

`planned` → `draft` → `in-review` → `revision` → `verified` → `approved`

Only the learner may mark a module `approved`. A module may not reach `verified` until it passes every hard gate in `RUBRIC.md`.

## Repository layout

```text
.
├── README.md
├── CHARTER.md
├── PROFILE.md
├── RUBRIC.md
├── ROADMAP.md
├── DECISIONS.md
├── AGENTS.md
├── CLAUDE.md
├── research/
│   ├── inbox/
│   ├── mega-dev-curriculum.md
│   └── source-index.md
├── evals/
│   └── curriculum-rubric.md
└── modules/
    └── 01-agentic-engineering-fundamentals/
        ├── brief.md
        ├── curriculum.md
        ├── sources.md
        ├── lab.md
        ├── claude-review.md
        └── codex-review.md
```

## Working agreement

- Prefer primary sources, real repositories, and reproducible experiments over summaries.
- Distinguish verified facts, assumptions, opinions, and unresolved questions.
- Keep beginner material only when it closes a demonstrated prerequisite gap.
- Every module must leave behind a useful engineering artifact, not only notes.
- Treat model and tool behavior as empirical and version-dependent.
- Log disagreement. Do not erase it by silently rewriting history.
- Keep the program mastery-paced. The four-week structure is organizational, not a deadline.

