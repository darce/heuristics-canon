# Constrained domains have solved it

Slug: `constrained-domains-have-solved-it`
Mechanism claim: When a task requires describing something in words, look first for a domain already forced to do it under an external constraint; that constraint is what produced a reusable vocabulary, grammar, or ordering rule.

## Scope

Covers: plan, schema, prompt, or product paths that turn a finite descriptive attribute, a media alternative, a control name, or a known technical sub-problem into free-form generation; decisions about lookup, classification, native platform semantics, or an adopted constrained-domain grammar versus open invention.

Excludes: pure literary or open-interpretive description with no inter-party agreement duty; which attribute classes may safely close into a controlled set (sibling card [controlled-vocabulary-caps-hallucination](controlled-vocabulary-caps-hallucination.md)); multi-budget survival rules once a description already exists (sibling card [compression-is-selection-not-truncation](compression-is-selection-not-truncation.md)); claim-bearer assignment for non-visible photo content (sibling card [attribute-claims-to-their-bearer](attribute-claims-to-their-bearer.md)).

## Observable triggers

- A plan, schema, or prompt field generates free text for a descriptive class that already has a named enum, code list, catalog term, or provider ID in the same artifact or its declared dependencies.
- A custom widget, invented ARIA role set, or bespoke control vocabulary appears where a native element already carries name, role, and keyboard behavior.
- Media description is drafted as unconstrained prose while a speech gap, overflow mode, event lock, or must-include cue is already in play.
- A model is asked to invent terms, labels, or algorithms for a problem that appears in a standard catalog, library, or domain lexicon already used by the project.
- Review prose renames the same technical referent for variety, or mints a coined concept label as if it were an established term.
- Output invents rank or order for image content from sentence order alone, without a pictorial cue.

## Causal mechanism

External constraints (legal access, spoken-only transmission, inter-party agreement, reproducibility, catalog correctness) force a domain to fix vocabulary, grammar, and order so strangers can check the result. Unconstrained free generation does not pay that cost, so it reinvents a private map that sounds precise and is not membership-checkable. Generating where a lookup, native control, or named catalog already works burns model cost and invents drift; the reusable artifact from the constrained domain was the cheap correct path.

## Required action

1. For each free-form generative description field, list any already-named vocabulary, enum, catalog, standard identifier, or constrained-domain grammar in the plan or dependencies ([AGT-11](../lexicons/engineering.md#agt-11), [ALG-06](../lexicons/engineering.md#alg-06)).
2. When a name is present, emit by lookup or classification and validate membership; do not open-generate the same class ([FM-04](../lexicons/ml-systems.md#fm-04), [COG-02](../lexicons/interaction-ux.md#cog-02), [AIPX-01](../lexicons/business-marketing.md#aipx-01)).
3. Prefer retrieve-and-cite for attributable or changing facts; do not fine-tune or free-generate them into the text ([FM-06](../lexicons/ml-systems.md#fm-06)).
4. For interactive controls, take the native element first; invent ARIA only after native fails ([A11Y-12](../lexicons/accessibility.md#a11y-12)).
5. For non-text media, meet the alternative-track duty, then adopt the audio-description fit, overflow, proximity, and hard-lock rules already forced by the speech constraint ([A11Y-09](../lexicons/accessibility.md#a11y-09), [A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-41](../lexicons/accessibility.md#a11y-41), [A11Y-42](../lexicons/accessibility.md#a11y-42), [A11Y-43](../lexicons/accessibility.md#a11y-43), [A11Y-44](../lexicons/accessibility.md#a11y-44)).
6. Keep purpose-fit alt and concrete, stable terms; refuse invented concept labels and elegant-variation synonyms ([A11Y-02](../lexicons/accessibility.md#a11y-02), [WRIT-03](../lexicons/writing.md#writ-03), [WRIT-06](../lexicons/writing.md#writ-06), [WRIT-27](../lexicons/writing.md#writ-27), [NAME-02](../lexicons/engineering.md#name-02), [DOM-03](../lexicons/engineering.md#dom-03)).
7. When no constrained-domain name appears in the artifact, do not mint a private closed vocabulary; keep free text under assertable bounds or mark acquisition of a real constrained domain as open work ([BOUND-01](../lexicons/depiction.md#bound-01), [ARCH-08](../lexicons/engineering.md#arch-08)).

## Predicted failure

Teams reinvent a controlled vocabulary badly: terms look specific, disagree across authors, and cannot be membership-checked. Generation replaces lookup, so model cost and hallucination risk buy a mapping that already existed. Accessibility alternatives invent rank, inventory, or timing the constrained domain already ordered. Readers and downstream machines treat private coinages as shared facts.

## Exemptions and boundaries

- Domains that describe for pleasure or open interpretation are not sources of binding vocabulary for product claims.
- This card does not decide which attribute classes may close; that cut belongs to [controlled-vocabulary-caps-hallucination](controlled-vocabulary-caps-hallucination.md).
- Length-budget selection (what must survive a shorter caption) belongs to [compression-is-selection-not-truncation](compression-is-selection-not-truncation.md).
- Who may own non-visual photo claims belongs to [attribute-claims-to-their-bearer](attribute-claims-to-their-bearer.md).
- A general "search the web for prior art" hunt with no named list in the plan is not a fireable action; name the candidate domain or keep free text.
- [ARCH-05](../lexicons/engineering.md#arch-05) still owns when shared assets change too fast to reuse; this card owns description vocabulary and constraint-born grammar, not platform reuse rates.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [FM-04](../lexicons/ml-systems.md#fm-04) schema-constrain machine-consumed emission | [BOUND-01](../lexicons/depiction.md#bound-01) refuse totalizing claims a still cannot warrant | close only classes with named checkable referents; keep free text or attribution for open interpretive residue |
| surface | [A11Y-12](../lexicons/accessibility.md#a11y-12) native control semantics first | [A11Y-02](../lexicons/accessibility.md#a11y-02) purpose-fit text when no native non-text equivalent exists | native owns interactive roles; alt/description owns non-text purpose, not reinvented widgets |
| sequence | [A11Y-39](../lexicons/accessibility.md#a11y-39) fit cues into non-speech gaps first | [A11Y-44](../lexicons/accessibility.md#a11y-44) hard-lock critical cues even if fit must extend or pause | compress and place first; only then pause or extend for locked cues, never silent-drop |
| object | [WRIT-06](../lexicons/writing.md#writ-06) / [NAME-02](../lexicons/engineering.md#name-02) reuse the established term | [WRIT-27](../lexicons/writing.md#writ-27) refuse undefended coined labels | reuse only terms with a real referent or lexicon home; do not invent a faux catalog |
| surface | [BOUND-05](../lexicons/depiction.md#bound-05) rank from pictorial cues only | [A11Y-43](../lexicons/accessibility.md#a11y-43) spend scarce gap time on non-audio visuals | selection under budget is editorial and explicit; never report word order as image privilege |

## Disconfirmers

- Free generation of a class with a named catalog in-repo yields lower error and lower cost than validated lookup under the same eval.
- A native control plus platform accessibility tree still fails name/role/keyboard where a carefully built custom widget passes both human AT and automated checks.
- Audio-description overflow and fit rules from the constrained domain increase listener error versus unconstrained free prose under the same gap budget.
- Coined project labels with no external constraint outperform stable domain terms on inter-reader agreement and maintenance cost.

## Verification

- Every free-form description field in the plan either cites a named vocabulary/provider ID or is explicitly marked free-text with assertable bounds.
- Emission paths for closed classes reject out-of-set strings (or take a declared degrade/abstain branch) rather than pass them.
- Custom widgets document why a native element was insufficient.
- Description timelines show gap fit, named overflow mode, and hard-locks for must-include cues.
- Diffs do not introduce synonym pairs for one concept or undefended coined concept labels.

## Rule IDs

- [ALG-06](../lexicons/engineering.md#alg-06): catalog the solved sub-problem before inventing code or terms
- [AIPX-01](../lexicons/business-marketing.md#aipx-01): ship deterministic lookup or heuristic before model generation
- [FM-04](../lexicons/ml-systems.md#fm-04): bind machine-consumed description to a validated schema or enum
- [FM-06](../lexicons/ml-systems.md#fm-06): retrieve attributable knowledge instead of generating it
- [AGT-11](../lexicons/engineering.md#agt-11): look up named facts already in the artifact before asking or inventing
- [A11Y-12](../lexicons/accessibility.md#a11y-12): take the platform-native control the constrained platform already solved
- [A11Y-02](../lexicons/accessibility.md#a11y-02): purpose-constrained text equivalent, not free inventory
- [A11Y-09](../lexicons/accessibility.md#a11y-09): require captions, audio description, or transcript as the access track
- [A11Y-39](../lexicons/accessibility.md#a11y-39): fit spoken description to non-speech gaps
- [A11Y-40](../lexicons/accessibility.md#a11y-40): name the overflow mode the AD domain already uses
- [A11Y-41](../lexicons/accessibility.md#a11y-41): prefer non-pausing placement before pause
- [A11Y-42](../lexicons/accessibility.md#a11y-42): keep event proximity; no early spoil placement
- [A11Y-43](../lexicons/accessibility.md#a11y-43): spend scarce gap budget on non-audio visuals
- [A11Y-44](../lexicons/accessibility.md#a11y-44): hard-lock critical cues under fit pressure
- [WRIT-03](../lexicons/writing.md#writ-03): name the concrete referent, not a decorative stand-in
- [WRIT-06](../lexicons/writing.md#writ-06): repeat the precise established term
- [WRIT-27](../lexicons/writing.md#writ-27): refuse invented concept labels as fake controlled vocabulary
- [NAME-02](../lexicons/engineering.md#name-02): one project word per concept when a lexicon term exists
- [DOM-03](../lexicons/engineering.md#dom-03): one meaning per term per context
- [COG-02](../lexicons/interaction-ux.md#cog-02): recognition and choosers beat free recall generation
- [BOUND-01](../lexicons/depiction.md#bound-01): keep free description inside what the still can warrant
- [BOUND-05](../lexicons/depiction.md#bound-05): do not treat sentence order as image privilege
- [ARCH-08](../lexicons/engineering.md#arch-08): prefer the boring existing solution while it fits

## Principles

- 18. A machine consumes contracts, not prose

## Evidence / source slugs

- [`algorithm-design-manual`](../SOURCES.md#src-algorithm-design-manual): supports [ALG-06](../lexicons/engineering.md#alg-06)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-01](../lexicons/business-marketing.md#aipx-01)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-04](../lexicons/ml-systems.md#fm-04), [FM-06](../lexicons/ml-systems.md#fm-06)
- [`agent-operations`](../SOURCES.md#src-agent-operations): supports [AGT-11](../lexicons/engineering.md#agt-11)
- [`wcag22-accessibility`](../SOURCES.md#src-wcag22-accessibility): supports [A11Y-02](../lexicons/accessibility.md#a11y-02), [A11Y-09](../lexicons/accessibility.md#a11y-09), [A11Y-12](../lexicons/accessibility.md#a11y-12)
- [`rescribe-audio-descriptions`](../SOURCES.md#src-rescribe-audio-descriptions): supports [A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-41](../lexicons/accessibility.md#a11y-41), [A11Y-42](../lexicons/accessibility.md#a11y-42), [A11Y-43](../lexicons/accessibility.md#a11y-43), [A11Y-44](../lexicons/accessibility.md#a11y-44)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-03](../lexicons/writing.md#writ-03), [WRIT-06](../lexicons/writing.md#writ-06), [WRIT-27](../lexicons/writing.md#writ-27)
- [`programmers-brain`](../SOURCES.md#src-programmers-brain): supports [NAME-02](../lexicons/engineering.md#name-02)
- [`learning-domain-driven-design`](../SOURCES.md#src-learning-domain-driven-design): supports [DOM-03](../lexicons/engineering.md#dom-03)
- [`designing-with-the-mind-in-mind`](../SOURCES.md#src-designing-with-the-mind-in-mind): supports [COG-02](../lexicons/interaction-ux.md#cog-02)
- [`berger-ways-of-seeing`](../SOURCES.md#src-berger-ways-of-seeing): supports [BOUND-01](../lexicons/depiction.md#bound-01)
- [`sontag-on-photography`](../SOURCES.md#src-sontag-on-photography): supports [BOUND-01](../lexicons/depiction.md#bound-01)
- [`barthes-image-music-text`](../SOURCES.md#src-barthes-image-music-text): supports [BOUND-01](../lexicons/depiction.md#bound-01)
- [`azoulay-civil-contract-of-photography`](../SOURCES.md#src-azoulay-civil-contract-of-photography): supports [BOUND-01](../lexicons/depiction.md#bound-01)
- [`barthes-systeme-de-la-mode`](../SOURCES.md#src-barthes-systeme-de-la-mode): supports [BOUND-05](../lexicons/depiction.md#bound-05)
- [`observability-engineering`](../SOURCES.md#src-observability-engineering): supports [ARCH-08](../lexicons/engineering.md#arch-08)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea about accessibility, controlled vocabularies, colour catalogs, archival practice, or algorithm libraries. It does not assert that an unnamed constrained domain "exists somewhere" is a fireable trigger, and it does not promote unregistered bridge standards as evidence. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
