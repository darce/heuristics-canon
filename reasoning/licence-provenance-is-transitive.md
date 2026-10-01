# Licence provenance is transitive

Slug: `licence-provenance-is-transitive`
ID: `CARD-26`
Mechanism claim: Document model and data provenance and named training sources; annotated transitive data dependencies support safe feature migration or deletion. Licence inheritance requires support from the applicable licence or another authoritative source.

## Scope

Covers: model and training-data documentation, annotated data-dependency closure for feature migration or deletion, and licence questions whose obligations are established by applicable terms or another authoritative source.
Excludes: first-party code licence choice, security CVE triage, and project-specific ban lists or clearance tickets. The cited provenance passages do not establish a licence-inheritance doctrine or registry ban-list gate.

## Observable triggers

- A candidate's top-level licence field is permissive while its dependency graph, base model, or training stack is uninspected.
- A wrapper or variant is proposed without documenting its model and training-data sources.
- Synthetic images, embeddings, or corpora lack documented generator and training-source lineage.
- Licence or capture/authorization basis lives only in prose, review comments, or a wiki page, not on the registry row the gate reads.
- An operator says an exception is "approved" without a dated, scoped decision artifact.

## Causal mechanism

Unannotated data dependencies make feature migration and deletion unsafe because consumers can remain hidden several hops away. Annotating sources and features and checking the full data-dependency closure exposes those consumers. Training-data documentation separately helps users assess model suitability and bias. Neither mechanism establishes that licence terms attach to dependencies or model outputs; that conclusion needs the applicable terms or another authoritative source.

## Required action

While any candidate may enter a shared registry or train/serve path:

1. Annotate data sources and features, and compute and check their transitive data-dependency closure before feature migration or deletion ([PROV-07](../lexicons/ml-systems.md#prov-07)). This closure does not establish licence or use-term inheritance.
2. Use automated checks to validate data-dependency annotations and closure for migration or deletion; any licence ban-list gate requires separate authoritative support.
3. Treat operator clearance as a dated, scoped decision artifact with owner and expiry or review date—not a chat comment or PR note.
4. For synthetic or derived corpora, document model and data provenance, including named training sources and their lineage; state output licence obligations only where the applicable terms or another authoritative source establishes them.
5. Version, review, and machine-check train/serve config, including feature counts, data-dependency closure, and unused keys ([PROV-08](../lexicons/ml-systems.md#prov-08)); this config discipline does not itself establish a licence ban-list policy.

## Predicted failure

An undocumented data dependency leaves a feature consumer undiscovered during migration or deletion. Missing training-source documentation also leaves users unable to assess relevant bias or suitability. Whether a licence violation occurs depends on the applicable terms, not on provenance alone.

## Worked example

A model card lists a permissive weight licence but omits named training sources, and a feature migration plan lists only direct consumers. Document the training sources and resolve the transitive data-dependency closure before migration. Assess any licence obligations against the applicable terms; the data-dependency graph alone does not establish them.

## Exemptions and boundaries

- Single-node research scratch space that never writes a shared registry entry and never leaves the machine: still record the stack if results may later be promoted.
- First-party code under an already-decided org licence: this card does not choose that licence; it only binds third-party and derived stacks.
- Software licence review requires applicable terms; this card's sourced closure requirement concerns data dependencies for feature migration or deletion.
- Access-control inheritance for personal data copies is a sibling concern under [PROV-11](../lexicons/ml-systems.md#prov-11); do not fold privacy ACL parity into licence ban-list logic.
- Capture-basis and enrollment authorization use the same "field on the row, gate refuses null" pattern ([MLDATA-14](../lexicons/ml-systems.md#mldata-14)) but answer a different legal question.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | Direct SPDX / package licence field describes the declared licence | [PROV-07](../lexicons/ml-systems.md#prov-07) annotated transitive data-dependency closure for migration or deletion | Keep licence assessment separate from data-dependency closure; the latter does not establish inherited terms |
| sequence | Speed: migrate a feature before resolving its consumers | [PROV-08](../lexicons/ml-systems.md#prov-08) reviewed config with automated dependency assertions | Resolve and check data dependencies before migration; licence gates require separate support |
| object | Synthetic train path when authentic galleries are unusable ([MLDATA-18](../lexicons/ml-systems.md#mldata-18)) | Model and training-source provenance remains necessary | Document the lineage; infer output obligations only from terms or another authoritative source that establishes them |

## Disconfirmers

- A competent licence review shows that for this use mode the nested terms do not attach (documented, dated, scoped)—the mechanism's default caution still applies until that review exists.
- Annotated data-dependency closure identifies all consumers needed for a feature migration or deletion.
- Migration and deletion paths already validate source annotations and transitive data dependencies.
- Derived synthetic corpora carry an explicit "outputs unrestricted for this use" field backed by the generator's terms, not by hope.

## Verification

- Check source and feature annotations and the transitive data-dependency closure used for migration or deletion.
- Check that automated dependency analysis finds a feature consumer two hops downstream.
- Sample recent admissions: none rely on review comments for clearance; clearances are dated decision records with scope.
- Check that training-data documentation names sources and, where full disclosure is blocked, supplies allowable factor distributions and label definitions.

## Rule IDs

- [PROV-07](../lexicons/ml-systems.md#prov-07): annotate and check transitive data dependencies for feature migration or deletion; this does not establish licence inheritance
- [PROV-08](../lexicons/ml-systems.md#prov-08): train/serve config is versioned, reviewed, and machine-checked, including data-dependency assertions
- [PROV-01](../lexicons/ml-systems.md#prov-01): provenance is relevant to tracing artifacts; the cited Model Cards for Model Reporting passage supports release-level model and training-source documentation, not licence inheritance
- [MLDATA-14](../lexicons/ml-systems.md#mldata-14): basis and obligation fields live on the record the gate reads; prose policy is not queryable
- [MLDATA-04](../lexicons/ml-systems.md#mldata-04): persist per-sample and per-batch origin so restricted sources remain filterable after merge
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

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. The retained title does not establish a general licence-inheritance rule: the cited closure passage concerns data dependencies, and licence obligations require separate authoritative support. It does not name project ban lists, clearance filenames, or ticket IDs. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
