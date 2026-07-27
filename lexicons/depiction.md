# Depiction & Description Heuristics Lexicon

## About this document

Decision rules for text whose subject is an *external referent*: alt text, a
caption, a figure gloss, a catalogue record, a generated image description.
What that text may assert about who or what is depicted, on whose authority,
and where it must stop. Referenced, not read end to end: a describing pass
cites a rule by ID at the sentence it fires on, and this file holds the claim
behind it.

Scope boundary: the writing lexicon owns how prose *reads* and fires on the
surface — diction, rhythm, markup, the tells of machine authorship — whatever
the subject. This lexicon owns what prose *asserts about something outside
itself*, so surface hygiene is necessary and not sufficient: a sentence can be
plain, unpadded, and correctly cited and still hand a viewer's inference to the
depicted person as fact. `ATTRIB` owns the warrant for an identity claim,
`BOUND` how far a description may reach past the frame; the borders with
`A11Y`, `CLM`, `PROV`, and `WRIT` are named at each family below. Human-written
and model-generated description are held to the same rows.

These two families sat in `lexicons/writing.md` until 2026-07-26, on the
argument that a describer already reading `WRIT` would not think to open a
second file. The route table had already answered that:
`image_description_or_alt_text_change` names `ATTRIB`, `BOUND`, `A11Y`, `WRIT`,
`CLM`, and `PROV`, so a describing pass was crossing four lexicons in any case.
Routes open files; proximity inside one file does not. What proximity did cost
was 46 rows of prose hygiene loaded to reach sixteen rows of description
discipline. The IDs did not move with the file — a rule's identity is its
family-qualified key, not the file that holds it — and the relocation is
recorded in `rule-ledger.json`.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. ATTRIB: Attribution & identity claims in description](#fam-attrib)
- [2. BOUND: Descriptive boundaries & the limits of the frame](#fam-bound)
- [Cross-lexicon links](#cross-lexicon-links)
- [Consumption](#consumption)

<!-- END GENERATED CONTENTS -->

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[ATTRIB-01]` |
| Trigger | observable in the description: a clause, a voice, a grammatical subject |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the description ships |
| T·P | tier and phase, below |
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md) |

Tier: **B**locker (asserts as depicted fact something the image cannot carry,
or speaks an oppressive record in the describing institution's own voice),
**S**hould (strong default), **J**udgment (weigh in context). Phase: **d**raft
(while composing the description), **e**dit (fix on revision), **v**erify
(check the description against what the image and the record actually carry).

## 1. ATTRIB: Attribution & identity claims in description<a name="fam-attrib"></a>

What a description may assert about *who or what is depicted*, and on whose
authority. Fires when prose names a person, place, event, or intent that the image
alone does not establish. ATTRIB owns the warrant for the claim; BOUND owns how far
a description may reach; accessibility `A11Y` owns whether the description serves
the reader's purpose; business-marketing `CLM` owns the unearned adjective wherever
it appears.

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| ATTRIB-01<a name="attrib-01"></a> | Depicted person is grammatical subject of a non-visual trait, will, or essence claim with no attributive frame | **Bearer, not the depicted**: face, pose, prop, or nude arrangement invites interior or will inference -> state visible cues only, or attribute the reading to viewer, convention, artefact, or named source; never the person as fact-owner -> blocks false psychology and objectification laundered as their attitude ↔ ux [[HAI-01]](interaction-ux.md#hai-01) ↔ biz [[CLM-04]](business-marketing.md#clm-04) | Is the person grammatical owner of a trait or will no pixel can confirm? | B·d | [berger-ways-of-seeing](../SOURCES.md#src-berger-ways-of-seeing) + [sontag-on-photography](../SOURCES.md#src-sontag-on-photography) + [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others) + [barthes-image-music-text](../SOURCES.md#src-barthes-image-music-text) + [berger-understanding-a-photograph](../SOURCES.md#src-berger-understanding-a-photograph) + [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| ATTRIB-02<a name="attrib-02"></a> | Description assigns faction, demonym, perpetrator or victim role, social identity, or guilt label to depicted people with no cited catalogue or source frame | **Captions explain or falsify identity**: uncited who, by-whom, identity, or guilt in FORENSIC voice -> put the claim in EDITORIAL or cited-source voice, or drop it -> readers treat a swapped side-label or verdict as what the frame shows ↔ [[WRIT-26]](writing.md#writ-26) ↔ ml [[PROV-01]](ml-systems.md#prov-01) ↔ ux [[HAI-01]](interaction-ux.md#hai-01) | Is every who, by-whom, identity, or guilt claim tagged to a record or marked non-forensic? | B·v | [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others) |
| ATTRIB-03<a name="attrib-03"></a> | Caption or alt states non-visible narrative, symbolic reading, or private singular affect in the same unmarked voice as visible objects, or presents the text as the image's secured full meaning | **Words re-author the image**: non-visible content co-voiced with inventory -> put it in EDITORIAL or INTERPRETIVE with an explicit bearer; keep FORENSIC to in-frame visibles; never write the text as exhaustive or permanently secured meaning -> stops the caption story from reading as pixel evidence for non-seeing users ↔ [[WRIT-26]](writing.md#writ-26) ↔ ml [[PROV-01]](ml-systems.md#prov-01) | Can a second viewer verify this sentence from the image alone, or is it written as the image's secured full meaning? | S·d | [berger-ways-of-seeing](../SOURCES.md#src-berger-ways-of-seeing) + [sontag-on-photography](../SOURCES.md#src-sontag-on-photography) + [berger-understanding-a-photograph](../SOURCES.md#src-berger-understanding-a-photograph) + [barthes-image-music-text](../SOURCES.md#src-barthes-image-music-text) + [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| ATTRIB-04<a name="attrib-04"></a> | Harm, vulnerability, violence, grief, or atrocity content co-occurs with unmarked compositional praise or intentional horror rhetoric stated as in-frame fact | **Distress undercoding, not beautify**: distress present in access text -> emit stubborn literal visible inventory; do not aestheticize form in the same voice as the harm inventory; tag affect, guilt, pity, or forced moral plot as viewer, institution, or source -> else agony is offered as visual pleasure or pathos is smuggled as emulsion fact ↔ biz [[CLM-04]](business-marketing.md#clm-04) | After stripping beauty words, affect epithets, and intentional parallels, what visible facts remain, and who owns the judgment? | S·e | [sontag-on-photography](../SOURCES.md#src-sontag-on-photography) |
| ATTRIB-05<a name="attrib-05"></a> | Source already decides a name, a withhold, or illustrative-versus-singular status, and the text rewrites that decision | **Honor source identity decisions**: record name or singularity status present -> emit the name and preserve illustrative versus singular status; never mint a plight-type to replace a missing name, invent a name when withheld, or write an interchangeable illustration line -> blocks logo-person prose and stock-horror captions ↔ [[WRIT-03]](writing.md#writ-03) | Did we strip, invent, type-cast, or rewrite a name, withhold, or singularity decision the source already made (primary-entry reordering of an enslaver-filed name is [[ATTRIB-09]](depiction.md#attrib-09), not this)? | S·v | [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others) + [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| ATTRIB-06<a name="attrib-06"></a> | Race is included or proposed in a description of people | **Race only with warrant and parity**: race as a descriptor -> only when relevant to meaning or intent and time allows; use currently-accepted terms rather than race assumed from appearance; when race is used, apply it to BIPOC and white individuals in that pass, or drop it from all of them -> one-sided race labeling marks only the non-default group, and each label can be separately warranted while the pass is still asymmetric ↔ [[ATTRIB-02]](depiction.md#attrib-02) ↔ [[ATTRIB-05]](depiction.md#attrib-05) | Is every race label warranted, non-assumed, and applied with white/BIPOC parity when race is in play? | S·v | [dcmp-description-key](../SOURCES.md#src-dcmp-description-key) |
| ATTRIB-07<a name="attrib-07"></a> | Racist or otherwise oppressive wording that came from the material's creator is carried into published description, where nothing distinguishes it from the describing institution's own words | **Quote the creator, never speak as them**: creator-supplied language preserved because the racism is context a reader needs -> mark it as the creator's by quotation, scope note, or processing note, and never let those terms appear unmarked in describer-supplied fields -> unmarked retention converts a historical artefact into the institution's present speech, and deleting it instead erases the evidence of how the record was made ↔ [[ATTRIB-02]](depiction.md#attrib-02) ↔ [[ATTRIB-03]](depiction.md#attrib-03) | Is every oppressive creator string voice-tagged, and is describer-supplied text free of unmarked reuse? | B·d | [anti-racist-description-resources](../SOURCES.md#src-anti-racist-description-resources) |
| ATTRIB-08<a name="attrib-08"></a> | Prose about violence, oppression, or enslavement uses an agentless passive or a mutual-event noun ("a clash", "were killed") | **Active voice keeps the agent**: an oppressive act described in agentless form -> when the actor is known or record-supported, make that actor the grammatical subject rather than dissolving them into a passive or a symmetry noun; when the record does not support naming who acted, state the gap rather than invent an agent -> agentless grammar relocates responsibility out of the sentence while every individual word stays defensible ↔ [[ATTRIB-02]](depiction.md#attrib-02) ↔ [[BOUND-03]](depiction.md#bound-03) | Does the sentence name who acted, mark the gap, or hide a record-supported agent in a passive or a "clash" frame? | S·d | [anti-racist-description-resources](../SOURCES.md#src-anti-racist-description-resources) |
| ATTRIB-09<a name="attrib-09"></a> | A person held in bondage is described or indexed under the name of the person who enslaved them, because that is how the record was filed | **Enslaved person's name is the entry**: a name by which an enslaved or formerly enslaved person identified is recoverable -> make it the primary entry, even when only a first name survives, and keep enslaver names as supplemental identifying data -> filing a person under their enslaver reproduces the record-keeping economy that treated them as property, and keyword search already reaches enslaver names held elsewhere in the description ↔ [[ATTRIB-05]](depiction.md#attrib-05) | Is the retrieval key this person's own name, or their enslaver's? | S·d | [anti-racist-description-resources](../SOURCES.md#src-anti-racist-description-resources) |
| ATTRIB-10<a name="attrib-10"></a> | Materials documenting oppressed or marginalized people carry rich description of who made the records and thin naming of who appears in them, though the names are recoverable from the records | **Name subjects to creator depth**: subject names present in the material -> describe subjects at least to the extent creators are described, subject to living-person and surveillance risk -> provenance-shaped effort makes the documented findable and the documented-about unfindable, so the imbalance is a retrieval decision rather than a records limitation ↔ [[ATTRIB-05]](depiction.md#attrib-05) ↔ [[ATTRIB-06]](depiction.md#attrib-06) | Are subjects named as findably as creators where the records support it? | S·e | [anti-racist-description-resources](../SOURCES.md#src-anti-racist-description-resources) |

<!-- BEGIN GENERATED SECTION SOURCES fam-attrib -->

**Sources for this section**

- [anti-racist-description-resources](../SOURCES.md#src-anti-racist-description-resources)
- [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography)
- [barthes-image-music-text](../SOURCES.md#src-barthes-image-music-text)
- [berger-understanding-a-photograph](../SOURCES.md#src-berger-understanding-a-photograph)
- [berger-ways-of-seeing](../SOURCES.md#src-berger-ways-of-seeing)
- [dcmp-description-key](../SOURCES.md#src-dcmp-description-key)
- [sontag-on-photography](../SOURCES.md#src-sontag-on-photography)
- [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others)

<!-- END GENERATED SECTION SOURCES fam-attrib -->

## 2. BOUND: Descriptive boundaries & the limits of the frame<a name="fam-bound"></a>

Where a description must stop: what the frame excludes, what the caption supplies
that the emulsion does not, and which of a viewer's inferences the prose may not
present as depicted fact. Fires when a description reports context, causation,
emphasis, or emotional content that the photograph cannot carry. BOUND owns the
boundary; ATTRIB owns the identity claim inside it.

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| BOUND-01<a name="bound-01"></a> | Output asserts narrative, functional, totalizing, off-frame, or whole-work claims with only the still as warrant | **Assertable set is bounded**: when the only evidence is a still -> keep surface, spatial relations, and past presence; source or drop cause, sequence, fate, duration-as-felt, completeness, and institutional thesis; mark known crop or detail -> else the system invents understanding the image cannot supply ↔ ml [[PROV-01]](ml-systems.md#prov-01) ↔ [[WRIT-26]](writing.md#writ-26) | What is inside this selection, and which clause would need a non-image source to be checkable? | S·d | [berger-ways-of-seeing](../SOURCES.md#src-berger-ways-of-seeing) + [sontag-on-photography](../SOURCES.md#src-sontag-on-photography) + [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others) + [barthes-image-music-text](../SOURCES.md#src-barthes-image-music-text) + [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| BOUND-02<a name="bound-02"></a> | Output mixes in-frame inventory with craft, candidness, motive, staging, credit, agency, or other production claims in one unmarked voice | **Narrowly selective transparency**: still written as unmediated show-through -> split FORENSIC surface from labelled craft or EDITORIAL construction; when production cues exist, speak depiction-as-made apart from depicted biography -> else selection is consumed as proof ↔ epi [[BIAS-03]](epistemics.md#bias-03) | Does any shows, documents, or captures clause smuggle take, pose, motive, or making without a craft frame? | S·e | [sontag-on-photography](../SOURCES.md#src-sontag-on-photography) + [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others) + [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| BOUND-03<a name="bound-03"></a> | Event caption or official purpose, threat-prevented, or routine-procedure language is present while high-salience control, body, or force cues are omitted | **Frame before institutional story**: accompanying event or purpose text given -> inventory visible relations of force first; put event, purpose, or justification in attributed EDITORIAL voice second -> blocks caption and purpose indifference to the photo ↔ epi [[BIAS-02]](epistemics.md#bias-02) | Does the text report what the picture shows before what the institution says it means? | S·d | [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| BOUND-04<a name="bound-04"></a> | Degrading undress or forced pose; text either restages the invasive gaze or suppresses all injury address | **Refuse restage, refuse erasure**: photograph shows humiliating forced undress or pose -> address the injury without unmediated restaging of the degrading gaze; refuse spectacle that reenacts and refuse total suppression that leaves injury unaddressed -> neither magnifies the ritual of humiliation nor abandons the field to pornographic fantasy | Does this description reenact the ritual of humiliation for the spectator, or erase the injury entirely? | J·d | [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography) |
| BOUND-05<a name="bound-05"></a> | Caption, alt, or description uses rank or itinerary language such as emphasizes, focus, main, or ordered walkthrough about image content | ***Emphase* is not image privilege**: if rank or order comes from the sentence, not from a visible crop, contrast, scale, or other pictorial cue -> state named traits as editorial selection or plain inventory; never report that hierarchy as a property of the photograph -> non-seeing users get a false map of what the image privileges ↔ a11y [[A11Y-02]](accessibility.md#a11y-02) | Is every emphasis word licensed by a pictorial cue, or only by word order? | S·d | [barthes-systeme-de-la-mode](../SOURCES.md#src-barthes-systeme-de-la-mode) |

<!-- BEGIN GENERATED SECTION SOURCES fam-bound -->

**Sources for this section**

- [azoulay-civil-contract-of-photography](../SOURCES.md#src-azoulay-civil-contract-of-photography)
- [barthes-image-music-text](../SOURCES.md#src-barthes-image-music-text)
- [barthes-systeme-de-la-mode](../SOURCES.md#src-barthes-systeme-de-la-mode)
- [berger-ways-of-seeing](../SOURCES.md#src-berger-ways-of-seeing)
- [sontag-on-photography](../SOURCES.md#src-sontag-on-photography)
- [sontag-regarding-the-pain-of-others](../SOURCES.md#src-sontag-regarding-the-pain-of-others)

<!-- END GENERATED SECTION SOURCES fam-bound -->

## Cross-lexicon links

- `↔ a11y A11Y-02` (alt serves purpose): the nearest neighbour to this whole lexicon and the one most easily mistaken for it. A11Y-02 asks what a non-seeing reader must *get* from the image; [[ATTRIB-01]](depiction.md#attrib-01) asks on whose authority the text names what is depicted, and [[BOUND-01]](depiction.md#bound-01) where the description must stop. A description can serve the reader's purpose perfectly and still overclaim — both checks run, and neither substitutes for the other.
- `↔ writing WRIT-26` (name the source or cut the claim): the same demand for a nameable authority, one level down. WRIT-26 fires on any prose that leans on "experts"; [[ATTRIB-02]](depiction.md#attrib-02) fires when the unnameable authority is what assigns a depicted person their side, their role, or their guilt.
- `↔ ml PROV-01` (every output walks back to its evidence): PROV-01 is the system obligation, stated for any generated output. [[BOUND-01]](depiction.md#bound-01) names which clauses in a description can never discharge it from the image alone, whoever wrote them.
- `↔ biz CLM-04` (adjectives are not evidence): CLM-04 owns the unearned adjective on any claim surface. [[ATTRIB-04]](depiction.md#attrib-04) is the case where that adjective is compositional praise laid over depicted harm, which is why it is a separate row and not an instance.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[BOUND-01]`) in description guidelines, alt-text review checklists, and the output instructions of any system that generates image descriptions. The rules bound what a description may assert; they do not decide whether an image should be described at all, or at what length. That is `A11Y`'s question and it runs first — a description that overclaims about an image nobody needed described has two problems, and this file only sees one of them.
