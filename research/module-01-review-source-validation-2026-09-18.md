# Module 01 Claude Finding Source Validation — 2026-09-18

## Scope and method

This is a source-validation note for C-002, C-005, C-006, and C-010 only. I
checked the current primary pages named in the review on 2026-09-18. Product
documentation is treated as a dated snapshot; it is not evidence about an
uncited prior version. The exact source URLs are cited below.

## C-002 — S10 is a rolling model guide with a stale description

**Recommendation: accept in substance; refine the required change.**

The current [OpenAI Model guidance](https://developers.openai.com/api/docs/guides/latest-model)
page is now headed “Using GPT-6 Astra” and identifies GPT-5.6 Sol as a prior
model. It therefore supports the review's central observation: the `latest-model`
URL is rolling, and `sources.md`'s 2026-09-02 verification note claiming a
GPT-5.6 reading is stale. Its current migration advice says to start at `low`
reasoning effort in the specified case and compare results; it does **not** say
to benchmark configuration changes on representative work. The current page
also continues to document product- and version-specific settings, so the
optional Unit 1 comparison remains useful only with that qualifier.

Implication for the cited material: retain S10 if desired, but label it a
rolling current-model guide; replace the stale GPT-5.6 verification note with
the family actually read and its checked date; and remove or separately source
the “representative-workload” attribution. A version-pinned replacement is not
strictly necessary if the page is explicitly marked rolling and rechecked
within the 30-day product-documentation window. Unit 1's optional comparison
should continue to require a checked date and prohibit generalizing the cited
settings to other harnesses.

## C-005 — Unit 4's required S08 span cannot fit its stated allocation

**Recommendation: accept.**

The wording in Unit 4 is unambiguous: it assigns everything from
[“Permission system”](https://code.claude.com/docs/en/permissions#permission-system)
through [“How permissions interact with sandboxing”](https://code.claude.com/docs/en/permissions#how-permissions-interact-with-sandboxing).
On Anthropic's current official Markdown rendering, that inclusive span is
lines 11–602: 592 lines, 26 headings/subheadings, and 8,592
whitespace-delimited words (measured locally from that rendering on
2026-09-18). At 200 words per minute, the text alone is about 43 minutes,
before the required note and interaction analysis. The span includes rule
syntax, wildcards, tool-specific rules, hooks, and working-directory material,
not only the two concepts the exercise asks learners to distinguish.

The current [S08 permissions page](https://code.claude.com/docs/en/permissions)
does support the lesson's technical distinction: permissions control tool and
file/domain access, whereas sandboxing provides OS-level enforcement for shell
process filesystem and network access. It does not support assigning the whole
reference span a 10-minute read.

Implication for the cited material: replace “through” with two discrete,
bounded excerpts: the `Permission system` section (before `Manage permissions`)
and `How permissions interact with sandboxing`. Move rule syntax, tool-specific
rules, hooks, and working-directory behavior to optional depth. That preserves
the exercise's approval-versus-sandbox objective and makes its 10-minute
allocation plausible.

## C-006 — S01's publication date is visible

**Recommendation: reject.**

As checked on 2026-09-18, the [Codex as a platform article](https://developers.openai.com/blog/codex-as-a-platform)
visibly displays “Aug 19, 2026” beneath the page navigation and above the
title. It also directly supports S01's harness relevance: the article defines
the harness as the execution system that maintains context, inspects
information, calls tools, exposes progress, handles failures, requests
approval, and returns a result. Therefore `sources.md`'s `2026-08-19` value is
currently verifiable and should remain.

This conclusion is a current-page result. It does not invalidate the reviewer's
reported 2026-09-04 observation that the date was then absent; the page can
have changed after that check.

## C-010 — supplementary cross-tool and research candidates

**Recommendation: accept as a note, with narrower paper wording; no required
source-registry change.**

The [AGENTS.md site](https://agents.md/) states that the format is stewarded by
the Agentic AI Foundation under the Linux Foundation and says the closest
`AGENTS.md` in the directory tree takes precedence. It is a suitable primary
source for those format-site claims and a credible non-vendor candidate for
Unit 3. It is not evidence that every coding-agent implementation follows that
precedence, so any use must retain a product-specific qualifier.

[arXiv:2606.25447v1](https://arxiv.org/html/2606.25447v1), submitted 2026-06-24,
is a primary research preprint and a relevant optional Unit 4 candidate. In its
ALFWorld tool-integrated setting, it treats the harness as a controllable
dimension, finds that training-time harness application outperforms post-hoc
application, and reports robustness differences under tool-environment shift.
That supports the narrower statement that harness design and post-training
have joint, configuration-dependent effects. The paper does not use an
additive-composition analysis; replace “interact rather than compose
additively” with that narrower statement. It studies ALFWorld rather than
coding agents, so it cannot establish cross-harness or cross-model transfer.

The current optional status is appropriate. Adding either source as a required
reading needs a separate scope/timebox decision (including D-008), not a
source-correction response.

## Disposition summary

| Finding | Validation result | Concise action |
| --- | --- | --- |
| C-002 | Supported in substance | Mark S10 rolling, refresh the checked content, and remove/separately source the representative-workload claim. |
| C-005 | Supported | Bound the required S08 excerpts; keep the broad reference material optional. |
| C-006 | Not supported as of 2026-09-18 | Keep S01's `2026-08-19` date; it is visible on the official article. |
| C-010 | Supported as a candidate note, with qualification | Preserve optional status; describe the paper's joint effects, not an untested additive claim. |
