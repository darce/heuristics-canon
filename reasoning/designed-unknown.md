# Designed unknown

Slug: `designed-unknown`
ID: `CARD-03`
Mechanism claim: When evidence runs out, ship a first-class unknown or
abstention state; forced certainty is a false answer.

## Scope

Covers: calibration thresholds and decline-to-decide paths; annotation and HITL
routing; empty/error/offline UI; graded uncertainty in forecasts; precision-first
guidance; competence "too tough" baskets; partial measurement as a valid state.

Excludes: measurement frames the system can shape (see [measurement-integrity](measurement-integrity.md));
correction loops after a wrong durable label (see [correction-at-source](correction-at-source.md));
timeouts as the only bound (see [feedback-bounded-waiting](feedback-bounded-waiting.md)).

## Observable triggers

- A classifier, matcher, or agent must always emit a positive class or identity.
- Low-confidence or low-agreement items still force an automated accept.
- Empty, error, offline, or first-run screens are blank framework defaults.
- Forecasts use vague words ("likely") where the decision needs a number or an
  explicit refuse.
- Product guidance prefers a polished wrong answer over silence.
- Plans wait forever for "exact" data instead of a narrowed range.

## Causal mechanism

Systems hate holes. Databases, UIs, and models fill missing evidence with a
guess because the schema or product narrative has no place for *unknown*. That
guess becomes identity, progress, or advice. The failure is structural: without
a designed third state, every path fabricates certainty. Calibration, annotation,
release design, forecasting, and strategy literatures each invent the same exit:
decline, escalate, or report partial knowledge on purpose.

## Required action

1. Define below-threshold and insufficient-evidence outcomes as valid results
   ([CAL-02](../lexicons/ml-systems.md#cal-02), [MEAS-02](../lexicons/epistemics.md#meas-02)).
2. Route low-agreement or eval-critical items to experts; keep human override
   ([HITL-07](../lexicons/ml-systems.md#hitl-07), [HAI-04](../lexicons/interaction-ux.md#hai-04)).
3. Design empty, error, offline, and first-run as intentional screens
   ([RLSE-04](../lexicons/engineering.md#rlse-04), [NAV-08](../lexicons/interaction-ux.md#nav-08)).
4. Prefer numeric uncertainty or explicit refuse over fake crisp labels
   ([FORE-01](../lexicons/epistemics.md#fore-01), [FORE-08](../lexicons/epistemics.md#fore-08)).
5. Precision-first guidance: silence beats wrong advice
   ([AIPX-07](../lexicons/business-marketing.md#aipx-07), [AIPX-14](../lexicons/business-marketing.md#aipx-14)); strategy keeps a too-tough basket
   ([STRAT-03](../lexicons/business-marketing.md#strat-03)).
6. Stream and API twins: late-event policy before "complete"
   ([FLOW-08](../lexicons/engineering.md#flow-08); empty match is success, not missing resource
   ([API-06](../lexicons/engineering.md#api-06)).

## Predicted failure

False identities merge. Silent wrong answers pass as product. Progress bars lie.
Annotators rubber-stamp machine labels. Users trust fluent hallucination.
Teams either freeze waiting for perfect data or invent fake precision.

## Worked example

A fusion stage always emits a best-guess person_id when embedding matches fall below the calibrated threshold. The trigger is forced resolution past evidence. Ship an explicit unknown / abstain output with a reason code and block auto-merge on it. Without designed unknown, low-evidence IDs enter the graph as facts and later audits cannot tell guess from match.

## Exemptions and boundaries

- Hard real-time control loops may require a default actuator command; still
  log and surface the low-evidence state to the next human or supervisor loop.
- Binary legal outcomes may be forced by statute; still separate the system's
  confidence from the legal decision path.
- Designed unknown is not a substitute for gathering cheap evidence (Principle
  13); it is what you ship when the evidence budget is spent.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [CAL-02](../lexicons/ml-systems.md#cal-02) abstain below threshold | [MEAS-02](../lexicons/epistemics.md#meas-02) partial narrowing is still measurement | abstain on the *decision*; still measure to shrink the range |
| surface | [AIPX-07](../lexicons/business-marketing.md#aipx-07) silence over wrong advice | [GTM-08](../lexicons/business-marketing.md#gtm-08) novelty-led debut packaging | marketing may tease; guidance and identity paths stay precision-first |
| sequence | [FORE-01](../lexicons/epistemics.md#fore-01) force a number when the decision needs one | [STRAT-03](../lexicons/business-marketing.md#strat-03) too-tough refuse | number the decidable; refuse the outside-competence case |

## Disconfirmers

- Forcing a call below threshold improves user or safety outcomes under
  controlled comparison (abstention was over-tuned).
- Designed empty/error states reduce recovery success (design was wrong, not
  the need for a state).
- Coarse bins do not change any decision the fine dial would (refuse extra
  precision theater).

## Verification

- Data model and UI enums include unknown / pending / abstain where identity or
  advice is emitted.
- Threshold policy names the action below the line (escalate, defer, silent).
- Forecast template requires number *or* explicit refuse with reason.
- Guidance product metrics track wrongful-advice rate, not only coverage.

## Rule IDs

- [CAL-02](../lexicons/ml-systems.md#cal-02): below-threshold action is a valid result
- [EMB-04](../lexicons/ml-systems.md#emb-04): de-emphasize identity-void inputs in training pressure
- [HITL-07](../lexicons/ml-systems.md#hitl-07): expert path for low agreement
- [HAI-04](../lexicons/interaction-ux.md#hai-04): human override when automation intent is unmet
- [RLSE-04](../lexicons/engineering.md#rlse-04): designed empty/error/offline states
- [NAV-08](../lexicons/interaction-ux.md#nav-08): first-run and dead-end as entry points
- [FORE-01](../lexicons/epistemics.md#fore-01) / [FORE-08](../lexicons/epistemics.md#fore-08): numeric uncertainty; refuse coarse fake precision when odds matter
- [WRIT-43](../lexicons/writing.md#writ-43): single weak cue is not an authorship verdict
- [FLOW-08](../lexicons/engineering.md#flow-08): late-event policy before complete windows
- [API-06](../lexicons/engineering.md#api-06): empty search is 200, not 404
- [AIPX-07](../lexicons/business-marketing.md#aipx-07) / [AIPX-14](../lexicons/business-marketing.md#aipx-14): silence and confidence gates
- [STRAT-03](../lexicons/business-marketing.md#strat-03): too-tough basket
- [MEAS-02](../lexicons/epistemics.md#meas-02): partial knowledge narrows range

## Principles

- 11. Unknown is a designed state

Also load Principle 13 when abstention would block a durable commit that still
needs evidence.

## Evidence / source slugs

- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [CAL-02](../lexicons/ml-systems.md#cal-02)
- [`adaface`](../SOURCES.md#src-adaface): supports [EMB-04](../lexicons/ml-systems.md#emb-04)
- [`human-in-the-loop-ml`](../SOURCES.md#src-human-in-the-loop-ml): supports [HITL-07](../lexicons/ml-systems.md#hitl-07)
- [`human-centered-ai`](../SOURCES.md#src-human-centered-ai): supports [HAI-04](../lexicons/interaction-ux.md#hai-04)
- [`bootstrap`](../SOURCES.md#src-bootstrap): supports [RLSE-04](../lexicons/engineering.md#rlse-04)
- [`designing-interfaces`](../SOURCES.md#src-designing-interfaces): supports [NAV-08](../lexicons/interaction-ux.md#nav-08)
- [`superforecasting`](../SOURCES.md#src-superforecasting): supports [FORE-01](../lexicons/epistemics.md#fore-01), [FORE-08](../lexicons/epistemics.md#fore-08)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-43](../lexicons/writing.md#writ-43)
- [`designing-data-intensive-applications`](../SOURCES.md#src-designing-data-intensive-applications): supports [FLOW-08](../lexicons/engineering.md#flow-08)
- [`restful-web-api-patterns`](../SOURCES.md#src-restful-web-api-patterns): supports [API-06](../lexicons/engineering.md#api-06)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-07](../lexicons/business-marketing.md#aipx-07), [AIPX-14](../lexicons/business-marketing.md#aipx-14)
- [`poor-charlies-almanack`](../SOURCES.md#src-poor-charlies-almanack): supports [STRAT-03](../lexicons/business-marketing.md#strat-03)
- [`hubbard-measure-anything-cybersecurity`](../SOURCES.md#src-hubbard-measure-anything-cybersecurity): supports [MEAS-02](../lexicons/epistemics.md#meas-02)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every calibration or UX-empty-state pattern. Open the rule rows for
triggers and tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not
a substitute for the original works.
