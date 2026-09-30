# Writing & Prose-Style Heuristics Lexicon

## About this document

Decision rules for prose that does not read as machine-generated: diction,
sentence rhythm, paragraph structure, stance, markup, composition, and sourcing.
Where the design lexicon owns visual identity, this one owns verbal identity:
the difference between text a person wrote and text a model emitted. Referenced,
not read end to end: an edit pass or authorship check cites a rule by ID at the
phrase it fires on, and this file holds the claim behind it.

Scope boundary: this lexicon is about how the writing reads, not what it argues.
Claims, evidence, and positioning live in the domain lexicons; every family here
fires on the surface (a phrase, a rhythm, a formatting habit) regardless of
subject. They apply to any prose output: docs, READMEs, essays, commit bodies,
and assistant replies. They do not override a format that legitimately calls for
a flagged pattern (an API reference bolds code identifiers; a pipeline diagram
uses arrows); the rules name those exemptions inline.

Description of images is not here. [`ATTRIB`](depiction.md#fam-attrib) (on whose authority a text names
what is depicted) and [`BOUND`](depiction.md#fam-bound) (how far a description may reach past the frame)
live in [`depiction.md`](depiction.md). They fire on prose whose subject is an
*external referent*, where what the text asserts is exactly what is at stake
and surface hygiene is necessary but not sufficient — a different question from the one
every row below asks. [`WRIT`](writing.md#fam-writ) still applies to a description like any other
prose, and the `image_description_or_alt_text_change` route loads both files.

Source-status warning: the sole registered source,
[`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes), bundles Ben Larbi's
"AI Writing Tropes" (tropes.fyi) with the Wikipedia "Signs of AI writing"
entry. A blog and a Wikipedia synthesis do not meet the corpus authority policy. Treat [`WRIT`](writing.md#fam-writ) rows as
provisional editorial failure checks, not grounded evidence or proof of AI
authorship, until each mechanism is re-grounded in citable research or a
standard. Rows keep the source slug for provenance only; they do not reproduce
that source's section outline. The trigger still supports inspection; the source
does not justify borrowing the row's tier as authority.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. Diction & Word Choice](#fam-writ)
- [2. Sentence Structure](#2-sentence-structure)
- [3. Paragraph & Rhythm](#3-paragraph--rhythm)
- [4. Tone & Stance](#4-tone--stance)
- [5. Formatting & Markup](#5-formatting--markup)
- [6. Composition & Structure](#6-composition--structure)
- [7. Sourcing & Citation](#7-sourcing--citation)
- [8. Detection Posture (meta)](#8-detection-posture-meta)
- [Cross-lexicon links](#cross-lexicon-links)
- [Consumption](#consumption)

<!-- END GENERATED CONTENTS -->

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[WRIT-30]` |
| Trigger | observable on the surface of the text: a phrase, a rhythm, a formatting habit |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the edit is made |
| T·P | tier and phase, below |
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md) |

Tier: **B**locker (reads as AI slop, or is factually hollow or unverifiable),
**S**hould (strong default), **J**udgment (weigh in context). Phase: **d**raft
(avoid while composing), **e**dit (fix on revision), **v**erify (detect AI
authorship or check sourcing).

## 1. Diction & Word Choice<a name="fam-writ"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-01<a name="writ-01"></a> | Repeated vague hedges (for example, “arguably” or “perhaps”) soften an ordinary prose claim without naming its limiting condition or degree | **Cut the adverb or earn it**: replace repeated vague hedges with a needed circumstance, estimate, or degree; cut qualifiers that name no limit, while keeping qualifications required by legal writing, falsifiable hypotheses, and statistical generalizations | Does each hedge name a circumstance, estimate, or degree the claim needs? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-02<a name="writ-02"></a> | A formal or wordy choice such as “utilize” has a familiar equivalent that preserves the intended meaning | **Plain word wins**: choose a familiar, direct expression when it preserves the needed distinction; keep the longer or technical term when it carries precision | Does the direct alternative preserve the needed meaning for this reader? | S·e | [Garner's Modern English Usage, §alphabetical-entries](../SOURCES.md#src-garner-modern-english-usage) |
| WRIT-03<a name="writ-03"></a> | A familiar abstract noun such as “synergy” or “landscape” stands in for a specific real object or relationship a general reader cannot identify, rather than naming a newly coined concept label | **Name the concrete referent**: for a general reader, describe the relevant object or action when an abstract label hides it, because concrete particulars expose what the claim depends on (↔ eng [[ARCH-11]](engineering.md#arch-11) a bare “-ility” is not a checkable risk) | What object, action, or relationship does this abstract label refer to? | S·e | [The Sense of Style, ch. 3](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-04<a name="writ-04"></a> | "serves as / stands as / represents / marks / functions as" replacing "is" or "are" | **Use the plain copula**: the repetition penalty pushes models off "is"; push back | Would "is" be clearer and shorter? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-05<a name="writ-05"></a> | A measured trend or effect is described with stacked vague magnitude words (“significant”, “notable”) although its size or degree can be stated | **One concrete claim**: state the measured size or degree instead of stacking vague magnitude qualifiers; retain a qualifier only when it expresses a distinct, evidenced meaning (↔ [[FORE-01]](epistemics.md#fore-01) vague words hide a scorable magnitude; ↔ biz [[CLM-04]](business-marketing.md#clm-04) adjectives are not evidence) | Can the measured size or degree replace these magnitude labels? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-06<a name="writ-06"></a> | The same technical referent is renamed in successive mentions while other candidate referents are active | **Repeat the precise term**: use a stable precise name when multiple candidates are active; a broader label can work only when it readily recalls the intended referent (↔ eng [[NAME-04]](engineering.md#name-04) consistency beats local quality) | Could a reader confuse which entity this label names? | S·e | [The Sense of Style, ch. 5](../SOURCES.md#src-pinker-sense-of-style) |

<!-- BEGIN GENERATED SECTION SOURCES fam-writ -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)
- [garner-modern-english-usage](../SOURCES.md#src-garner-modern-english-usage)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES fam-writ -->

## 2. Sentence Structure

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-07<a name="writ-07"></a> | negative parallelism: "It's not X — it's Y", "not because X but because Y", "The question isn't X. It's Y." | **Cap manufactured not-X-but-Y pivots**: use at most one per piece; models use the form to fake a surprising reframe, and a stack of them is a pattern failure | How many not-X-but-Y pivots appear in this piece, and is there more than one? | B·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-08<a name="writ-08"></a> | dramatic countdown "Not X. Not Y. Just Z." | **State the point without the countdown**: cut the suspense scaffolding and write Z directly | Am I narrowing to the point, or performing the narrowing? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-09<a name="writ-09"></a> | self-posed rhetorical question answered at once ("The result? Devastating.") | **Make it a statement**: nobody asked the question | Did a reader actually pose this? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-10<a name="writ-10"></a> | anaphora: three-plus sentences opening with the same words in quick succession | **Vary the openings**: repetition-as-rhythm is a model habit, not emphasis | Do consecutive sentences start identically? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-11<a name="writ-11"></a> | tricolon abuse: rule-of-three (or four, five) back to back | **One triad, then vary**: a single tricolon is elegant; three in a row is a pattern failure | Is this the third parallel triad running? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-12<a name="writ-12"></a> | A transition announces importance or a new point but provides no relation to the preceding idea, and the material’s path is already clear | **Cut it**: remove transition language only when it narrates an already clear path; keep a short signpost when readers would otherwise lose the route or need the relation between sections | Does this phrase show a real turn, a relation, or a route the reader needs? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-13<a name="writ-13"></a> | A completed event is followed by a trailing “-ing” clause that claims importance or trends but leaves the actor, action, or concrete change unspecified | **Cut or replace with a specific effect**: state the actor and action, or name the concrete change the trailing clause adds, so the reader can see what happened | Does the trailing clause identify the actor, action, or concrete change? | S·e | [The Sense of Style, ch. 3](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-14<a name="writ-14"></a> | false range "from X to Y" where X and Y are not on any real scale | **List them plainly**: a true range has a meaningful middle | What lies between X and Y? If nothing, it's not a range | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |

<!-- BEGIN GENERATED SECTION SOURCES 2-sentence-structure -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES 2-sentence-structure -->

## 3. Paragraph & Rhythm

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-15<a name="writ-15"></a> | sentence fragments stand alone as one-line paragraphs in quick succession | **Vary paragraph lengths**: Short units are usually easy to absorb, but a run of uniform fragments can become mechanical. | Do these short paragraphs vary enough to preserve the intended pace? | S·e | [garner-legal-writing-plain-english § 26](../SOURCES.md#src-garner-legal-writing-plain-english) |
| WRIT-16<a name="writ-16"></a> | listicle in prose: "The first… The second… The third…" wrapping what is really a list | **Set off distinct points**: Use bullets or another list form when readers need to scan separate items; keep connected reasoning in prose when a list would hide how the points relate. | Do readers need to distinguish separate items, or follow how the prose connects them? | S·e | [garner-legal-writing-plain-english § 43](../SOURCES.md#src-garner-legal-writing-plain-english) |
| WRIT-17<a name="writ-17"></a> | Successive paragraphs rephrase one thesis without adding a point, participant, or relation; near-verbatim copies are a separate trigger ([[WRIT-40]](writing.md#writ-40)). | **Develop the same thread**: Remove rephrased material that adds no topic, point, participant, or relation; each unit should advance a coherent thread. | What topic, point, participant, or relation does this unit advance? | S·e | [The Sense of Style, ch. 5](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-18<a name="writ-18"></a> | dead metaphor: one figure beaten across the whole piece | **Test a recurring image's effect**: If repetition makes an image stale or distracting, replace it with a concrete description or refresh it deliberately; keep it when it helps readers perceive the subject. | Does the recurring image still help readers perceive the subject? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |

<!-- BEGIN GENERATED SECTION SOURCES 3-paragraph--rhythm -->

**Sources for this section**

- [garner-legal-writing-plain-english](../SOURCES.md#src-garner-legal-writing-plain-english)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES 3-paragraph--rhythm -->

## 4. Tone & Stance

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-19<a name="writ-19"></a> | A formulaic suspense cue ("here's the kicker/thing/where it gets interesting/what most people miss") introduces an ordinary claim; negative countdowns are [[WRIT-08]](writing.md#writ-08). | **Cut empty setup**: Omit writer-centered commentary that delays a clear path; keep an opening that creates a useful question or a transition that marks a genuine turn. | Does this opening create a useful question or mark a genuine turn? | S·e | [The Sense of Style, ch. 1](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-20<a name="writ-20"></a> | A "think of it as..." or "it's like..." opener introduces an analogy for an abstract concept in technical or peer-addressed prose. | **Test the analogy's effect**: Keep a comparison when it helps the intended reader see an abstract concept; state the concept or a concrete event instead when the comparison obscures it. | Does this comparison help the intended reader see the concept? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-21<a name="writ-21"></a> | "imagine a world where…" futurism selling a premise | **Argue from evidence, not invitation**: don't sell with a fantasy the reader must accept | Am I inviting agreement instead of earning it? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-22<a name="writ-22"></a> | performative vulnerability ("and yes, I'll admit…", "this isn't a rant, it's a diagnosis") | **Cut risk-free confessions**: real candor is specific and costly; polished self-critique that risks nothing is stance theater | Does this admission actually risk anything? | J·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-23<a name="writ-23"></a> | A factual or historical claim is introduced as "the truth is simple", "history is clear", or "the reality is..." without showing a reason, rather than a hypothetical scenario invitation. | **Show the basis for the claim**: Replace unsupported clarity labels with the concrete particulars and reasoning readers need to assess it (↔ biz [[AIPX-10]](business-marketing.md#aipx-10) no confidence theater). | What particulars or reasoning let readers assess this claim? | S·e | [The Sense of Style, ch. 3](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-24<a name="writ-24"></a> | A small, bounded subject's direct consequences are inflated to world-historical scale; outside praise or coverage claims are [[WRIT-28]](writing.md#writ-28). | **State significance at its supportable scale**: Name the circumstance, estimate, or degree that the evidence establishes instead of stacking vague qualifiers. | Does the stated degree match the evidence and direct consequences? | B·d | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-25<a name="writ-25"></a> | An explicit lesson-opening ("let's break this down", "let's unpack", "let's dive in") addresses an expert audience; analogy openers are [[WRIT-20]](writing.md#writ-20). | **Calibrate the explanation**: Omit steps the intended experts already share, but define a term, supply a missing inference, or describe the referent when they need it. | What does this audience need explained here? | S·e | [The Sense of Style, ch. 3](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-26<a name="writ-26"></a> | vague attribution (experts argue, observers note, industry reports suggest, several publications) | **Name the source or cut the claim**: an unnameable authority is not a source (↔ ml [[PROV-01]](ml-systems.md#prov-01) every output walks back to its evidence; ↔ ux [[HAI-01]](interaction-ux.md#hai-01) evidence before label) | Can I name who said this, specifically? | B·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-27<a name="writ-27"></a> | A newly coined abstract label is presented as established shorthand without an in-text definition or explanation. | **Explain what the coined label means**: Define a new or specialized term for its readers and spell out the mechanism or missing inference it summarizes, so the label does not carry the reasoning by itself. | What mechanism or inference does this label stand for? | S·e | [The Sense of Style, ch. 3](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-28<a name="writ-28"></a> | Identified outside sources are said to show widespread attention or praise, but their scope or scale is unstated; unnamed authorities are [[WRIT-26]](writing.md#writ-26). | **Bound the reception claim**: Give the circumstance, estimate, or degree that supports a claim of broad attention or praise; avoid vague qualifiers when the source's scope is not shown (↔ biz [[CLM-04]](business-marketing.md#clm-04) adjectives are not evidence). | What scope or degree do the cited sources establish? | S·v | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-29<a name="writ-29"></a> | An analytical document's last paragraph lists generic challenges or future work without a specific conclusion or reason; this concerns closing substance, not a conclusion signpost alone. | **Close with the specific conclusion**: In analytical writing, state the decision sought and why; a generic future-work paragraph does not supply that close. | Does this close state the document-specific conclusion and reason? | S·e | [garner-legal-writing-plain-english § 21](../SOURCES.md#src-garner-legal-writing-plain-english) |

<!-- BEGIN GENERATED SECTION SOURCES 4-tone--stance -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)
- [garner-legal-writing-plain-english](../SOURCES.md#src-garner-legal-writing-plain-english)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES 4-tone--stance -->

## 5. Formatting & Markup

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-30<a name="writ-30"></a> | An em-dash insertion makes a sentence's phrase boundaries or syntax open to a misleading parse | **Punctuate for the intended reading**: replace or reposition a mark that creates a garden path because punctuation provides readers with cues to phrase boundaries. | Does the punctuation guide the intended parse? | S·e | [The Sense of Style, ch. 6](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-31<a name="writ-31"></a> | bold-first bullets: every list item opens with a bolded keyword or phrase | **Bold only data-bearing labels**: fake emphasis on every bullet is a documentation tell; a bolded code identifier in an API list is exempt (↔ design [[COL-09]](design-aesthetics.md#col-09) dense accent is noise) | Is this bold navigation, or decoration on every line? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-32<a name="writ-32"></a> | Quotation marks in prose use a form or direction inconsistent with the language or editorial convention | **Follow punctuation conventions**: choose quotation marks for the governing language and house style, because their form and direction vary by convention. | Does this quotation mark follow the language and house style? | S·e | [Detail in Typography (Jost Hochuli), ch. 5](../SOURCES.md#src-hochuli-detail-in-typography) |
| WRIT-33<a name="writ-33"></a> | emoji used as headings, hierarchy, or warmth in technical prose | **Remove it**: checkmark/rocket/lightbulb scaffolding is an assistant-output tell | Is the emoji carrying meaning a word cannot? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-34<a name="writ-34"></a> | inline-header vertical list (Background:/Impact:/Legacy:) repeated line after line | **Use a paragraph or a true list**: the colon-prefixed template reads as a skeleton | Is this a filled-in outline rather than writing? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-35<a name="writ-35"></a> | Heading labels use unnecessary title capitals or the same typographic weight for unlike section levels | **Make heading hierarchy visible**: use informative headings and typographic weight differences to show real section levels; keep ordinary capitalization unless a name or format requires otherwise (↔ eng [[UI-01]](engineering.md#ui-01) one-off values re-litigate the scale; ↔ design [[COL-09]](design-aesthetics.md#col-09) thrift of accent) | Do the heading label and weight reveal the document's actual structure? | J·e | [Legal Writing in Plain English, ch. 4](../SOURCES.md#src-garner-legal-writing-plain-english) + [Asymmetric Typography (Jan Tschichold), ch. 5](../SOURCES.md#src-asymmetric-typography) |
| WRIT-36<a name="writ-36"></a> | table with no data need (vague high/medium/important cells, symmetry-only rows) | **Prose or a list instead**: force information into a table only when the cells carry distinct data | Does every cell hold a real, distinct value? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |

<!-- BEGIN GENERATED SECTION SOURCES 5-formatting--markup -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)
- [asymmetric-typography](../SOURCES.md#src-asymmetric-typography)
- [garner-legal-writing-plain-english](../SOURCES.md#src-garner-legal-writing-plain-english)
- [hochuli-detail-in-typography](../SOURCES.md#src-hochuli-detail-in-typography)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES 5-formatting--markup -->

## 6. Composition & Structure

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-37<a name="writ-37"></a> | A draft repeats section previews or recaps at multiple levels even though its written order already gives the reader a clear route | **Orient through the subject**: remove writer-centered previews and recaps when the written order already gives readers a clear route; keep concise signposts when they clarify a genuine change, because guidance should help readers follow the subject. | Would removing this announcement make the reader lose the route? | S·e | [The Sense of Style, ch. 2](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-38<a name="writ-38"></a> | An analytical or persuasive legal document ends with a stock closing phrase that adds no conclusion or requested action | **Let the ending land**: sum up the argument and say what decision maker should do and why; replace a formula that says nothing with the conclusion itself. | Does the close state the result and why? | S·e | [Legal Writing in Plain English, ch. 2](../SOURCES.md#src-garner-legal-writing-plain-english) |
| WRIT-39<a name="writ-39"></a> | Historical comparisons among companies or technology eras appear in succession without stating how they advance the central theme | **Make the connection explicit**: keep a historical comparison only when it advances the central theme and show how it connects; an unexplained name-drop list weakens coherence (↔ biz [[STRAT-05]](business-marketing.md#strat-05) status-mediated desire is not independent evidence) | Can a reader tell how each comparison advances the point? | S·e | [The Sense of Style, ch. 5](../SOURCES.md#src-pinker-sense-of-style) |
| WRIT-40<a name="writ-40"></a> | A paragraph or section appears twice near-verbatim in the same piece without adding a distinct point or consequence | **Deduplicate**: remove a repeated passage when it adds no distinct meaning, because extra wording can be cut without changing the point. | Does the repeated passage add a distinct point? | B·v | [Legal Writing in Plain English, ch. 1](../SOURCES.md#src-garner-legal-writing-plain-english) |

<!-- BEGIN GENERATED SECTION SOURCES 6-composition--structure -->

**Sources for this section**

- [garner-legal-writing-plain-english](../SOURCES.md#src-garner-legal-writing-plain-english)
- [pinker-sense-of-style](../SOURCES.md#src-pinker-sense-of-style)

<!-- END GENERATED SECTION SOURCES 6-composition--structure -->

## 7. Sourcing & Citation

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-41<a name="writ-41"></a> | hollow or fabricated citations (invalid DOI/ISBN, refs that resolve to nothing, missing page numbers, tracking junk in URLs) | **Every citation resolves and is checkable**: a reference that looks complete but can't be verified is worse than none (↔ ml [[RAG-07]](ml-systems.md#rag-07) a citation must materially support its claim; ↔ ml [[PROV-01]](ml-systems.md#prov-01) every output walks back to its evidence) | Can a reader actually follow this to the source? | B·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-42<a name="writ-42"></a> | assistant-output leakage in finished prose (knowledge-cutoff disclaimers, `[insert source here]`, "this section can be expanded", tool tokens, "as of my last update", forced collaborative voice "we can now explore…") | **Strip all scaffolding**: template and tool residue is unmistakable machine debris | Is there any placeholder or disclaimer left in? | B·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |

<!-- BEGIN GENERATED SECTION SOURCES 7-sourcing--citation -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)

<!-- END GENERATED SECTION SOURCES 7-sourcing--citation -->

## 8. Detection Posture (meta)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-43<a name="writ-43"></a> | judging AI authorship from one stylistic tell, or from a detector score | **Cluster over single cue; scrutiny not certainty**: any one pattern can be human; detectors are weak evidence; a dense cluster is the real signal (↔ ml [[CAL-02]](ml-systems.md#cal-02) unknown is a valid result; ↔ [[FORE-04]](epistemics.md#fore-04) one outcome does not grade a probability; ↔ [[NDM-05]](epistemics.md#ndm-05) do not explain away the set one cue at a time) | Is this one phrase, or a pile of tells together? | J·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-44<a name="writ-44"></a> | editing pass that swaps the flagged phrase but leaves the underlying problem | **Fix the cause, not the phrase**: vague→source or cut; inflated→narrow the claim; decorative→simplify; synonym churn→one precise term; template residue→rewrite (↔ eng [[DBG-10]](engineering.md#dbg-10) fix the cause, not the symptom; ↔ ux [[HAI-02]](interaction-ux.md#hai-02) correction must reach the source) | Did I fix the sentence, or just launder the tell? | S·e | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-45<a name="writ-45"></a> | an authorship check treats every stylistic tell as affirmative and ignores signs that point away | **Weigh counter-evidence against authorship claims**: pre-ChatGPT text, or text whose author can explain specific editorial choices, weighs against AI authorship (↔ [[WRIT-43]](writing.md#writ-43) a cluster is still scrutiny, not proof) | Is there pre-ChatGPT provenance, or can the author defend specific editorial choices? | J·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |
| WRIT-46<a name="writ-46"></a> | detection or edit pass relies on historical tells (old refusal styles, abrupt cutoffs) that decay with model drift | **Prefer durable structural signals**: weight genericity, inflation, template structure, and citation sloppiness; historical phrase-level tells age out as models change (↔ [[WRIT-43]](writing.md#writ-43) cluster of durable classes, not one obsolete tell) | Am I scoring durable structure, or a tell that already aged out? | S·v | [AI Writing Tropes](../SOURCES.md#src-ai-writing-tropes) |

<!-- BEGIN GENERATED SECTION SOURCES 8-detection-posture-meta -->

**Sources for this section**

- [ai-writing-tropes](../SOURCES.md#src-ai-writing-tropes)

<!-- END GENERATED SECTION SOURCES 8-detection-posture-meta -->

## Cross-lexicon links

- `↔ eng NAME-04` (consistency beats local quality): [[WRIT-06]](writing.md#writ-06) and [[WRIT-35]](writing.md#writ-35) serve the same end: match the established convention over personal style.
- `↔ eng UI-01` / design `TYPE-05`: the token-scale discipline that [[WRIT-35]](writing.md#writ-35) applies to prose markup.
- `↔ business GTM-07` (title = emotional first line): a naming rule that legitimately *wants* memorable phrasing: [[WRIT-27]](writing.md#writ-27)'s ban on coined labels is about undefended shorthand, not deliberate, earned names.
- `↔ depiction ATTRIB-02` / `BOUND-01`: [[WRIT-26]](writing.md#writ-26) refuses the unnameable authority in any prose; the depiction rows refuse it for identity claims in captions and archival description, and add the limit of the frame that no prose rule can supply.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[WRIT-07]`) in style guides, review checklists, and agent output instructions. The rules are editing and detection heuristics, not infallible laws: apply [[WRIT-43]](writing.md#writ-43) before calling anything AI-authored, and prefer fixing the cause ([[WRIT-44]](writing.md#writ-44)) over swapping the phrase.
