# Artifact-only control for synthetic occlusion

Slug: `synthetic-artifact-control-arm`
ID: `CARD-31`
Mechanism claim: Detecting a compositing signature rather than handling occlusion is a testable shortcut hypothesis, not a mechanism established by the linked sources; synthetic scores must stay separate from operational occlusion evidence.

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

Hypothesis to test: a shared compositor may leave cues such as fringes or boundary errors that a model could exploit on synthetic holdouts. The linked sources do not measure this shortcut. Hard-alpha versus blended twins test the effect of edge treatment; an artifact-only control is a proposed additional experiment. Neither synthetic scores nor that proposed control replace evaluation on operational imagery, including real occlusion for an occlusion claim.

## Required action

While synthetic occlusion is in the train or gate path:

1. If the paste recipe includes seam blending or alpha smoothing, train geometry-matched hard-alpha and blended twins, differing only in edge treatment, and compare the target metric before treating blend as necessary ([MLDATA-22](../lexicons/ml-systems.md#mldata-22)).
2. An artifact-only control using the same operator with an identity-preserving, non-occluding patch is a proposed experiment, pending independent support. If used, compare it with the uncomposited baseline and occluded synthetic arm; shared movement would motivate further shortcut tests, not establish signature detection.
3. Independently keep a real-occlusion holdout the synthetic pipeline never wrote, and require movement there before claiming occlusion competence.
4. On fractional-alpha paths, store and composite as premultiplied RGBA (Porter-Duff over or equivalent) before any occlusion claim.
5. Before promoting the recipe as train mass, ablate hard vs blended twins if seam blending or alpha smoothing is present, and audit automatic-mask fidelity if automatic mattes are used.

## Predicted failure

Under the shortcut hypothesis, masked or occluded recall could rise on synthetic evaluation while staying flat on real occlusion. A synthetic-only release gate could then pass without field improvement. This pattern would expose a gap in operational evidence, not prove the model learned compositing signatures.

## Worked example

Ship gate for an occlusion restorer reports only recall on soft alpha pastes from the training compositor. Hold out real phone photos with hands and scarves, and compare geometry-matched hard-alpha and blended training twins. An artifact-only control could be added as a proposed experiment. If scores rise only on synthetic pastes, operational occlusion competence remains unestablished; the result does not identify a matte-edge shortcut.

## Exemptions and boundaries

- Applies only when the claim or gate is about occlusion or composite-induced degradation under a shared synthetic recipe.
- Strict hard binary paste with no soft alpha, blend, or resample stage still needs a real-occlusion holdout if synthetic occlusion is the only robustness evidence; the proposed control targets a suspected composite signature, not a demonstrated one.
- Premultiplied correctness ([MLDATA-21](../lexicons/ml-systems.md#mldata-21)) reduces one fringe class; it does not establish or rule out the hypothesized lighting, resample, or mask-boundary shortcuts.
- Operational certification of synthetic-trained models remains under [MLDATA-20](../lexicons/ml-systems.md#mldata-20); this card owns the signature-vs-occlusion partition on the composite path, not full synthetic privacy or identity-label structure.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [MLDATA-10](../lexicons/ml-systems.md#mldata-10) synthesize degradations to match measured target statistics | Proposed artifact-only control + [MLDATA-20](../lexicons/ml-systems.md#mldata-20) real holdout before competence claims | Match statistics on train mass; never treat synthetic-only recovery as the ship proof |
| surface | [MLDATA-21](../lexicons/ml-systems.md#mldata-21) premultiplied over for fractional coverage | [MLDATA-22](../lexicons/ml-systems.md#mldata-22) hard vs blended ablation for seam recipes | Correct coverage first; then measure whether blend buys metric, not assume it |
| sequence | [EVAL-06](../lexicons/ml-systems.md#eval-06) prefer models that win on production-like perturbation | [MLDATA-09](../lexicons/ml-systems.md#mldata-09) retain non-frontal poses when a frontal-biased detector harvest supports an unconstrained recognition claim; [MLDATA-20](../lexicons/ml-systems.md#mldata-20) operational imagery for deployment claims | Perturb and composite for training signal; gate competence on cells the product still sees |
| object | [MLDATA-23](../lexicons/ml-systems.md#mldata-23) automatic masks at scale after fidelity audit | Human-corrected or hard masks when audit fails the bar | Scale only after the pre-registered boundary bar; do not let unmeasured matte bias own every edge |

## Disconfirmers

- If the proposed control is used, its metric stays within noise of the uncomposited baseline while the occluded synthetic arm moves, and real-occlusion holdout moves in the same direction and magnitude.
- Independent real-occlusion sets from multiple capture conditions show the same gain without any shared composite operator.
- Switching blend, resample, or alpha representation kills the synthetic gain and leaves real-occlusion gain intact (evidence to investigate operator dependence, not proof of signature detection).
- Premultiplied path and hard-paste path agree within noise on both control and occluded arms for this task and data regime.

## Verification

- If the proposed artifact-only experiment is run, control-arm assets exist, share the composite code path and config hash with the occluded arm, and differ only by non-occluding patch content.
- If the paste recipe includes seam blending or alpha smoothing, report the hard-alpha versus blended-twin target metrics. If the proposed control is run, also report uncomposited baseline, artifact-only control, and occluded synthetic metrics; keep these separate from operational occlusion results.
- Real-occlusion holdout IDs are disjoint from every synthetic generator input and composite cache.
- Soft-alpha fixture: stored pixels and composite kernel match premultiplied over (pixel-diff zero only on that path).
- If seam blending or alpha smoothing is used, the hard/blended twin comparison is on the training report; if automatic masks are used, mask IoU or human-boundary audit numbers are on the report.

## Rule IDs

- [MLDATA-09](../lexicons/ml-systems.md#mldata-09): preserve non-frontal pose coverage when frontal-biased detector harvesting supports an unconstrained face-recognition claim
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

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not assert a dedicated lexicon row whose sole name is "compositing-signature control arm"; the artifact-only control is proposed here and needs independent support before being treated as settled guidance. It does not cover synthetic identity privacy, generator labeled-ID dependence, or FID-style corpus ranking. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
