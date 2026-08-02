# Reversible commitments

Slug: `reversible-commitments`
ID: `CARD-15`
Mechanism claim: Prefer the cheap reversible option while the irreversible path
is underpriced; write the soft side and the rollback before freeze.

## Scope

Covers: ship and rollback plans; claim language and early a11y cost; isolation
and idempotency choices; fear-setting before freezing a reversible decision.

Excludes: second exits from external landlords and cut vertices (see
[second-exit-hostile-landlord](second-exit-hostile-landlord.md)); standing privilege and dual control (see
[least-privilege-blast-radius](least-privilege-blast-radius.md), [dual-control-two-keys](dual-control-two-keys.md)); correction at source
(see [correction-at-source](correction-at-source.md)); step size after the gate (see
[step-size-by-feedback](step-size-by-feedback.md)); evidence clocks before durable commit (see
[evidence-before-commitment](evidence-before-commitment.md)).

## Observable triggers

- A plan freezes a reversible decision out of vague dread, or ships with no
  rollback section.
- Weaker isolation, non-idempotent retries, or check-then-act under snapshot
  isolation is chosen because it "looks free" at write time.
- Claim language, accessibility deferral, or cutover plan prices the soft side
  as expensive and the hard side as free.

## Causal mechanism

Irreversibility is a price curve, not a mood. At decision time the soft verb,
request ID, or phased cutover costs a little; crossing the line costs a
rewrite, a data-integrity incident, or a regulator later. People systematically
underprice the irreversible side because the bill arrives later and elsewhere.
Keeping a second platform or dependency exit is a different decision: external
control points, not the price of this choice.

## Required action

1. When options differ in reversibility, take the reversible side unless a
   written exemption says otherwise (Principle 3). Write rollback *before*
   ship, including data written by the new build
   ([RLSE-08](../lexicons/engineering.md#rlse-08)).
2. Prefer safe claim language and early reversible accessibility cost over
   late rewrite ([CLM-02](../lexicons/business-marketing.md#clm-02),
   [A11Y-25](../lexicons/accessibility.md#a11y-25)).
3. Name worst cases and repair paths before freezing a reversible decision
   ([STRAT-14](../lexicons/business-marketing.md#strat-14)); do not freeze by
   dread alone.
4. Record real isolation behavior; test invariants before defaulting to weak
   isolation ([DATA-17](../lexicons/engineering.md#data-17),
   [DATA-18](../lexicons/engineering.md#data-18)). Make writes idempotent
   end-to-end ([DATA-13](../lexicons/engineering.md#data-13),
   [API-02](../lexicons/engineering.md#api-02)).

## Predicted failure

Aggressive claims and deferred a11y create outsized exposure. Weak isolation
commits silent integrity loss. Retries double-apply. At 2am there is no
rollback plan, only invention.

## Worked example

A migration plan rewrites a production table in place with no rollback section because the forward SQL "looks simple." The trigger is freezing a hard path while a dual-write was available. Dual-write to the new shape, cut reads with a flag, keep reverse path until soak. Without reversibility, a bad night leaves invent-a-restore as the only plan.

## Exemptions and boundaries

- Truly irreversible legal or physical acts still need dual control and
  evidence before commit; raise the gate via [dual-control-two-keys](dual-control-two-keys.md) and
  [evidence-before-commitment](evidence-before-commitment.md).
- Privilege sizing is owned by [least-privilege-blast-radius](least-privilege-blast-radius.md) (Principle 14);
  two-key completion by [dual-control-two-keys](dual-control-two-keys.md) (Principle 17); plain pointer
  only.
- Multi-home, adapters, cut vertices, and hostile-landlord exits are owned by
  [second-exit-hostile-landlord](second-exit-hostile-landlord.md) (Principle 8); plain pointer only.
- "We can fix it after launch" is not an exemption; it is usually the
  expensive answer this card refuses.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [RLSE-08](../lexicons/engineering.md#rlse-08) rollback written before ship | hard cutovers when the product requires a single moment | keep claim language and data-path rollback on the safe side even if the calendar shows one date ([CLM-02](../lexicons/business-marketing.md#clm-02)) |
| surface | [DATA-18](../lexicons/engineering.md#data-18) concurrency integrity under weak isolation | [DATA-13](../lexicons/engineering.md#data-13) / [API-02](../lexicons/engineering.md#api-02) end-to-end idempotency | same underpriced-irreversible trade on isolation vs retry surfaces |

## Disconfirmers

- Rollback was executed in rehearsal and restored both code and data path.
- Isolation anomaly tests fail closed before production defaults weaken.
- Safe claim language was chosen and conversion loss stayed within a stated
  bound (reversible side was not free-riding).

## Verification

- Rollback section answers: can the old build read new data?
- Request IDs and idempotency keys on every retried side effect.
- Claim and a11y plans show the cheap reversible side was taken unless
  exempted in writing.

## Rule IDs

- [CLM-02](../lexicons/business-marketing.md#clm-02): safe claim language is underpriced insurance
- [A11Y-25](../lexicons/accessibility.md#a11y-25): early reversible a11y cost vs late rewrite
- [RLSE-08](../lexicons/engineering.md#rlse-08): rollback written before ship
- [STRAT-14](../lexicons/business-marketing.md#strat-14): fear-setting before reversible freezes
- [DATA-17](../lexicons/engineering.md#data-17) / [DATA-18](../lexicons/engineering.md#data-18): isolation names vs real anomalies; check-then-act gap
- [DATA-13](../lexicons/engineering.md#data-13) / [API-02](../lexicons/engineering.md#api-02): end-to-end idempotency

## Principles

- 3. The safe side is cheap; the wrong side is not

## Evidence / source slugs

- [`bootstrap`](../SOURCES.md#src-bootstrap): supports [CLM-02](../lexicons/business-marketing.md#clm-02), [A11Y-25](../lexicons/accessibility.md#a11y-25)
- [`four-hour-workweek`](../SOURCES.md#src-four-hour-workweek): supports [STRAT-14](../lexicons/business-marketing.md#strat-14)
- [`designing-data-intensive-applications`](../SOURCES.md#src-designing-data-intensive-applications): supports [DATA-17](../lexicons/engineering.md#data-17), [DATA-18](../lexicons/engineering.md#data-18), [DATA-13](../lexicons/engineering.md#data-13), [RLSE-08](../lexicons/engineering.md#rlse-08)
- [`restful-web-api-patterns`](../SOURCES.md#src-restful-web-api-patterns): supports [API-02](../lexicons/engineering.md#api-02)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to catalogue every irreversibility pattern. Open the rule rows for triggers and
tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not a substitute
for the original works.
