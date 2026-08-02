# Signal density, not length

Slug: `signal-density-not-length`
ID: `CARD-30`
Mechanism claim: When description quality metrics rise with word count, optimization treats listener time as free benefit and the verbose candidate wins.

## Scope

Covers: scorecards, bake-offs, and model-ranking reports for image or video descriptions, alt text, audio description, or other linearly consumed captions where a quality, richness, or coverage score correlates with length; any judge or rubric that rewards longer-is-richer without a density companion.

Excludes: time-aligned *composition* fit of spoken cues into speech gaps (owned by accessibility placement rows, not this scorecard cut); general prose brevity for human-written articles with free skim; pure retrieval or answer grounding at emission time; ranking-list depth metrics for operators who scan rather than listen.

## Observable triggers

- A bake-off or harness ranks description systems on BLEU, CIDEr, holistic human quality, coverage, or similar scores that move upward with word count, with no density column.
- A pairwise judge is not length-matched and longer answers win systematically.
- Reported quality climbs while estimated speech seconds and unverified detail also climb.
- Length is treated as a free quality surrogate rather than a budget or cost column.
- Unverifiable color, brand, age, or identity detail scores the same as pixel-checkable facts.

## Causal mechanism

Linear consumers (screen readers, TTS, time-aligned audio description) pay every extra word in fixed-rate listen time with little skim. Metrics that rise with length pay the system for producing those words. Optimization therefore lengthens. Unless the scorecard also rewards *verified* facts per unit of listening cost, and zeros unverifiable specificity, fluency and decorative detail crowd out checkable substance. Comprehension per second falls while every reported number rises. Composition rules may still budget gap time correctly; this failure is the *selection* meter, not the authoring timeline.

## Required action

1. When any description quality metric is length-correlated, report verified facts per estimated listener-second (or per 100 words at a fixed, documented speech-rate proxy) as a required companion column, and treat length as a budget or cost, not as free quality ([EVAL-11](../lexicons/ml-systems.md#eval-11), [UXR-03](../lexicons/interaction-ux.md#uxr-03), [A11Y-16](../lexicons/accessibility.md#a11y-16)).
2. Count a fact in the numerator only when it is checkable against the image or a trusted supplied field; unverifiable specificity scores zero ([PROV-01](../lexicons/ml-systems.md#prov-01), [RAG-07](../lexicons/ml-systems.md#rag-07), [WRIT-05](../lexicons/writing.md#writ-05)).
3. Length-match or otherwise control verbosity when a judge ranks candidates; report position and verbosity effects ([EVAL-14](../lexicons/ml-systems.md#eval-14)).
4. Do not let the system mint its own success divisor; fixed external exposure or a fixed speech-rate proxy for the density denominator ([EVAL-19](../lexicons/ml-systems.md#eval-19)).
5. Prefer media-local visual content over restatement and ornament when words are scarce; alt and description still serve purpose, not decoration ([A11Y-43](../lexicons/accessibility.md#a11y-43), [A11Y-02](../lexicons/accessibility.md#a11y-02), [WRIT-17](../lexicons/writing.md#writ-17)).
6. Before trusting a length-friendly offline score as a ship gate, validate that moving it moves a user or product metric, not only word count ([EVAL-22](../lexicons/ml-systems.md#eval-22), [AIPX-02](../lexicons/business-marketing.md#aipx-02), [RSCH-07](../lexicons/epistemics.md#rsch-07)).

## Predicted failure

The bake-off winner is the most verbose candidate. Holistic quality and coverage rise; denser, more checkable systems lose on paper. Screen-reader and TTS users pay more seconds for less substance. Unverifiable invention is rewarded as richness. Teams ship the long model and discover that listening cost bought padding.

## Worked example

A museum alt bake-off scores three systems on holistic richness. System B wins by inventing fabric brands and ages no pixel supports, while the shorter inventory that names coat, hatstand, and doorway loses. Length-match every pair and score only verified facts per listener-second. Otherwise the verbose model ships and screen-reader users sit through padding that adds no new fact.

## Exemptions and boundaries

- Time-aligned cue *placement* against speech gaps, overflow modes, and pause-vs-compress order are composition decisions ([A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-41](../lexicons/accessibility.md#a11y-41)); this card owns the *scorecard* density cut, not gap collision.
- Hard-locked verbatim on-screen text or must-include cues may force length without density gain; lock those units rather than punish them as padding ([A11Y-44](../lexicons/accessibility.md#a11y-44)).
- Non-spoken text where the reader truly skims: still report density; do not invent a speech-rate harm you cannot measure.
- General proxy-vs-outcome gaming without a length-as-listen-cost path is owned by [proxy-outcome-integrity](proxy-outcome-integrity.md). Shaped denominators and frames are owned by [measurement-integrity](measurement-integrity.md).
- Runtime answer grounding and citation support remain [RAG-06](../lexicons/ml-systems.md#rag-06) / [RAG-07](../lexicons/ml-systems.md#rag-07) / [PROV-01](../lexicons/ml-systems.md#prov-01); this card is evaluation and ranking of description systems, not the emission gate.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | Holistic coverage / human richness that often rises with length | Verified density and listen-time cost ([EVAL-11](../lexicons/ml-systems.md#eval-11), [A11Y-16](../lexicons/accessibility.md#a11y-16)) | Report both columns; never collapse to one averaged length |
| object | [A11Y-39](../lexicons/accessibility.md#a11y-39) / [A11Y-40](../lexicons/accessibility.md#a11y-40) timeline fit for spoken cues | Density scorecard for any linearly consumed description | Gap non-overlap is video-timeline composition; density is the ranking meter |
| sequence | [PROV-01](../lexicons/ml-systems.md#prov-01) / [RAG-07](../lexicons/ml-systems.md#rag-07) checkable claims at emission | Density numerator zeros unverifiable detail at selection | Same verification duty; different moment (score vs ship) |
| object | [WRIT-17](../lexicons/writing.md#writ-17) cut padding in prose | Keep locked critical visual cues under fit pressure ([A11Y-44](../lexicons/accessibility.md#a11y-44)) | Drop ornament, not hard-locked content |

## Disconfirmers

- Length-matched candidates reverse the quality ranking that verbosity previously produced (length was load-bearing for the old score).
- Adding a verified-density column does not change rank order on the same run (length was not driving the gate).
- Unverifiable-but-specific claims, when zeroed, leave the winner unchanged (invention was not being rewarded).
- Live listen-time or task success does not move when word count rises under a fixed density floor (length is not the cost that matters for that product).

## Verification

- Bake-off or harness config exposes a density column next to any length-correlated quality metric.
- Sample N outputs: recompute checkable atomic claims / estimated speech-seconds (or /100 words at a stated rate); unverifiable specific claims contribute 0.
- Judge protocol is length-matched or reports verbosity effect size ([EVAL-14](../lexicons/ml-systems.md#eval-14)).
- Rank order with density vs quality-only on the same candidate set is recorded; ship gate names which column decides ties.
- No promotion on a length-friendly score that has never been degraded against a user or product metric ([EVAL-22](../lexicons/ml-systems.md#eval-22)).

## Rule IDs

- [EVAL-11](../lexicons/ml-systems.md#eval-11): open-ended description needs a scorer that measures task success, not wording length
- [EVAL-14](../lexicons/ml-systems.md#eval-14): length-match and report verbosity bias in judges
- [EVAL-19](../lexicons/ml-systems.md#eval-19): do not let a system-controlled volume mint the success rate
- [EVAL-22](../lexicons/ml-systems.md#eval-22): offline length-friendly scores need a live degrade check
- [AIPX-02](../lexicons/business-marketing.md#aipx-02): offline score up is not product acceptance
- [RSCH-07](../lexicons/epistemics.md#rsch-07): simulate how the measured system optimizes the number
- [UXR-03](../lexicons/interaction-ux.md#uxr-03): choose the metric for the listen-time goal
- [A11Y-02](../lexicons/accessibility.md#a11y-02): alt and description serve purpose, not a word dump
- [A11Y-09](../lexicons/accessibility.md#a11y-09): captions and alternatives exist for non-text content
- [A11Y-16](../lexicons/accessibility.md#a11y-16): the user's time is the scarce resource
- [A11Y-39](../lexicons/accessibility.md#a11y-39): spoken description duration is a timeline budget (composition sibling)
- [A11Y-40](../lexicons/accessibility.md#a11y-40): overflow must be a named mode, not silent bloat
- [A11Y-43](../lexicons/accessibility.md#a11y-43): spend scarce words on non-audio visuals
- [A11Y-44](../lexicons/accessibility.md#a11y-44): hard-lock critical cues; do not score them as padding
- [PROV-01](../lexicons/ml-systems.md#prov-01): every counted fact walks back to evidence
- [RAG-07](../lexicons/ml-systems.md#rag-07): a claim without material support is not a fact in the numerator
- [WRIT-05](../lexicons/writing.md#writ-05): intensifiers are not evidence
- [WRIT-17](../lexicons/writing.md#writ-17): restating one thesis is not more signal

## Principles

- 4. You get the number you pay for, not the outcome you want
- 15. A measurement the measured party can shape is not a measurement

## Evidence / source slugs

- [`rescribe-audio-descriptions`](../SOURCES.md#src-rescribe-audio-descriptions): supports [A11Y-39](../lexicons/accessibility.md#a11y-39), [A11Y-40](../lexicons/accessibility.md#a11y-40), [A11Y-43](../lexicons/accessibility.md#a11y-43), [A11Y-44](../lexicons/accessibility.md#a11y-44)
- [`wcag22-accessibility`](../SOURCES.md#src-wcag22-accessibility): supports [A11Y-02](../lexicons/accessibility.md#a11y-02), [A11Y-09](../lexicons/accessibility.md#a11y-09), [A11Y-16](../lexicons/accessibility.md#a11y-16)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [EVAL-11](../lexicons/ml-systems.md#eval-11), [EVAL-14](../lexicons/ml-systems.md#eval-14), [RAG-07](../lexicons/ml-systems.md#rag-07)
- [`janus-benchmark-c`](../SOURCES.md#src-janus-benchmark-c): supports [EVAL-19](../lexicons/ml-systems.md#eval-19)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [EVAL-22](../lexicons/ml-systems.md#eval-22)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-02](../lexicons/business-marketing.md#aipx-02)
- [`hamming-art-of-doing-science`](../SOURCES.md#src-hamming-art-of-doing-science): supports [RSCH-07](../lexicons/epistemics.md#rsch-07)
- [`measuring-the-ux-albert-tullis`](../SOURCES.md#src-measuring-the-ux-albert-tullis): supports [UXR-03](../lexicons/interaction-ux.md#uxr-03)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-05](../lexicons/writing.md#writ-05), [WRIT-17](../lexicons/writing.md#writ-17)
- [`model-cards`](../SOURCES.md#src-model-cards): supports [PROV-01](../lexicons/ml-systems.md#prov-01)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea about accessibility, evaluation, or captioning. It does not assert a dedicated inventory row for "signal-density scoring"; the decision is synthesized from the cited rules. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
