# Step size by feedback

Slug: `step-size-by-feedback`
Mechanism claim: Keep each plan and rollout increment inside what a real
feedback signal can catch before the next commitment.

## Scope

Covers: plan and design step size relative to near feedback; cheapest
falsifying artifact first; shadow/canary then cutover; phased exposure with
pre-named stops; learning-loop windows where delayed labels or self-generated
serving diet set how far the next step may go.

Excludes: pre-commit evidence clocks for a single durable gate (see
`evidence-before-commitment`); pure timeouts and queue bounds (see
`feedback-bounded-waiting`); fail-loudly channel design (see
`fail-loudly-succeed-quietly`); pure privilege sizing (see
`least-privilege-blast-radius`); correction reaching source of truth (see
`correction-at-source`) except where a "fix" is only a temporary patch sized
to the next feedback check.

## Observable triggers

- A plan's next increment is larger than any near feedback channel can observe.
- Rollout jumps 0→100% without named stop criteria.
- Shadow or canary is skipped before cutover.
- Negatives are recorded after a fixed window while true positives still arrive
  later; the model trains on its own served diet without priced exploration.

## Causal mechanism

A plan or rollout step is a bet about the world. Independent signal arrives
only after some exposure and some delay. When the bet is larger than that
horizon, failure shows up only after full commitment. Delayed labels and
self-served training diets shrink the horizon further: close the window before
truth arrives, and the next step optimizes yesterday's policy, not the world.

## Required action

1. Keep step size inside what feedback can catch: small replaceable steps
   ([REF-28](../lexicons/engineering.md#ref-28), Principle 19).
2. Ship the cheapest artifact that can falsify the riskiest assumption first
   ([PROD-03](../lexicons/business-marketing.md#prod-03)).
3. Shadow, then canary, then cutover; phase exposure with pre-named stops
   ([AIPX-06](../lexicons/business-marketing.md#aipx-06),
   [RLSE-07](../lexicons/engineering.md#rlse-07)).
4. Window delayed labels to the real feedback lag; price exploration when
   serving shapes future training ([MLDATA-05](../lexicons/ml-systems.md#mldata-05),
   [COST-14](../lexicons/ml-systems.md#cost-14)).

## Predicted failure

Large releases discover failure only after full exposure. Plans commit months
of work before any independent check. Models learn their own recommendations
and mark late converters as permanent negatives.

## Exemptions and boundaries

- Single-moment launches may still be required for coordination; bound the
  *risk radius* and keep stop criteria even if the calendar shows one date.
- Evidence before the first durable freeze is owned by
  `evidence-before-commitment` (Principle 13); named disconfirmers as posture
  by `falsification-disconfirmers` (Principle 2); this card owns increments
  after that gate.
- Client timeouts and pool bounds are owned by `feedback-bounded-waiting`;
  plain pointer only.
- Channel design for success/failure signals is owned by
  `fail-loudly-succeed-quietly` (Principle 16); plain pointer only.
- Labels that must reach the next train as *source correction* are owned by
  `correction-at-source` ([HITL-01](../lexicons/ml-systems.md#hitl-01)); this
  card owns how large a step you take before delayed truth can arrive.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [REF-28](../lexicons/engineering.md#ref-28) / [RLSE-07](../lexicons/engineering.md#rlse-07) small steps and phased exposure | single-moment launches when coordination demands it | bound the *risk radius* even if the calendar shows one date; stop criteria still required |
| sequence | [MLDATA-05](../lexicons/ml-systems.md#mldata-05) wait long enough for delayed truth | step-size pressure to close the window early | close the loop, but do not cut the label window shorter than the feedback process |
| sequence | [HITL-01](../lexicons/ml-systems.md#hitl-01) labels into next train (owned by `correction-at-source`) | [MLDATA-05](../lexicons/ml-systems.md#mldata-05) wait for delayed truth | route corrections to source; size the training step to the lag |

## Disconfirmers

- A canary stop criterion fires in rehearsal on synthetic degradation.
- Post-window label audit shows residual positives below an accepted bound.
- A larger single step outperforms phased exposure under the same stop metrics
  (step-size rule was over-applied for that class of change).

## Verification

- Rollout plan names metric, window, and pause rule before traffic moves.
- Plan increments name the independent feedback that would kill the next step.
- Label policy documents feedback-loop length and exploration budget.

## Rule IDs

- [REF-28](../lexicons/engineering.md#ref-28): do not outrun your headlights
- [PROD-03](../lexicons/business-marketing.md#prod-03): cheapest falsifying artifact first
- [AIPX-06](../lexicons/business-marketing.md#aipx-06): shadow, canary, then cutover
- [RLSE-07](../lexicons/engineering.md#rlse-07): phased rollout with stop criteria
- [MLDATA-05](../lexicons/ml-systems.md#mldata-05): window delayed feedback
- [COST-14](../lexicons/ml-systems.md#cost-14): feedback-loop economics and exploration

## Principles

- 19. Step size is bounded by the feedback that can catch it

Also load Principle 13 when the step is a durable commit, not only a size
question (see `evidence-before-commitment`). Load Principle 2 when the gap is
missing kill criteria rather than step size (see
`falsification-disconfirmers`).

## Evidence / source slugs

- [`pragmatic-programmer`](../SOURCES.md#src-pragmatic-programmer): supports [REF-28](../lexicons/engineering.md#ref-28)
- [`lean-ux`](../SOURCES.md#src-lean-ux): supports [PROD-03](../lexicons/business-marketing.md#prod-03)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-06](../lexicons/business-marketing.md#aipx-06)
- [`software-architecture-in-practice`](../SOURCES.md#src-software-architecture-in-practice): supports [RLSE-07](../lexicons/engineering.md#rlse-07)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [MLDATA-05](../lexicons/ml-systems.md#mldata-05)
- [`reliable-machine-learning`](../SOURCES.md#src-reliable-machine-learning): supports [COST-14](../lexicons/ml-systems.md#cost-14)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to cover every planning or rollout pattern. It is a decision aid over existing
rule IDs. [SOURCES.md](../SOURCES.md) is a bibliography registry, not a substitute
for the original works.
