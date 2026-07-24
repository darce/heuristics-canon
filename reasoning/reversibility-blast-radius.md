# Reversibility and blast radius

Slug: `reversibility-blast-radius`
Mechanism claim: Prefer the cheap reversible option while the irreversible
path is underpriced; shrink what one failure or one principal can reach.

## Scope

Covers: ship and rollback plans; isolation and idempotency choices; LLM and
automation side effects; privilege grants; dual control on high-impact acts;
graph and dependency single points of failure; irreversible product or claim
language.

Excludes: pure taste decisions with symmetric undo cost; performance tuning
that does not change durability or authority; measurement integrity (see
`measurement-integrity`) except where a weak meter *gates* an irreversible act.

## Observable triggers

- A plan freezes a reversible decision out of vague dread, or ships with no
  rollback section.
- Weaker isolation, non-idempotent retries, or check-then-act under snapshot
  isolation is chosen because it "looks free" at write time.
- An agent, model, or service can complete financial, destructive, or
  evidence-erasing actions without a second key.
- Roles, tokens, or tools hold more authority than the named function needs
  (`PUBLIC` grants, fat train/promote/serve identities, broad tool scope).
- A single external platform, dependency, or internal node is a bridge whose
  loss partitions the system.
- Edits correct a display or derived store without reaching the source of
  truth, so recompute restores the error.

## Causal mechanism

Irreversibility is a price curve, not a mood. At decision time the soft verb,
narrow grant, human gate, request ID, or phased cutover costs a little;
crossing the line costs a rewrite, a data-integrity incident, a regulator, or
a hostile landlord with no exit. People systematically underprice the
irreversible side because the bill arrives later and elsewhere.

Blast radius is the same curve in space: every credential and component is a
circle of inheritance. Compromise or honest mistake exercises everything the
principal holds. Dual control closes the remaining gap where one trusted
principal can finish an act nobody else sees.

## Required action

1. When options differ in reversibility, take the reversible side unless a
   written exemption says otherwise (Principle 3). Write rollback *before*
   ship, including data written by the new build ([RLSE-08]).
2. Name worst cases and repair paths before freezing a reversible decision
   ([STRAT-14]); do not freeze by dread alone.
3. Record real isolation behavior; test invariants before defaulting to weak
   isolation ([DATA-17], [DATA-18]). Make writes idempotent end-to-end
   ([DATA-13], [API-02]).
4. Gate irreversible, financial, or destructive automation behind a human or
   independent check ([SEC-05], [AIPX-09]); use dual control for value-creating,
   value-destroying, or evidence-erasing acts ([SECD-04]).
5. Grant least privilege; minimize the trusted computing base; split
   train/promote/serve and refuse needless `PUBLIC` or write-heavy ops roles
   ([SECD-02], [SEC-04], [PG-01], [SEC-16], [PG-06], [PG-14]).
6. Detect cut vertices and multi-home across hostile landlords ([GRPH-05],
   [BOOT-07]).
7. Correct at the source with reversible operations on real data ([INT-09],
   [HAI-02], [DATA-14], Principle 12).

## Predicted failure

Aggressive claims and unsupervised model accepts create outsized exposure.
Weak isolation commits silent integrity loss. Retries double-apply. A
jailbroken agent spends everything in scope. A stolen ops role rewrites the
cluster. One platform ToS change zeros the business. Cosmetic UI fixes return
after recompute. At 2am there is no rollback plan, only invention.

## Exemptions and boundaries

- Truly irreversible legal or physical acts still need dual control and
  evidence *before* commit (Principle 13); "no rollback possible" raises the
  gate, it does not remove it.
- Break-glass emergency paths may temporarily widen scope if time-boxed,
  audited, and dual-controlled on entry.
- Read-only broad visibility is a smaller radius than write; still minimize
  sensitive read sets when compromise is the threat model.
- Phased rollout ([RLSE-07]) reduces blast radius of *change*; it does not
  replace least privilege on standing credentials.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [RLSE-07] phased rollout with stop criteria | launch stunts / hard cutovers when the product requires a single moment | phase the *capability exposure*; keep claim language on the safe side the whole time ([CLM-02]) |
| object | [SEC-04] least privilege (radius) | [SECD-04] dual control (completion) | small grants limit damage; two keys stop one principal finishing the act |
| surface | [DATA-18] concurrency integrity under weak isolation | [SEC-05] human gate on agent side effects | same underpriced-irreversible trade on storage vs automation surfaces |
| object | [INT-09] reversible command on real data | [SERVE-04] refuse post-hoc corrector cascades | undo on the source; do not stack fixers on a frozen wrong model |

## Disconfirmers

- Rollback was executed in rehearsal and restored both code and data path.
- A red-team or fault injection shows a compromised principal cannot complete
  the high-impact act alone.
- Isolation anomaly tests fail closed before production defaults weaken.
- Removing a suspected bridge node leaves the graph connected (or multi-home
  is proven).

## Verification

- Rollback section answers: can the old build read new data?
- Request IDs and idempotency keys on every retried side effect.
- Tool/ACL inventory: each principal's maximum write blast radius in one
  paragraph.
- Dual-control config on value move, destroy, and audit-delete paths.
- Articulation-point list for critical external and internal dependencies.

## Rule IDs

- [CLM-02]: safe claim language is underpriced insurance
- [A11Y-25]: early reversible a11y cost vs late rewrite
- [RLSE-08]: rollback written before ship
- [RLSE-07]: phased rollout as blast-radius control
- [STRAT-14]: fear-setting before reversible freezes
- [DATA-17] / [DATA-18]: isolation names vs real anomalies; check-then-act gap
- [DATA-13] / [API-02]: end-to-end idempotency
- [DATA-14]: no dual writes of truth
- [SEC-04] / [SEC-05]: least privilege; human gate on side effects
- [SECD-02] / [SECD-04]: minimize TCB; dual control
- [PG-01] / [PG-06] / [PG-14]: non-superuser app; no casual PUBLIC; ops write radius
- [SEC-16]: split train / promote / serve rights
- [AIPX-09]: secondary verification for high-stakes model output
- [GRPH-05]: cut vertices and bridges
- [BOOT-07]: hostile landlord; second exit
- [INT-09] / [HAI-02]: reversible correction on the real source
- [SERVE-04]: no post-hoc corrector deadlock

## Principles

- 3. The safe side is cheap; the wrong side is not
- 8. Assume a hostile landlord and keep a second exit
- 12. Correction must reach the source
- 14. Grant the least privilege; minimize what a compromise reaches
- 17. High-impact actions take two independent keys

## Evidence / source slugs

- `product-deploy-agents-fields`: rollback, claims exposure, phased ship
- `designing-data-intensive-applications`: isolation, idempotency, dual writes
- `llm-security-playbook`: agent scope and human gates
- `anderson-security-engineering`: TCB and dual control
- `postgresql-security`: grant radius
- `sotiropoulos-adversarial-ai`: train/promote/serve split
- `designing-ai-interfaces`: high-stakes accept path
- `graph-theory-with-applications`: articulation points
- `porn-work`: platform landlord risk (labor study arrival)
- `designing-interfaces-int-form`: reversible command stack
- `human-in-the-loop-ml`: correction reaching training/source
- `hidden-technical-debt-ml`: corrector cascades
- `four-hour-workweek`: fear-setting
- `restful-web-api-patterns`: idempotent API retries

Related critical note: [designing-data-intensive-applications](../sources/designing-data-intensive-applications.md).

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to catalogue every irreversibility pattern in security or data systems. Rule
rows hold triggers and tiers. Source notes hold support calibration. Private
distillations are not published.
