# Hostile landlord and second exit

Slug: `second-exit-hostile-landlord`
Mechanism claim: Assume a single external control point will turn; keep a
second exit cheap enough to throw before you need it.

## Scope

Covers: multi-home of masters and rails; ownership of rights, name, and direct
contact path; renting distribution under your own label; adapters around third
parties; cut vertices and bridges whose loss partitions the system; trust
change at every external boundary.

Excludes: pricing reversible vs irreversible *choices* inside your own plan
(see `reversible-commitments`); standing privilege radius (see
`least-privilege-blast-radius`); dual-control completion (see
`dual-control-two-keys`); perceived-vs-enforced boundary lies alone (see
`perceived-enforced-boundaries`).

## Observable triggers

- A single external platform, dependency, or model provider carries revenue,
  masters, or identity with no multi-home or adapter exit.
- Rights, name, or customer contact path live only on a landlord's surface.
- An internal node or link is a bridge: its removal splits the graph, and no
  alternate path is designed.
- Distribution waits on one partner's blessing with no owned label residual.

## Causal mechanism

External control points eventually change ToS, pricing, ranking, or
availability. When masters, rails, and contact live only there, a single policy
change zeros the residual. A second exit that is too expensive to throw is not
an exit. Internal cut vertices are the same failure shape: one node or link
whose loss partitions the system. Choosing soft claim language or writing a
rollback is a different price curve, owned elsewhere.

## Required action

1. Multi-home masters and rails before you need them; own rights, name, and a
   direct contact path ([BOOT-07](../lexicons/business-marketing.md#boot-07),
   [BOOT-01](../lexicons/business-marketing.md#boot-01), Principle 8).
2. Rent distribution muscle under your own label rather than waiting on one
   platform's blessing ([GTM-04](../lexicons/business-marketing.md#gtm-04)).
3. Wrap third parties behind adapters
   ([REF-15](../lexicons/engineering.md#ref-15)).
4. Detect cut vertices; ask how many components remain if this node dies
   ([GRPH-05](../lexicons/graph-theory.md#grph-05)). Trust changes at every
   external boundary ([SEC-01](../lexicons/security.md#sec-01)).

## Predicted failure

One platform ToS change zeros the business. A dependency or model provider
outage has no alternate path. Brand and customer list vanish with the landlord.
A single bridge node fails and partitions the system.

## Exemptions and boundaries

- Temporary single-homing during discovery is allowed if the exit cost and
  deadline are written; "we will multi-home later" without a date is not an
  exit.
- Soft claim language, rollback plans, and isolation defaults are owned by
  `reversible-commitments` (Principle 3); plain pointer only.
- Shrink of standing grants is owned by `least-privilege-blast-radius`
  (Principle 14); do not load privilege sizing from this card alone.
- When the issue is a boundary users *believe* but the system does not
  *enforce*, also open `perceived-enforced-boundaries`; SEC-01 may load both.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [BOOT-07](../lexicons/business-marketing.md#boot-07) multi-home before need | [GRPH-05](../lexicons/graph-theory.md#grph-05) cut vertices | external landlord exit and internal bridge analysis are the same second-exit reflex |
| surface | [REF-15](../lexicons/engineering.md#ref-15) adapter around third parties | [GTM-04](../lexicons/business-marketing.md#gtm-04) own-label distribution | engineering wrap vs go-to-market residual; both keep a throw-able exit |

## Disconfirmers

- Removing a suspected bridge node leaves the graph connected (or multi-home
  is proven).
- A platform exit drill completes within a stated cost and time bound.
- Rights, name, and direct contact path survive a simulated landlord loss.

## Verification

- Articulation-point list for critical external and internal dependencies.
- Exit drill: restore masters and rails from the alternate path within the
  stated bound.
- Customer contact and brand assets are owned outside any single platform.

## Rule IDs

- [BOOT-07](../lexicons/business-marketing.md#boot-07): hostile landlord; second exit
- [BOOT-01](../lexicons/business-marketing.md#boot-01): own rights, name, and direct contact path
- [GTM-04](../lexicons/business-marketing.md#gtm-04): rent distribution under your own label
- [REF-15](../lexicons/engineering.md#ref-15): wrap third parties behind adapters
- [GRPH-05](../lexicons/graph-theory.md#grph-05): cut vertices and bridges
- [SEC-01](../lexicons/security.md#sec-01): trust changes at every boundary

## Principles

- 8. Assume a hostile landlord and keep a second exit

## Evidence / source slugs

- [`porn-work`](../SOURCES.md#src-porn-work): supports [BOOT-07](../lexicons/business-marketing.md#boot-07), [BOOT-01](../lexicons/business-marketing.md#boot-01)
- [`klf-the-manual`](../SOURCES.md#src-klf-the-manual): supports [GTM-04](../lexicons/business-marketing.md#gtm-04)
- [`modern-software-engineering`](../SOURCES.md#src-modern-software-engineering): supports [REF-15](../lexicons/engineering.md#ref-15)
- [`graph-theory-with-applications`](../SOURCES.md#src-graph-theory-with-applications): supports [GRPH-05](../lexicons/graph-theory.md#grph-05)
- [`llm-security-playbook`](../SOURCES.md#src-llm-security-playbook): supports [SEC-01](../lexicons/security.md#sec-01)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to catalogue every multi-home pattern. Open the rule rows for triggers and
tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not a substitute
for the original works.
