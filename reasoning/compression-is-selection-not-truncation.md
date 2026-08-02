# Compression is selection, not truncation

Slug: `compression-is-selection-not-truncation`
ID: `CARD-21`
Mechanism claim: A short output at a tighter budget is a different selection under declared survival rules, not a tail-cut of a longer draft.

## Scope

Covers: Decisions that shrink captions, alt text, audio description, summaries, or other bounded access text when character, time, gap, or token budget tightens; declaring what must survive and what may drop before writing the short form.

Excludes: Full media captioning policy when no budget squeeze exists ([A11Y-09](../lexicons/accessibility.md#a11y-09)); long-form prose style without a hard length or timeline cap; retrieval top-k assembly ([RAG-05](../lexicons/ml-systems.md#rag-05) owns that surface); image assertability and voice splits when the issue is warrant, not budget ([BOUND-01](../lexicons/depiction.md#bound-01), [ATTRIB-03](../lexicons/depiction.md#attrib-03)).

## Observable triggers

- A long draft is shortened by end-cut, ellipsis, or max-length trim with no ranked keep/drop list.
- Short alt, caption, or description keeps decorative color, mood, or filler and omits purpose-critical facts (who/what action, on-screen text, locked cues).
- Audio-description draft exceeds usable non-speech gaps and the fit silently drops cues or overlaps speech.
- Overflow is handled without naming shorten, extend-gap, or pause ([A11Y-40](../lexicons/accessibility.md#a11y-40)).
- Must-include, verbatim, or time-locked cues can be deleted by the fitter ([A11Y-44](../lexicons/accessibility.md#a11y-44)).
- Gap time restates dialog while non-audio visuals remain undescribed ([A11Y-43](../lexicons/accessibility.md#a11y-43)).
- Rank words (main, focus, emphasizes) appear only because the short sentence order invented them ([BOUND-05](../lexicons/depiction.md#bound-05)).

## Causal mechanism

Truncation is positional: last tokens, last sentences, or overflow after a fixed window die first. Importance is not positional. When a tighter budget is treated as "write long, then cut the end," mandatory facts that happen to land late die, and early decorative material survives. The short form then fails its purpose for non-seeing users and under timeline fit: the listener or reader gets residual style and loses locked content. Selection under declared survival rules reverses the order: rank substance, hard-lock critical cues, spend scarce budget on non-redundant information, and name the overflow mode. The short output is a new selection, not a mutilated long one.

## Required action

While a length, gap, or token budget binds:

1. List purpose-critical facts and hard-locked cues before drafting the short form ([A11Y-02](../lexicons/accessibility.md#a11y-02), [A11Y-44](../lexicons/accessibility.md#a11y-44)).
2. Rank substance ahead of style: concrete referents and one sourced claim over intensifiers, filler, and ceremonial "-ing" ([WRIT-03](../lexicons/writing.md#writ-03), [WRIT-05](../lexicons/writing.md#writ-05), [WRIT-12](../lexicons/writing.md#writ-12), [WRIT-13](../lexicons/writing.md#writ-13), [WRIT-17](../lexicons/writing.md#writ-17)).
3. Under audio-description time budgets, fit cues to non-speech gaps; spend gaps on visuals the soundtrack does not already give ([A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-43](../lexicons/accessibility.md#a11y-43)).
4. When draft exceeds budget, name overflow mode: shorten-to-inline, extend non-speech, or pause; prefer place-and-compress before pause; never silent-drop or silent-overlap ([A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-41](../lexicons/accessibility.md#a11y-41)).
5. Locked cues extend or pause rather than delete or relocate ([A11Y-44](../lexicons/accessibility.md#a11y-44)).
6. Mark pure decoration empty or omit it; do not spend budget on style that does not serve purpose ([A11Y-02](../lexicons/accessibility.md#a11y-02), [WRIT-31](../lexicons/writing.md#writ-31), [WRIT-35](../lexicons/writing.md#writ-35)).
7. If rank or order is editorial selection under the budget, say so; do not present sentence order as image privilege ([BOUND-05](../lexicons/depiction.md#bound-05)).

## Predicted failure

The short form drops mandatory facts and keeps decorative ones. Non-seeing users receive a false map of purpose. Critical on-screen text or time-locked events vanish because the optimizer or truncate step treated them as disposable tail. Dialog is restated while unique visuals go undescribed. Overflow freezes or hides content with no recorded decision. Trust in every later short caption falls because survivors look polished and incompleteness is invisible.

## Worked example

The long product caption ends with the on-screen price. Someone pastes it into the 125-character alt field and trims the overflow, so the short form keeps "soft morning light" and loses the price. Write the must-keep list first (name, price, primary action), then draft the short alt to that list. End-trim alone leaves the money fact on the cutting-room floor.

## Exemptions and boundaries

- No hard budget and full-length access text is allowed: compress only for clarity, not as this card's decision.
- Decorative images with intentional empty alt: omit, do not invent a short story ([A11Y-02](../lexicons/accessibility.md#a11y-02)).
- Event proximity and no-spoil timing remain binding when placing compressed cues ([A11Y-42](../lexicons/accessibility.md#a11y-42)); this card does not relax timing to save words.
- Caption voice, identity attribution, and assertable set limits stay in force; a short form may not invent off-frame meaning to sound complete ([ATTRIB-02](../lexicons/depiction.md#attrib-02), [ATTRIB-03](../lexicons/depiction.md#attrib-03), [BOUND-01](../lexicons/depiction.md#bound-01), [BOUND-03](../lexicons/depiction.md#bound-03)).
- Context-window packing for models is a sibling budget problem; do not re-own [RAG-05](../lexicons/ml-systems.md#rag-05) or [FM-02](../lexicons/ml-systems.md#fm-02) here.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [A11Y-41](../lexicons/accessibility.md#a11y-41) compress into non-speech gaps before pause | [A11Y-44](../lexicons/accessibility.md#a11y-44) hard-lock must-include and time-critical cues | Compress free text first; locked cues force extend or pause, never delete |
| object | [A11Y-43](../lexicons/accessibility.md#a11y-43) spend scarce gap time on non-audio visuals | [BOUND-01](../lexicons/depiction.md#bound-01) keep only assertable in-frame inventory | Prioritize visible, checkable facts the soundtrack omits; drop off-frame narrative under the same budget |
| surface | [WRIT-17](../lexicons/writing.md#writ-17) / [WRIT-12](../lexicons/writing.md#writ-12) cut padding and one-point dilution | [A11Y-02](../lexicons/accessibility.md#a11y-02) purpose-critical equivalent must survive | Style and filler lose; purpose payload is not "padding" |
| sequence | [A11Y-40](../lexicons/accessibility.md#a11y-40) name overflow mode when draft exceeds budget | Silent end-truncation of a long draft | Overflow is an explicit mode choice, not a position-based cut |
| surface | [BOUND-05](../lexicons/depiction.md#bound-05) editorial selection under budget | Pictorial rank from crop, contrast, scale | Sentence order may choose what to keep; it must not claim the image ordered it |

## Disconfirmers

- Short and long forms, written independently under the same survival list, retain the same purpose-critical set while only style differs.
- Position-based truncate never removes locked or purpose cues because those always occupy protected slots and the fitter cannot drop them.
- Measured listener or AT outcomes show no gap between "write short under rules" and "truncate long" on comprehension of mandatory facts.
- Overflow is always recorded as shorten, extend, or pause, and silent-drop never appears in production logs.

## Verification

- Diff short vs long: every item on the survival list appears in the short form; every retained decorative phrase is optional under the list.
- Confirm no must-include, verbatim, or time-locked cue was deleted or moved solely to fit ([A11Y-44](../lexicons/accessibility.md#a11y-44)).
- For description tracks: no cue overlaps speech; overflow segments name shorten, extend, or pause ([A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40)).
- Gap-time audit: sentences that only restate dialog are gone when non-audio visuals still need words ([A11Y-43](../lexicons/accessibility.md#a11y-43)).
- Alt check: a non-seeing user gets the purpose; decorative images are empty, not trimmed prose ([A11Y-02](../lexicons/accessibility.md#a11y-02)).
- Strip intensifiers, filler transitions, and ceremonial clauses; if meaning collapses, substance was never ranked ([WRIT-05](../lexicons/writing.md#writ-05), [WRIT-12](../lexicons/writing.md#writ-12), [WRIT-13](../lexicons/writing.md#writ-13)).

## Rule IDs

- [A11Y-02](../lexicons/accessibility.md#a11y-02): purpose (or decorative empty) is the survival criterion for short alt
- [A11Y-39](../lexicons/accessibility.md#a11y-39): non-speech gaps are the real time budget for description
- [A11Y-40](../lexicons/accessibility.md#a11y-40): overflow must be an explicit mode, not silent drop
- [A11Y-41](../lexicons/accessibility.md#a11y-41): compress into gaps before pausing media
- [A11Y-43](../lexicons/accessibility.md#a11y-43): under budget, prefer non-redundant visuals over restated audio
- [A11Y-44](../lexicons/accessibility.md#a11y-44): hard-lock critical cues against optimizer delete
- [WRIT-03](../lexicons/writing.md#writ-03): keep concrete referents; drop decorative stand-ins
- [WRIT-05](../lexicons/writing.md#writ-05): one sourced claim beats intensifier clusters in scarce space
- [WRIT-12](../lexicons/writing.md#writ-12): cut filler that consumes budget without information
- [WRIT-13](../lexicons/writing.md#writ-13): cut ceremonial significance that displaces facts
- [WRIT-17](../lexicons/writing.md#writ-17): cut dilution; short form is one argument, not a trimmed long restatement
- [WRIT-31](../lexicons/writing.md#writ-31): bold and label only data-bearing material under tight layout
- [WRIT-35](../lexicons/writing.md#writ-35): emphasis only where earned, not as template filler
- [BOUND-05](../lexicons/depiction.md#bound-05): budget-driven order is editorial selection, not image privilege

## Principles

- 5. Rank the substance before you style it

## Evidence / source slugs

- [`rescribe-audio-descriptions`](../SOURCES.md#src-rescribe-audio-descriptions): supports [A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-41](../lexicons/accessibility.md#a11y-41), [A11Y-43](../lexicons/accessibility.md#a11y-43), [A11Y-44](../lexicons/accessibility.md#a11y-44)
- [`wcag22-accessibility`](../SOURCES.md#src-wcag22-accessibility): supports [A11Y-02](../lexicons/accessibility.md#a11y-02)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-03](../lexicons/writing.md#writ-03), [WRIT-05](../lexicons/writing.md#writ-05), [WRIT-12](../lexicons/writing.md#writ-12), [WRIT-13](../lexicons/writing.md#writ-13), [WRIT-17](../lexicons/writing.md#writ-17), [WRIT-31](../lexicons/writing.md#writ-31), [WRIT-35](../lexicons/writing.md#writ-35)
- [`barthes-systeme-de-la-mode`](../SOURCES.md#src-barthes-systeme-de-la-mode): supports [BOUND-05](../lexicons/depiction.md#bound-05)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not own full caption ethics, WCAG media requirements outside budget fit, or model context selection. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
