# Controlled vocabulary caps hallucination

Slug: `controlled-vocabulary-caps-hallucination`
ID: `CARD-24`
Mechanism claim: Free-form attribute words can sound precise without being checkable; binding those attributes to a closed, named vocabulary makes specificity falsifiable and stops rare confident nouns from counting as quality.

## Scope

Covers: decisions that emit attribute labels with pretended fixed identity (colour first; any other class with a defensible closed catalog) from free-form generation, where the term will be stored, ranked, filtered, or trusted as a system label.

Excludes: open literary description with no claim of catalog identity; continuous numeric colour spaces used without named membership; full caption or narrative style rules; face-identity match thresholds; bibliography or citation hygiene outside attribute terms.

## Observable triggers

- Schema field, prompt, or post-process path allows unconstrained free text for colour (or another closed attribute class) while treating the string as a token, recipe key, filter, or validated label.
- Outputs contain rare, precise-sounding attribute nouns (`cerulean`, period labels, affect adjectives) with no membership check against a named set.
- Review or reward metrics score "informativeness" or lexical specificity higher when the term is rarer, without a grounding or membership check.
- Downstream code parses attribute prose instead of a schema-validated enum or catalog id.
- Out-of-set strings are silently accepted, synonym-churned, or rephrased rather than rejected or mapped into the set.

## Causal mechanism

Specificity and accuracy are independent. Under free-form description, a model can emit a precise-sounding word it has no evidence for. Readers and scorers treat precision as a trust signal, so confident rare nouns raise informativeness scores while the hallucination rate rises with them. A controlled vocabulary with named referents turns the specific word into a membership test: the term is either in the set (and therefore checkable) or it is not. Without that test, precision is free and the system cannot tell style from evidence.

## Required action

While the trigger holds:

1. Identify attribute classes with a defensible closed set; treat colour as the default case requiring a bound catalog of fixed referents.
2. Bind generation of those fields to the catalog (schema, enum, constrained decode, or post-generation membership check). Prefer structured, validated output over free prose for machine-consumed fields.
3. Validate every emitted term deterministically against the set. Out-of-set terms are rejected, marked unknown, or degraded to the nearest in-set term by an explicit mapping rule—not passed through.
4. When evidence does not support any in-set term, emit unknown / abstain rather than inventing a precise-sounding label.
5. Once an in-set term is chosen, reuse that exact term; do not elegant-vary synonyms that escape the catalog.
6. Score and gate attribute quality with a scorer that cannot treat free rare nouns as success; membership and grounding beat lexical flash.

## Predicted failure

If the action is skipped or faked (prompt advice without a hard membership gate), informativeness and specificity metrics climb with the hallucination rate: the rarest confident nouns score best, readers trust false precision, and filters, recipes, and audits treat invented labels as real identity.

## Worked example

A labelling schema accepts free-text "scene mood" and the model emits confident rare nouns that no two annotators reuse. The trigger is an open attribute string where membership is uncheckable. Bind the field to a closed enum with an Other+note escape. Without the closed set, eval treats inventive synonyms as new classes and rare confident words score as precision.

## Exemptions and boundaries

- Open prose that does not claim catalog membership (mood, scene, metaphor) is outside this card; plain-language style still applies, but not a closed colour identity gate.
- Continuous measurements (hex, Lab, wavelength) used as values, not as pretence of a named system term, are not closed-vocabulary membership claims.
- When no closed set is defensible for the attribute class, do not invent a fake catalog; either design unknown as a state or leave the class out of system identity.
- Cross-lexicon colour interaction and design tokens live outside this inventory; do not treat this card as a design-system or pigment treatise.
- Sibling concerns: general structured-output contracts and unknown-as-designed-state apply beyond colour; this card owns the mechanism where free specificity becomes uncheckable attribute identity.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | Human-facing prose may use ordinary colour words without catalog pretence ([WRIT-02](../lexicons/writing.md#writ-02), [WRIT-03](../lexicons/writing.md#writ-03)) | Machine-consumed or identity-bearing colour must be catalog-bound and validated ([FM-04](../lexicons/ml-systems.md#fm-04)) | If the string is a token, filter, recipe, or validated label, Side B; if it is narrative only, Side A |
| object | Concrete referent over decorative abstraction in open prose ([WRIT-03](../lexicons/writing.md#writ-03)) | Membership only in the closed assertable set ([BOUND-01](../lexicons/depiction.md#bound-01)) | Concrete free words that are not in the set never become system identity; map, reject, or abstain |
| sequence | Prefer rich description before edit for human draft | Validate membership before accept; unknown when unsupported ([CAL-02](../lexicons/ml-systems.md#cal-02), [PROV-01](../lexicons/ml-systems.md#prov-01)) | Generation may draft freely; commitment gates only in-set, evidenced terms |

## Disconfirmers

- Under free-form attribute emission, rare confident nouns do not increase false membership or reader-trusted error relative to controlled terms.
- A hard catalog gate raises measured error (wrong in-set picks) more than it reduces invented out-of-set labels, with no compensating audit benefit.
- Downstream consumers never treat attribute strings as identity, filters, or keys—only as disposable prose—so membership checks never fire.
- Human raters and automatic scorers already penalize ungrounded rare nouns as heavily as false membership, so free specificity is not free.

## Verification

- Every colour (or other closed-class) field in the schema names a vocabulary id and rejects strings outside the set in tests.
- Sample N recent outputs: zero out-of-set terms on gated fields; out-of-set attempts end in reject, unknown, or documented nearest-term map.
- Diff or config shows the catalog version pinned with the generation contract.
- Metric definition for attribute quality does not reward lexical rarity without membership or grounding.
- Spot-check: forced weak-evidence cases produce unknown / abstain, not a precise invented noun.

## Rule IDs

- [FM-04](../lexicons/ml-systems.md#fm-04): schema-constrain and validate attribute output before use
- [CAL-02](../lexicons/ml-systems.md#cal-02): when no in-set term is supported, unknown / abstain instead of forced precise label
- [BOUND-01](../lexicons/depiction.md#bound-01): keep the assertable attribute set bounded so free words do not expand claimed identity
- [WRIT-03](../lexicons/writing.md#writ-03): demand a concrete referent, then only commit if that referent is in-set and checkable
- [WRIT-06](../lexicons/writing.md#writ-06): once an in-set term is chosen, repeat it; synonym churn escapes the catalog
- [PROV-01](../lexicons/ml-systems.md#prov-01): an attribute claim must walk back to evidence or catalog membership, not to fluent invention
- [EVAL-11](../lexicons/ml-systems.md#eval-11): open attribute tasks need a scorer that does not treat rare free nouns as success
- [WRIT-44](../lexicons/writing.md#writ-44): fix free-vocabulary generation, not a single hallucinated synonym after the fact

## Principles

- 11. Unknown is a designed state
- 18. A machine consumes contracts, not prose

## Evidence / source slugs

- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-04](../lexicons/ml-systems.md#fm-04)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [CAL-02](../lexicons/ml-systems.md#cal-02)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-03](../lexicons/writing.md#writ-03), [WRIT-06](../lexicons/writing.md#writ-06), [WRIT-44](../lexicons/writing.md#writ-44)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not invent a general "controlled vocabulary" rule beyond the listed IDs, does not cite design-lexicon colour rows outside this inventory, and does not rest on source slugs absent from SOURCES.md. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
