# Compose at the boundary before inside the graph

Slug: `compose-at-the-boundary-before-inside-the-graph`
ID: `CARD-20`
Mechanism claim: Two independently exported inference graphs composed as sequential runtime sessions keep a debuggable, independently versionable seam; merging them into one graph for unmeasured latency deletes that seam and turns graph-surgery defects into silent numeric drift.

## Scope

Covers: How to land a multi-stage inference path when two (or more) model graphs are independently exported and must run in sequence—compose at the session or owned I/O boundary first, or fuse into one graph—and what evidence earns a later merge.

Excludes: Single-export end-to-end graphs with no composition choice; train-time multi-task fusion recipes; continuous batching, KV-cache sizing, and scheduler tuning; service-mesh or microservice splits unrelated to inference graphs; any project ticket, slice name, or target metric.

## Observable triggers

- A plan or diff proposes merging two independently exported models into one runtime graph (or equivalent graph surgery) for the first production landing.
- Latency or hop count is given as the reason to fuse without a fixed-input parity suite against a two-session path.
- Each stage already exports alone and can be versioned, tested, or rolled back without rebuilding the other.
- A fused path is labeled equivalent without an exactness or bit-parity gate.
- Rollback or debug for stage A requires stage B to share the same graph artifact.

## Causal mechanism

Each independently exported graph has its own contract surface: inputs, outputs, versions, and failure modes. Sequential sessions preserve that surface as a real runtime seam, so stage A can fail, pin, or roll back without rewriting stage B. Graph merge deletes the seam to remove one session boundary. The latency win is a hypothesis until measured. Bad merges rarely fail loudly: shape errors may throw, but operator fusion, dtype promotion, intermediate pruning, and initializer rewrites often change numbers while still loading. Without a two-session reference and a bit-parity (or declared exact numerical equivalence) gate on a fixed input set, those defects ship as silent drift. Shipping boundary composition first keeps the reversible step behind evidence and keeps the two-session path as the oracle any fused path must match.

## Required action

While independently exported stages must run in sequence and a merge has not earned promotion:

1. Ship composition at the boundary: sequential runtime sessions (or an equivalent owned I/O handoff), each stage loadable, version-pinned, and revertible alone.
2. Do not promote a fused graph as the production path until a fixed input set shows bit-parity (or predeclared exact numerical equivalence) against the two-session reference; treat any deviation as an implementation defect, not an accepted quality trade.
3. Keep the two-session path as the reference implementation after any merge lands; the slower or simpler loop owns the oracle ([OBS-10](../lexicons/engineering.md#obs-10)).
4. Measure end-to-end latency of the two-session path before treating session-boundary cost as a reason to fuse ([PERF-06](../lexicons/engineering.md#perf-06)); classify whether delay is the hop or the compute ([PERF-16](../lexicons/engineering.md#perf-16)).
5. When a merge later ships, gate it as a behaviour-changing serving optimization under [SERVE-07](../lexicons/ml-systems.md#serve-07), with rollback written first ([RLSE-08](../lexicons/engineering.md#rlse-08)).

## Predicted failure

Skipping the action lands a fused graph as the first path. Graph-surgery and optimizer bugs surface as silent numeric drift rather than hard errors. Stages lose independent versioning and rollback ([RLSE-10](../lexicons/engineering.md#rlse-10)). Claimed latency wins stay unmeasured. Offline shapes and happy-path scores look fine while production numbers diverge from a staged path no longer kept as reference.

## Worked example

On-device launch wants the face embedder and the matcher fused into one optimized binary "to cut a hop," with no fixed-input parity suite. Ship them as sequential sessions first, pin the handoff tensor, and promote fusion only after bit-parity holds. Without that sequence, a graph-surgery bug looks like quiet score drift, and neither stage can roll back alone.

## Exemptions and boundaries

- One export already owns both stages end-to-end with no independent second artifact: composition choice does not arise; this card does not apply.
- A host allows only one loadable artifact: document the constraint; still retain an offline staged reference for parity where CI can run it.
- Bit-parity on the fixed suite plus a measured, material latency win on the real envelope: merge may promote; retire the two-session path only by evidence, not convenience.
- Train/serve featurization skew is [SERVE-08](../lexicons/ml-systems.md#serve-08); apply that row when transforms diverge, not when two graphs fuse.
- Continuous batching and KV-cache budgets are [SERVE-06](../lexicons/ml-systems.md#serve-06) and [SERVE-05](../lexicons/ml-systems.md#serve-05); they do not justify deleting a model-stage seam.
- Frozen-trunk additive residuals ([FM-09](../lexicons/ml-systems.md#fm-09), [FM-10](../lexicons/ml-systems.md#fm-10)) are the training-time cousin of keeping stages separable; this card is the serving composition decision, not the adapter training recipe.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence: first landing vs later optimize | [SERVE-01](../lexicons/ml-systems.md#serve-01) owned boundary; [REF-12](../lexicons/engineering.md#ref-12) no speculative fuse; [ARCH-08](../lexicons/engineering.md#arch-08) boring path first | [PERF-06](../lexicons/engineering.md#perf-06) measured delay; [COST-06](../lexicons/ml-systems.md#cost-06) remove proven waste | Ship two-session first; fuse only after measure and parity |
| object: fused artifact vs stage artifacts | [RLSE-10](../lexicons/engineering.md#rlse-10) each model separately revertible; [OBS-10](../lexicons/engineering.md#obs-10) reference owns truth | [SERVE-07](../lexicons/ml-systems.md#serve-07) parity-gated optimization may promote one path | Merge is a gated optimization over stage artifacts, not their replacement as oracle |
| surface: runtime seam vs in-graph edge | [API-10](../lexicons/engineering.md#api-10) and [SERVE-01](../lexicons/ml-systems.md#serve-01) handoff contract you own | In-graph edges only after [SERVE-07](../lexicons/ml-systems.md#serve-07) equivalence holds | Prefer session or API seam until parity proves internal edges preserve numbers |
| sequence: pin behaviour vs change structure | [TEST-03](../lexicons/engineering.md#test-03) pin current behaviour; [EVAL-08](../lexicons/ml-systems.md#eval-08) measure before accept | Structural fuse when the gate passes | Pin two-session outputs, then change graph structure |

## Disconfirmers

- On a fixed production-like input suite, a correctly built merge matches the two-session reference bit-for-bit (or within a predeclared exactness contract), and residual mismatches always fail closed rather than as quiet score drift.
- Measured session-boundary cost dominates the latency budget under realistic load, and no cheaper non-fuse fix removes it.
- Independent stage versioning is impossible by host constraint, and a staged offline reference is still retained solely for parity CI.
- Extended production observation for a given toolchain shows fused-graph defects always fail at load or shape check and never as silent numeric change (weakens the silent-drift claim for that toolchain only).

## Verification

- First landing runs two sequential sessions (or equivalent boundary handoff), not a single merged graph, unless a recorded parity gate has passed.
- A fixed input set exists; two-session outputs are stored as the reference; any merge job compares against them and fails closed on mismatch.
- Each stage artifact has its own version pin and rollback path; rolling back stage A does not require rebuilding stage B.
- Latency justification for a proposed merge cites measured two-session profiles ([PERF-06](../lexicons/engineering.md#perf-06)), not hop-count intuition.
- Experimental fuse branches are inventoried or removed from the live serve path ([SERVE-03](../lexicons/ml-systems.md#serve-03)).

## Rule IDs

- [SERVE-01](../lexicons/ml-systems.md#serve-01): own a stable I/O boundary so stages compose without freezing package glue
- [SERVE-07](../lexicons/ml-systems.md#serve-07): parity or exact-equivalence gate before promoting a merge that can change numerics
- [SERVE-03](../lexicons/ml-systems.md#serve-03): do not leave unearned fuse branches live beside the reference path
- [FM-09](../lexicons/ml-systems.md#fm-09): prefer additive or separable attachment over trunk fusion when residual composition is the mechanism
- [PERF-06](../lexicons/engineering.md#perf-06): measure session-boundary cost before optimizing it away
- [PERF-16](../lexicons/engineering.md#perf-16): classify whether delay is the hop or the compute before choosing fuse
- [REF-12](../lexicons/engineering.md#ref-12): refuse speculative graph generality until the need is real
- [ARCH-08](../lexicons/engineering.md#arch-08): land the boring two-session path before novel graph surgery
- [RLSE-08](../lexicons/engineering.md#rlse-08): write rollback for the fuse path before promoting it
- [RLSE-10](../lexicons/engineering.md#rlse-10): keep each stage a separately revertible model artifact
- [OBS-10](../lexicons/engineering.md#obs-10): two-session path remains the reference after optimization
- [TEST-03](../lexicons/engineering.md#test-03): pin two-session behaviour before structural change
- [EVAL-08](../lexicons/ml-systems.md#eval-08): accept a merge only after measured comparison on held inputs
- [API-10](../lexicons/engineering.md#api-10): stage handoff is its own interface artifact, not an internal tensor layout leak
- [COST-06](../lexicons/ml-systems.md#cost-06): remove proven waste only after the cheap path exists to compare

## Principles

- 3. The safe side is cheap; the wrong side is not
- 13. Evidence precedes commitment

## Evidence / source slugs

- [`side-tuning-additive`](../SOURCES.md#src-side-tuning-additive): supports [FM-09](../lexicons/ml-systems.md#fm-09)
- [`hidden-technical-debt-ml`](../SOURCES.md#src-hidden-technical-debt-ml): supports [SERVE-01](../lexicons/ml-systems.md#serve-01), [SERVE-03](../lexicons/ml-systems.md#serve-03)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [SERVE-07](../lexicons/ml-systems.md#serve-07)
- [`observability-engineering`](../SOURCES.md#src-observability-engineering): supports [ARCH-08](../lexicons/engineering.md#arch-08)
- [`restful-web-api-patterns`](../SOURCES.md#src-restful-web-api-patterns): supports [API-10](../lexicons/engineering.md#api-10)
- [`working-effectively-with-legacy-code`](../SOURCES.md#src-working-effectively-with-legacy-code): supports [TEST-03](../lexicons/engineering.md#test-03)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not encode vendor runtime compose APIs, graph-format specifications, or project-specific landing plans. It does not cover train/serve feature skew, continuous batching, or KV-cache capacity as primary decisions. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
