# Aggregate retention is not the adoption metric

Slug: `quantization-delta-on-the-failure-metric`
ID: `CARD-28`
Mechanism claim: An aggregate retention figure for a quantized or reduced-precision model is not evidence about the metric that ranks it; gate the change on the stratified delta of the failure mode that decides adoption.

## Scope

Covers: ship / no-ship and parity decisions for behaviour-changing serving optimizations (quantization, reduced precision, dtype or provider swaps, and similar numerical or sampling changes) when a headline “retained X% of overall score” is offered as proof of quality.
Excludes: training-time architecture search, pure cost or latency sizing with no quality claim, fairness audits that are not attached to a serving-optimization delta, and continuous-retrain go/no-go without a precision change.

## Observable triggers

- A review or card cites only overall accuracy, MMLU-style totals, or “95% retention” after quantization or bit reduction.
- The adoption-critical failure mode (factual error rate, calibration of *p* as a rate, worst-cohort FMR/FNMR, task regression) is unreported or reported only for the full-precision baseline.
- A cheaper tier is promoted under [COST-07](../lexicons/ml-systems.md#cost-07) with a quality floor stated only as an aggregate parity percentage.
- Slice or task deltas are missing while the change is known to alter numerics or sampling ([SERVE-07](../lexicons/ml-systems.md#serve-07)).
- Readiness or release is scored as one total that averages categories or tasks ([EVAL-23](../lexicons/ml-systems.md#eval-23)).

## Causal mechanism

Quantization and related serving optimizations change numerical behaviour. Easy majority cases often stay green, so the aggregate score barely moves. The loss concentrates on harder strata and on the failure mode that actually decides whether the product can ship (factual misses, miscalibrated probabilities, worst-cohort operating errors). Reporting aggregate retention answers a substituted question—how much of the average score remained—while the decision needs the delta on the named failure metric, sliced. Without that delta, a locally cheap model is adopted on a number that cannot see the adoption-critical break.

## Required action

1. Name the single failure metric (or fixed constrained set) that decides adoption for this product surface ([EXP-03](../lexicons/epistemics.md#exp-03)); do not let aggregate retention stand in for it ([BIAS-02](../lexicons/epistemics.md#bias-02)).
2. Before promoting the optimized artifact, run a task-plus-regression gate on the behaviour-changing change ([SERVE-07](../lexicons/ml-systems.md#serve-07)).
3. Report full-precision vs optimized deltas on that failure metric, not only on the aggregate, and floor critical slices so Simpson flips cannot clear the change ([EVAL-08](../lexicons/ml-systems.md#eval-08), [EVAL-04](../lexicons/ml-systems.md#eval-04)).
4. When human-facing error types matter, publish disaggregated operating errors and gate on the worst cohort or condition, not the mean ([FAIR-01](../lexicons/ml-systems.md#fair-01)).
5. When predicted probabilities are consumed as rates, re-check reliability after the precision change ([CAL-03](../lexicons/ml-systems.md#cal-03)).
6. Treat aggregate retention as a surrogate only under an explicit link to the adoption metric and hard constraints that block “green average, broken failure mode” ([EXP-04](../lexicons/epistemics.md#exp-04)); report practical significance of the delta, not a bare retained percentage ([EXP-12](../lexicons/epistemics.md#exp-12)).
7. If the offline failure metric itself is unvalidated against product outcomes, degrade deliberately and check direction before it may gate release ([EVAL-22](../lexicons/ml-systems.md#eval-22)).

## Predicted failure

A quantized model that retains most of its aggregate score while losing most of its factual calibration (or other adoption-critical failure mode) is adopted on the aggregate. Users and reviewers see a reassuring retention figure; the product ships the cheaper path; the failure that should have blocked promotion is invisible until production.

## Worked example

Product wants INT8 to cut GPU cost. The release note celebrates ninety-seven percent MMLU retention. The shopping task that decides ship is price-citation error, and that number exists only for the full-precision build. Hold the promote until full-precision versus INT8 price-error is on the same sheet. Otherwise the cheaper build ships and wrong prices climb without a gate that can see them.

## Exemptions and boundaries

- Does not apply when the optimization is proven distributionally exact and equivalence is tested as an implementation property, not a quality trade ([SERVE-07](../lexicons/ml-systems.md#serve-07)).
- Pure capacity or KV-cache budgeting without a quality claim is out of scope.
- Protected-cohort fairness without a serving-optimization delta is owned by the FAIR rows; this card only requires disaggregation when that is the adoption-critical surface for the change.
- Product-metric sovereignty and live A/B design beyond the offline stratified delta are adjacent, not owned here.
- Still applies whenever a retention percentage is used to clear a numerical or sampling change, even if another card covers cost tiers or continuous push.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [COST-07](../lexicons/ml-systems.md#cost-07) route easy traffic to a cheaper quantized tier | [SERVE-07](../lexicons/ml-systems.md#serve-07) [EVAL-08](../lexicons/ml-systems.md#eval-08) quality-gate and slice the change before promotion | Measure the failure-metric quality floor on the cheap path first; only then route |
| object | Aggregate speed/cost win on easy majority traffic | [EVAL-04](../lexicons/ml-systems.md#eval-04) [FAIR-01](../lexicons/ml-systems.md#fair-01) floors on critical slices and worst cohort | Cost savings may use the majority; the gate is the stratified failure delta |
| surface | [EXP-03](../lexicons/epistemics.md#exp-03) one OEC ranks the ship decision | [EVAL-04](../lexicons/ml-systems.md#eval-04) [EVAL-23](../lexicons/ml-systems.md#eval-23) multi-slice and weakest-category floors | OEC ranks among candidates that already clear hard slice/category floors |
| metric role | Offline aggregate as a cheap dashboard number | [EXP-04](../lexicons/epistemics.md#exp-04) [EVAL-22](../lexicons/ml-systems.md#eval-22) surrogate only with goal link, constraints, and proven product movement | Dashboard may show retention; adoption may not |

## Disconfirmers

- On this product, the adoption-critical failure metric moves in lockstep with the aggregate across repeated precision changes (no hidden concentration of loss).
- Task-plus-regression and slice floors pass with non-trivial power, and a known-worse quantized artifact moves the product metric as predicted ([EVAL-22](../lexicons/ml-systems.md#eval-22), [EXP-12](../lexicons/epistemics.md#exp-12)).
- Probabilities are never consumed as rates, and no cohort or task slice is decision-relevant—so aggregate parity is the true OEC by explicit declaration, not by default.

## Verification

- Ship review names the adoption failure metric and shows full-precision vs optimized deltas with intervals or practical thresholds ([EXP-03](../lexicons/epistemics.md#exp-03), [EXP-12](../lexicons/epistemics.md#exp-12)).
- Critical slices (and worst cohort when applicable) are tabled; none is green only because the mean is green ([EVAL-04](../lexicons/ml-systems.md#eval-04), [FAIR-01](../lexicons/ml-systems.md#fair-01)).
- SERVE optimization checklist includes task+regression (or exact-equivalence) for this artifact ([SERVE-07](../lexicons/ml-systems.md#serve-07)).
- If *p* is a rate, a post-quantization reliability check is attached ([CAL-03](../lexicons/ml-systems.md#cal-03)).
- No release note uses “X% retained” as the sole quality claim for the change.

## Rule IDs

- [SERVE-07](../lexicons/ml-systems.md#serve-07): quality-gate any quantization or other behaviour-changing serving optimization before promote
- [EVAL-08](../lexicons/ml-systems.md#eval-08): require slice and system prediction deltas on the change (CACE)
- [EVAL-04](../lexicons/ml-systems.md#eval-04): floor and report critical slices; refuse aggregate-only clearance
- [EXP-03](../lexicons/epistemics.md#exp-03): pre-declare the metric that decides adoption
- [BIAS-02](../lexicons/epistemics.md#bias-02): ban substituting aggregate retention for that metric
- [EXP-04](../lexicons/epistemics.md#exp-04): treat aggregate retention as a constrained surrogate, not the goal
- [EXP-12](../lexicons/epistemics.md#exp-12): report practical significance of the failure-metric delta
- [EVAL-22](../lexicons/ml-systems.md#eval-22): validate offline proxies by known degradation before they gate release
- [EVAL-23](../lexicons/ml-systems.md#eval-23): refuse readiness or quality totals that average away a weak category
- [FAIR-01](../lexicons/ml-systems.md#fair-01): disaggregate operating errors and gate on the worst cohort when harm is group-shaped
- [CAL-03](../lexicons/ml-systems.md#cal-03): re-check reliability when probabilities are used as rates after precision change
- [COST-07](../lexicons/ml-systems.md#cost-07): cheap-tier quality floor must be the stratified failure metric, not aggregate retention
- [RSCH-07](../lexicons/epistemics.md#rsch-07): installing retention as the KPI will optimize retention, not the failure mode
- [EVAL-01](../lexicons/ml-systems.md#eval-01): interpret optimized scores only as deltas against fixed baselines

## Principles

- 4. You get the number you pay for, not the outcome you want
- 13. Evidence precedes commitment

## Evidence / source slugs

- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [SERVE-07](../lexicons/ml-systems.md#serve-07)
- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [EVAL-08](../lexicons/ml-systems.md#eval-08)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [EVAL-01](../lexicons/ml-systems.md#eval-01), [EVAL-04](../lexicons/ml-systems.md#eval-04), [CAL-03](../lexicons/ml-systems.md#cal-03)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [EVAL-22](../lexicons/ml-systems.md#eval-22), [EVAL-23](../lexicons/ml-systems.md#eval-23)
- [`kahneman-thinking-fast-slow`](../SOURCES.md#src-kahneman-thinking-fast-slow): supports [BIAS-02](../lexicons/epistemics.md#bias-02)
- [`trustworthy-controlled-experiments`](../SOURCES.md#src-trustworthy-controlled-experiments): supports [EXP-03](../lexicons/epistemics.md#exp-03), [EXP-04](../lexicons/epistemics.md#exp-04), [EXP-12](../lexicons/epistemics.md#exp-12)
- [`gender-shades`](../SOURCES.md#src-gender-shades): supports [FAIR-01](../lexicons/ml-systems.md#fair-01)
- [`reliable-machine-learning`](../SOURCES.md#src-reliable-machine-learning): supports [COST-07](../lexicons/ml-systems.md#cost-07)
- [`hamming-art-of-doing-science`](../SOURCES.md#src-hamming-art-of-doing-science): supports [RSCH-07](../lexicons/epistemics.md#rsch-07)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not prescribe a bit width, a calibration algorithm, or a universal retention threshold. It does not own live experiment design beyond requiring a named adoption metric and stratified deltas, nor does it replace full fairness, continuous-ML, or capacity cards. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
