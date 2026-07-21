# Writing & Prose-Style Heuristics Lexicon

## About this document

Decision rules for prose that does not read as machine-generated: diction,
sentence rhythm, paragraph structure, stance, markup, composition, and sourcing.
Where the design lexicon owns visual identity, this one owns verbal identity:
the difference between text a person wrote and text a model emitted. Referenced,
not read end to end: an edit pass or authorship check cites a rule by ID at the
phrase it fires on, and this file holds the claim behind it.

Scope boundary: this lexicon is about how the writing reads, not what it argues.
Claims, evidence, and positioning live in the domain lexicons; this one fires on
the surface (a phrase, a rhythm, a formatting habit) regardless of subject. It
applies to any prose output: docs, READMEs, essays, commit bodies, and assistant
replies. It does not override a format that legitimately calls for a flagged
pattern (an API reference bolds code identifiers; a pipeline diagram uses
arrows); the rules name those exemptions inline.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. Diction & Word Choice](#1-diction--word-choice)
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
| Src | source slug, resolved in the Sources section at the end of this file; the distillation behind it stays in the private research corpus |

Tier: **B**locker (reads as AI slop, or is factually hollow or unverifiable),
**S**hould (strong default), **J**udgment (weigh in context). Phase: **d**raft
(avoid while composing), **e**dit (fix on revision), **v**erify (detect AI
authorship or check sourcing).

## 1. Diction & Word Choice

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-01<a name="writ-01"></a> | magic adverbs (quietly, deeply, fundamentally, remarkably, arguably) pad significance onto a plain statement | **Cut the adverb or earn it** — if deleting it loses no meaning, it was inflation | Does the sentence lose anything when the adverb goes? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |
| WRIT-02<a name="writ-02"></a> | AI-vocabulary tell (delve, utilize, leverage-as-verb, robust, streamline, harness, seamless, certainly) | **Plain word wins** — use the word a person would say out loud | Would a human say "use" here, not "utilize"? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |
| WRIT-03<a name="writ-03"></a> | ornate abstract noun (tapestry, landscape, paradigm, synergy, ecosystem) standing in for anything interconnected | **Name the concrete referent** — grand nouns hide the absence of a specific one (↔ eng [[ARCH-11]](engineering.md#arch-11) a bare "-ility" is not a checkable risk) | Is this the actual thing or a decorative stand-in? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |
| WRIT-04<a name="writ-04"></a> | "serves as / stands as / represents / marks / functions as" replacing "is" or "are" | **Use the plain copula** — the repetition penalty pushes models off "is"; push back | Would "is" be clearer and shorter? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |
| WRIT-05<a name="writ-05"></a> | intensifier cluster (significant, crucial, pivotal, dynamic, evolving, broader, notable) stacked in one passage | **One claim, sourced** — five abstract intensifiers replace one concrete fact (↔ [[FORE-01]](epistemics.md#fore-01) vague words hide a scorable magnitude; ↔ biz [[CLM-04]](business-marketing.md#clm-04) adjectives are not evidence) | How many empty intensifiers are in this paragraph? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |
| WRIT-06<a name="writ-06"></a> | elegant variation: the same subject renamed each mention to avoid repetition | **Repeat the precise term** — synonym-swapping blurs a technical referent (↔ eng [[NAME-04]](engineering.md#name-04) consistency beats local quality) | Did the noun change while the thing didn't? | S·e | [ai-writing-tropes §diction](#src-ai-writing-tropes) |

## 2. Sentence Structure

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-07<a name="writ-07"></a> | negative parallelism: "It's not X — it's Y", "not because X but because Y", "The question isn't X. It's Y." | **The signature tell — at most one per piece** — models use it to fake a surprising reframe; before LLMs nobody wrote this at scale | Is this a real contrast or a manufactured pivot? | B·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-08<a name="writ-08"></a> | dramatic countdown "Not X. Not Y. Just Z." | **State Z** — cut the suspense scaffolding | Am I narrowing to the point, or performing the narrowing? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-09<a name="writ-09"></a> | self-posed rhetorical question answered at once ("The result? Devastating.") | **Make it a statement** — nobody asked the question | Did a reader actually pose this? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-10<a name="writ-10"></a> | anaphora: three-plus sentences opening with the same words in quick succession | **Vary the openings** — repetition-as-rhythm is a model habit, not emphasis | Do consecutive sentences start identically? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-11<a name="writ-11"></a> | tricolon abuse: rule-of-three (or four, five) back to back | **One triad, then vary** — a single tricolon is elegant; three in a row is a pattern failure | Is this the third parallel triad running? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-12<a name="writ-12"></a> | filler transition (it's worth noting, importantly, notably, interestingly, it bears mentioning) | **Cut it** — these signal a new point without connecting it to the argument | Does the phrase carry any information? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-13<a name="writ-13"></a> | trailing "-ing" pseudo-analysis (highlighting its importance, reflecting broader trends, underscoring its role) | **Cut or replace with a specific effect** — the participle attaches fake significance to a plain fact | Is the "-ing" clause falsifiable, or ceremonial? | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |
| WRIT-14<a name="writ-14"></a> | false range "from X to Y" where X and Y are not on any real scale | **List them plainly** — a true range has a meaningful middle | What lies between X and Y? If nothing, it's not a range | S·e | [ai-writing-tropes §sentence-structure](#src-ai-writing-tropes) |

## 3. Paragraph & Rhythm

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-15<a name="writ-15"></a> | short punchy fragments as standalone paragraphs for manufactured emphasis | **Restore real sentences** — one-thought-per-line is an inhuman RLHF-readability style | Is this fragment earning the drama, or faking it? | S·e | [ai-writing-tropes §paragraph](#src-ai-writing-tropes) |
| WRIT-16<a name="writ-16"></a> | listicle in prose: "The first… The second… The third…" wrapping what is really a list | **Use a real list or real prose** — don't disguise a listicle as paragraphs | Is this a numbered list in a trench coat? | S·e | [ai-writing-tropes §paragraph](#src-ai-writing-tropes) |
| WRIT-17<a name="writ-17"></a> | one-point dilution: a single thesis restated many ways to feel comprehensive | **Cut to the one argument** — 800 words padded to 4000 adds nothing | Does this paragraph add a new point, or re-skin the last? | S·e | [ai-writing-tropes §paragraph](#src-ai-writing-tropes) |
| WRIT-18<a name="writ-18"></a> | dead metaphor: one figure beaten across the whole piece | **Introduce, use once, move on** — a human drops a metaphor; a model repeats it 5–10× | How many times has this same image recurred? | S·e | [ai-writing-tropes §paragraph](#src-ai-writing-tropes) |

## 4. Tone & Stance

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-19<a name="writ-19"></a> | false-suspense transition (here's the kicker/thing/deal, here's where it gets interesting, here's what most people miss) | **Deliver the point** — the payoff never justifies the buildup | Does what follows need the drumroll? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-20<a name="writ-20"></a> | patronizing analogy (think of it as…, it's like a…) aimed at a capable reader | **State the concept directly** — the analogy is often less clear than the thing | Does the reader need a metaphor here, or the fact? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-21<a name="writ-21"></a> | "imagine a world where…" futurism selling a premise | **Argue from evidence, not invitation** — don't sell with a fantasy the reader must accept | Am I inviting agreement instead of earning it? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-22<a name="writ-22"></a> | performative vulnerability ("and yes, I'll admit…", "this isn't a rant, it's a diagnosis") | **Cut the risk-free confession** — real candor is specific and costly; model candor is polished and risk-free | Does this admission actually risk anything? | J·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-23<a name="writ-23"></a> | asserting clarity instead of proving it (the truth is simple, history is clear, the reality is…) | **Show the evidence** — if you must announce your point is obvious, it isn't (↔ biz [[AIPX-10]](business-marketing.md#aipx-10) no confidence theater) | Am I claiming clarity I have not demonstrated? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-24<a name="writ-24"></a> | grandiose stakes inflation: a small topic framed as world-historical | **Match stakes to subject** — an API-pricing post is not the fate of civilization | Does the significance language fit what this actually is? | B·d | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-25<a name="writ-25"></a> | pedagogical voice (let's break this down, let's unpack, let's dive in) to an expert audience | **Drop the teacher framing** — write to a peer, not a student | Does this reader need hand-holding? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-26<a name="writ-26"></a> | vague attribution (experts argue, observers note, industry reports suggest, several publications) | **Name the source or cut the claim** — an unnameable authority is not a source (↔ ml [[PROV-01]](ml-systems.md#prov-01) every output walks back to its evidence; ↔ ux [[HAI-01]](interaction-ux.md#hai-01) evidence before label) | Can I name who said this, specifically? | B·v | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-27<a name="writ-27"></a> | invented concept labels (the supervision paradox, the acceleration trap, workload creep) used as established terms | **Make the argument, don't name it** — coined labels skip the reasoning they imply | Is this a defined term or rhetorical shorthand? | S·e | [ai-writing-tropes §tone](#src-ai-writing-tropes) |
| WRIT-28<a name="writ-28"></a> | significance / media-coverage puffery (drew wide attention, a pivotal moment, widely praised) | **Concrete effect + named source, or omit** — routine facts framed as legacy is a padding tell (↔ biz [[CLM-04]](business-marketing.md#clm-04) adjectives are not evidence) | Who, specifically, and with what measurable effect? | S·v | [ai-writing-tropes §sourcing](#src-ai-writing-tropes) |
| WRIT-29<a name="writ-29"></a> | "despite its challenges…" acknowledge-then-dismiss template close | **One real constraint, one real next step — or cut** — the generic challenges/future paragraph fits any topic | Is this a real caveat or a template wrap-up? | S·e | [ai-writing-tropes §composition](#src-ai-writing-tropes) |

## 5. Formatting & Markup

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-30<a name="writ-30"></a> | em-dash addiction: 20+ where a human uses two or three | **Vary the punctuation** — commas, periods, and parentheses carry most of the load | Am I past a small handful of em dashes? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-31<a name="writ-31"></a> | bold-first bullets: every list item opens with a bolded keyword or phrase | **Bold only data-bearing labels** — fake emphasis on every bullet is a documentation tell; a bolded code identifier in an API list is exempt (↔ design [[COL-09]](design-aesthetics.md#col-09) dense accent is noise) | Is this bold navigation, or decoration on every line? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-32<a name="writ-32"></a> | unicode decoration (→, ⇒, smart quotes, middots) in plain or code-adjacent text | **Type ASCII** — use `->` and straight quotes a keyboard produces; a rendered diagram is exempt | Could I type this character without a menu? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-33<a name="writ-33"></a> | emoji used as headings, hierarchy, or warmth in technical prose | **Remove it** — checkmark/rocket/lightbulb scaffolding is an assistant-output tell | Is the emoji carrying meaning a word cannot? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-34<a name="writ-34"></a> | inline-header vertical list (Background:/Impact:/Legacy:) repeated line after line | **Use a paragraph or a true list** — the colon-prefixed template reads as a skeleton | Is this a filled-in outline rather than writing? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-35<a name="writ-35"></a> | excess boldface, title-case drift, decorative rules before every heading, skipped heading levels | **Emphasis and structure only where earned** — mechanical symmetry signals a template, not an author (↔ eng [[UI-01]](engineering.md#ui-01) one-off values re-litigate the scale; ↔ design [[COL-09]](design-aesthetics.md#col-09) thrift of accent) | Is this markup doing rhetorical work, or filling a mold? | J·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |
| WRIT-36<a name="writ-36"></a> | table with no data need (vague high/medium/important cells, symmetry-only rows) | **Prose or a list instead** — force information into a table only when the cells carry distinct data | Does every cell hold a real, distinct value? | S·e | [ai-writing-tropes §formatting](#src-ai-writing-tropes) |

## 6. Composition & Structure

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-37<a name="writ-37"></a> | fractal summaries: every section previews itself and recaps itself | **Summarize once, at most** — "what I'll tell you / what I told you" at every level is a template | Am I re-announcing what the reader just read? | S·e | [ai-writing-tropes §composition](#src-ai-writing-tropes) |
| WRIT-38<a name="writ-38"></a> | signposted conclusion (in conclusion, to sum up, in summary) | **Let the ending land** — competent writing does not announce that it is ending | Does the reader need the label to feel the close? | S·e | [ai-writing-tropes §composition](#src-ai-writing-tropes) |
| WRIT-39<a name="writ-39"></a> | historical-analogy stacking: rapid-fire company or tech-era name-drops for borrowed authority | **One apt example, cut the parade** — the list of famous names is authority theater (↔ biz [[STRAT-05]](business-marketing.md#strat-05) status-mediated desire is not independent evidence) | Is this evidence, or a roll call? | S·e | [ai-writing-tropes §composition](#src-ai-writing-tropes) |
| WRIT-40<a name="writ-40"></a> | content duplication: a section or paragraph repeated near-verbatim within one piece | **Deduplicate** — a dead giveaway of unedited long-form model output | Did I already write this passage? | B·v | [ai-writing-tropes §composition](#src-ai-writing-tropes) |

## 7. Sourcing & Citation

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-41<a name="writ-41"></a> | hollow or fabricated citations (invalid DOI/ISBN, refs that resolve to nothing, missing page numbers, tracking junk in URLs) | **Every citation resolves and is checkable** — a reference that looks complete but can't be verified is worse than none (↔ ml [[RAG-07]](ml-systems.md#rag-07) a citation must materially support its claim; ↔ ml [[PROV-01]](ml-systems.md#prov-01) every output walks back to its evidence) | Can a reader actually follow this to the source? | B·v | [ai-writing-tropes §sourcing](#src-ai-writing-tropes) |
| WRIT-42<a name="writ-42"></a> | assistant-output leakage in finished prose (knowledge-cutoff disclaimers, `[insert source here]`, tool tokens, "as of my last update") | **Strip all scaffolding** — template and tool residue is unmistakable machine debris | Is there any placeholder or disclaimer left in? | B·v | [ai-writing-tropes §sourcing](#src-ai-writing-tropes) |

## 8. Detection Posture (meta)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| WRIT-43<a name="writ-43"></a> | judging AI authorship from one stylistic tell, or from a detector score | **Cluster over single; scrutiny not certainty** — any one pattern can be human; detectors are weak evidence; a dense cluster is the real signal (↔ ml [[CAL-02]](ml-systems.md#cal-02) unknown is a valid result; ↔ [[FORE-04]](epistemics.md#fore-04) one outcome does not grade a probability; ↔ [[NDM-05]](epistemics.md#ndm-05) do not explain away the set one cue at a time) | Is this one phrase, or a pile of tells together? | J·v | [ai-writing-tropes §detection](#src-ai-writing-tropes) |
| WRIT-44<a name="writ-44"></a> | editing pass that swaps the flagged phrase but leaves the underlying problem | **Fix the cause, not the phrase** — vague→source or cut; inflated→narrow the claim; decorative→simplify; synonym churn→one precise term; template residue→rewrite (↔ eng [[DBG-10]](engineering.md#dbg-10) fix the cause, not the symptom; ↔ ux [[HAI-02]](interaction-ux.md#hai-02) correction must reach the source) | Did I fix the sentence, or just launder the tell? | S·e | [ai-writing-tropes §detection](#src-ai-writing-tropes) |

## Cross-lexicon links

- `↔ eng NAME-04` (consistency beats local quality): [[WRIT-06]](writing.md#writ-06) and [[WRIT-35]](writing.md#writ-35) serve the same end: match the established convention over personal style.
- `↔ eng UI-01` / design `TYPE-05`: the token-scale discipline that [[WRIT-35]](writing.md#writ-35) applies to prose markup.
- `↔ business GTM-07` (title = emotional first line): a naming rule that legitimately *wants* memorable phrasing: [[WRIT-27]](writing.md#writ-27)'s ban on coined labels is about undefended shorthand, not deliberate, earned names.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[WRIT-07]`) in style guides, review checklists, and agent output instructions. The rules are editing and detection heuristics, not infallible laws: apply [[WRIT-43]](writing.md#writ-43) before calling anything AI-authored, and prefer fixing the cause ([[WRIT-44]](writing.md#writ-44)) over swapping the phrase.

<!-- BEGIN GENERATED SOURCES -->

## Sources

Every `Src` cell above names one of these. The citation is the work itself; the distillation behind it stays in the private research corpus.

| Src | Source | Rules here |
|---|---|---|
| <a name="src-ai-writing-tropes"></a>`ai-writing-tropes` | Ben Larbi, Ossama. "AI Writing Tropes." *tropes.fyi*, n.d., https://tropes.fyi. Wikipedia contributors. "Signs of AI writing." *Wikipedia*, n.d., https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing | 44 |

<!-- END GENERATED SOURCES -->
