# Reasoning card contract

A reasoning card reconstructs a *decision* around one causal mechanism. It is
not a book digest, a chapter tour, or a complete reading of any source.

Cards live under `reasoning/` in a published layout (authored as this tree).
They are optional intermediate depth above the lexicon row.
[SOURCES.md](../SOURCES.md) is the bibliography registry only and is not a
substitute for original works.

## Audiences on a card

- **Human-readable:** Title, Scope, Observable triggers, Causal mechanism,
  Predicted failure, Worked example, Exemptions and boundaries, Non-claims.
  Explain the mechanism in plain language.
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
narrative. Every required section must have a non-empty body. The literal `<!--`
substring is refused anywhere in a card body (see **No HTML comments** below),
so HTML comments cannot pad or hide section content; HTML tags and link
reference definitions do not count as body text. A CommonMark HTML block is
rejected when it is unterminated (types 1–5 run to EOF) or when its span covers
required `##` headings or their bodies — including a terminated opener in the
preamble that wraps the whole card. Types covered for that span check: 1 and
3–6 (`<script`/`<pre`/`<style`/`<textarea`, `<?`, `<!` + letter, `<![CDATA[`,
and block-level tags such as `<div>`). Type 2 (`<!-- … -->`) is already
refused by the literal-`<!--` ban, so type-2 classification cannot change
acceptance — any remaining type-2 handling is redundant diagnostic only.
Type 7 is out of scope. Required `##` headings inside fenced code blocks do
not satisfy a required section; HTML comments are banned outright and so
cannot supply one.
Invisible characters and HTML entities that render as nothing also do not count.
The Worked example gate is a **bounded writing aid**, not a security boundary
and not a complete confusable detector. It counts prose words after stripping
those non-rendered constructs (NFKC, entity-decode, drop format/control/
combining marks; tokens need a letter/number core of length at least two),
applies a **bounded** confusable skeleton (script-agnostic single-letter Unicode
names plus a hand-written multi-token name map — multi-token names absent from
that map, e.g. LISU LETTER CA, stay unfolded; full confusable closure is not
stdlib-achievable), requires a corpus-derived minimum length (with margin below
the live corpus minimum), and a soft distinct-word ratio (first use of each
skeleton key costs fully; further repeats cost less, so coherent domain-verb
reuse is not penalised as padding) with margin below the measured whole-body
minimum on live cards. Length alone is not concreteness: single-token padding,
tag soup, link-definition padding, and *in-bound* lookalike padding fail those
checks. Soft distinctness does **not** reject every short-phrase reuse — an
eight-word phrase repeated three times can still score above the 0.65 floor
(soft ≈0.667) and pass; a human reviewer still reads the card.

## Card identity

Two identities sit side by side:

- **Path / slug** — published surface. The path is `reasoning/<slug>.md`; the
  `Slug:` line must equal the filename stem. A post-publication rename is
  **retire + add**, not `mv` — the old slug stays retired and is never reused.
- **Card ID** — immutable lineage. The body carries an `ID:` line in the same
  backticked form as `Slug:` (value `CARD-NN`; never a path segment). Once
  issued, an ID is never reused or reassigned, including after retirement.
  (Authoring tracks issuance in a private ledger that is not part of the
  published tree; public consumers treat the body `ID:` line as the durable
  identifier.)

**No HTML comments in a card body.** The literal substring `<!--` is refused
anywhere in a card, including inside fenced and indented code. There is no
escape hatch: a card that needs to discuss the opener must describe it rather
than write it.

**Card identity scan.** A line is an identity line when its first content
character is the start of `ID:` or `Slug:`. "First content" means after
skipping whitespace and Unicode characters whose general category is one of
`Cf`, `Cc`, `Mn`, `Mc`, or `Me` (a category membership test, not a code-point
list). That skip applies **only when locating the first content character on
the line**; those characters are **not** removed from inside the keyword, so
`I` + U+200B + `D:` (or `ID` + U+200B + `:`, or `S` + U+200B + `lug:`) is not
an identity line. The scan runs over every raw body line — including lines
inside fenced and indented code blocks. Exactly one `ID:` identity line and
exactly one `Slug:` identity line are required; a second of either kind is a
duplicate and is refused. The sole line of each kind must match the strict
backticked pattern (Slug and ID each written as the keyword, optional
whitespace, then a backticked value) with the keyword at column 0: a sole
identity line that has leading whitespace or a skipped-category prefix before
the keyword is refused as indented (identity lines must start at column 0),
not accepted. Do not add `Lo` or `So` to the skip set: `Lo` includes ordinary
CJK and Hangul letters, so skipping it would misclassify multilingual prose
such as a line that begins with Japanese text then `ID:`. Do not add `Po`
either: it includes ordinary punctuation (`!`, `.`, `,`, `#`, `%`, `&`, `*`),
so skipping it would misclassify far more prose than the CJK case. Residual
hiders are a class — any character that renders as nothing yet falls outside
`{Cf, Cc, Mn, Mc, Me}` and outside `str.isspace()` — not a closed list;
non-exhaustive examples include U+3164 HANGUL FILLER (`Lo`) and U+2800
BRAILLE PATTERN BLANK (`So`). A CommonMark list marker (`-`, `1.`),
blockquote marker (`>`), or heading marker (`#`) before the text means the
line is not an identity line; those markers are not stripped. Card body text
is normalized so CRLF and lone CR become LF before the scan (including
`.json` string values), so a CR-glued second identity line is still a
duplicate.

The H1 title is free to move independently of the slug (many cards already
carry an H1 that no longer kebab-cases to their slug).

| Section | Content | Audience |
|---|---|---|
| Title, slug, and ID | Stable filename slug; body-level `CARD-NN`; one-line mechanism claim | both |
| Scope | What decision class this card covers; what it deliberately excludes | human |
| Observable triggers | Concrete signals in artifacts, plans, metrics, or diffs | human |
| Causal mechanism | Why those triggers produce the named failure | human |
| Required action | What to do while the trigger holds | agent |
| Predicted failure | What breaks if the action is skipped or faked | human |
| Worked example | One concrete situation: trigger, action applied, failure without it | human |
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
ID: `CARD-NN`
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

## Worked example

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

Apply the [`WRIT`](../lexicons/writing.md#fam-writ) family to card prose: plain
diction, sparse markup, few em dashes, no bold-first bullet theater, no fractal
section previews. Prefer checkable nouns over intensifiers.
