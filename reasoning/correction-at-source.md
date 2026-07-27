# Correction at source

Slug: `correction-at-source`
Mechanism claim: A correction is real only when it updates the source of truth
that recomputation will read; surface patches return after the next rebuild.

## Scope

Covers: human edits on AI or graph review surfaces; annotation feedback into
training; derived stores and materialized views; mirrored fields; outbox and
event publish; prose edits that leave the underlying defect; post-hoc model
corrector cascades.

Excludes: pure privilege and dual-control design (see
`least-privilege-blast-radius`, `dual-control-two-keys`); reversible choice and
landlord exit (see `reversible-commitments`, `second-exit-hostile-landlord`);
measurement frame ownership (see `measurement-integrity`); wrong-proxy targets
(see `proxy-outcome-integrity`); step size of rollouts (see
`step-size-by-feedback`) except where a "fix" is only a temporary patch.

This card exclusively owns the correction-at-source decision for
[HAI-02](../lexicons/interaction-ux.md#hai-02),
[HITL-01](../lexicons/ml-systems.md#hitl-01),
[SERVE-04](../lexicons/ml-systems.md#serve-04),
[INT-09](../lexicons/interaction-ux.md#int-09),
[DATA-14](../lexicons/engineering.md#data-14), and Principle 12. Other cards
may point here from boundaries; they must not re-list those IDs as owned
actions.

## Observable triggers

- Review UI saves a label or entity that the next recompute or train will
  overwrite.
- Teams hand-patch rows in a derived store while the log or raw facts stay
  wrong.
- A second model or rules layer "fixes" a frozen model's outputs in production.
- Edit pass swaps flagged phrases without fixing inflation, vagueness, or
  template structure.
- Events publish outside the transaction that changed state, creating two
  truths.

## Causal mechanism

Derived state is cheap to show and expensive to trust. When the wrong answer is
fixed only on the copy the user sees, every rebuild, retrain, or cache fill
restores the error. Real correction changes the input, rule, log offset, or
training label that *produces* the next copy. Stacked correctors freeze the
underlying model and train the organization to paper over it forever.

## Required action

1. Route human edits to the underlying model, graph, or record with provenance
   and reverse path ([HAI-02](../lexicons/interaction-ux.md#hai-02),
   [INT-09](../lexicons/interaction-ux.md#int-09)).
2. Feed fresh human labels into the next training run; re-queue by model state
   ([HITL-01](../lexicons/ml-systems.md#hitl-01), [AIPX-03](../lexicons/business-marketing.md#aipx-03)).
3. Repair derived stores by reprocessing retained logs into a fresh view; do not
   hand-patch as truth ([FLOW-06](../lexicons/engineering.md#flow-06),
   [DATA-14](../lexicons/engineering.md#data-14)).
4. Refuse post-hoc corrector cascades on frozen wrong models
   ([SERVE-04](../lexicons/ml-systems.md#serve-04)).
5. Treat mirrored fields and cubes as optimisations with freshness, not as
   sources ([REF-09](../lexicons/engineering.md#ref-09), [STOR-07](../lexicons/engineering.md#stor-07)).
6. Publish domain events in the same transaction as the state change
   ([DOM-06](../lexicons/engineering.md#dom-06)); fix the underlying prose defect, not only the tell
   ([WRIT-44](../lexicons/writing.md#writ-44)).

## Predicted failure

The same wrong entity returns after retrain. Patched dashboards diverge from
the warehouse rebuild. Corrector layers deadlock improvement. Brand voice
"fixes" reappear next draft. Event consumers and the database disagree forever.

## Exemptions and boundaries

- Emergency display flags may hide harm short-term if a ticket and deadline
  force a source fix; the flag is not the correction.
- Read replicas lag by design; correction still targets the primary or log, not
  the replica alone.
- User-visible undo stacks must invert real operations
  ([INT-09](../lexicons/interaction-ux.md#int-09)), not only local component state.
- Missing walkable lineage for a claim or artifact is Principle 9 (open
  PRINCIPLES starting at GRPH-14), not this card's owned decision; plain pointer
  only.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [HAI-02](../lexicons/interaction-ux.md#hai-02) edit reaches source | [SERVE-04](../lexicons/ml-systems.md#serve-04) no corrector stack on frozen model | fix source or retrain; do not add a second model that hides the first |
| sequence | [HITL-01](../lexicons/ml-systems.md#hitl-01) labels into next train | [MLDATA-05](../lexicons/ml-systems.md#mldata-05) wait for delayed truth | close the loop, but do not cut the label window shorter than feedback |
| surface | [FLOW-06](../lexicons/engineering.md#flow-06) rebuild from log | [WRIT-44](../lexicons/writing.md#writ-44) fix underlying prose defect | same source-first reflex on dataflow vs draft |

## Disconfirmers

- After edit and full recompute/retrain, the wrong claim returns (source was
  not updated).
- Hand-patched derived row survives rebuild without log change (patch was
  mistaken for truth and environment is misconfigured).
- Removing a corrector layer does not change outputs (cascade was dead weight).

## Verification

- Edit path writes to the system of record; recompute job reads that record.
- Training dataset version includes post-review labels with timestamps.
- No production corrector without an owned plan to update the base model.
- Outbox or transactional publish test: crash between state and event cannot
  diverge silently.

## Rule IDs

- [HAI-02](../lexicons/interaction-ux.md#hai-02): correction reaches source, reversible, with provenance
- [HITL-01](../lexicons/ml-systems.md#hitl-01): fresh labels into the next train
- [INT-09](../lexicons/interaction-ux.md#int-09): discrete reversible operations on real data
- [SERVE-04](../lexicons/ml-systems.md#serve-04): refuse post-hoc corrector deadlock
- [DATA-14](../lexicons/engineering.md#data-14): no dual writes of truth
- [FLOW-06](../lexicons/engineering.md#flow-06): rebuild derived views from the log
- [REF-09](../lexicons/engineering.md#ref-09): mirrored fields drift
- [STOR-07](../lexicons/engineering.md#stor-07): cubes are optimisations with freshness
- [DOM-06](../lexicons/engineering.md#dom-06): outbox / same-transaction publish
- [AIPX-03](../lexicons/business-marketing.md#aipx-03): production accept/edit as label source
- [WRIT-44](../lexicons/writing.md#writ-44): fix the underlying defect, not only the tell

## Principles

- 12. Correction must reach the source

Missing walkable lineage is Principle 9 (open PRINCIPLES starting at GRPH-14),
not a claimed principle on this card.

## Evidence / source slugs

- [`human-in-the-loop-ml`](../SOURCES.md#src-human-in-the-loop-ml): supports [HAI-02](../lexicons/interaction-ux.md#hai-02), [HITL-01](../lexicons/ml-systems.md#hitl-01)
- [`designing-interfaces`](../SOURCES.md#src-designing-interfaces): supports [INT-09](../lexicons/interaction-ux.md#int-09)
- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [SERVE-04](../lexicons/ml-systems.md#serve-04)
- [`designing-data-intensive-applications`](../SOURCES.md#src-designing-data-intensive-applications): supports [DATA-14](../lexicons/engineering.md#data-14), [FLOW-06](../lexicons/engineering.md#flow-06), [STOR-07](../lexicons/engineering.md#stor-07)
- [`refactoring-fowler-beck`](../SOURCES.md#src-refactoring-fowler-beck): supports [REF-09](../lexicons/engineering.md#ref-09)
- [`learning-domain-driven-design`](../SOURCES.md#src-learning-domain-driven-design): supports [DOM-06](../lexicons/engineering.md#dom-06)
- [`building-ml-powered-applications`](../SOURCES.md#src-building-ml-powered-applications): supports [AIPX-03](../lexicons/business-marketing.md#aipx-03)
- [`ai-writing-tropes`](../SOURCES.md#src-ai-writing-tropes): supports [WRIT-44](../lexicons/writing.md#writ-44)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every data-repair or HITL pattern. Open the rule rows for triggers and
tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not a substitute
for the original works.
