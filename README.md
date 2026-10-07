# Calculus I — the chain rule (interactive lesson)

A standalone, self-contained interactive lesson page for Rize's **Calculus I** course
(catalog code `MATHS I`), **Unit 6** (the chain rule). Khan-Academy-style: a warm-up,
a try-first problem, a find-the-part interactive, the rule card, worked examples,
fill-in steps checked row by row, a find-the-mistake drill, graded problem sets with
an unlock gate, and an exam-rehearsal section. No login, no backend — student
progress is saved in the browser's own `localStorage`.

**Live:** https://rizecomputerscience.github.io/calc1-chain-rule/

**Source and full build record:** `/Users/samuel/projects/interactive-lessons/` on
Samuel's machine (`lesson/chain-rule.html` is this same file before the self-check
block described below; `lesson/chain-rule.dc.html` is the editable Claude Design
source; `history/` has every review round; `toolkit/` has the reusable patterns,
math engine, and screenshot tooling). Start there with `NOTE-TO-CLAUDES.md` before
building the next page in this kit.

Built October 2026 in a Claude Cowork session with Rize's instructional design lead,
over five rounds of design review.

## What's different in this copy

`index.html` here is the source file plus one appended, clearly marked `<script>`
block that was **not** in the original. The source file never defines
`window.__selfCheck()`, and per the kit's own rule ("do not edit the source"), it
still doesn't — the self-check is additive, added only to this hosted copy, to
satisfy Rize's automated page-health monitor (`swachtel-dev/rize-interactive-health`,
status board at <https://swachtel-dev.github.io/rize-interactive-health/>). It
covers three things:

1. **The page's main sections rendered** — the warm-up, the two worked sections, the
   harder-examples section, exam rehearsal, and the closing summary all mounted with
   real content, and at least 15 problem cards are present (catches a Preact mount
   that silently produces an empty shell).
2. **Math typeset without errors** — the custom typesetter (this page has no MathJax
   or any other CDN dependency) actually produced a `<sup>` for an exponent, and no
   raw `{{...}}` template syntax or `NaN`/`undefined` leaked into the rendered page.
3. **The answer checker grades a known key correctly** — types the correct derivative
   of the warm-up problem (`f(x) = x^4` → `4x^3`) into the real input, clicks the
   real Check button, and asserts the feedback is marked right; then does the same
   with a deliberately wrong answer and asserts it is marked wrong. Restores the
   input and the page's saved-progress `localStorage` entry afterward, so the check
   leaves no trace.

Everything else about the page — the lesson content, the math engine, the fonts — is
unchanged from the source.

## Fonts

Loads Google Fonts (Newsreader, Source Sans 3, IBM Plex Mono) over HTTPS and falls
back to system serif/sans faces if that fails. This is the one external request the
page makes; there is no other CDN or script dependency (Preact is vendored inline,
MIT-licensed, attribution in the page's own script comment).
