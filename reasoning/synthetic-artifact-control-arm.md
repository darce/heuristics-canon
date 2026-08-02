# Artifact-only control for synthetic occlusion

Slug: `synthetic-artifact-control-arm`
ID: `CARD-31`
Mechanism claim: A model can hit a synthetic-occlusion metric by detecting the compositing signature rather than the occlusion, so gains need an artifact-only control arm and a real-occlusion holdout.

## Scope

Covers: train or eval paths that create occlusion (or other face degradation) by compositing an occluder over imagery, then score a recovery or robustness metric on synthetic holdouts from the same recipe; the decision whether a metric move means occlusion competence.

Excludes: fully real capture of physical occlusion with no synthetic composite path; pure hard binary paste with no alpha, resample, or blend stage when no composite signature is claimed; identity-generator quality metrics unrelated to occlusion compositing; project tickets, corpus names, or single-run metric values.

## Observable triggers

- Occlusion is produced by alpha paste, soft matte, anti-aliased silhouette, or smoothed mask over a face crop.
- The ship or research gate reports masked or occluded recovery only on synthetic composites from that pipeline.
- Train and synthetic-eval share the same blend, resample, lighting, or mask generator.
- Soft-alpha or matting is in the path without a premultiplied-RGBA check.
- Automatic masks supply every composite alpha at scale with no fidelity audit sample.
- Metric climbs on synthetic occlusion while real masked or occluded imagery is unreported or flat.

## Causal mechanism

Compositing leaves stable side effects: non-premultiplied fringe, matting halo, resample ringing, lighting mismatch, mask-boundary bias. Those cues co-occur with the occluder label on every synthetic train and synthetic test sample. A model can score well by detecting the cue rather than reading through occlusion. Because the held-out synthetic set reuses the same operator, the evaluation rewards the shortcut. Without a non-occluding composite that keeps the same artifact path, and without real occlusion the pipeline never touched, the green gate does not mean product occlusion competence.

## Required action

While synthetic occlusion is in the train or gate path:

1. Build an artifact-only control arm: same composite operator (alpha, resample, blend, lighting path) with an identity-preserving, non-occluding patch (for example, paste of the underlying face pixels through the same coverage and resample path).
2. Score the target metric on the control arm. If it moves with the occluded synthetic arm, treat the gain as signature detection, not occlusion recovery.
3. Independently keep a real-occlusion holdout the synthetic pipeline never wrote, and require movement there before claiming occlusion competence.
4. On fractional-alpha paths, store and composite as premultiplied RGBA (Porter-Duff over or equivalent) before any occlusion claim.
5. If the paste recipe includes blend or automatic mattes, ablate hard vs blended twins and audit automatic-mask fidelity before promoting the recipe as train mass.

## Predicted failure

Masked or occluded recall rises on synthetic evaluation and stays flat on real occlusion. The release gate passes. Field occlusion performance does not improve. Teams then amplify the synthetic recipe, deepen the shortcut, and delete hard real cells as outliers, locking the false win in.

## Worked example

Ship gate for an occlusion restorer reports only recall on soft alpha pastes from the same compositor used at train time. Hold out real phone photos with hands and scarves, plus a control set that pastes a neutral patch with no identity change. If scores rise only on the soft paste set, the model is reading the matte edge, not recovering the face under real cover.

## Exemptions and boundaries

- Applies only when the claim or gate is about occlusion or composite-induced degradation under a shared synthetic recipe.
- Strict hard binary paste with no soft alpha, blend, or resample stage still needs a real-occlusion holdout if synthetic occlusion is the only robustness evidence; the control arm is less informative when no composite signature exists.
- Premultiplied correctness ([MLDATA-21](../lexicons/ml-systems.md#mldata-21)) reduces one fringe class; it does not retire the control arm for lighting, resample, or mask-boundary signatures.
- Operational certification of synthetic-trained models remains under [MLDATA-20](../lexicons/ml-systems.md#mldata-20); this card owns the signature-vs-occlusion partition on the composite path, not full synthetic privacy or identity-label structure.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [MLDATA-10](../lexicons/ml-systems.md#mldata-10) synthesize degradations to match measured target statistics | Artifact-only control + [MLDATA-20](../lexicons/ml-systems.md#mldata-20) real holdout before competence claims | Match statistics on train mass; never treat synthetic-only recovery as the ship proof |
| surface | [MLDATA-21](../lexicons/ml-systems.md#mldata-21) premultiplied over for fractional coverage | [MLDATA-22](../lexicons/ml-systems.md#mldata-22) hard vs blended ablation for seam recipes | Correct coverage first; then measure whether blend buys metric, not assume it |
| sequence | [EVAL-06](../lexicons/ml-systems.md#eval-06) prefer models that win on production-like perturbation | [MLDATA-09](../lexicons/ml-systems.md#mldata-09) keep hard real occlusion cells as strata, not filter rejects | Perturb and composite for training signal; gate competence on cells the product still sees |
| object | [MLDATA-23](../lexicons/ml-systems.md#mldata-23) automatic masks at scale after fidelity audit | Human-corrected or hard masks when audit fails the bar | Scale only after the pre-registered boundary bar; do not let unmeasured matte bias own every edge |

## Disconfirmers

- Control-arm metric stays within noise of the uncomposited baseline while the occluded synthetic arm moves, and real-occlusion holdout moves in the same direction and magnitude.
- Independent real-occlusion sets from multiple capture conditions show the same gain without any shared composite operator.
- Switching blend, resample, or alpha representation kills the synthetic gain and leaves real-occlusion gain intact (signature-dependent win).
- Premultiplied path and hard-paste path agree within noise on both control and occluded arms for this task and data regime.

## Verification

- Control-arm assets exist, share the composite code path and config hash with the occluded arm, and differ only by non-occluding patch content.
- Report table includes three columns: uncomposited baseline, artifact-only control, occluded synthetic; control movement is reviewed before any occlusion claim.
- Real-occlusion holdout IDs are disjoint from every synthetic generator input and composite cache.
- Soft-alpha fixture: stored pixels and composite kernel match premultiplied over (pixel-diff zero only on that path).
- If blend or automatic masks are used: hard/blended twin comparison and mask IoU or human-boundary audit numbers are on the training report.

## Rule IDs

- [MLDATA-09](../lexicons/ml-systems.md#mldata-09): refuse filters and cleanups that delete real hard occlusion from the claim set
- [MLDATA-10](../lexicons/ml-systems.md#mldata-10): size synthetic degradation from measured target statistics, then re-check on true target data
- [MLDATA-20](../lexicons/ml-systems.md#mldata-20): synthetic scores show trainability; operational occlusion still needs real imagery
- [MLDATA-21](../lexicons/ml-systems.md#mldata-21): premultiplied RGBA so fractional coverage does not mint fringe signatures
- [MLDATA-22](../lexicons/ml-systems.md#mldata-22): ablate hard vs blended paste before treating seam blend as necessary
- [MLDATA-23](../lexicons/ml-systems.md#mldata-23): gate automatic mattes on audited boundary fidelity before they enter every composite
- [EVAL-06](../lexicons/ml-systems.md#eval-06): choose models that win under production-like perturbation, not only clean synthetic

## Principles

- 15. A measurement the measured party can shape is not a measurement

## Evidence / source slugs

- [`porter-duff-compositing`](../SOURCES.md#src-porter-duff-compositing): supports [MLDATA-21](../lexicons/ml-systems.md#mldata-21)
- [`simple-copy-paste`](../SOURCES.md#src-simple-copy-paste): supports [MLDATA-22](../lexicons/ml-systems.md#mldata-22)
- [`segment-anything`](../SOURCES.md#src-segment-anything): supports [MLDATA-23](../lexicons/ml-systems.md#mldata-23)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [EVAL-06](../lexicons/ml-systems.md#eval-06)
- [`janus-benchmark-c`](../SOURCES.md#src-janus-benchmark-c): supports [MLDATA-09](../lexicons/ml-systems.md#mldata-09)
- [`video-to-video-face-surveillance`](../SOURCES.md#src-video-to-video-face-surveillance): supports [MLDATA-10](../lexicons/ml-systems.md#mldata-10)
- [`sface-synthetic-data`](../SOURCES.md#src-sface-synthetic-data): supports [MLDATA-20](../lexicons/ml-systems.md#mldata-20)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not assert a dedicated lexicon row whose sole name is "compositing-signature control arm"; that decision is synthesized here from the linked rules. It does not cover synthetic identity privacy, generator labeled-ID dependence, or FID-style corpus ranking. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
