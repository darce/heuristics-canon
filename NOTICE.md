# Licensing and rights

This repo holds several kinds of material under distinct postures. The public
repo's [`NOTICE.md`](https://github.com/darce/heuristics-canon/blob/main/NOTICE.md)
is the published projection of this file. Nothing here is a legal conclusion
about fair use, secondary liability, or downstream redistribution rights.

## Own expression (CC BY 4.0), published

The following are written here, in our own words, and are offered under
**CC BY 4.0** when projected to the public repo (which carries the license text):

| Material | Location (private → public) |
|---|---|
| Rule rows | `lexicons/*.md` → `lexicons/*.md` |
| Convergence principles | `PRINCIPLES.md` → `PRINCIPLES.md` |
| Reasoning-card prose | `public/reasoning/**` → `reasoning/**` |
| Critical source-note prose | `public/sources/**` → `sources/**` |
| Public entrypoint prose | `public/README.md`, `public/AGENTS.md` → root templates |

A rule states a condition and the action it calls for; what it takes from a
source is the *idea* — which copyright does not cover — and not the source's
sentences, which it does. That is what makes these files ours to license, and
it is a claim each row has to keep earning: a row (or card, or note) that
reproduces a source's phrasing rather than restating its mechanism is a defect,
and `distilled/` exists precisely so the condensations that do track their
sources closely never leave this repo.

Attribution string:

> Heuristics Canon by Daniel Arcé (github.com/darce/heuristics-canon), licensed under CC BY 4.0.

## Explicitly outside the CC BY grant

The CC BY 4.0 grant above covers **only** the original rule, principle, card,
and note prose (and the public entrypoint templates). It does **not** cover:

- third-party books, papers, standards, or other works identified in
  `SOURCES.md`, source notes, or rule `Src` cells;
- any quotation, paraphrase, or chapter-level condensation of those works;
- material under `distilled/` or `literature/` (research copies and
  authoring arguments; never distributed);
- third-party marks, titles, or identities used only for citation.

Cited works remain the property of their authors and publishers. Citation is
not a license to reproduce expression. Source notes state a conservative
citation posture only; they do not grant rights and do not clear publication
of source text.

## Tooling

`tools/` is MIT: [`tools/LICENSE`](tools/LICENSE). That includes
`tools/eval_reasoning.py` and the reasoning-eval fixtures under
`tools/fixtures/reasoning-eval/` (scenarios, sample responses, protocol).
Fixtures never embed private distillation body text.

## Research copies, never distributed

`distilled/` and `literature/` derive from third-party sources held
`research-copy-only`. They are not licensed for distribution and are never
published: copyright protects a source's expression, not its ideas, and a
chapter-by-chapter condensation can substitute for the book. The one-line rules
and intermediate public cards/notes ship; the condensations do not. This is the
whole reason this repo is private and the public repo exists.

Per-source rights posture lives in this repo's `tools/canon.py` (`RIGHTS_DEFAULT`,
relaxed only by an explicit `RIGHTS_OVERRIDES` entry, never by guessing from a
label) — the durable machine record. The public projection does not break rights
out per source: its generated `SOURCES.md` points to the public `NOTICE.md`, which
states the single conservative posture (every cited work belongs to its authors;
cited, never reproduced).

## Public projection surface (for operators)

What `tools/publish.py` projects: lexicons, PRINCIPLES.md, generated SOURCES.md,
public README/AGENTS templates, `reasoning/`, `sources/`, and on cut a
`heuristics-canon/release@2` manifest with SHA-256 digests. Removal of a
published rule ID, card, or note is a breaking release; addition is minor;
content-only change is patch. See `AGENTS.md` and the public README.

_Last reviewed: 2026-07-24._
