# Measurement integrity

Slug: `measurement-integrity`
Mechanism claim: A number the measured system can shape, or a proxy that drifted
from the outcome it stands for, is not evidence of that outcome.

## Scope

Covers: choosing, publishing, and gating on metrics; load and eval apparatus;
dataset filters that define a benchmark; risk scores treated as arithmetic;
claims that "we measured X" when the instrument deleted the hard cases.

Excludes: pure product-taste decisions with no claimed metric; security policy
authoring without a measurement claim (see contract-before-components);
full experimental design for online A/B (see epistemic experiment rules).

## Observable triggers

- A dashboard, SLO, or release gate optimizes a score the team can raise without
  improving the user or risk outcome.
- The sampling frame, denominator, or pass threshold is editable by the system
  under test (filters, auto-baselines, detector-harvested sets).
- A wait-then-send or completeness-assuming loader pauses when the system stalls,
  so slow cases never enter the histogram.
- Ordinal heat-map cells are multiplied or ranked as if they were ratio data.
- Offline model metrics move while product acceptance, cohort success, or
  harm-typed error rates do not.
- The plan refuses any estimate until data are "exact," or treats a green scan
  as full conformance.

## Causal mechanism

Measurement is an apparatus plus a claim. Under pressure, people and systems
optimize the apparatus: they exclude hard cells, widen the divisor, pause the
load generator, or chase a proxy that pays at 2am. The report stays green
because the observations that would falsify the claim never land. Integrity
fails at the frame and the denominator first; the formula is usually fine.

A second failure mode is honest instruments aimed at the wrong target: coverage
instead of change-failure, CPU instead of user-visible degradation, composite
UX scores while task success collapses. The meter may be ungameable and still
answer the wrong question.

## Required action

1. Name the decision the number must change; rank measurements by value of
   information for that decision ([MEAS-07]).
2. Fix the sampling frame and divisor *outside* the system under test; put an
   independent watcher on goal, sample, or threshold ([OBS-09], Principle 15).
3. Prefer outcome or symptom metrics over convenient proxies; page and gate on
   what the user or risk actually feels ([OBS-07], [AIPX-02], [UXR-03]).
4. Treat measurement as uncertainty reduction, not perfect certainty; use
   partial observations that narrow a stated range ([MEAS-02]).
5. Refuse ordinal arithmetic and colour movement as risk math ([MEAS-01],
   [MEAS-05]).
6. Before trusting a suite or eval, confirm it has been seen red on the failure
   it claims to catch ([TEST-06], [TEST-15]).

## Predicted failure

Teams ship confidence. Latency looks fine while tails burn. Benchmarks pass
because hard cases were filtered. Risk matrices invent false rankings. Model
promotions win offline and lose live. Accessibility scanners go green while
almost no page meets the real bar. The next incident postmortem discovers the
meter never could have gone red.

## Exemptions and boundaries

- Exploratory telemetry that is not used to gate, promote, or claim compliance
  may stay rough; the card fires when the number *decides*.
- Temporary proxies are allowed if labeled as unvalidated and scheduled for a
  degrade-and-check against the product metric ([EVAL-22] when model gates are
  involved).
- Regulatory or contractual metrics you did not choose still need an integrity
  audit; "required by audit" is not an exemption from a shaped sample.
- Expert judgment under high validity and fast feedback ([NDM-01]) can outrank
  a weak meter *for operational micro-decisions*; it does not license a public
  numeric claim without apparatus.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [OPS-01] / [RSCH-07] (you get the behavior the metric pays for) | [MEAS-02] (partial quantitative narrowing is still measurement) | Gaming applies to *incentive-linked* meters; VoI measurement still wants partial data on the decision quantity |
| surface | [PERF-03] / [MLDATA-09] (apparatus deletes hard cases) | [OBS-11] (absolute bar vs eroding goal) | Frame integrity vs bar integrity; both can fail independently |
| sequence | [TEST-06] (never trust a test never seen failing) | [MEAS-08] (small samples already bound a prior) | First install a falsifiable instrument; then accept small-n baselines for priors, not for greenwashed gates |

## Disconfirmers

- A deliberate degrade of the system moves the product or harm metric in the
  predicted direction while the proxy stays flat (proxy is wrong).
- Expanding the sample to include previously filtered hard cells does not move
  the score (filter was not load-bearing).
- An independent lab or held-out owner recomputes the metric and matches within
  stated error (watcher is real).
- The measured party cannot change frame, divisor, or threshold without an
  external change-control path (Principle 15 structure holds).

## Verification

- For each gate metric: who owns the frame, who can edit it, and what decision
  it is allowed to make.
- Load or eval config: open-loop arrival (or equivalent) so stalls still generate
  observations ([PERF-03]).
- Dataset card or filter list: every exclusion checked against the claim's
  covered conditions ([MLDATA-09], [MLDATA-08]).
- Denominator predefined and not emitted by the system under test ([UXR-07],
  [EVAL-19]).
- Risk report shows probability and loss units, not only ordinal products
  ([MEAS-01], [MEAS-03]).

## Rule IDs

- [PERF-03]: coordinated omission in load apparatus
- [OBS-09]: independent watcher the optimizer cannot tune
- [OBS-07]: page on symptoms, not cause proxies
- [OBS-11]: absolute standards against eroding goals
- [OPS-01]: incentives pay for the 2am behavior
- [RSCH-07]: simulate how the measured party optimizes the number
- [TEST-11]: coverage is gameable; prefer stability outcomes
- [TEST-06]: a test never seen failing may assert nothing
- [TEST-15]: add a measurement point that can go red
- [MLDATA-08]: detector-harvested sets inherit blind spots
- [MLDATA-09]: filters that remove the regime under test
- [EVAL-03]: evaluate on the real mix, not a rebalanced fantasy
- [EVAL-19]: denominator must not be system-minted
- [EVAL-22]: offline gate needs a live degrade check
- [UXR-03] / [UXR-15]: measure the decision variable; composites can lie
- [UXR-07]: predefined denominator
- [MEAS-01] / [MEAS-05]: probability and loss over ordinal risk arithmetic
- [MEAS-02]: measurement narrows uncertainty
- [MEAS-07]: measure where uncertainty is decision-expensive (VoI)
- [MEAS-08]: sparse samples still set a prior before "unknown"
- [AIPX-02]: offline score up, acceptance flat
- [A11Y-23]: scanner-green is not conformance
- [FORE-03]: score forecasts; unscored accuracy is theater
- [NDM-01]: validity and feedback gate for expert judgment

## Principles

- 4. You get the number you pay for, not the outcome you want
- 11. Unknown is a designed state (partial knowledge, not fake precision)
- 13. Evidence precedes commitment
- 15. A measurement the measured party can shape is not a measurement

## Evidence / source slugs

- `latency-reduce-delay-in-software-systems`: open-loop vs wait-then-send load
- `thinking-in-systems`: watcher and eroding-goal structure
- `observability-engineering`: symptom-first paging
- `poor-charlies-almanack`: incentive primacy
- `hamming-art-of-doing-science`: metric-induced behavior
- `modern-software-engineering`: tests and coverage as instruments
- `janus-benchmark-c` / `gender-shades`: regime deletion and harvest bias
- `designing-ml-systems`: eval mix and delayed labels (adjacent)
- `measuring-the-ux-albert-tullis`: decision variables and denominators
- `hubbard-measure-anything-cybersecurity`: uncertainty reduction and ordinal refusal
- `building-ml-powered-applications`: offline vs product acceptance
- `wcag22-accessibility`: scan vs conformance gap
- `superforecasting`: scored accuracy

Related critical note: [hubbard-measure-anything-cybersecurity](../sources/hubbard-measure-anything-cybersecurity.md).

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every important idea about statistics, UX research, or ML evaluation.
Open the rule rows for triggers and tiers. Open the source note for support
verdicts. Private distillations are not published.
