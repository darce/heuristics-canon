# Graph-Theory Heuristics Lexicon

## About this document

Decision rules for one move: recognising when a problem is a graph, and which
classical graph result then decides it. The engineering lexicon states this once
(`[ALG-01]`: most messy applied problems reduce to a classical graph problem
once vertices and edges are designed); this lexicon is that rule's expansion,
the specific structures (DAGs, cuts, matchings, spectra) and the decisions each
one forces. Referenced, not read end to end: a plan or review cites a rule by ID
where the modelling decision happens.

What it covers, four uses in reading order:

- dependency and reasoning structure: ordering, reachability, single points of
  failure, natural partitions
- assignment, cost, and importance: matching, shortest-path, colouring, spanning
  trees, centrality
- knowledge modelling: property graphs vs trees, ontologies as DAGs, provenance,
  graph vs table storage
- clustering and entity grouping: turning embeddings into a similarity graph and
  cutting it into entities

Scope boundary: decision heuristics, not a graph-algorithms textbook. It tells
you which structure a situation is and what that decides, not how to implement
Dijkstra or prove the four-colour theorem. Deep algorithm mechanics stay in the
texts.

Classical structure comes from Skiena's
[*The Algorithm Design Manual*](../SOURCES.md#src-algorithm-design-manual) and
Bondy and Murty's [*Graph Theory with Applications*](../SOURCES.md#src-graph-theory-with-applications);
knowledge-graph modelling from Barrasa and Webber's
[*Building Knowledge Graphs*](../SOURCES.md#src-building-knowledge-graphs). A
smaller set of pipeline rows is unsourced practice.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. Dependency & Reasoning Structure](#fam-grph)
- [2. Assignment, Cost & Importance](#2-assignment-cost--importance)
- [3. Knowledge Modelling as Graphs](#3-knowledge-modelling-as-graphs)
- [4. Clustering & Entity Grouping (embeddings → graphs)](#4-clustering--entity-grouping-embeddings--graphs)
- [5. Control Flow & Agent Loops as Graphs](#5-control-flow--agent-loops-as-graphs)
- [6. Cross-lexicon links](#6-cross-lexicon-links)
- [Consumption](#consumption)

<!-- END GENERATED CONTENTS -->

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[GRPH-01]` |
| Trigger | observable in a plan, data model, or implementation under review |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the decision is made |
| T·P | tier and phase, below |
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md) |

Tier: **B**locker (a wrong answer corrupts correctness or names the wrong
entity), **S**hould (strong default), **J**udgment. Phase: **p**lan (modelling
and design), **w**rite (implementation), **r**eview. Cross-lexicon borders cite
`↔ eng/sec` rules rather than restating them.


## 1. Dependency & Reasoning Structure<a name="fam-grph"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-01<a name="grph-01"></a> | Plan has ordered steps, build targets, migrations, or module dependencies | **Model the work as a DAG, then topological-sort**: only a directed *acyclic* dependency graph yields a legal execution order; sequence invented by gut invents illegal ones (↔ eng [[DATA-15]](engineering.md#data-15) order from the causal structure, not wall-clock or gut) | What are the nodes, the directed edges, and the proven acyclic order? | S·p | [The Algorithm Design Manual, ch. 7](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-02<a name="grph-02"></a> | Circular import, mutual service call, or A→B→C→A in the design | **A cycle is one indivisible unit**: no topological order exists until you break, invert, or fuse the cycle; "just start somewhere" is undefined behaviour (↔ eng [[CON-13]](engineering.md#con-13) circular wait has no legal entry until a partial order is imposed) | Where is the back-edge, and which edge do you cut or invert? | B·p | [Graph Theory with Applications: grounding distillation, ch. 10](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-03<a name="grph-03"></a> | "Will this change affect X?" asked without a reachability argument | **Answer by reachability, not intuition**: only nodes reachable from the change (descendants, or ancestors when tracing cause) can be affected; the rest is noise (↔ eng [[DIAG-07]](engineering.md#diag-07) a fault becomes a failure only along the coupling edges that spread it) | From this node, what is reachable under the dependency/dataflow edges? | S·r | [The Algorithm Design Manual, ch. 18](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-04<a name="grph-04"></a> | A rule, ACL, type bound, or cache invalidation must apply "and everything under it" | **Compute the transitive closure deliberately**: "everything under it" is a reachability query, not a one-hop check; a single missed hop is a silent leak | Is the decision using direct edges, or the full reachability relation? | S·w | [The Algorithm Design Manual, ch. 18](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-05<a name="grph-05"></a> | One module, service, person, or link whose removal would split the system | **Name the cut vertices and bridges as single points of failure**: articulation points and bridges are the *only* nodes/edges whose loss disconnects the graph (↔ biz [[BOOT-07]](business-marketing.md#boot-07) multi-home before the platform is a bridge) | If this node/edge dies, how many components remain, and is that acceptable? | S·p | [Graph Theory with Applications: grounding distillation, ch. 2](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-06<a name="grph-06"></a> | dependency, call, or org graph is being partitioned into modules, services, or ownership units without a connected-component inventory | **Partition by connected components first**: pieces with no path between them are the coarsest natural seams; cut there before inventing layers (↔ eng [[ARCH-01]](engineering.md#arch-01) a split needs a real disintegrator, not an invented layer) | What are the maximal pieces with no edge crossing between them? | S·p | [Graph Theory with Applications: grounding distillation, ch. 1](../SOURCES.md#src-graph-theory-with-applications) |

<!-- BEGIN GENERATED SECTION SOURCES fam-grph -->

**Sources for this section**

- [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual)
- [graph-theory-with-applications](../SOURCES.md#src-graph-theory-with-applications)

<!-- END GENERATED SECTION SOURCES fam-grph -->

## 2. Assignment, Cost & Importance

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-07<a name="grph-07"></a> | Assigning people↔tasks, pods↔nodes, or keys↔slots under capacity limits | **Cast assignment as bipartite matching, then flow**: two partitions plus edge capacities beat greedy pairing and expose infeasibility before you ship it | What are the two sides, the permitted edges, and is a complete matching possible? | S·p | [The Algorithm Design Manual, ch. 8](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-08<a name="grph-08"></a> | A plan represents alternative routes as an explicitly weighted graph and must choose a route | **Shortest weighted path**: define what each edge weight measures, then use the minimum-weight path as the cheapest route in that model. | What do the edge weights measure, and which route minimizes their total? | J·p | [The Algorithm Design Manual, ch. 8](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-09<a name="grph-09"></a> | Scheduling jobs, or allocating locks/registers/rooms with pairwise conflicts | **Colour the conflict graph**: the chromatic number is the minimum resources for a conflict-free assignment, and the largest clique is a hard lower bound on it | What is the conflict graph, and can it be coloured with the resources you have? | S·p | [Graph Theory with Applications: grounding distillation, ch. 8](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-10<a name="grph-10"></a> | Wiring a network, linking sites, or connecting stores at minimal total cost | **Prefer a minimum spanning tree over a full mesh**: the MST is the cheapest structure that keeps everything connected; every edge beyond it is paid-for redundancy, not connectivity | Is connectivity the goal, and is total edge weight minimised for it? | S·p | [The Algorithm Design Manual, ch. 8](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-11<a name="grph-11"></a> | A graph model assigns each vertex a weight through an adjacency eigenvector | **Score nodes by the recursive neighbour-sum (Perron eigenvector)**: under the adjacency-eigenvector equation a node's weight equals the sum of its neighbours' weights scaled by the eigenvalue, and for a connected nonnegative graph the positive Perron vector is the unique (up to scale) positive solution | What neighbour-sum equation does each eigenvector weight satisfy? | J·p | [Algebraic Graph Theory: grounding distillation, ch. 8](../SOURCES.md#src-algebraic-graph-theory) |

<!-- BEGIN GENERATED SECTION SOURCES 2-assignment-cost--importance -->

**Sources for this section**

- [algebraic-graph-theory](../SOURCES.md#src-algebraic-graph-theory)
- [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual)
- [graph-theory-with-applications](../SOURCES.md#src-graph-theory-with-applications)

<!-- END GENERATED SECTION SOURCES 2-assignment-cost--importance -->

## 3. Knowledge Modelling as Graphs

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-12<a name="grph-12"></a> | Knowledge, docs, or entities that need lateral or multi-type relationships beyond a pure hierarchy | **Admit non-hierarchical edges as first-class**: a labelled property graph places no limit on relationship count or type, and ontologies are not restricted to hierarchical structures, so cross-cutting links stay model edges rather than out-of-band notes (↔ eng [[MODEL-01]](engineering.md#model-01) the data model must admit the relationships the access pattern needs) | Which relationships are non-hierarchical, and does the model allow them as first-class edges? | S·p | [Building Knowledge Graphs: grounding distillation, ch. 2](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-13<a name="grph-13"></a> | A taxonomy, ontology, or type system that admits only one parent per concept | **Allow multi-parent / multi-hierarchy membership**: broader–narrower taxonomies support multi-category attachment and composing multiple organisational hierarchies at once; a single-parent schema rejects valid dual membership | Can a concept belong to two categories without breaking the schema? | S·p | [Building Knowledge Graphs: grounding distillation, ch. 2](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-14<a name="grph-14"></a> | Claims, datasets, or model outputs stored without lineage | **Record provenance as a walkable lineage graph**: every artifact points at the inputs that produced it so an audit can walk sources and producers, and a filename cannot (↔ eng [[DATA-14]](engineering.md#data-14): one authority owns the lineage) | For this claim, what is the ancestor path back to primary evidence? | S·w | [Building Knowledge Graphs: grounding distillation, ch. 8](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-15<a name="grph-15"></a> | Choosing storage when a query requires recursive, arbitrary-depth path analysis | **Graph storage for deep paths**: use a graph when the query requires recursive, arbitrary-depth path analysis, because relational technology was not designed for that operation (↔ eng [[MODEL-01]](engineering.md#model-01) derive graph vs table from the primary access pattern) | Does this query require recursive or arbitrary-depth path analysis? | J·p | [Building Knowledge Graphs: grounding distillation, ch. 11](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-16<a name="grph-16"></a> | A domain narrative that "everything depends on everything" | **Cut at low-conductance seams, not invented layers**: modular structure is dense-within / sparse-between, so partition where cuts have few external edges relative to denser regions (conductance / expansion), not where an org chart draws a box (↔ eng [[ARCH-01]](engineering.md#arch-01) both refuse a split with no measured driver behind it) | Where are the sparse cuts that let this be modularised? | S·p | [Graph Partitioning and Graph Clustering: grounding distillation, §natural-cuts](../SOURCES.md#src-graph-partitioning-and-clustering) |
| GRPH-24<a name="grph-24"></a> | A retrieval/research stage enumerates its full query set before any result is read; no edge from any retrieval result back into query generation | **Generate query k from the answers to 1..k−1**: when a retrieval stage produces its own queries, emit them one at a time conditioned on what earlier queries returned, never as an up-front batch, because a fixed question budget spent as one unconditioned batch collapses coverage and can underperform a no-retrieval baseline (↔ ml [[HITL-01]](ml-systems.md#hitl-01), the same conditioning discipline on label acquisition). Exempt: fixed compliance checklists and schema-driven extraction, where the query set is genuinely knowable in advance; latency-bound paths pay a serialisation cost that sequential conditioning incurs. | Which of these queries was written before any result came back? | S·p | [STORM: multi-perspective pre-writing, ch. 5](../SOURCES.md#src-storm-multi-perspective-prewriting) |
| GRPH-25<a name="grph-25"></a> | A program- or model-grown knowledge hierarchy has empty leaves or unary nodes, or is being structurally reorganized after new information is inserted | **A grown hierarchy must contain no contentless leaf and no unary chain**: in each structural reorganization, trim empty leaves to a fixpoint, merge one-child nodes bottom-up by retaining each parent and absorbing the child's content and grandchildren, expand nodes at the configured item-count threshold only when the split yields more than one subsection, then trim and merge again and recompute all paths; deleting a leaf can orphan its parent and a unary node classifies nothing (↔ eng [[MODEL-02]](engineering.md#model-02) for the item-count threshold that triggers a split) | Did the pass trim, merge, expand, clean again, and recompute paths, leaving no empty leaf or unary node? | S·w | [STORM / Co-STORM knowledge curation system](../SOURCES.md#src-storm-knowledge-curation-system) |
| GRPH-35<a name="grph-35"></a> | A generator writes over a context window pooling items retrieved by independent research branches | **Co-presence is not an edge**: when the generation context pools several retrieval branches, gate at the sentence level on entailment against the *specific* cited item and require a source that asserts any relation the sentence asserts, because enlarging the pool improves organisation and coverage while leaving unsupported *joins* between co-present facts as a dominant error class, invisible to hallucination checks when each fact exists and only the link is invented (↔ [[GRPH-18]](graph-theory.md#grph-18) same false-edge failure class, different edge source; ↔ [[GRPH-14]](graph-theory.md#grph-14) provenance edges need their own admission test) | For each sentence joining two retrieved facts, which single source asserts the join? | B·r | [STORM: multi-perspective pre-writing, ch. 11](../SOURCES.md#src-storm-multi-perspective-prewriting) |
| GRPH-37<a name="grph-37"></a> | A knowledge graph, mind map, or concept hierarchy is the system of record for the items it organises | **Keep the concept hierarchy a disposable projection over a flat evidence table**: when a curation system maintains a browsable hierarchy, store each item once under a stable surrogate id, let nodes hold only id sets, and treat ancestor paths as derived metadata recomputed after every rewrite, because only then is automatic restructuring free of data migration (↔ eng [[DATA-14]](engineering.md#data-14) one authority owns the record; ↔ [[GRPH-15]](graph-theory.md#grph-15) tables for the fixed payload when the navigable layer is a projection) | If the hierarchy were deleted and rebuilt from the item table, would any item or citation be lost? | S·p | [STORM / Co-STORM knowledge curation system](../SOURCES.md#src-storm-knowledge-curation-system) |
| GRPH-38<a name="grph-38"></a> | Assignment into a hierarchy decided by a single top-1 similarity match, with no "none of these" branch | **Shortlist by similarity, adjudicate, allow abstention, backstop with traversal**: rank top-k candidate paths by embedding, let a judge pick one *or* return "no reasonable choice", and route abstention into a deterministic root-down walk that always terminates at a node, because a ranker with no abstain places everything and one with no backstop drops what it abstains on (↔ [[GRPH-22]](graph-theory.md#grph-22) partition-plus-verification; ↔ [[GRPH-36]](graph-theory.md#grph-36) similarity ranks, never adjudicates) | What happens to an item the ranker has no good slot for: silently placed, dropped, or re-decided by an exhaustive pass? | S·w | [STORM / Co-STORM knowledge curation system](../SOURCES.md#src-storm-knowledge-curation-system) |
| GRPH-39<a name="grph-39"></a> | Placement, classification, or assignment work over a mutable graph is run on a thread pool or parallel map | **Parallelise only against a frozen topology**: when the callee can create or move nodes, run sequentially and re-derive the structure snapshot per item; parallelise only when the structure provably cannot change, because a decision computed off a stale snapshot resolves to a path that has moved, and a write-side mutex does not cover the decision | Can any worker in this pool create or move a node while another worker is deciding a path? | B·w | [STORM / Co-STORM knowledge curation system](../SOURCES.md#src-storm-knowledge-curation-system) |

<!-- BEGIN GENERATED SECTION SOURCES 3-knowledge-modelling-as-graphs -->

**Sources for this section**

- [building-knowledge-graphs](../SOURCES.md#src-building-knowledge-graphs)
- [graph-partitioning-and-clustering](../SOURCES.md#src-graph-partitioning-and-clustering)
- [storm-knowledge-curation-system](../SOURCES.md#src-storm-knowledge-curation-system)
- [storm-multi-perspective-prewriting](../SOURCES.md#src-storm-multi-perspective-prewriting)

<!-- END GENERATED SECTION SOURCES 3-knowledge-modelling-as-graphs -->

## 4. Clustering & Entity Grouping (embeddings → graphs)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-17<a name="grph-17"></a> | Building identity or similarity clusters from embeddings | **Build a mutual k-NN graph, not a complete similarity graph**: all-pairs edges are O(n²) and over-connect impostors; each node keeping its k nearest (ideally mutual) neighbours bounds both cost and false links (↔ eng [[PERF-05]](engineering.md#perf-05) both fail when an all-pairs construction meets production scale) | Is the graph mutual-kNN with k chosen on validation, not "all pairs above τ"? | S·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-18<a name="grph-18"></a> | Clustering entities by thresholding similarity, then taking connected components | **Never trust the transitive closure of a raw similarity threshold**: A~B and B~C does not make A~C; a chain of borderline matches glues distinct entities into one cluster (the chaining failure), and when that cluster is named, it names the wrong one (↔ sec [[SEC-05]](security.md#sec-05): the clustering analogue of the irreversible LLM action it gates) | On held-out pairs, how often does a path link entities verified as different? | B·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-19<a name="grph-19"></a> | Splitting an over-merged cluster, or choosing where to cut | **Cut on normalised cut / conductance, not plain min-cut**: unnormalised min-cut shaves off single outliers; a normalised objective balances the cut against cluster volume and finds the real boundary | Does the cut minimise the boundary relative to cluster size, or just raw edge weight? | S·w | [Spectral Clustering and Biclustering: grounding distillation, ch. 2](../SOURCES.md#src-spectral-clustering-and-biclustering) |
| GRPH-20<a name="grph-20"></a> | Choosing whether a graph has a two-cluster spectral split using the normalized Laplacian eigengap | **Use the two-way Laplacian eigengap as evidence**: for two clusters, a larger gap between the two smallest positive normalized-Laplacian eigenvalues supports better classification of the spectral representatives and a small 2-way normalized cut; use the Fiedler vector for the primary split, and do not generalize this result to k > 2 without further analysis | Is this a two-cluster case, and what is the gap between the two smallest positive normalized-Laplacian eigenvalues? | S·w | [Spectral Clustering and Biclustering: grounding distillation, ch. 2](../SOURCES.md#src-spectral-clustering-and-biclustering) |
| GRPH-21<a name="grph-21"></a> | A graph community-detection implementation needs an objective for comparing candidate partitions | **Modularity as a community-detection objective**: consider modularity, a popular graph-clustering objective, while accounting for its NP-hard optimum and the listed heuristics—spectral, divisive, and agglomerative methods; a later pair-level audit of residual bridges is [[GRPH-22]](graph-theory.md#grph-22), not part of the modularity objective | Is modularity the objective being considered, and how will the search handle its NP-hard optimum? | J·w | [Graph Partitioning and Graph Clustering: grounding distillation, §modularity](../SOURCES.md#src-graph-partitioning-and-clustering) |
| GRPH-22<a name="grph-22"></a> | Production clustering still merges distinct entities or splits one entity | **Replace hard-τ-plus-components with partition-plus-verification**: keep only high-precision edges, cut with a constrained objective ([[GRPH-19]](graph-theory.md#grph-19); community detection at scale is [[GRPH-21]](graph-theory.md#grph-21)), then re-verify the residual cross-group bridges pairwise; gate on pair precision/recall at the operating edge set, not component purity | What is pair-level precision at the operating edge set, and which bridges are re-verified? | S·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-23<a name="grph-23"></a> | A similarity graph built with one global cosine/L2 threshold | **Calibrate the edge policy per quality stratum**: pose, age, and capture quality shift the similarity distribution, so one global τ over-links easy negatives and under-links hard positives; use adaptive or learned thresholds per regime (edge construction itself: see [[GRPH-17]](graph-theory.md#grph-17)) | Is the edge policy validated across quality strata, or only on clean high-quality pairs? | S·w | [Handbook of Face Recognition (3rd ed.), ch. 11](../SOURCES.md#src-handbook-face-recognition) |
| GRPH-36<a name="grph-36"></a> | An eval scores free-text answers by cosine similarity to a reference, with short or numeric reference answers | **Similarity ranks candidates; it never issues the verdict**: when scoring correctness, use a rubric that separates correctness from relatedness and demands per-score justification, because embedding similarity can rank a wrong answer nearly as high as a right one when both are topically related, while a correctness rubric separates them cleanly (↔ [[GRPH-18]](graph-theory.md#grph-18) the score proposes, something else decides) | Would this metric clearly separate a right verbose answer from a wrong verbose one, or only rank topical relatedness? | B·r | [ChatP&ID — GraphRAG for engineering diagrams, ch. 5](../SOURCES.md#src-chatpid-graphrag-engineering-diagrams) |

<!-- BEGIN GENERATED SECTION SOURCES 4-clustering--entity-grouping-embeddings--graphs -->

**Sources for this section**

- [chatpid-graphrag-engineering-diagrams](../SOURCES.md#src-chatpid-graphrag-engineering-diagrams)
- [graph-partitioning-and-clustering](../SOURCES.md#src-graph-partitioning-and-clustering)
- [handbook-face-recognition](../SOURCES.md#src-handbook-face-recognition)
- [spectral-clustering-and-biclustering](../SOURCES.md#src-spectral-clustering-and-biclustering)
- [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice)

<!-- END GENERATED SECTION SOURCES 4-clustering--entity-grouping-embeddings--graphs -->

## 5. Control Flow & Agent Loops as Graphs

The first four sections treat a graph as a thing you *analyse*: a dependency order, an
assignment, a taxonomy, a similarity structure. This section treats a graph as the thing the
system **executes**: states as nodes, transitions as edges, the run as a walk. Agent frameworks
arrived here by their own route (chains → loops → graphs) and rediscovered the finite state
machine, so the rules below are stated in the classical vocabulary rather than any framework's.

**Read the cycle partition before applying anything here.** `[GRPH-02]` ("a cycle is one
indivisible unit") governs *dependency* graphs, where a cycle means nothing can be built first
and the only remedy is to cut, invert, or fuse an edge. The rules below govern *control-flow
iteration*, where the back-edge is deliberate (a retry, a re-plan, a loop until nothing new
appears) and the discipline is a termination argument (`GRPH-30`), not an edge cut. Applying
`[GRPH-02]` to a discovery loop forbids a correct pattern; applying `GRPH-30` to a circular
import licenses an unbuildable system. Naming which graph you are holding is the first move.

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-26<a name="grph-26"></a> | A formal finite-state or Turing-machine model represents an unbounded quantity or payload as another control-state variant | **Split the finite control from the unbounded store**: keep a formal machine’s state set finite and represent unbounded contents in its store or configuration, such as a Turing machine’s tape, because a configuration carries both finite control and tape contents (↔ [[GRPH-27]](graph-theory.md#grph-27) states × events coverage becomes infeasible once control itself is unbounded) | Is this datum part of the finite control set, or part of the machine’s potentially unbounded store? | S·p | [Models of Computation (Erickson): grounding distillation, §TM](../SOURCES.md#src-erickson-models-of-computation) |
| GRPH-27<a name="grph-27"></a> | A stateful event handler or transition model dispatches by event without making current state part of the transition relation | **Key the transition on (state, event), state first**: model allowed transitions as explicit state/event pairs; make a machine total over every pair or give undefined pairs an explicit reject/fail path, rather than implying an omitted pair is a no-op (↔ ml [[FM-04]](ml-systems.md#fm-04), which admits shape, not legality; ↔ sec [[SEC-05]](security.md#sec-05) for the gate it leads to; ↔ eng [[REF-02]](engineering.md#ref-02), which keys a handler map on one dimension; this requires two). Exempt: an event whose effect is identical from every mode needs no state key. | Which (state, event) pairs are defined, and what explicit path handles every other pair? | S·w | [Models of Computation (Erickson): grounding distillation, §DFA](../SOURCES.md#src-erickson-models-of-computation) |
| GRPH-28<a name="grph-28"></a> | The same transition label (`DISCONNECT`, `CANCEL`) appears on every member of a group of states | **Pull up a duplicated transition (Pull Up Method)**: when sibling states share the same transition handler, declare it once on the common parent type rather than copying it onto each sibling, because duplicated sibling members are a breeding ground for silent divergence and the state added last is the one missing the edge (Fowler's Pull Up Method on a transition graph; ↔ [[REF-10]](engineering.md#ref-10) hoist only genuinely-shared behavior, not edges that merely look alike). Exempt: a group small enough that the hierarchy costs more than the duplication; and note that hoisting hides the edge from a flat read of any one child. | Which transition labels are repeated across siblings, and does every sibling carry all of them? | S·w | [Refactoring: Improving the Design of Existing Code (2nd ed), ch. 12](../SOURCES.md#src-refactoring-fowler-beck) |
| GRPH-29<a name="grph-29"></a> | A log-backed stream consumer must recover or hand off after a failure | **Resume from a durable position**: persist the consumer offset and resume from the last recorded offset after a failure, because a replacement consumer can continue where the failed consumer left off | Which durable offset lets a replacement consumer resume after failure? | S·p | [Designing Data-Intensive Applications, ch. 11](../SOURCES.md#src-designing-data-intensive-applications) |
| GRPH-30<a name="grph-30"></a> | A loop-until-dry / repeat-until-nothing-new search dedupes candidates against the *accepted* or *confirmed* set | **Dedupe against everything ever surfaced, not against what was accepted**: in a loop-until-dry search, every candidate that has ever appeared, *including rejected ones*, enters a monotone seen-set, because deduping only against accepted results makes rejects resurface every round, no round is ever empty, the dry-round predicate never fires, and the run pays to rediscover the same dead ends until the budget is gone. Bound the loop itself per ml [[FM-08]](ml-systems.md#fm-08): a dry-round rule is a heuristic stopping rule, not a termination proof, and a semantic near-duplicate with a distinct key defeats the seen-set (↔ [[GRPH-18]](graph-theory.md#grph-18): a *similarity*-based seen-set can instead glue distinct candidates and suppress real findings). (this is graph traversal's discovered/processed set: mark a candidate the first time it is surfaced, never on acceptance, exactly as BFS ignores an edge into an already-discovered vertex; the loop-until-dry search is the agent application of that visited-set discipline) | What exactly enters the seen-set: does a *rejected* candidate enter it? | S·w | [The Algorithm Design Manual, ch. 7](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-31<a name="grph-31"></a> | A set of tasks with dependencies must run across workers, threads, or lanes and the schedule or degree of parallelism is being guessed | **Critical-path schedule the task DAG**: with unlimited workers, the critical path is the makespan floor; in topological order, start each job when its latest prerequisite completes. With a finite worker count and arbitrary precedence, makespan is strongly NP-hard; for unit-time jobs with tree precedence, the Critical Path (CP) rule prioritizes a ready job at the head of the longest string (↔ [[GRPH-01]](graph-theory.md#grph-01) the DAG is the substrate this schedules over; ↔ [[GRPH-09]](graph-theory.md#grph-09) pairwise interference without precedence is the sibling colouring structure, not this; ↔ [[PERF-04]](engineering.md#perf-04) the DAG's serial spine still caps speedup by Amdahl). | What is the unlimited-worker critical-path floor, and when can each job start? Is finite-worker precedence arbitrary, or unit-time tree, and which CP priority applies? | S·p | [The Algorithm Design Manual, ch. 17](../SOURCES.md#src-algorithm-design-manual) + [Scheduling: Theory, Algorithms, and Systems, ch. 5](../SOURCES.md#src-pinedo-scheduling) |
| GRPH-32<a name="grph-32"></a> | An agent pipeline whose steps are chained by "and then" with no data passed between them | **An edge exists only where data moves**: when a step is sequenced after another, require that the downstream node actually read a named field of the upstream node's output, and delete the arrow when no such field can be named, because arrows inherited from typing order serialize independent work for nothing (↔ eng [[DATA-15]](engineering.md#data-15) order from the causal structure, not wall-clock or gut; ↔ [[GRPH-01]](graph-theory.md#grph-01) toposort only after the edges are real). Exempt: arrows required for side-effect order, resource exclusivity, rate limits, or idempotency even when no data field is read — name the non-data constraint instead of deleting the edge. | For this arrow, which field of the previous output does the next node read? | S·p | [bootstrap](../SOURCES.md#src-bootstrap) |
| GRPH-33<a name="grph-33"></a> | A node reads from shared conversation context, or returns free text a later node must parse | **A node without a contract cannot be parallelised**: when a node is to run concurrently, pass its inputs explicitly and constrain its output with a schema the runtime validates, because an implicit shared-window read is an undeclared in-edge that makes the drawn topology not the real one (↔ [[GRPH-32]](graph-theory.md#grph-32) declared edges must carry named data) | What are this node's declared inputs, and does it still produce the same output in a fresh context? | S·w | [bootstrap](../SOURCES.md#src-bootstrap) |
| GRPH-34<a name="grph-34"></a> | A model-backed node whose whole job is flatten, dedupe, filter, sort, or reshape between two stages | **Edge work is code, not a node**: when a step is a pure function of shapes already returned upstream, move it into the orchestration script, because orchestration executed as code costs zero model tokens and is reproducible, while a node costs a turn and can perform a deterministic transform wrongly (↔ [[GRPH-32]](graph-theory.md#grph-32) an edge is a data promise, not a model turn) | Is this step judgment on content, or a pure function of the shapes upstream already returned? | S·w | [bootstrap](../SOURCES.md#src-bootstrap) |

<!-- BEGIN GENERATED SECTION SOURCES 5-control-flow--agent-loops-as-graphs -->

**Sources for this section**

- [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual)
- [bootstrap](../SOURCES.md#src-bootstrap)
- [designing-data-intensive-applications](../SOURCES.md#src-designing-data-intensive-applications)
- [erickson-models-of-computation](../SOURCES.md#src-erickson-models-of-computation)
- [pinedo-scheduling](../SOURCES.md#src-pinedo-scheduling)
- [refactoring-fowler-beck](../SOURCES.md#src-refactoring-fowler-beck)

<!-- END GENERATED SECTION SOURCES 5-control-flow--agent-loops-as-graphs -->

## 6. Cross-lexicon links

Graph theory is a spanning way of *seeing*, so its rules border several lexicons rather than sitting apart:

- **Parent rule.** This lexicon expands engineering's `[ALG-01]` ("graph in disguise"). Where `[ALG-01]` says *recognise the graph*, `GRPH-01..16` say *which graph, and what it then decides*. Hardness still defers to `[ALG-05]` and the brute-force budget to `[ALG-02]`: colouring (`GRPH-09`) and balanced cuts are NP-hard in general, so pick the escape (exact / approximation / heuristic) deliberately.
- **Cost & scale.** `GRPH-17` (mutual k-NN over all-pairs) is engineering's `[PERF-05]` (O(n²) on a hot path) in graph form: the complete similarity graph *is* the quadratic blow-up.
- **Authority & lineage.** `GRPH-14` (provenance as a directed graph) meets `[DATA-14]` (no dual writes; one authority owns the record). Both insist a derived fact points back to a single source of truth.
- **Architecture seams.** `GRPH-06` and `GRPH-16` (partition by components / sparsify at low-conductance cuts) are the measurement behind `[ARCH-01]` (a service split needs a real disintegrator): the sparse cut is the disintegrator made visible.
- **High-harm automation.** `GRPH-18` (the chaining failure) borders `[SEC-05]`, which gates an LLM's irreversible actions behind a human: a borderline merge that *names* an entity is the clustering analogue of the action that rule gates. Extending the gate to non-LLM automated naming is where a future **ML/embeddings and fairness pass** attaches: per-cohort error rates and confidence-gated naming would live there, citing `GRPH-18/22` as their clustering substrate.

## Consumption

Referenced by ID at the decision point, never read front-to-back. `GRPH-01..16` and `GRPH-24..25` fire mostly at **plan/design**: when a spec has ordering, conflicts, hierarchy, retrieval, or "everything connects to everything," cite the row that names the structure. `GRPH-17..23` are the **applied core**: they fire in clustering and entity-curation code, and `GRPH-18` (`B·w`) is the one to cite on any pipeline that thresholds similarity and unions the result: it is the single rule standing between a similarity graph and a wrongly-merged identity. `GRPH-26..30` are the **control-flow core**: they fire on any state machine, agent loop, or scheduler, and `GRPH-27` is the one to cite when a dispatcher decides what an event may do: it is where an illegal-but-well-formed event is refused by construction rather than by prompt. A consuming harness inlines the trigger plus the question by phase tag and cites the ID; the argument stays here.
