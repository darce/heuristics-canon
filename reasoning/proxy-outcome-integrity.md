# Proxy-outcome integrity

Slug: `proxy-outcome-integrity`
Mechanism claim: A proxy that drifted from the outcome it stands for is not
evidence of that outcome; under pressure you get the number you pay for.

## Scope

Covers: KPIs, SLOs, offline model scores, coverage, composites, and scanner
greens used to gate, promote, page, or claim success; incentive design that
pays for a number instead of a user or risk outcome.

Excludes: sampling-frame / denominator ownership when the *target* is already
right (see [measurement-integrity](measurement-integrity.md)); evidence clocks before a durable commit
(see [evidence-before-commitment](evidence-before-commitment.md)); pure taste with no claimed metric.

## Observable triggers

- A dashboard, SLO, or release gate optimizes a score the team can raise
  without improving the user or risk outcome.
- Offline model metrics move while product acceptance, cohort success, or
  harm-typed error rates do not.
- Coverage, tokens-per-second, or composite UX scores stand in for change
  failure, goodput at latency, or task success.
- A green accessibility scan or unscored forecast is treated as conformance or
  accuracy.
- Comp, pricing, or SLA language pays for the proxy, not the 2am behavior you
  meant.

## Causal mechanism

A gate, page, or pay line that watches a convenient number will steer work
toward that number. Detection is a paired check: move the real outcome (or
deliberately degrade it) and see whether the proxy moves with it; if not, the
proxy is not evidence of the outcome. Action is to rename the gate to the
outcome or symptom that users or risk actually feel, run a live degrade path
before trusting offline scores, and refuse incentives that pay for the number
alone. Frame-valid meters can still fail this test when they answer the wrong
question.

## Required action

1. Name the outcome the decision must change; ship and pay only for valuable
   behavior change ([PROD-01](../lexicons/business-marketing.md#prod-01),
   [OPS-01](../lexicons/business-marketing.md#ops-01), Principle 4).
2. Prefer outcome or symptom metrics over convenient proxies; page and gate on
   what the user or risk actually feels
   ([OBS-07](../lexicons/engineering.md#obs-07),
   [UXR-03](../lexicons/interaction-ux.md#uxr-03)).
3. Simulate how the measured party will optimize the number before adopting it
   ([RSCH-07](../lexicons/epistemics.md#rsch-07)).
4. Treat offline score up / acceptance flat as proxy failure
   ([AIPX-02](../lexicons/business-marketing.md#aipx-02)); require a live
   degrade check before trusting offline gates
   ([EVAL-22](../lexicons/ml-systems.md#eval-22)).
5. Prefer stability outcomes over gameable coverage
   ([TEST-11](../lexicons/engineering.md#test-11)); score forecasts rather than
   narrative confidence ([FORE-03](../lexicons/epistemics.md#fore-03)).
6. For software quality economics: refuse cost-per-defect and coverage-as-target;
   pair multi-origin defect potential with defect-removal efficiency and escapes
   ([OPS-18](../lexicons/business-marketing.md#ops-18),
   [OPS-19](../lexicons/business-marketing.md#ops-19),
   [RLSE-14](../lexicons/engineering.md#rlse-14)).
7. Refuse scanner-green as conformance and tokens-per-second as goodput at the
   latency target ([A11Y-23](../lexicons/accessibility.md#a11y-23),
   [COST-15](../lexicons/ml-systems.md#cost-15)).
8. Measure the decision variable; composites can lie
   ([UXR-15](../lexicons/interaction-ux.md#uxr-15)).

## Predicted failure

Teams ship confidence. Model promotions win offline and lose live. Coverage
climbs while change-failure stays flat. Accessibility scanners go green while
almost no page meets the real bar. Comp plans reward the wrong 2am behavior.

## Exemptions and boundaries

- Temporary proxies are allowed if labeled as unvalidated and scheduled for a
  degrade-and-check against the product metric
  ([EVAL-22](../lexicons/ml-systems.md#eval-22)).
- Frame, sample, and denominator integrity (shaped apparatus with the *right*
  target) is owned by [measurement-integrity](measurement-integrity.md) (Principle 15).
- Expert judgment under high validity and fast feedback may outrank a weak
  meter for operational micro-decisions; it does not license a public numeric
  claim that the proxy is the outcome.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [OPS-01](../lexicons/business-marketing.md#ops-01) / [RSCH-07](../lexicons/epistemics.md#rsch-07) (you get the behavior the metric pays for) | [PROD-01](../lexicons/business-marketing.md#prod-01) (ship outcome change) | Gaming applies to incentive-linked meters; still name the outcome the proxy pretends to stand for |
| surface | [TEST-11](../lexicons/engineering.md#test-11) (coverage is gameable) | [OBS-07](../lexicons/engineering.md#obs-07) (page on symptoms) | Different proxies; same cut: outcome over convenient number |

## Disconfirmers

- A deliberate degrade of the system moves the product or harm metric in the
  predicted direction while the proxy stays flat (proxy is wrong).
- Changing the incentive away from the proxy improves the real outcome without
  the proxy's cooperation (proxy was load-bearing for behavior, not truth).
- Live cohort success tracks the offline score within stated error after a
  degrade check (proxy still aligned).

## Verification

- For each gate metric: which user, risk, or money outcome it is allowed to
  stand for, and who can re-point that mapping.
- Offline model or eval gate has a documented live degrade path
  ([EVAL-22](../lexicons/ml-systems.md#eval-22)).
- Comp / SLA / page policy names the 2am behavior paid for
  ([OPS-01](../lexicons/business-marketing.md#ops-01)).
- Composites decompose to the decision variable
  ([UXR-03](../lexicons/interaction-ux.md#uxr-03)).

## Rule IDs

- [OPS-01](../lexicons/business-marketing.md#ops-01): incentives pay for the 2am behavior
- [PROD-01](../lexicons/business-marketing.md#prod-01): ship outcome, not output theater
- [RSCH-07](../lexicons/epistemics.md#rsch-07): simulate how the measured party optimizes the number
- [OBS-07](../lexicons/engineering.md#obs-07): page on symptoms, not cause proxies
- [TEST-11](../lexicons/engineering.md#test-11): coverage is gameable; prefer stability outcomes
- [OPS-18](../lexicons/business-marketing.md#ops-18): ban cost-per-defect as quality proof
- [OPS-19](../lexicons/business-marketing.md#ops-19): defect potential + DRE pair
- [RLSE-14](../lexicons/engineering.md#rlse-14): DRE and escapes over coverage targets
- [TEAM-12](../lexicons/engineering.md#team-12): name the decision a metric changes before collecting it
- [AIPX-02](../lexicons/business-marketing.md#aipx-02): offline score up, acceptance flat
- [EVAL-22](../lexicons/ml-systems.md#eval-22): offline gate needs a live degrade check
- [UXR-03](../lexicons/interaction-ux.md#uxr-03) / [UXR-15](../lexicons/interaction-ux.md#uxr-15): measure the decision variable; composites can lie
- [FORE-03](../lexicons/epistemics.md#fore-03): score forecasts; unscored accuracy is theater
- [A11Y-23](../lexicons/accessibility.md#a11y-23): scanner-green is not conformance
- [COST-15](../lexicons/ml-systems.md#cost-15): tokens-per-second is not goodput at latency

## Principles

- 4. You get the number you pay for, not the outcome you want

## Evidence / source slugs

- [`poor-charlies-almanack`](../SOURCES.md#src-poor-charlies-almanack): supports [OPS-01](../lexicons/business-marketing.md#ops-01)
- [`lean-ux`](../SOURCES.md#src-lean-ux): supports [PROD-01](../lexicons/business-marketing.md#prod-01)
- [`hamming-art-of-doing-science`](../SOURCES.md#src-hamming-art-of-doing-science): supports [RSCH-07](../lexicons/epistemics.md#rsch-07)
- [`observability-engineering`](../SOURCES.md#src-observability-engineering): supports [OBS-07](../lexicons/engineering.md#obs-07)
- [`modern-software-engineering`](../SOURCES.md#src-modern-software-engineering): supports [TEST-11](../lexicons/engineering.md#test-11)
- [`software-development-patterns-antipatterns`](../SOURCES.md#src-software-development-patterns-antipatterns): supports [OPS-18](../lexicons/business-marketing.md#ops-18), [OPS-19](../lexicons/business-marketing.md#ops-19), [RLSE-14](../lexicons/engineering.md#rlse-14)
- [`antipatterns-laplante-neill`](../SOURCES.md#src-antipatterns-laplante-neill): supports [TEAM-12](../lexicons/engineering.md#team-12)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-02](../lexicons/business-marketing.md#aipx-02)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [EVAL-22](../lexicons/ml-systems.md#eval-22)
- [`measuring-the-ux-albert-tullis`](../SOURCES.md#src-measuring-the-ux-albert-tullis): supports [UXR-03](../lexicons/interaction-ux.md#uxr-03), [UXR-15](../lexicons/interaction-ux.md#uxr-15)
- [`superforecasting`](../SOURCES.md#src-superforecasting): supports [FORE-03](../lexicons/epistemics.md#fore-03)
- [`webaim-million`](../SOURCES.md#src-webaim-million): supports [A11Y-23](../lexicons/accessibility.md#a11y-23)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [COST-15](../lexicons/ml-systems.md#cost-15)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every important idea about incentives or evaluation. Open the rule rows
for triggers and tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry,
not a substitute for the original works.
