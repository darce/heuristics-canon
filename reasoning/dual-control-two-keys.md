# Dual control and two independent keys

Slug: `dual-control-two-keys`
Mechanism claim: High-impact acts must not complete under one principal or one
mechanism class; split completion across two independent keys.

## Scope

Covers: dual control on value-creating, value-destroying, or evidence-erasing
acts; human or independent gates on irreversible automation side effects;
secondary verification on high-stakes model accepts; expert adjudication before
low-agreement high-impact labels enter training.

Excludes: standing privilege sizing and TCB shrink (see
`least-privilege-blast-radius`); pricing reversible vs irreversible *choices*
and hostile-landlord exits (see `reversible-commitments`,
`second-exit-hostile-landlord`); designed unknown as abstention state alone
(see `designed-unknown`); evidence clocks before durable commit (see
`evidence-before-commitment`).

## Observable triggers

- An agent, model, or service can complete financial, destructive, or
  evidence-erasing actions without a second key.
- Break-glass or ops write paths lack dual control, audit, or time box.
- High-stakes model output is accepted without a human or independent check.
- Low-agreement labels with high training impact enter the set without expert
  adjudication.

## Causal mechanism

Small grants still leave one gap: a single trusted principal, honestly
convinced or quietly compromised, can finish an act nobody else sees. Dual
control closes that gap by requiring two independent authorizers or mechanism
classes before value moves, data dies, audit evidence vanishes, or a high-stakes
accept becomes durable. Least privilege is a different decision: it shrinks
standing radius, it does not replace the second key on completion.

## Required action

1. Gate irreversible, financial, or destructive automation behind a human or
   independent check ([SEC-05](../lexicons/security.md#sec-05),
   [AIPX-09](../lexicons/business-marketing.md#aipx-09)).
2. Use dual control for value-creating, value-destroying, or evidence-erasing
   acts ([SECD-04](../lexicons/security.md#secd-04), Principle 17).
3. Route low-agreement high-impact labels through expert adjudication before
   they enter training ([HITL-07](../lexicons/ml-systems.md#hitl-07)).

## Predicted failure

One trusted principal completes a fund move, data destroy, or audit delete
alone. High-stakes model accepts create outsized exposure with no second key.
Low-agreement labels poison training without an expert gate.

## Exemptions and boundaries

- Truly irreversible legal or physical acts still need dual control and
  evidence *before* commit (Principle 13 via `evidence-before-commitment`);
  "no rollback possible" raises the gate, it does not remove it.
- Break-glass emergency paths may temporarily complete under urgency if
  time-boxed, audited, and dual-controlled on entry.
- Standing privilege and TCB sizing are owned by
  `least-privilege-blast-radius` (Principle 14); plain pointer only. Do not
  load grant-sizing machinery from this card's triggers alone.
- When the same low-agreement path is about *forcing a class* rather than
  *who may authorize the label*, also open `designed-unknown` (Principle 11);
  both mechanisms can apply.
- Corrections that must update the system of record are owned by
  `correction-at-source` (Principle 12); plain pointer only.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | [SEC-05](../lexicons/security.md#sec-05) human gate on agent side effects | [AIPX-09](../lexicons/business-marketing.md#aipx-09) secondary check on high-stakes model output | same two-key idea on automation vs model-accept surfaces |
| object | [SECD-04](../lexicons/security.md#secd-04) dual control on value/evidence acts | [HITL-07](../lexicons/ml-systems.md#hitl-07) expert adjudication before high-impact labels | second key on ops completion vs label-to-train path |

## Disconfirmers

- A red-team or fault injection shows a compromised principal cannot complete
  the high-impact act alone.
- Dual-control config is present on value move, destroy, and audit-delete
  paths and was exercised in rehearsal.
- Low-agreement high-impact items have an expert path that can block train
  entry.

## Verification

- Dual-control config on value move, destroy, and audit-delete paths.
- Agent tool lists exclude irreversible side effects without a human gate
  ([SEC-05](../lexicons/security.md#sec-05)).
- High-stakes model accept checklist names the independent check
  ([AIPX-09](../lexicons/business-marketing.md#aipx-09)).

## Rule IDs

- [SEC-05](../lexicons/security.md#sec-05): human gate on irreversible side effects
- [SECD-04](../lexicons/security.md#secd-04): dual control for high-impact acts
- [AIPX-09](../lexicons/business-marketing.md#aipx-09): secondary verification for high-stakes model output
- [HITL-07](../lexicons/ml-systems.md#hitl-07): expert adjudication before high-impact labels land

## Principles

- 17. High-impact actions take two independent keys

## Evidence / source slugs

- [`llm-security-playbook`](../SOURCES.md#src-llm-security-playbook): supports [SEC-05](../lexicons/security.md#sec-05)
- [`anderson-security-engineering`](../SOURCES.md#src-anderson-security-engineering): supports [SECD-04](../lexicons/security.md#secd-04)
- [`designing-ai-interfaces`](../SOURCES.md#src-designing-ai-interfaces): supports [AIPX-09](../lexicons/business-marketing.md#aipx-09)
- [`human-in-the-loop-ml`](../SOURCES.md#src-human-in-the-loop-ml): supports [HITL-07](../lexicons/ml-systems.md#hitl-07)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to catalogue every dual-control pattern. Rule rows hold triggers and tiers.
[SOURCES.md](../SOURCES.md) lists cited works for bibliography lookup; it is
not a substitute for the originals.
