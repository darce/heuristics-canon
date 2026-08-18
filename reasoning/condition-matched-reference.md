# Match the reference to the query's conditions

Slug: `condition-matched-reference`
ID: `CARD-32`
Mechanism claim: When the reference side of a comparison was built under conditions the query never had, both sides can be honest and the metric can look fine while the comparison silently fails — so build or re-stratify the reference under the query's conditions before trusting the number.

## Scope

Covers: decisions that compare a live probe, input, or query against a gallery, lineup, training distribution, impostor set, test suite, or serving transform; the act of constructing or stratifying that reference so its conditions match the query's (occlusion class, capture quality, demographics of non-mates, featurization path, production-like noise).

Excludes: choosing the wrong outcome metric or proxy (Principle 4); filters, pauses, or denominator minting by the measured system that reshape the sample (Principle 15; [MLDATA-09](../lexicons/ml-systems.md#mldata-09) is owned there); evidence timing relative to a durable commit (Principle 13); compositing-signature shortcuts on synthetic occlusion ([synthetic-artifact-control-arm](synthetic-artifact-control-arm.md), CARD-31); project tickets, corpus names, or single-run metric values.

## Observable triggers

- Identification or match uses a probe under a named covering or partial-face view, but the gallery, lineup, or enrollment set is full-face by default.
- Partial or occlusion-determined probe support is scored against full-face or differently partitioned gallery vectors with no part correspondence.
- Occlusion is handled only as a global quality or confidence multiplier on a full-face compare, with no estimate of which support is hidden.
- Real-world occlusion robustness is claimed from rectangle, noise, or unrelated-image fills only.
- Training uses clean high-quality captures while deployment is degraded, with no measured target degradation driving the train recipe.
- Serving re-implements train-time featurization, or train and serve featurize through different unpinned code.
- Operating threshold is fit on pooled or zero-effort impostor pairs while real attacks are demographically matched.
- One threshold or one accuracy number spans quality regimes or query×enrolled capture cells the product actually runs.
- Model selection wins on clean holdout while production noise is known and untested.

## Causal mechanism

A comparison has two constructed sides. The reference is usually assembled first under conditions that were easy to collect — clean mugshots, full-face enrollments, zero-effort impostors, curated train transforms, laboratory noise. The query arrives later under different conditions. Nothing about either artifact is forged, and nothing about the reported number looks broken, so the mismatch is invisible to inspection of the metric alone. The failure is in reference construction: the system is answering a different question than the one the query poses. The prescribed act is therefore construction, not reporting — rebuild or re-stratify the reference under the query's conditions, or name the unmatched stratum instead of pooling across it.

## Required action

While a comparison's reference may have been built under different conditions than the query:

1. Name the query's condition class (occlusion covering, capture quality, demographic pairing of non-mates, featurization version, production noise) before scoring.
2. Build or select the reference under that same class: condition-matched gallery or lineup, part-aligned support, quality-matched train degradation, demographically matched impostors, train/serve transform parity, production-like perturbation suite.
3. When full match is impossible, report and gate by the named stratum or query×enrolled cell rather than a pooled number that hides the mismatch.
4. For regional occlusion, estimate hidden support and establish correspondence to the same gallery semantics before score; do not rely only on a scalar quality penalty.
5. For real-occlusion product claims, require real or realistic-accessory cells — synthetic blocks alone do not certify them.

## Predicted failure

Hit rates and discriminability fall on masked or partial probes while full-face gallery metrics stay green. Thresholds set on easy impostors understate field false-match risk. Clean-trained models collapse under deployment blur and compression. Offline scores stay high while production features diverge. One ship-gate number certifies every capture cell and none of the hard ones. Teams then trust the convenient reference harder, never seeing that the comparison was never condition-matched.

## Worked example

A review desk identifies people from short video where the subject wears a lower-face covering. The default candidate set is full-face enrollment photos. Operators treat "more face visible" as strictly better and ship a hit-rate number on that full-face gallery. Rebuild the candidate set under the same covering class as the probe and re-run identification on the same masked probes. If hits rise only under the matched set, the prior green number measured transfer-inappropriate retrieval, not identification under the query's conditions. Without the rebuild, the desk keeps a reference that never shared the probe's occlusion state.

## Exemptions and boundaries

- Applies when a decision compares two sides and the reference's collection or construction conditions can differ from the query's.
- Does not apply when both sides are contractually the same condition and that cell is the only one measured and shipped.
- Wrong proxy quantity is Principle 4; shaped sampling frames and hard-cell deletion are Principle 15 ([MLDATA-09](../lexicons/ml-systems.md#mldata-09)); commit-before-evidence is Principle 13.
- Synthetic occlusion that leaves a compositing signature the model can detect instead of reading through occlusion is [synthetic-artifact-control-arm](synthetic-artifact-control-arm.md) (CARD-31). This card owns condition mismatch of the reference with no shortcut cue required. The two share [MLDATA-10](../lexicons/ml-systems.md#mldata-10) and [EVAL-06](../lexicons/ml-systems.md#eval-06) as construction and gate twins under different mechanisms.
- Measuring every pair cell ([EVAL-20](../lexicons/ml-systems.md#eval-20)) does not replace building a condition-matched path ([HITL-15](../lexicons/ml-systems.md#hitl-15)); both stay in force.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [HITL-15](../lexicons/ml-systems.md#hitl-15) construct a covering-matched gallery for the probe | [EVAL-20](../lexicons/ml-systems.md#eval-20) measure every production query×enrolled cell | Build the matched path for the active query; still report the mismatch cell before claiming the product works there |
| object | [MLDATA-10](../lexicons/ml-systems.md#mldata-10) match train degradation to measured target statistics | [EVAL-28](../lexicons/ml-systems.md#eval-28) real-occlusion claims need real or realistic-accessory cells | Match degradations on train mass; do not treat synthetic-only occlusion scores as the real-occlusion ship proof |
| object | [CAL-04](../lexicons/ml-systems.md#cal-04) fit T on demographically matched non-mates | [CAL-01](../lexicons/ml-systems.md#cal-01) calibrate FAR/FRR per quality stratum | Match impostor covariates for security FMR; do not pool quality regimes under one unmeasured T |
| sequence | [SERVE-08](../lexicons/ml-systems.md#serve-08) identical train/serve transforms at construction | [EVAL-06](../lexicons/ml-systems.md#eval-06) choose models that win under production-like perturbation | Parity makes the features comparable; the gate still picks the model that wins on the matched noise suite |
| surface | [EMB-11](../lexicons/ml-systems.md#emb-11) / [EMB-12](../lexicons/ml-systems.md#emb-12) spatial support and part correspondence for this compare | Broad multi-condition reference kept for other query regimes | Match support to the active query's visible region; keep other strata named rather than one convenient full-face default for every probe |

## Disconfirmers

- Condition-matched and unmatched references produce the same hit rates, thresholds, and ship-gate ranks within noise on the product's real query distribution.
- Train and serve golden fixtures already match, and live feature-skew checks stay at zero without a packaged or pinned transform.
- Zero-effort and demographically matched impostor FMR agree at the operating threshold for this matcher and population.
- Every production query×enrolled and quality cell is measured and none moves the decision relative to the convenient single-cell number.
- Real-accessory and synthetic-block occlusion cells rank models identically for the claimed deployment.

## Verification

- Query condition class is named on the eval or ops report (covering, quality, pairing, transform version, noise suite).
- Reference assets or recipes for that class exist: matched gallery IDs, part-correspondence path, measured degradation schedule, matched-impostor pairing rule, transform package or pin, perturbation suite.
- Ship table includes the matched cell (or stratum) separately from any convenient unmatched pool.
- Train-vs-serve golden fixtures match feature-for-feature under the pinned contract.
- Real-occlusion claims cite real or realistic-accessory cells, not only rectangle or unrelated fills.

## Rule IDs

- [HITL-15](../lexicons/ml-systems.md#hitl-15): construct or select gallery/lineup under the probe's covering class
- [EMB-11](../lexicons/ml-systems.md#emb-11): treat occlusion as which support is hidden, not only a scalar quality penalty
- [EMB-12](../lexicons/ml-systems.md#emb-12): align partial probe support to the same gallery part semantics before score
- [EVAL-28](../lexicons/ml-systems.md#eval-28): real-occlusion claims require real or realistic-accessory protocol cells
- [MLDATA-10](../lexicons/ml-systems.md#mldata-10): size training degradations from measured target statistics
- [SERVE-08](../lexicons/ml-systems.md#serve-08): identical featurization on train and serve via package or pinned contract
- [CAL-04](../lexicons/ml-systems.md#cal-04): fit the operating threshold on demographically matched non-mates
- [CAL-01](../lexicons/ml-systems.md#cal-01): measure and set policy per quality stratum, not one pooled T
- [EVAL-20](../lexicons/ml-systems.md#eval-20): stratify by query×enrolled capture cell, not one side alone
- [EVAL-06](../lexicons/ml-systems.md#eval-06): select models that win under production-like perturbation

## Principles

- 20. Match the reference to the conditions of the query

## Evidence / source slugs

- [`mask-wearing-identification`](../SOURCES.md#src-mask-wearing-identification): supports [HITL-15](../lexicons/ml-systems.md#hitl-15)
- [`occluded-face-recognition-survey`](../SOURCES.md#src-occluded-face-recognition-survey): supports [EMB-11](../lexicons/ml-systems.md#emb-11), [EMB-12](../lexicons/ml-systems.md#emb-12), [EVAL-28](../lexicons/ml-systems.md#eval-28)
- [`video-to-video-face-surveillance`](../SOURCES.md#src-video-to-video-face-surveillance): supports [MLDATA-10](../lexicons/ml-systems.md#mldata-10)
- [`ml-design-patterns`](../SOURCES.md#src-ml-design-patterns): supports [SERVE-08](../lexicons/ml-systems.md#serve-08)
- [`nist-frvt-demographics`](../SOURCES.md#src-nist-frvt-demographics): supports [CAL-04](../lexicons/ml-systems.md#cal-04), [CAL-01](../lexicons/ml-systems.md#cal-01)
- [`handbook-face-recognition`](../SOURCES.md#src-handbook-face-recognition): supports [EVAL-20](../lexicons/ml-systems.md#eval-20)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [EVAL-06](../lexicons/ml-systems.md#eval-06)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not restate Principle 4's proxy failure, Principle 15's shaped sample, or Principle 13's evidence clock. It does not own compositing-signature control arms (CARD-31). For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
