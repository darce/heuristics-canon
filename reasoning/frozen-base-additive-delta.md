# Frozen base, additive residual delta

Slug: `frozen-base-additive-delta`
Mechanism claim: When consumers already hold vectors or bind a shared trunk, adapt with a frozen base plus a zero-at-init additive residual so the base function stays bit-identical until trained and remains a control arm and rollback.

## Scope

Covers: decisions to adapt a shared embedding or foundation trunk while prior consumers, indexes, or eval routes still bind the pre-adaptation base checkpoint or space.
Excludes: green-field models with no persisted vectors or prior-task consumers; pure prompt or retrieval changes that leave weights untouched; full re-embed cutovers already planned under a new version identity; colour-identity or instruction-authority generation contracts.

## Observable triggers

- Training config or plan would put shared trunk tensors in the optimizer while a serve route, gallery index, or prior-task suite still names the pre-adaptation base.
- Residual, side-net, bottleneck adapter, or low-rank factors are added on a frozen stack without an identity-at-init rule in the run config.
- Vectors from a newly fine-tuned trunk and the old trunk would land in one index or one similarity query.
- A live embedding table, mapping, or upstream model output can hot-swap under production with no version pin.
- Full-weight fine-tune is the default adaptation before a PEFT residual path is tried.

## Causal mechanism

Persisted comparisons assume one geometry. Updating shared trunk weights under the same base identity moves every stored vector’s meaning without rewriting the store, so old and new coordinates share an index and pairwise scores lose their contract. An additive residual trained only on new modules, with trunk frozen and init that makes the composed forward equal the base at step 0, keeps the unadapted path available: training starts as a no-op, control-arm eval stays honest, and rollback does not require restoring overwritten weights. Skipping that leaves the cost of change as silent re-geometry of the corpus rather than a declared re-embed under a new version.

## Required action

While prior consumers bind the base, freeze trunk tensors (no grad; absent from optimizer param groups) and train only additive residual modules. Initialize so base and adapted forwards match on a fixed probe batch before the first optimizer step, within a declared tolerance, and record the init rule in the run config. Keep an unmerged base or trunk-only forward path (or retained base factors if residuals merge for deploy). Pin embedding and mapping versions for consumers; never mix spaces in one comparison. Prefer PEFT residual over full-weight adaptation until PEFT is shown insufficient. Dual-eval any cutover that would replace the space.

## Predicted failure

Trunk fine-tune silently changes the space. Old and new vectors coexist under one index or version label; similarities are incomparable. Failure shows as slow accuracy rot, not a hard train error, and is found months later when galleries and probes no longer share a contract.

## Exemptions and boundaries

- No prior consumer, no persisted vectors, and no shared-trunk binding: full fine-tune may still be wrong for other reasons, but this card’s freeze-and-delta obligation does not fire.
- A deliberate new embedding version with full re-embed, dual-eval, and cutover under a new pin: follow space and pin rules; do not fake a frozen base under the old ID.
- Prompt, retrieval, or tool-only adaptation with frozen weights: use the adaptation ladder; residual modules are not required.
- TRACK appearance gates and multi-target association are sibling identity problems in video linking, not this weight-adaptation mechanism.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object: trunk tensors | [FM-09](../lexicons/ml-systems.md#fm-09) freeze trunk; residual only | [FM-07](../lexicons/ml-systems.md#fm-07) / [FM-05](../lexicons/ml-systems.md#fm-05) adapt when cheaper layers fail | Train residual modules only; escalate full-weight only after PEFT miss on a declared target |
| surface: comparison space | [EMB-01](../lexicons/ml-systems.md#emb-01) one space per comparison | Domain need for a new geometry | New model/preprocess contract under a new pin; never mix old and new in one query or index |
| sequence: init then train | [FM-10](../lexicons/ml-systems.md#fm-10) identity at step 0 | Product pressure to ship a random-init adapter | Probe match before first optimizer step; reject base-shifting inits |
| sequence: promote upstream | [EMB-05](../lexicons/ml-systems.md#emb-05) / [DRIFT-02](../lexicons/ml-systems.md#drift-02) pin and dual-eval | Live “upstream fix” hot-swap | Promote only after consumer eval on a frozen versioned copy |

## Disconfirmers

- Base and adapted forwards already diverge at step 0 under the claimed identity init (mechanism’s safety property fails).
- No serve route, index, or prior-task suite still binds the pre-adaptation base (no shared-trunk consumer).
- Every consumer re-embeds under an explicit new version pin before any comparison uses the new space (cost is paid as re-embed, not silent geometry shift).
- Measured quality requires full-weight updates that residual PEFT cannot meet after a fair PEFT trial, and the cutover is versioned end-to-end.

## Verification

- Optimizer param groups list residual modules only; trunk has `requires_grad=False` or equivalent.
- Fixed probe batch: base vs adapted max deviation at step 0 within the declared tolerance; init rule present in run config.
- Deploy artifact retains trunk-only or unmerged base path for control-arm and rollback.
- Consumer requests name an embedding/map version; index build rejects mixed model IDs.
- Before space cutover: dual-eval on old and new pins is recorded; no single index holds both.

## Rule IDs

- [FM-09](../lexicons/ml-systems.md#fm-09): freeze shared trunk; train additive residual; keep unadapted path
- [FM-10](../lexicons/ml-systems.md#fm-10): identity-at-init so adaptation starts as a no-op on the base function
- [EMB-01](../lexicons/ml-systems.md#emb-01): forbid mixed spaces in one comparison or index
- [EMB-05](../lexicons/ml-systems.md#emb-05): pin embedding and mapping versions; dual-eval before cutover
- [DRIFT-02](../lexicons/ml-systems.md#drift-02): pin non-owned upstream signals that can hot-swap under production
- [FM-07](../lexicons/ml-systems.md#fm-07): try PEFT residual before full-weight adaptation
- [FM-05](../lexicons/ml-systems.md#fm-05): climb the adaptation ladder; do not jump to weight change unproven

## Principles

- 3. The safe side is cheap; the wrong side is not

## Evidence / source slugs

- [`residual-adapters-multi-domain`](../SOURCES.md#src-residual-adapters-multi-domain): supports [FM-09](../lexicons/ml-systems.md#fm-09), [FM-10](../lexicons/ml-systems.md#fm-10)
- [`side-tuning-additive`](../SOURCES.md#src-side-tuning-additive): supports [FM-09](../lexicons/ml-systems.md#fm-09)
- [`lora-low-rank-adaptation`](../SOURCES.md#src-lora-low-rank-adaptation): supports [FM-09](../lexicons/ml-systems.md#fm-09), [FM-10](../lexicons/ml-systems.md#fm-10)
- [`peft-adapters-nlp`](../SOURCES.md#src-peft-adapters-nlp): supports [FM-09](../lexicons/ml-systems.md#fm-09), [FM-10](../lexicons/ml-systems.md#fm-10)
- [`bruch-vector-retrieval`](../SOURCES.md#src-bruch-vector-retrieval): supports [EMB-01](../lexicons/ml-systems.md#emb-01)
- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [EMB-05](../lexicons/ml-systems.md#emb-05), [DRIFT-02](../lexicons/ml-systems.md#drift-02)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-05](../lexicons/ml-systems.md#fm-05), [FM-07](../lexicons/ml-systems.md#fm-07)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not cover catastrophic-forgetting regularizers as a substitute for a frozen trunk, trainable-fraction budgets as a standalone rule ID (none is in the inventory under that name), or project-specific re-embed tickets. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
