# Reasoning card contract

A reasoning card reconstructs a *decision* around one causal mechanism. It is
not a book digest, a chapter tour, or a complete reading of any source.

Cards live under `reasoning/` in a published layout (authored as this tree).
They are optional intermediate depth above the lexicon row.
[SOURCES.md](../SOURCES.md) is the bibliography registry only and is not a
substitute for original works.

## Audiences on a card

- **Human-readable:** Title, Scope, Observable triggers, Causal mechanism,
  Predicted failure, Exemptions, Non-claims. Explain the mechanism in plain
  language.
- **Agent application:** Required action, Tensions, Disconfirmers, Verification,
  Rule IDs, Principles, Evidence / source slugs. Imperative checks, partitions,
  and resolvable links live here.

Do not paste the same paragraphs into README, AGENTS, PRINCIPLES, and cards.
Rows hold triggers and tiers; principles hold cross-domain navigation; cards
hold multi-rule decision synthesis. Prefer one causal mechanism per card; do
not merge opposed principles into a force-level mega-card.

## What a card must enable

An agent (or reviewer) reading only the card and the cited rule rows should be
able to:

1. notice when the mechanism is in play (observable triggers);
2. name the failure mode if the action is skipped;
3. take a concrete action with named exemptions;
4. partition tensions by surface, object, or sequence instead of averaging;
5. state what would disconfirm the mechanism and how to verify compliance;
6. walk outward to principles, linked rule IDs, and linked source-registry
   slugs for deeper audit.

## Required sections

Use these headings in order. Keep each section short. Prefer named lists over
narrative.

| Section | Content | Audience |
|---|---|---|
| Title and slug | Stable filename slug; one-line mechanism claim | both |
| Scope | What decision class this card covers; what it deliberately excludes | human |
| Observable triggers | Concrete signals in artifacts, plans, metrics, or diffs | human |
| Causal mechanism | Why those triggers produce the named failure | human |
| Required action | What to do while the trigger holds | agent |
| Predicted failure | What breaks if the action is skipped or faked | human |
| Exemptions and boundaries | When the card does not apply; what still does; plain pointers to sibling cards | human |
| Tensions | Opposed rules, each fully right on a surface / object / sequence cut | agent |
| Disconfirmers | Observations that would weaken or retire the mechanism claim | agent |
| Verification | Cheap checks that the action was actually taken | agent |
| Rule IDs | Existing `[FAM-NN]` only, each a Markdown link to the lexicon row anchor (e.g. `[RES-02](../lexicons/engineering.md#res-02)`). Discovery indexes only this section. The same ID may appear on multiple cards when mechanisms genuinely share it; consumers open every matching card once in slug order. Exclusive ownership (when stated) means sibling cards may only plain-pointer in boundaries, not re-list the ID as an owned action. | agent |
| Principles | Numbered entries in `PRINCIPLES.md` that carry this mechanism | agent |
| Evidence / source slugs | Existing `SOURCES.md` slugs only, each a Markdown link to `../SOURCES.md#src-<slug>`. Phrase each entry as support for the linked public rule IDs on this card, not as a mini-summary of the source's contribution. | agent |
| Non-claims | Explicit book-reconstruction refusals | human |

Rule ID references elsewhere on the card (prose, tables, lists) use the same
lexicon-anchor link form. Relative paths are correct from `reasoning/`.

## Anti-reconstruction rules (hard)

Do not:

- order material as a book's table of contents or as an author-specific
  argument sequence;
- quote sources at length, paraphrase signature examples, or invent "the
  author's" catchphrases as if they were the card's voice;
- claim completeness ("everything important about X");
- invent rule IDs, principle numbers, or source slugs that are not already
  in the canon;
- reproduce chapter-tour structure, long source-specific exemption tours, or
  other book-reconstruction scaffolding.

Do:

- synthesize across *unrelated* sources when they share a mechanism;
- keep prose compact so the card remains a decision aid, not a substitute for
  any source;
- cite IDs so a reader can open the rule row for trigger text and tier;
- stay a compact mechanism synthesis of existing rules with bibliography
  pointers.

## Coverage policy

Cards are selective pilots for hot multi-source mechanisms. Prefer depth on a
few useful mechanisms over a thin card per principle or per rule. There is no
claim of full principle or force coverage. Overlap of rule IDs across cards is
allowed when each card keeps one causal mechanism; consumers open every
matching card once in slug order. When two cards would repeat the same
decision, merge or delete one. Plain cross-card pointers belong in
Exemptions and boundaries, not duplicated Rule IDs sections.

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
| surface / object / sequence | [ID](../lexicons/<file>.md#id) ... | [ID](../lexicons/<file>.md#id) ... | ... |

## Disconfirmers

- ...

## Verification

- ...

## Rule IDs

- [FAM-NN](../lexicons/<file>.md#fam-nn): role in this card (one short clause)

## Principles

- N. <principle title as in PRINCIPLES.md>

## Evidence / source slugs

- [`slug`](../SOURCES.md#src-slug): supports [FAM-NN](../lexicons/<file>.md#fam-nn)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every important idea in its domain. For bibliography identity, open
SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a
substitute for the original work.
```

## Style

Apply the `WRIT` family to card prose: plain diction, sparse markup, few em
dashes, no bold-first bullet theater, no fractal section previews. Prefer
checkable nouns over intensifiers.
