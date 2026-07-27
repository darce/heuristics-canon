# Seal the margin and size the floor from design-effect n_eff

Slug: `margin-and-design-effect-before-the-run`
Mechanism claim: A non-inferiority margin sealed after the data, or a floor sized from clustered row count instead of design-effect n_eff, both move the gate toward a false pass.

## Scope

Covers: ship and audit gates that decide non-inferiority or practical-significance floors on paired or clustered evaluation units (multiple images per subject, frames per container, faces per image), including pre-run sealing of margin, interval method class, harm direction per floor, and α allocation over K candidates.

Excludes: choice of a specific interval formula (score forms and implementation detail belong to a sibling interval card); model architecture choice; fairness cohort construction beyond naming the dominant-harm error type; convenience-sample legitimacy (owned by probability-sample rules, not this margin mechanism).

## Observable triggers

- A non-inferiority or practical-significance δ appears in the report but has no pre-run seal, or matches the observed delta after the fact.
- Sample size or power uses row count, frame count, or face count while units share a subject, video, album, or other cluster.
- The report states n and a CI as if units were independent SRS, with no psu, deff/ICC, or n_eff.
- K candidates, slices, or floors share one α with no pre-allocated split.
- Harm direction for a floor (which error type failing is worse) is missing or flipped after results are known.
- Estimand is two separate significance calls rather than a paired difference with a paired interval.

## Causal mechanism

A margin fixed after seeing the estimate is not a pre-commitment; it is a restatement of the result, so the gate cannot fail for the reason the margin was invented. Clustered draws inflate apparent n: within-cluster correlation raises design effect, so effective sample size is n/deff, not the row count. Powering or setting a floor against inflated n pretends precision the design never bought. Both errors loosen the same direction: more false passes, and the write-up still looks methodical because δ and n look numerical.

## Required action

While a non-inferiority or practical-significance gate is in play on clustered or paired units:

1. Before the run, seal in writing: margin δ (or minimum effect worth detecting), interval method class, harm direction for each floor, and α allocation across K candidates.
2. Name sampling unit vs observation unit; estimate deff (or ICC), compute n_eff = n/deff, and set the floor and power from n_eff, not raw row count.
3. State the estimand as a paired difference and analyse with a paired interval on that difference.
4. Treat a post-data margin, harm flip, or α reallocation as invalid for the gate (re-seal and re-run, or downgrade the claim).

## Predicted failure

The gate passes at a margin a correctly sized study would have failed. Failure is hard to see in the report: δ looks principled and n looks large, while both hide under-powered clustered precision and a post-hoc pass criterion.

## Exemptions and boundaries

- Pure descriptive counts with no design-based CI, no non-inferiority claim, and no ship floor: this card does not apply; still name the frame if a population rate is claimed ([AUDIT-07](../lexicons/ml-systems.md#audit-07)).
- Truly independent observation units (deff ≈ 1 verified): design-effect adjustment is vacuous; pre-seal of margin and α still applies.
- Interval *implementation* (specific score forms): sibling card; this card only requires the method class to be sealed before the run.
- Cohort tables and capture-condition strata: [FAIR-01](../lexicons/ml-systems.md#fair-01) / [FAIR-05](../lexicons/ml-systems.md#fair-05) and slice gates; this card owns pre-sealed floors and n_eff, not stratum taxonomy.
- No dedicated MEAS row owns pre-sealed margin, design-effect floors, or harm-direction declaration; do not stretch Hubbard measurement rows into this mechanism.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [EXP-12](../lexicons/epistemics.md#exp-12) pre-declare MDE / practical δ and power to it | [AUDIT-11](../lexicons/ml-systems.md#audit-11) / [EXP-23](../lexicons/epistemics.md#exp-23) n_eff may force a larger δ or more clusters | Compute n_eff first; only then seal a feasible δ and n; never shrink δ after peeking |
| object | [FAIR-04](../lexicons/ml-systems.md#fair-04) name which error type is dominant harm per floor | [EXP-10](../lexicons/epistemics.md#exp-10) pre-allocate α over K candidates / metrics | Harm type is a floor object; α split is a multiplicity budget — set both before the run, do not average them |
| surface | [EXP-22](../lexicons/epistemics.md#exp-22) selection on the outcome invalidates the test | [EXP-09](../lexicons/epistemics.md#exp-09) fixed horizon / no classical peeking | Post-hoc δ is double-dipping on the decision surface; early stopping is peeking on the time surface — both are pre-commitment failures |
| sequence | [AUDIT-09](../lexicons/ml-systems.md#audit-09) declare target e and α to size n | [EXP-12](../lexicons/epistemics.md#exp-12) declare MDE to power the experiment | Survey-style e and experiment MDE are the same pre-run contract on different estimands; both must precede draw and analysis |

## Disconfirmers

- Pre-run artifact (timestamped protocol or sealed config) shows δ, method class, harm directions, and α split unchanged after results.
- Verified deff ≈ 1 (or analysis already uses cluster-robust / hierarchical SEs with reported n_eff) and the floor was set from that n_eff.
- Independent replications at the planned n_eff fail at the same rate the power calculation predicted (no excess passes).
- Units are not clustered and the estimand is not a non-inferiority or practical-significance gate.

## Verification

- Diff or protocol review: margin, method class, harm direction per floor, and α_K appear in a pre-run revision, not only in the final report.
- Report lists psu, deff or ICC, n, and n_eff; floor or power formula inputs match n_eff.
- Primary estimand is written as a paired difference; interval is on that difference, not two one-arm p-values.
- Changing δ, harm direction, or α after unblinding is treated as a protocol breach (gate void or claim downgraded).

## Rule IDs

- [EXP-09](../lexicons/epistemics.md#exp-09): fix analysis timing before the run; no classical peek-to-pass
- [EXP-10](../lexicons/epistemics.md#exp-10): pre-register primary and allocate α across K candidates
- [EXP-12](../lexicons/epistemics.md#exp-12): pre-declare minimum effect / margin, power to it, report CI on delta
- [EXP-18](../lexicons/epistemics.md#exp-18): under-powered passes inflate δ; do not plan from winner's-curse margins
- [EXP-19](../lexicons/epistemics.md#exp-19): test or interval the paired contrast, not chained separate significance
- [EXP-22](../lexicons/epistemics.md#exp-22): post-data margin or threshold selection is circular analysis
- [EXP-23](../lexicons/epistemics.md#exp-23): N is independent replicates, not repeated measures inside clusters
- [EXP-24](../lexicons/epistemics.md#exp-24): report an interval on the effect, not a bare pass/fail p
- [AUDIT-07](../lexicons/ml-systems.md#audit-07): name target, frame, sampling unit, and observation unit before a rate or floor claim
- [AUDIT-09](../lexicons/ml-systems.md#audit-09): declare e and α to size n; do not invent n as a percent of N
- [AUDIT-11](../lexicons/ml-systems.md#audit-11): apply cluster design effect; report and use n_eff
- [FAIR-04](../lexicons/ml-systems.md#fair-04): declare dominant-harm error type per floor before the run

## Principles

- 2. Specify what would prove you wrong

## Evidence / source slugs

- [`trustworthy-controlled-experiments`](../SOURCES.md#src-trustworthy-controlled-experiments): supports [EXP-09](../lexicons/epistemics.md#exp-09), [EXP-10](../lexicons/epistemics.md#exp-10), [EXP-12](../lexicons/epistemics.md#exp-12)
- [`reinhart-statistics-done-wrong`](../SOURCES.md#src-reinhart-statistics-done-wrong): supports [EXP-18](../lexicons/epistemics.md#exp-18), [EXP-19](../lexicons/epistemics.md#exp-19), [EXP-22](../lexicons/epistemics.md#exp-22), [EXP-23](../lexicons/epistemics.md#exp-23), [EXP-24](../lexicons/epistemics.md#exp-24)
- [`lohr-sampling-design-analysis`](../SOURCES.md#src-lohr-sampling-design-analysis): supports [AUDIT-07](../lexicons/ml-systems.md#audit-07), [AUDIT-09](../lexicons/ml-systems.md#audit-09), [AUDIT-11](../lexicons/ml-systems.md#audit-11)
- [`nist-frvt-demographics`](../SOURCES.md#src-nist-frvt-demographics): supports [FAIR-04](../lexicons/ml-systems.md#fair-04)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not prescribe a named interval formula, a project-specific δ formula, or ticket-level gate numbers. It does not treat MEAS rows as owners of pre-sealed margins or design-effect floors. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
