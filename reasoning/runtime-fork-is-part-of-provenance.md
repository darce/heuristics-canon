# Runtime fork is part of provenance

Slug: `runtime-fork-is-part-of-provenance`
ID: `CARD-29`
Mechanism claim: A model that requires a vendor fork of the inference runtime carries that fork as a production dependency and as part of output provenance; the weight licence alone does not close the lineage question.

## Scope

Covers: adoption, pin, release, rollback, and audit decisions when a model only loads or scores correctly on a non-stock inference runtime (vendor fork, patched engine, private kernel/tokenizer/scheduler image), so that runtime must appear in the dependency closure and serving contract.

Excludes: pure legal review of weight licences; training-data lineage; managed-API endpoints where the provider owns the runtime and the contract surface is an API version you do not operate; stock runtimes differing only by reviewed config; general model-card discipline when no fork is required.

## Observable triggers

- Release notes, model card, or vendor docs state a required private runtime, fork, or "only supported on our engine."
- Serve manifests pin a private image, fork branch, or patched engine that is not a public upstream tag.
- Weights fail to load, tokenize, or sample correctly on the stock runtime the rest of the fleet uses.
- Rollback or incident plans restore a previous checkpoint but leave the runtime image unnamed or unreverted.
- Provenance records list weight hash and licence and omit runtime identity, digest, or owner.
- An ADR or design treats the fork as "infra detail" outside model lineage and the deployable unit.

## Causal mechanism

Production outputs are not determined by weights alone. Kernels, batching, dtype paths, tokenizer behaviour, sampling, and scheduler semantics sit on the path and can change numerical or sampling behaviour. A required vendor fork is a privately versioned behaviour surface and a landlord-controlled dependency. If provenance, cards, and rollback name only the checkpoint and its licence, a fork bump or outage is unattributable, hard to revert as a model incident, and invisible to anyone who audited "the model" by licence and weight hash. The fork is therefore in the same provenance class as the served artifact, not an optional ops footnote.

## Required action

While a required runtime fork is in play:

1. Put the fork in the dependency closure: name, version or image digest, licence, owner, and whether production cannot run without it ([PROV-07](../lexicons/ml-systems.md#prov-07)).
2. Attach runtime identity to the serving or generation contract with model identity so each output walks back to weights and engine ([PROV-01](../lexicons/ml-systems.md#prov-01), [PROV-06](../lexicons/ml-systems.md#prov-06), [PROV-09](../lexicons/ml-systems.md#prov-09)).
3. Version-lock the card (or release record) to the same pair: re-issue on fork change that can alter behaviour, not only on weight change ([PROV-03](../lexicons/ml-systems.md#prov-03)).
4. Treat the pin as a reviewed, asserted artifact in version control (diffable, machine-checked where possible) ([PROV-08](../lexicons/ml-systems.md#prov-08)).
5. Isolate the package behind an owned I/O boundary so the rest of the path does not freeze fork peculiarities ([SERVE-01](../lexicons/ml-systems.md#serve-01), [REF-15](../lexicons/engineering.md#ref-15)).
6. Quality-gate any fork bump or runtime optimization that can change numerical or sampling behaviour before promote ([SERVE-07](../lexicons/ml-systems.md#serve-07)).
7. Write rollback before ship so previous-good weights and previous-good runtime can be restored without inventing a procedure under load; widen the deployable unit when green must include the runtime image ([RLSE-08](../lexicons/engineering.md#rlse-08), [RLSE-10](../lexicons/engineering.md#rlse-10), [RLSE-12](../lexicons/engineering.md#rlse-12)).
8. Name a second exit (upstream stock runtime with proven parity, alternate model, or managed endpoint) before the fork becomes the only path that can serve production.

## Predicted failure

- Audit and cards claim complete provenance from weight licence while behaviour is owned by an untracked fork.
- Regressions attributed to "the model" after a silent runtime image bump; no contract id binds the engine.
- Rollback reverts the checkpoint and leaves the failing fork; recovery still requires a code or image release nobody planned.
- Train/serve or multi-environment skew when featurization or decode paths live only in the forked stack ([SERVE-08](../lexicons/ml-systems.md#serve-08)).
- Landlord lock-in: the fork is the only runnable path, with no second exit and no isolatable API.
- Dead experimental runtime branches remain callable in production ([SERVE-03](../lexicons/ml-systems.md#serve-03)).

## Worked example

Incident review for a scoring drift finds the checkpoint hash and licence on the model card, but the private engine image that actually ran is missing from the card and the rollback runbook. Add the image digest, licence, and owner beside the checkpoint in the generation contract. Without those fields, the next bump of that engine can change outputs while every card still reads as complete lineage.

## Exemptions and boundaries

- Managed inference APIs where you do not operate a local fork: contract the provider version and typed prediction identity; this card's local-image closure does not apply.
- Stock upstream runtime with only config, prompt, or decoding differences: still pin behaviour-affecting config ([PROV-08](../lexicons/ml-systems.md#prov-08), [PROV-09](../lexicons/ml-systems.md#prov-09)); do not invent a "fork" where none exists.
- Offline research that never produces production decisions or customer-facing scores.
- Weight-licence and redistribution legal review remains a separate decision; it does not satisfy runtime provenance.
- Sibling general provenance and model-card cards: this card only when a required runtime fork is on the serve path. Do not re-own their full rule sets here.
- Continuous-batching and KV-cache sizing are capacity decisions ([SERVE-05](../lexicons/ml-systems.md#serve-05), [SERVE-06](../lexicons/ml-systems.md#serve-06)); cite them only when the fork is also the capacity owner, not as substitutes for lineage.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | [SERVE-01](../lexicons/ml-systems.md#serve-01) / [REF-15](../lexicons/engineering.md#ref-15): hide the fork behind a stable owned API | [PROV-01](../lexicons/ml-systems.md#prov-01) / [PROV-09](../lexicons/ml-systems.md#prov-09): still emit runtime identity on the contract | Isolation stops glue freeze; the contract still names the engine that produced the score |
| object | [RLSE-10](../lexicons/engineering.md#rlse-10): model artifact separately revertible from app binary | Required fork couples behaviour to a runtime image | Restore previous-good weights and previous-good runtime together when behaviour depends on the fork; separate only when stock runtime is proven interchangeable |
| sequence | [ARCH-08](../lexicons/engineering.md#arch-08): prefer boring stock technology first | Capability may require a vendor fork | Adopt the fork only after second exit, pin, and quality gate; capability earns the exception, it does not erase provenance |
| sequence | [SERVE-07](../lexicons/ml-systems.md#serve-07): gate behaviour-changing runtime changes | Shipping pressure to bump the vendor image | No promote of a fork digest that can alter numerics or sampling without a task-plus-regression (or exact-equivalence) gate |

## Disconfirmers

- The checkpoint runs with bit-compatible behaviour on a public stock runtime tag under automated parity tests; no private fork is required.
- Production uses only a managed endpoint whose versioned API is the whole contract surface (no local engine image).
- Swapping runtime images never changes scores or sampling under the eval gate that ships with the model (fork is not behaviour-affecting for this artifact).
- Dependency closure, cards, and rollback already treat runtime digests as first-class and drills restore them without inventing procedure.

## Verification

- Serving or generation contract for a production output includes model id/version and runtime fork identity (version or image digest).
- Model card or release record is version-locked to that pair; a fork-only bump either re-issues the card or is forbidden.
- `PROV-07`-style dependency list for the model names the runtime package and owner.
- Rollback runbook answers: which previous-good weight artifact and which previous-good runtime image, and whether restore needs a full app release.
- Pipeline green scope includes the runtime image when the model cannot serve without it ([RLSE-12](../lexicons/engineering.md#rlse-12)).
- Inventory of serve path shows no abandoned experimental runtime branches still executable ([SERVE-03](../lexicons/ml-systems.md#serve-03)).
- Second-exit note exists: stock runtime parity result, alternate model, or managed fallback named before sole dependence on the fork.

## Rule IDs

- [PROV-01](../lexicons/ml-systems.md#prov-01): outputs must walk back through engine and weights, not weights alone
- [PROV-03](../lexicons/ml-systems.md#prov-03): card version moves when the behaviour-affecting runtime pin moves
- [PROV-06](../lexicons/ml-systems.md#prov-06): typed predictions carry producer identity usable with the serve contract
- [PROV-07](../lexicons/ml-systems.md#prov-07): transitive dependency closure includes the required runtime fork
- [PROV-08](../lexicons/ml-systems.md#prov-08): runtime pin is a reviewed, asserted config-class artifact
- [PROV-09](../lexicons/ml-systems.md#prov-09): generation/serving contract id covers behaviour-affecting runtime components
- [SERVE-01](../lexicons/ml-systems.md#serve-01): isolate the vendor package so the fork does not freeze the whole path
- [SERVE-03](../lexicons/ml-systems.md#serve-03): remove dead experimental runtime codepaths from production
- [SERVE-07](../lexicons/ml-systems.md#serve-07): quality-gate fork and serving changes that can alter numerics or sampling
- [SERVE-08](../lexicons/ml-systems.md#serve-08): keep train/serve transforms identical when featurization lives on the runtime path
- [RLSE-08](../lexicons/engineering.md#rlse-08): write rollback that includes runtime restore before ship
- [RLSE-10](../lexicons/engineering.md#rlse-10): previous-good model path must not depend on an unplanned release; couple runtime when required
- [RLSE-12](../lexicons/engineering.md#rlse-12): deployable unit includes the runtime image when green must mean runnable
- [REF-15](../lexicons/engineering.md#ref-15): ports-and-adapters boundary around the volatile engine
- [ARCH-08](../lexicons/engineering.md#arch-08): stock/boring default until the fork earns its exception

## Principles

- 3. The safe side is cheap; the wrong side is not
- 8. Assume a hostile landlord and keep a second exit

## Evidence / source slugs

- [`model-cards`](../SOURCES.md#src-model-cards): supports [PROV-01](../lexicons/ml-systems.md#prov-01), [PROV-02](../lexicons/ml-systems.md#prov-02), [PROV-03](../lexicons/ml-systems.md#prov-03)
- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [PROV-06](../lexicons/ml-systems.md#prov-06), [PROV-07](../lexicons/ml-systems.md#prov-07), [PROV-08](../lexicons/ml-systems.md#prov-08), [SERVE-01](../lexicons/ml-systems.md#serve-01), [SERVE-03](../lexicons/ml-systems.md#serve-03)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [PROV-09](../lexicons/ml-systems.md#prov-09), [SERVE-07](../lexicons/ml-systems.md#serve-07)
- [`ml-design-patterns`](../SOURCES.md#src-ml-design-patterns): supports [SERVE-08](../lexicons/ml-systems.md#serve-08)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [RLSE-10](../lexicons/engineering.md#rlse-10)
- [`designing-data-intensive-applications`](../SOURCES.md#src-designing-data-intensive-applications): supports [RLSE-08](../lexicons/engineering.md#rlse-08)
- [`modern-software-engineering`](../SOURCES.md#src-modern-software-engineering): supports [RLSE-12](../lexicons/engineering.md#rlse-12)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not decide weight-licence compliance, training-data rights, or security review of a fork's supply chain beyond naming the fork as a production dependency. It does not claim every SERVE capacity rule or every PROV fairness/deletion rule is owned here. Rules outside the engineering and ml-systems inventories in scope for this card are not cited. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
