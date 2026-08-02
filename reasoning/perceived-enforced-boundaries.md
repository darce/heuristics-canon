# Perceived and enforced boundaries

Slug: `perceived-enforced-boundaries`
ID: `CARD-12`
Mechanism claim: A grouping the surface implies but the system does not enforce
is a lie the user (or operator) believes.

## Scope

Covers: Gestalt and layout groups vs real structure; IA labels and homes;
authorization scopes, object auth, RLS, and complete mediation; cluster or
similarity membership; automation envelopes named beyond test; org splits vs
software splits; policy text vs implementation; click affordances that match
reality.

Excludes: contract-before-components gatekeeper specs (see
[contract-before-components](contract-before-components.md)); least-privilege radius and dual control (see
[least-privilege-blast-radius](least-privilege-blast-radius.md), [dual-control-two-keys](dual-control-two-keys.md)); pure measurement
frames (see [measurement-integrity](measurement-integrity.md)).

## Observable triggers

- Visual grouping, DOM, or IA implies one entity while navigation, focus order,
  or data model places it in two homes, or none.
- Similarity chaining or cluster labels assert an entity the data never
  enforced.
- UI or docs promise a privacy, tenancy, or autonomy boundary the auth path,
  RLS policy, or tested envelope does not hold.
- A software module split is not a team communication boundary (or the reverse).
- Object access relies on obscurity of IDs; multi-tenant rows lack row-level
  enforcement; a property is left to "everyone will be careful."
- A control looks clickable (or safe) when the action is unavailable, destructive,
  or out of scope.

## Causal mechanism

People read boundaries first, with the eye, the org chart, the policy page, or
the cluster label, and act as if the machine honours the same cut. When
enforcement is weaker, elsewhere, or absent, every downstream decision is made
on a false map. The failure is the same in UI, tenancy, architecture, and
claims: perceived boundary ≠ enforced boundary.

## Required action

1. Audit implied layout and interaction groups against real structure and focus
   order ([PERC-03](../lexicons/interaction-ux.md#perc-03),
   [INT-01](../lexicons/interaction-ux.md#int-01)).
2. Keep IA labels MECE: one home per thing
   ([NAV-05](../lexicons/interaction-ux.md#nav-05)).
3. Refuse similarity or cluster membership as identity without an enforced
   entity boundary ([GRPH-18](../lexicons/graph-theory.md#grph-18)).
4. Re-evaluate trust at every crossing; grant only what the named boundary
   needs ([SEC-01](../lexicons/security.md#sec-01)).
5. Enforce object auth, RLS, and complete mediation on each use, not only at
   the front door ([WEB-08](../lexicons/security.md#web-08),
   [PG-02](../lexicons/security.md#pg-02),
   [SECD-03](../lexicons/security.md#secd-03)).
6. Name automation only inside the tested envelope
   ([HAI-05](../lexicons/interaction-ux.md#hai-05)); label synthetic content that
   could pass as human ([AIPX-13](../lexicons/business-marketing.md#aipx-13)).
7. Align privacy and policy text with implementation
   ([CLM-03](../lexicons/business-marketing.md#clm-03)).
8. Make a software split a team split first
   ([TEAM-01](../lexicons/engineering.md#team-01)); hoist must-hold properties
   into structure so violation fails closed
   ([ARCH-13](../lexicons/engineering.md#arch-13)).

## Predicted failure

Users click a "group" that is only pixels. Tenants read each other's rows via
IDOR. Policy promises privacy the product does not implement. Org charts and
service boundaries diverge until every change is a cross-team negotiation.
Autonomy marketing outruns the tested envelope and causes harm.

## Worked example

Settings shows Work and Private as two tabs. Draft notes still share one ACL table, so a coworker who guesses a note ID opens a private draft. Bind separate principals in the API, or drop the Private tab so the surface stops promising a wall that is not there. People currently treat the tab edge as security and paste secrets into the wrong side.

## Exemptions and boundaries

- Exploratory sketches may imply structure before enforcement exists if labeled
  as non-normative; the card fires when the boundary is presented as real.
- Privilege *radius* remains [least-privilege-blast-radius](least-privilege-blast-radius.md); two-key completion
  remains [dual-control-two-keys](dual-control-two-keys.md); this card asks whether the boundary users
  perceive is the one mediation enforces.
- Gatekeeper *contracts* before shipping are
  [contract-before-components](contract-before-components.md); this card is the match between perceived and
  enforced cuts after a boundary is claimed.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | [PERC-03](../lexicons/interaction-ux.md#perc-03) / [INT-01](../lexicons/interaction-ux.md#int-01) visual and click affordances | [WEB-08](../lexicons/security.md#web-08) / [PG-02](../lexicons/security.md#pg-02) object auth and RLS | same audit: perceived cut vs machine cut, UI vs data plane |
| object | [TEAM-01](../lexicons/engineering.md#team-01) team split first | [ARCH-13](../lexicons/engineering.md#arch-13) structure enforces the property | org boundary and structural hoist are both enforcement; neither is a diagram alone |
| sequence | [CLM-03](../lexicons/business-marketing.md#clm-03) policy matches implementation | [SECD-03](../lexicons/security.md#secd-03) complete mediation on each use | write the true boundary, then re-check it on every use |

## Disconfirmers

- A user or red-team test treats the implied boundary as real and cannot cross
  it without an authorized path.
- Removing a visual or IA group does not change task success (group was not
  load-bearing as a boundary claim).
- Tenant isolation and object-auth tests fail closed when the implied scope is
  exceeded.

## Verification

- For each major surface group: accessibility tree / focus order / data model
  enforce the same cut the pixels imply.
- Auth checks: object-level authorization and RLS on every tenant-scoped read
  and write path.
- Policy sentences map 1:1 to enforced controls with owners.
- Autonomy or automation claims cite a tested envelope document.

## Rule IDs

- [PERC-03](../lexicons/interaction-ux.md#perc-03): implied layout relations vs real structure
- [NAV-05](../lexicons/interaction-ux.md#nav-05): MECE labels; one home per thing
- [INT-01](../lexicons/interaction-ux.md#int-01): click affordances match reality
- [GRPH-18](../lexicons/graph-theory.md#grph-18): similarity chaining is not an enforced entity
- [SEC-01](../lexicons/security.md#sec-01): trust changes at every boundary
- [HAI-05](../lexicons/interaction-ux.md#hai-05): do not name full autonomy beyond the tested envelope
- [CLM-03](../lexicons/business-marketing.md#clm-03): policy must match implementation
- [AIPX-13](../lexicons/business-marketing.md#aipx-13): label synthetic content that could pass as human
- [TEAM-01](../lexicons/engineering.md#team-01): software split is a team split first
- [ARCH-13](../lexicons/engineering.md#arch-13): hoist must-hold properties into structure
- [WEB-08](../lexicons/security.md#web-08): object authorization; no IDOR
- [PG-02](../lexicons/security.md#pg-02): multi-tenant rows need RLS
- [SECD-03](../lexicons/security.md#secd-03): complete mediation on each use

## Principles

- 10. Perceived boundaries must match enforced boundaries

## Evidence / source slugs

- [`designing-with-the-mind-in-mind`](../SOURCES.md#src-designing-with-the-mind-in-mind): supports [PERC-03](../lexicons/interaction-ux.md#perc-03)
- [`designing-interfaces`](../SOURCES.md#src-designing-interfaces): supports [NAV-05](../lexicons/interaction-ux.md#nav-05)
- [`designing-interfaces`](../SOURCES.md#src-designing-interfaces): supports [INT-01](../lexicons/interaction-ux.md#int-01)
- [`video-pipeline-practice`](../SOURCES.md#src-video-pipeline-practice): supports [GRPH-18](../lexicons/graph-theory.md#grph-18)
- [`llm-security-playbook`](../SOURCES.md#src-llm-security-playbook): supports [SEC-01](../lexicons/security.md#sec-01)
- [`human-centered-ai`](../SOURCES.md#src-human-centered-ai): supports [HAI-05](../lexicons/interaction-ux.md#hai-05)
- [`bootstrap`](../SOURCES.md#src-bootstrap): supports [CLM-03](../lexicons/business-marketing.md#clm-03)
- [`designing-ai-interfaces`](../SOURCES.md#src-designing-ai-interfaces): supports [AIPX-13](../lexicons/business-marketing.md#aipx-13)
- [`team-topologies`](../SOURCES.md#src-team-topologies): supports [TEAM-01](../lexicons/engineering.md#team-01)
- [`just-enough-software-architecture`](../SOURCES.md#src-just-enough-software-architecture): supports [ARCH-13](../lexicons/engineering.md#arch-13)
- [`stuttard-wahh`](../SOURCES.md#src-stuttard-wahh): supports [WEB-08](../lexicons/security.md#web-08)
- [`postgresql-security`](../SOURCES.md#src-postgresql-security): supports [PG-02](../lexicons/security.md#pg-02)
- [`anderson-security-engineering`](../SOURCES.md#src-anderson-security-engineering): supports [SECD-03](../lexicons/security.md#secd-03)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every authorization, IA, or org-design pattern. Open the rule rows for
triggers and tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not
a substitute for the original works.
