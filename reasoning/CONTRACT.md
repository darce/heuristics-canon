# Reasoning card contract

A reasoning card reconstructs a *decision* around one causal mechanism. It is
not a book digest, a chapter tour, or a complete reading of any source.

Cards live under `public/reasoning/`. They ship with the public projection when
the operator includes this tree. Private `distilled/` material never becomes a
card by renaming; a card must be re-authored as mechanism, not condensation.

## What a card must enable

An agent (or reviewer) reading only the card and the cited rule rows should be
able to:

1. notice when the mechanism is in play (observable triggers);
2. name the failure mode if the action is skipped;
3. take a concrete action with named exemptions;
4. partition tensions by surface, object, or sequence instead of averaging;
5. state what would disconfirm the mechanism and how to verify compliance;
6. walk outward to principles, rule IDs, and source slugs for deeper audit.

## Required sections

Use these headings in order. Keep each section short. Prefer named lists over
narrative.

| Section | Content |
|---|---|
| Title and slug | Stable filename slug; one-line mechanism claim |
| Scope | What decision class this card covers; what it deliberately excludes |
| Observable triggers | Concrete signals in artifacts, plans, metrics, or diffs |
| Causal mechanism | Why those triggers produce the named failure |
| Required action | What to do while the trigger holds |
| Predicted failure | What breaks if the action is skipped or faked |
| Exemptions and boundaries | When the card does not apply; what still does |
| Tensions | Opposed rules, each fully right on a surface / object / sequence cut |
| Disconfirmers | Observations that would weaken or retire the mechanism claim |
| Verification | Cheap checks that the action was actually taken |
| Rule IDs | Existing `[FAM-NN]` only; verify they resolve in the lexicons. Discovery indexes only this section. The same ID may appear on multiple cards; consumers open every matching card once in slug order. |
| Principles | Numbered entries in `PRINCIPLES.md` that carry this mechanism |
| Evidence / source slugs | Existing `SOURCES.md` slugs only; no chapter tour |
| Non-claims | Explicit book-reconstruction refusals |

## Anti-reconstruction rules (hard)

Do not:

- order material as a book's table of contents or author argument sequence;
- quote sources, paraphrase signature examples, or invent "the author's"
  catchphrases as if they were the card's voice;
- claim completeness ("everything important about X");
- introduce rule IDs, principle numbers, or source slugs that are not already
  in the private canon;
- smuggle private distillation structure (candidate row blocks, chapter maps,
  long exemption matrices copied from `distilled/`).

Do:

- synthesize across *unrelated* sources when they share a mechanism;
- keep prose shorter than a private distillation for the same topic;
- cite IDs so a reader can open the rule row for trigger text and tier.

## Template

Copy this skeleton when adding a card. Delete instructional comments.

```markdown
# <Mechanism title>

Slug: `<kebab-slug>`
Mechanism claim: <one sentence>

## Scope

Covers: ...
Excludes: ...

## Observable triggers

- ...

## Causal mechanism

...

## Required action

...

## Predicted failure

...

## Exemptions and boundaries

- ...

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface / object / sequence | [ID] ... | [ID] ... | ... |

## Disconfirmers

- ...

## Verification

- ...

## Rule IDs

- [FAM-NN]: role in this card (one short clause)

## Principles

- N. <principle title as in PRINCIPLES.md>

## Evidence / source slugs

- `slug`: what this source contributes to the *mechanism* (not a chapter list)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every important idea in its domain. For bibliography and support
verdicts, open the linked source note when one exists. For the full rule row,
open the lexicon. Private distillations are not published.
```

## Style

Apply the `WRIT` family to card prose: plain diction, sparse markup, few em
dashes, no bold-first bullet theater, no fractal section previews. Prefer
checkable nouns over intensifiers.
