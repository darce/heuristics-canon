# Critical source note contract

A critical source note calibrates how far a cited work actually supports the
rules that point at it. It is evidence criticism, not a neutral summary and not
a substitute for reading the source.

Notes live under `public/sources/`. Filename matches the `SOURCES.md` slug
(example: `hubbard-measure-anything-cybersecurity.md`).

## What a note must enable

A reader who already has a rule ID or reasoning card should be able to:

1. identify the work (bibliography) without treating the note as a license
   opinion;
2. see the *narrow question* this note asks of the source;
3. read support / partial / not-found verdicts tied to rule IDs and
   page or section pointers already used in the canon;
4. learn limitations, obsolescence risks, and conflicts with other canon
   arrivals;
5. see what the canon should do next (keep, narrow, re-ground, or refuse);
6. know explicitly what the note cannot answer.

## Required sections

| Section | Content |
|---|---|
| Identity | Slug, bibliographic citation, link to `SOURCES.md` anchor |
| Rights posture | Conservative citation posture; no legal conclusion |
| Narrow question | One question the note is competent to answer |
| Verdicts | Rows: rule ID, verdict, pointer, notes |
| Limitations and obsolescence | Where the source is weak, dated, or domain-bound |
| Conflicts | Where other canon sources pull against this one |
| Canon consequences | Keep / narrow / re-ground / refuse actions |
| Cannot answer | Explicit out-of-scope list |

## Verdict vocabulary

Use only these three verdicts:

| Verdict | Meaning |
|---|---|
| support | The source text, at the pointer, carries the mechanism the rule states |
| partial | Related material exists, but only half the rule (or a weaker form) is present |
| not-found | The rule's mechanism is not located at the cited pointer (or in the work) |

Do not invent intermediate labels. A `partial` row must say which half holds.

Pointers may be chapter, section, or page ranges already used in rule `Src`
cells or verified against the work. Prefer the canon's existing anchors
(`ch-7`, section titles) over new numbering schemes.

## Anti-summary rules (hard)

Do not:

- walk the book in chapter order as a condensation;
- quote the source;
- retell signature stories or worked examples as if they were the note;
- claim the note replaces reading the original;
- state legal conclusions about fair use, license grant, or infringement risk.

Do:

- criticize fitness for the rules that cite the work;
- separate "good book" from "supports this rule ID";
- record gaps honestly so `UNSOURCED` and re-grounding work can proceed upstream.

## Rights posture (fixed language)

Use this posture block unless the operator supplies a stricter one. Do not
strengthen or weaken it into a legal opinion:

> This note identifies a third-party work for citation and evidence
> calibration. The work remains the property of its authors and publishers.
> Citation is not a license to reproduce expression. The private corpus may
> hold research copies under its own `NOTICE.md`; those copies and any
> chapter-level distillations do not ship in the public projection. This note
> makes no determination about fair use, secondary liability, or downstream
> redistribution rights.

## Template

```markdown
# Source note: `<slug>`

## Identity

- Slug: `slug`
- Citation: Author. *Title*. Publisher, year.
- Canon registry: [SOURCES.md](../SOURCES.md#src-slug)

## Rights posture

> This note identifies a third-party work for citation and evidence
> calibration. The work remains the property of its authors and publishers.
> Citation is not a license to reproduce expression. The private corpus may
> hold research copies under its own `NOTICE.md`; those copies and any
> chapter-level distillations do not ship in the public projection. This note
> makes no determination about fair use, secondary liability, or downstream
> redistribution rights.

## Narrow question

...

## Verdicts

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [FAM-NN] | support / partial / not-found | ch-N or section | ... |

## Limitations and obsolescence

- ...

## Conflicts

- ...

## Canon consequences

- ...

## Cannot answer

- ...
```

## Style

Same `WRIT` discipline as reasoning cards. Sparse tables for verdicts; prose
only where a cell would smuggle an argument.
