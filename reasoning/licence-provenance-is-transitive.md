# Licence provenance is transitive

Slug: `licence-provenance-is-transitive`
Mechanism claim: A permissive direct licence does not launder the terms of what a package calls, embeds, or was trained on; only a machine-checked transitive closure at the registry can refuse a ban-list hit before ship.

## Scope

Covers: decisions that admit a model, library, weight set, synthetic generator, or benchmark candidate into a shared registry or pipeline when licence or use-term obligations may attach through dependency, derivation, or training lineage.
Excludes: first-party code licence choice, security CVE triage, pure data-lineage debugging without a licence or use-term question, and project-specific ban lists or clearance tickets (those live outside this card).

## Observable triggers

- A candidate's top-level licence field is permissive while its dependency graph, base model, or training stack is uninspected.
- A "wrapper" or "fast" variant is proposed because the parent package's own SPDX line looks clean.
- Synthetic images, embeddings, or corpora are generated from weights or generators whose terms restrict commercial use or redistribution of outputs.
- Licence or capture/authorization basis lives only in prose, review comments, or a wiki page, not on the registry row the gate reads.
- An operator says an exception is "approved" without a dated, scoped decision artifact.

## Causal mechanism

Licence and use-term obligations follow the derivation graph, not the nearest `LICENSE` file. Reviewers see the import or the top-level field; the restricted artifact often sits two hops down (a dependency of a dependency, a base detector under a wrapper, a generator whose train terms bind outputs). If the registry accepts an entry on a single-hop field, CI and reviewers both green-light a ban-list intersection that only full closure would show. The failure is silent until commercialisation, redistribution, or an audit forces the graph open—when the cost of removal is highest.

## Required action

While any candidate may enter a shared registry or train/serve path:

1. Require a licence (or use-term) field on the registry entry, including the computed transitive closure over dependencies, base weights, and generator lineage—not only the direct package string.
2. Enforce at the registry gate: refuse any entry whose closure intersects the ban list; do not rely on human review to notice a nested copyleft or non-commercial generator.
3. Treat operator clearance as a dated, scoped decision artifact with owner and expiry or review date—not a chat comment or PR note.
4. For synthetic or derived corpora, record whether outputs inherit generator or weight restrictions, and refuse promotion when inheritance is unknown.
5. Keep the ban list and clearance decisions as machine-readable config that CI asserts, same class of discipline as other production config.

## Predicted failure

A banned transitive dependency or non-commercial generator enters the benchmark or product path under a permissive wrapper name. The violation ships, is discovered at commercialisation or partner review, and forces emergency removal of models, corpora, and published comparisons after sunk evaluation cost.

## Exemptions and boundaries

- Single-node research scratch space that never writes a shared registry entry and never leaves the machine: still record the stack if results may later be promoted.
- First-party code under an already-decided org licence: this card does not choose that licence; it only binds third-party and derived stacks.
- Pure runtime service dependencies with no model weights and no redistributable derived corpus: still run ordinary software licence process; this card's registry closure is for candidates that become product or published eval artifacts.
- Access-control inheritance for personal data copies is a sibling concern under [PROV-11](../lexicons/ml-systems.md#prov-11); do not fold privacy ACL parity into licence ban-list logic.
- Capture-basis and enrollment authorization use the same "field on the row, gate refuses null" pattern ([MLDATA-14](../lexicons/ml-systems.md#mldata-14)) but answer a different legal question.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | Direct SPDX / package licence field looks permissive and is enough for cataloguing | [PROV-07](../lexicons/ml-systems.md#prov-07) full transitive closure before ship | Cataloguing may show the direct string; admission to a shared registry requires closure over deps and generators |
| object | Benchmark wants every published "fast" baseline in the table ([EVAL-01](../lexicons/ml-systems.md#eval-01)) | [RLSE-02](../lexicons/engineering.md#rlse-02) gates refuse ban-list hits | Exclude or replace the banned baseline; do not average "completeness" against licence risk |
| sequence | Speed: admit candidate, licence later in review | [PROV-08](../lexicons/ml-systems.md#prov-08) / [RLSE-02](../lexicons/engineering.md#rlse-02) machine gate before merge | Closure and ban check run at registry write, not after metrics look good |
| object | Synthetic train path when authentic galleries are unusable ([MLDATA-18](../lexicons/ml-systems.md#mldata-18)) | Output-inherited generator or weight terms still bind the corpus | Substitution is allowed only when inheritance is declared and still clear of the ban list |

## Disconfirmers

- A competent licence review shows that for this use mode the nested terms do not attach (documented, dated, scoped)—the mechanism's default caution still applies until that review exists.
- Automated closure over the admitted stack is empty of ban-list licences and of generators with output-inherited restrictions.
- Every registry admission path already refuses null/unknown closure fields; review-only exceptions go to zero for a sustained period.
- Derived synthetic corpora carry an explicit "outputs unrestricted for this use" field backed by the generator's terms, not by hope.

## Verification

- Diff the registry schema: each candidate row has direct licence, transitive closure (or tool-produced equivalent), and inheritance flag for generated outputs.
- Run CI against a fixture entry whose only ban-list hit is two hops down; the gate must fail.
- Sample recent admissions: none rely on review comments for clearance; clearances are dated decision records with scope.
- Query for null or "unknown" closure fields on active candidates; count must be zero or explicitly quarantined.

## Rule IDs

- [PROV-07](../lexicons/ml-systems.md#prov-07): require the full dependency/data closure before admitting a feature, model, or candidate—not a one-hop licence glance
- [PROV-08](../lexicons/ml-systems.md#prov-08): registry and ban-list config are versioned, reviewed, and machine-asserted
- [PROV-01](../lexicons/ml-systems.md#prov-01): outputs and claims must walk back to producing artifacts (weights, generators, deps)
- [MLDATA-14](../lexicons/ml-systems.md#mldata-14): basis and obligation fields live on the record the gate reads; prose policy is not queryable
- [MLDATA-04](../lexicons/ml-systems.md#mldata-04): persist per-sample and per-batch origin so restricted sources remain filterable after merge
- [MLDATA-26](../lexicons/ml-systems.md#mldata-26): declare generator dependence on identity-labeled (or otherwise restricted) real data when synthetic claims are made
- [RLSE-02](../lexicons/engineering.md#rlse-02): licence closure against the ban list is a gate, not a suggestion at review
- [RLSE-05](../lexicons/engineering.md#rlse-05): silent miss of a nested restricted dependency is worse than a loud registry refusal
- [AGT-17](../lexicons/engineering.md#agt-17): keep ban-list policy separate from the closure-checking mechanism so either can change without rewriting the other

## Principles

- 13. Evidence precedes commitment
- 16. Fail loudly, succeed quietly

## Evidence / source slugs

- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [PROV-07](../lexicons/ml-systems.md#prov-07), [PROV-08](../lexicons/ml-systems.md#prov-08)
- [`model-cards`](../SOURCES.md#src-model-cards): supports [PROV-01](../lexicons/ml-systems.md#prov-01)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [PROV-11](../lexicons/ml-systems.md#prov-11)
- [`face-recognition-compulsory-visibility`](../SOURCES.md#src-face-recognition-compulsory-visibility): supports [MLDATA-14](../lexicons/ml-systems.md#mldata-14)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [MLDATA-04](../lexicons/ml-systems.md#mldata-04)
- [`sdfr-synthetic-competition`](../SOURCES.md#src-sdfr-synthetic-competition): supports [MLDATA-26](../lexicons/ml-systems.md#mldata-26)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not invent dedicated "transitive licence" lexicon IDs; no such titled rows appear in the supplied inventory, so the mechanism is synthesized from existing closure, inheritance, registry-field, and gate rules. It does not name project ban lists, clearance filenames, or ticket IDs. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
