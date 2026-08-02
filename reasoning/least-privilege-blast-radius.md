# Least privilege and blast radius

Slug: `least-privilege-blast-radius`
ID: `CARD-10`
Mechanism claim: Every principal inherits exactly the authority it holds; grant
the minimum so compromise or mistake reaches little.

## Scope

Covers: privilege grants and tool scope; trusted computing base size; split of
train / promote / serve and other high-impact identities; non-superuser app
roles; refusal of needless `PUBLIC` or write-heavy ops grants.

Excludes: two-key completion of high-impact acts (see [dual-control-two-keys](dual-control-two-keys.md));
pricing reversible vs irreversible *choices* and hostile-landlord exits (see
[reversible-commitments](reversible-commitments.md), [second-exit-hostile-landlord](second-exit-hostile-landlord.md)); correction at source
of truth (see [correction-at-source](correction-at-source.md)); step size of rollouts (see
[step-size-by-feedback](step-size-by-feedback.md)); pure measurement integrity (see
[measurement-integrity](measurement-integrity.md)).

## Observable triggers

- Roles, tokens, or tools hold more authority than the named function needs
  (`PUBLIC` grants, fat train/promote/serve identities, broad tool scope).
- An agent or service role can write, spend, or promote far beyond its job.
- Ops, backup, or replication identities carry write paths they never need.
- A single compromised credential would inherit cluster-wide or registry-wide
  mutation rights.

## Causal mechanism

Authority is inherited, not requested at the moment of misuse. A jailbroken
agent, stolen token, or buggy job exercises every grant on its identity.
Shrinking the grant shrinks the damage of that inheritance. Dual control of a
single act is a different decision: it stops one principal finishing the act,
but does not replace small standing scope.

## Required action

1. Grant least privilege; minimize the trusted computing base; split
   train/promote/serve and refuse needless `PUBLIC` or write-heavy ops roles
   ([SECD-02](../lexicons/security.md#secd-02),
   [SEC-04](../lexicons/security.md#sec-04),
   [PG-01](../lexicons/security.md#pg-01),
   [SEC-16](../lexicons/security.md#sec-16),
   [PG-06](../lexicons/security.md#pg-06),
   [PG-14](../lexicons/security.md#pg-14), Principle 14).

## Predicted failure

A jailbroken agent spends everything in scope. A stolen ops role rewrites the
cluster. One fat identity silently replaces production weights or labels.
`PUBLIC` grants hand every role unintended DML.

## Worked example

A CI job that only needs package-read holds org-admin tokens so it can also push tags. The trigger is a principal inheriting authority beyond its task. Split tokens: read-only for build, a separate protected job for tag push. Without the split, a compromised build script can rewrite releases.

## Exemptions and boundaries

- Break-glass emergency paths may temporarily widen scope if time-boxed,
  audited, and dual-controlled on entry (dual control owned by
  [dual-control-two-keys](dual-control-two-keys.md)).
- Read-only broad visibility is a smaller radius than write; still minimize
  sensitive read sets when compromise is the threat model.
- Human gates, dual authorizers, and secondary checks on irreversible acts are
  owned by [dual-control-two-keys](dual-control-two-keys.md) (Principle 17); plain pointer only. Do not
  load two-key machinery from this card's triggers alone.
- Reversible claim language, rollback plans, isolation/idempotency defaults are
  owned by [reversible-commitments](reversible-commitments.md) (Principle 3); second exits from external
  landlords by [second-exit-hostile-landlord](second-exit-hostile-landlord.md) (Principle 8).
- Phased rollout reduces blast radius of *change* as step size; that decision
  is owned by [step-size-by-feedback](step-size-by-feedback.md) (Principle 19).

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [SEC-16](../lexicons/security.md#sec-16) split train/promote/serve | [PG-14](../lexicons/security.md#pg-14) ops write radius | identity split and ops radius both shrink compromise inheritance |
| object | [SEC-04](../lexicons/security.md#sec-04) least privilege on agent tools | [PG-01](../lexicons/security.md#pg-01) non-superuser app role | same small-grant reflex on model agency vs database role |

## Disconfirmers

- Removing unused write grants does not break the named function (scope was
  larger than needed).
- A red-team exercise shows a compromised principal cannot reach beyond the
  intended function set.
- Train / promote / serve rights cannot be held by one identity in the live
  config.

## Verification

- Tool/ACL inventory: each principal's maximum write blast radius in one
  paragraph.
- Train / promote / serve (or equivalent) rights are not held by one identity
  ([SEC-16](../lexicons/security.md#sec-16)).
- App role is non-superuser with only the schema privileges it needs
  ([PG-01](../lexicons/security.md#pg-01)).

## Rule IDs

- [SEC-04](../lexicons/security.md#sec-04): least privilege on tools and credentials
- [SECD-02](../lexicons/security.md#secd-02): minimize trusted computing base
- [PG-01](../lexicons/security.md#pg-01): non-superuser application role
- [PG-06](../lexicons/security.md#pg-06): no casual `PUBLIC` grants
- [PG-14](../lexicons/security.md#pg-14): ops write radius
- [SEC-16](../lexicons/security.md#sec-16): split train / promote / serve rights

## Principles

- 14. Grant the least privilege; minimize what a compromise reaches

## Evidence / source slugs

- [`llm-security-playbook`](../SOURCES.md#src-llm-security-playbook): supports [SEC-04](../lexicons/security.md#sec-04)
- [`anderson-security-engineering`](../SOURCES.md#src-anderson-security-engineering): supports [SECD-02](../lexicons/security.md#secd-02)
- [`postgresql-security`](../SOURCES.md#src-postgresql-security): supports [PG-01](../lexicons/security.md#pg-01), [PG-06](../lexicons/security.md#pg-06), [PG-14](../lexicons/security.md#pg-14)
- [`sotiropoulos-adversarial-ai`](../SOURCES.md#src-sotiropoulos-adversarial-ai): supports [SEC-16](../lexicons/security.md#sec-16)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to catalogue every privilege pattern. Rule rows hold triggers and tiers.
[SOURCES.md](../SOURCES.md) lists cited works for bibliography lookup; it is
not a substitute for the originals.
