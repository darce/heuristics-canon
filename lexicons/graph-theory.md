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

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. Dependency & Reasoning Structure](#1-dependency--reasoning-structure)
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
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md); the distillation behind it stays in the private research corpus |

Tier: **B**locker (a wrong answer corrupts correctness or names the wrong
entity), **S**hould (strong default), **J**udgment. Phase: **p**lan (modelling
and design), **w**rite (implementation), **r**eview. Cross-lexicon borders cite
`↔ eng/sec` rules rather than restating them.


## 1. Dependency & Reasoning Structure

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-01<a name="grph-01"></a> | Plan has ordered steps, build targets, migrations, or module dependencies | **Model the work as a DAG, then topological-sort**: only a directed *acyclic* dependency graph yields a legal execution order; sequence invented by gut invents illegal ones (↔ eng [[DATA-15]](engineering.md#data-15) order from the causal structure, not wall-clock or gut) | What are the nodes, the directed edges, and the proven acyclic order? | S·p | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-02<a name="grph-02"></a> | Circular import, mutual service call, or A→B→C→A in the design | **A cycle is one indivisible unit**: no topological order exists until you break, invert, or fuse the cycle; "just start somewhere" is undefined behaviour (↔ eng [[CON-13]](engineering.md#con-13) circular wait has no legal entry until a partial order is imposed) | Where is the back-edge, and which edge do you cut or invert? | B·p | [graph-theory-with-applications ch-10](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-03<a name="grph-03"></a> | "Will this change affect X?" asked without a reachability argument | **Answer by reachability, not intuition**: only nodes reachable from the change (descendants, or ancestors when tracing cause) can be affected; the rest is noise (↔ eng [[DIAG-07]](engineering.md#diag-07) a fault becomes a failure only along the coupling edges that spread it) | From this node, what is reachable under the dependency/dataflow edges? | S·r | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-04<a name="grph-04"></a> | A rule, ACL, type bound, or cache invalidation must apply "and everything under it" | **Compute the transitive closure deliberately**: "everything under it" is a reachability query, not a one-hop check; a single missed hop is a silent leak | Is the decision using direct edges, or the full reachability relation? | S·w | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-05<a name="grph-05"></a> | One module, service, person, or link whose removal would split the system | **Name the cut vertices and bridges as single points of failure**: articulation points and bridges are the *only* nodes/edges whose loss disconnects the graph (↔ biz [[BOOT-07]](business-marketing.md#boot-07) multi-home before the platform is a bridge) | If this node/edge dies, how many components remain, and is that acceptable? | S·p | [graph-theory-with-applications ch-2](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-06<a name="grph-06"></a> | A system, codebase, or org that reads as one ball of mud | **Partition by connected components first**: pieces with no path between them are the coarsest natural seams; cut there before inventing layers (↔ eng [[ARCH-01]](engineering.md#arch-01) a split needs a real disintegrator, not an invented layer) | What are the maximal pieces with no edge crossing between them? | S·p | [graph-theory-with-applications ch-1](../SOURCES.md#src-graph-theory-with-applications) |

## 2. Assignment, Cost & Importance

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-07<a name="grph-07"></a> | Assigning people↔tasks, pods↔nodes, or keys↔slots under capacity limits | **Cast assignment as bipartite matching, then flow**: two partitions plus edge capacities beat greedy pairing and expose infeasibility before you ship it | What are the two sides, the permitted edges, and is a complete matching possible? | S·p | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-08<a name="grph-08"></a> | Choosing among justifications, migration paths, or root-cause chains | **Shortest weighted path is the cheapest sufficient explanation**: weight edges by cost/risk/latency and the min-weight path is the claim you can defend; the framing forces you to name the weights | What edge weights define "cheap," and which path minimises their sum? | J·p | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-09<a name="grph-09"></a> | Scheduling jobs, or allocating locks/registers/rooms with pairwise conflicts | **Colour the conflict graph**: the chromatic number is the minimum resources for a conflict-free assignment, and the largest clique is a hard lower bound on it | What is the conflict graph, and can it be coloured with the resources you have? | S·p | [graph-theory-with-applications ch-8](../SOURCES.md#src-graph-theory-with-applications) |
| GRPH-10<a name="grph-10"></a> | Wiring a network, linking sites, or connecting stores at minimal total cost | **Prefer a minimum spanning tree over a full mesh**: the MST is the cheapest structure that keeps everything connected; every edge beyond it is paid-for redundancy, not connectivity | Is connectivity the goal, and is total edge weight minimised for it? | S·p | [algorithm-design-manual](../SOURCES.md#src-algorithm-design-manual) |
| GRPH-11<a name="grph-11"></a> | Ranking which service, person, or concept matters most in a network | **Rank importance by eigenvector centrality, not raw degree**: a node's weight is the recursive sum of its neighbours' weights, so endorsement by important nodes outranks many weak links (the Perron eigenvector); degree and betweenness answer narrower questions (local load, bridge traffic) and are the cheaper checks to rule out first | Is "important" recursive endorsement, or would a degree/betweenness count answer the real question? | J·p | [algebraic-graph-theory ch-8](../SOURCES.md#src-algebraic-graph-theory) |

## 3. Knowledge Modelling as Graphs

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-12<a name="grph-12"></a> | Knowledge, docs, or entities forced into a single-parent folder tree | **Use a labelled property graph when cross-links exist**: a tree forbids multiple parents and lateral edges; real knowledge has both, and the tree silently drops them (↔ eng [[MODEL-01]](engineering.md#model-01) the data model must admit the relationships the access pattern needs) | Which relationships are non-hierarchical, and does the model allow them as first-class edges? | S·p | [building-knowledge-graphs ch-2](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-13<a name="grph-13"></a> | A taxonomy, ontology, or type system drawn as a strict hierarchy | **Model is-a / broader–narrower as a DAG, not a tree**: polyhierarchy is normal; forcing one parent fabricates a classification that is not true | Can a concept have two parents without breaking the schema? | S·p | [building-knowledge-graphs ch-2](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-14<a name="grph-14"></a> | Claims, datasets, or model outputs stored without lineage | **Record provenance as a directed acyclic citation graph**: every artifact points at the inputs that produced it; an audit walks ancestors, and a filename cannot (↔ eng [[DATA-14]](engineering.md#data-14): one authority owns the lineage) | For this claim, what is the ancestor path back to primary evidence? | S·w | [building-knowledge-graphs ch-8](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-15<a name="grph-15"></a> | Choosing storage for highly relational data: rows/columns vs nodes/edges | **Tables for fixed attributes; a graph when the query is a path**: join-heavy multi-hop "who connects to whom" is graph-native; flat fixed-schema aggregation is not (↔ eng [[MODEL-01]](engineering.md#model-01) derive graph vs table from the primary access pattern) | Is the dominant question multi-hop traversal, or fixed-schema aggregation? | J·p | [building-knowledge-graphs ch-11](../SOURCES.md#src-building-knowledge-graphs) |
| GRPH-16<a name="grph-16"></a> | A domain narrative that "everything depends on everything" | **Make the dense graph explicit, then sparsify at the low-conductance cuts**: a near-complete dependency graph is the absence of architecture; the modular seams are the sparse cuts you can only see once it is drawn (↔ eng [[ARCH-01]](engineering.md#arch-01) both refuse a split with no measured driver behind it) | Where are the sparse cuts that let this be modularised? | S·p | [graph-partitioning-and-clustering §natural-cuts](../SOURCES.md#src-graph-partitioning-and-clustering) |
| GRPH-24<a name="grph-24"></a> | A retrieval/research stage enumerates its full query set before any result is read; no edge from any retrieval result back into query generation | **Generate query k from the answers to 1..k−1**: when a retrieval stage produces its own queries, emit them one at a time conditioned on what earlier queries returned, never as an up-front batch, because the same question budget issued as one batch dropped unique references 99.83→39.56 and entity recall 40.52→31.98 (Tables 3/5, GPT-3.5): below the *no-retrieval* baseline of 32.39, i.e. the batch was worse than not retrieving at all (↔ ml [[HITL-01]](ml-systems.md#hitl-01), the same conditioning discipline on label acquisition). Exempt: fixed compliance checklists and schema-driven extraction, where the query set is genuinely knowable in advance; latency-bound paths pay a serialisation cost the source never priced. | Which of these queries was written before any result came back? | S·p | [storm-multi-perspective-prewriting](../SOURCES.md#src-storm-multi-perspective-prewriting) |
| GRPH-25<a name="grph-25"></a> | A hierarchy *grown or generated* by a program or model (not authored by a human) is being finalised or serialised | **A grown hierarchy must contain no contentless leaf and no unary chain**: trim empty leaves to a *fixpoint* and merge every node that has exactly one child into that child, because deleting one leaf can orphan its parent (a single pass is not enough) and a node with exactly one child classifies nothing (↔ eng [[MODEL-02]](engineering.md#model-02) for the item-count threshold that triggers a *split*). Exempt: human-authored taxonomies where a single-child level is semantically load-bearing (statutory numbering, a required biological rank), and intentional placeholders awaiting content; the trim pass destroys both. | Does the finished structure contain any empty leaf, or any node with exactly one child? | S·w | [storm-knowledge-curation-system](../SOURCES.md#src-storm-knowledge-curation-system) |

## 4. Clustering & Entity Grouping (embeddings → graphs)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GRPH-17<a name="grph-17"></a> | Building identity or similarity clusters from embeddings | **Build a mutual k-NN graph, not a complete similarity graph**: all-pairs edges are O(n²) and over-connect impostors; each node keeping its k nearest (ideally mutual) neighbours bounds both cost and false links (↔ eng [[PERF-05]](engineering.md#perf-05) both fail when an all-pairs construction meets production scale) | Is the graph mutual-kNN with k chosen on validation, not "all pairs above τ"? | S·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-18<a name="grph-18"></a> | Clustering entities by thresholding similarity, then taking connected components | **Never trust the transitive closure of a raw similarity threshold**: A~B and B~C does not make A~C; a chain of borderline matches glues distinct entities into one cluster (the chaining failure), and when that cluster is named, it names the wrong one (↔ sec [[SEC-05]](security.md#sec-05): the clustering analogue of the irreversible LLM action it gates) | On held-out pairs, how often does a path link entities verified as different? | B·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-19<a name="grph-19"></a> | Splitting an over-merged cluster, or choosing where to cut | **Cut on normalised cut / conductance, not plain min-cut**: unnormalised min-cut shaves off single outliers; a normalised objective balances the cut against cluster volume and finds the real boundary | Does the cut minimise the boundary relative to cluster size, or just raw edge weight? | S·w | [spectral-clustering-and-biclustering ch-2](../SOURCES.md#src-spectral-clustering-and-biclustering) |
| GRPH-20<a name="grph-20"></a> | Choosing the number of clusters k for spectral clustering | **Read k from the Laplacian eigengap; don't guess it**: cluster on the first k eigenvectors of the graph Laplacian, and the largest gap λ(k+1) − λ(k) is the data's own answer for k; the Fiedler vector gives the primary split | Where is the eigengap, and does clustering at that k cut false merges on validation? | S·w | [spectral-clustering-and-biclustering ch-2](../SOURCES.md#src-spectral-clustering-and-biclustering) |
| GRPH-21<a name="grph-21"></a> | A gallery too large for global spectral clustering | **Detect communities by modularity, then verify the seams**: modularity/Louvain finds dense-within/sparse-between groups cheaply, but the high-similarity edges *crossing* communities still need a pairwise second check | Does within-cluster density beat the null model, and are cross-community strong edges audited? | J·w | [graph-partitioning-and-clustering §modularity](../SOURCES.md#src-graph-partitioning-and-clustering) |
| GRPH-22<a name="grph-22"></a> | Production clustering still merges distinct entities or splits one entity | **Replace hard-τ-plus-components with partition-plus-verification**: keep only high-precision edges, cut with a constrained objective ([[GRPH-19]](graph-theory.md#grph-19)), then re-verify the residual cross-group bridges ([[GRPH-21]](graph-theory.md#grph-21)); gate on pair precision/recall at the operating edge set, not component purity | What is pair-level precision at the operating edge set, and which bridges are re-verified? | S·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |
| GRPH-23<a name="grph-23"></a> | A similarity graph built with one global cosine/L2 threshold | **Calibrate the edge policy per quality stratum**: pose, age, and capture quality shift the similarity distribution, so one global τ over-links easy negatives and under-links hard positives; use adaptive or learned thresholds per regime (edge construction itself: see [[GRPH-17]](graph-theory.md#grph-17)) | Is the edge policy validated across quality strata, or only on clean high-quality pairs? | S·w | [video-pipeline-practice](../SOURCES.md#src-video-pipeline-practice) |

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
| GRPH-26<a name="grph-26"></a> | A state or mode name encodes a quantity or payload (`retrying_2`, `loading_with_partial_data`), or the state enum grows a variant per remembered datum | **Split the finite mode from the unbounded context**: keep the state set qualitative and enumerable and put quantities (retry counts, form values, fetched data) in a context record the machine never enumerates, because an unbounded state set cannot be walked, so the states × events coverage check of [[GRPH-27]](graph-theory.md#grph-27) becomes infeasible. A quantity *is* a mode when its value changes which transitions are legal (draft/review/published); it is context when it only changes what a transition carries. | Does this value change which transitions are legal, or only what a transition carries? | S·p | [erickson-models-of-computation §TM](../SOURCES.md#src-erickson-models-of-computation) |
| GRPH-27<a name="grph-27"></a> | A reducer, dispatcher, or handler switches on the event/action type first, with the current state checked inside the branch or not at all; or a model's output selects the next step directly | **Key the transition on (state, event), state first**: resolve the current state before the event and store the relation as data or an exhaustiveness-checked table, so an unlisted pair is a no-op *by construction* and is counted/logged as an unadmitted event, because event-first dispatch lets any event mutate anything from any state and turns every duplicate fire into a bespoke lock/debounce problem; and because a *well-formed but illegal* model event passes schema validation and still moves the agent, so the safety-critical route must be an edge in the table, not a sentence in a prompt (↔ ml [[FM-04]](ml-systems.md#fm-04), which admits shape, not legality; ↔ sec [[SEC-05]](security.md#sec-05) for the gate it leads to; ↔ eng [[REF-02]](engineering.md#ref-02), which keys a handler map on one dimension; this requires two). Exempt: an event whose effect is identical from every mode needs no state key. | Which (state, event) pairs are undefined here, and is that by intent or by omission? | S·w | [erickson-models-of-computation §DFA](../SOURCES.md#src-erickson-models-of-computation) |
| GRPH-28<a name="grph-28"></a> | The same transition label (`DISCONNECT`, `CANCEL`) appears on every member of a group of states | **Hoist a shared transition to the common parent**: declare the edge once on the enclosing state rather than on each child, because the state added last is the one that will be missing it, and any sibling already missing it is a bug today (this is Fowler's Pull Up Method for a transition graph: sibling states duplicating an edge is the duplicated-code smell, and hoisting to the common parent is the fix that a new sibling inherits by construction; ↔ [[REF-10]](engineering.md#ref-10) hoist only genuinely-shared behavior, not edges that merely look alike). Exempt: a group small enough that the hierarchy costs more than the duplication; and note that hoisting hides the edge from a flat read of any one child. | Which transition labels are repeated across siblings, and does every sibling carry all of them? | S·w | [refactoring-fowler-beck ch-12](../SOURCES.md#src-refactoring-fowler-beck) |
| GRPH-29<a name="grph-29"></a> | A workflow waits on a human approval, a webhook, or a multi-day external event while holding a live process, call stack, or in-memory loop variable | **`(state, context)` is the resumable unit**: persist the machine's position as one small serializable pair, release the process, and rehydrate when the external event arrives, because a wait bounded by process lifetime loses the run to any deploy or restart, and a position held in a call stack cannot answer "what is this agent doing?" with a query. Exempt: sub-minute in-process waits; a context holding sockets, open handles, or closures is not serializable; shrink the context rather than forcing the pattern. | If this process died right now, which row would let it resume, and which column says where it is? | S·p | [designing-data-intensive-applications ch-9](../SOURCES.md#src-designing-data-intensive-applications) |
| GRPH-30<a name="grph-30"></a> | A loop-until-dry / repeat-until-nothing-new search dedupes candidates against the *accepted* or *confirmed* set | **Dedupe against everything ever surfaced, not against what was accepted**: in a loop-until-dry search, every candidate that has ever appeared, *including rejected ones*, enters a monotone seen-set, because deduping only against accepted results makes rejects resurface every round, no round is ever empty, the dry-round predicate never fires, and the run pays to rediscover the same dead ends until the budget is gone. Bound the loop itself per ml [[FM-08]](ml-systems.md#fm-08): a dry-round rule is a heuristic stopping rule, not a termination proof, and a semantic near-duplicate with a distinct key defeats the seen-set (↔ [[GRPH-18]](graph-theory.md#grph-18): a *similarity*-based seen-set can instead glue distinct candidates and suppress real findings). (this is graph traversal's discovered/processed set: mark a candidate the first time it is surfaced, never on acceptance, exactly as BFS ignores an edge into an already-discovered vertex; the loop-until-dry search is the agent application of that visited-set discipline) | What exactly enters the seen-set: does a *rejected* candidate enter it? | S·w | [skiena-algorithm-design-manual ch-7](../SOURCES.md#src-skiena-algorithm-design-manual) |
| GRPH-31<a name="grph-31"></a> | a set of tasks with dependencies must run across workers, threads, or lanes and the schedule or degree of parallelism is being guessed | **Critical-path schedule the task DAG**: take a legal order by topological sort, treat the critical path (longest chain) as the makespan floor, and under a finite worker count list-schedule ready tasks by longest-remaining-chain (critical-path) priority; parallel makespan with arbitrary precedence is strongly NP-hard, so claim no free optimum (↔ [[GRPH-01]](graph-theory.md#grph-01) the DAG is the substrate this schedules over; ↔ [[GRPH-09]](graph-theory.md#grph-09) pairwise interference without precedence is the sibling colouring structure, not this; ↔ [[PERF-04]](engineering.md#perf-04) the DAG's serial spine still caps speedup by Amdahl) | What is the critical-path floor, which ready task has the longest remaining chain, and what hardness bound holds under the worker cap? | S·p | [skiena-algorithm-design-manual ch-17](../SOURCES.md#src-skiena-algorithm-design-manual) + pinedo-scheduling ch-5 |

## 6. Cross-lexicon links

Graph theory is a spanning way of *seeing*, so its rules border several lexicons rather than sitting apart:

- **Parent rule.** This lexicon expands engineering's `[ALG-01]` ("graph in disguise"). Where `[ALG-01]` says *recognise the graph*, `GRPH-01..16` say *which graph, and what it then decides*. Hardness still defers to `[ALG-05]` and the brute-force budget to `[ALG-02]`: colouring (`GRPH-09`) and balanced cuts are NP-hard in general, so pick the escape (exact / approximation / heuristic) deliberately.
- **Cost & scale.** `GRPH-17` (mutual k-NN over all-pairs) is engineering's `[PERF-05]` (O(n²) on a hot path) in graph form: the complete similarity graph *is* the quadratic blow-up.
- **Authority & lineage.** `GRPH-14` (provenance as a directed graph) meets `[DATA-14]` (no dual writes; one authority owns the record). Both insist a derived fact points back to a single source of truth.
- **Architecture seams.** `GRPH-06` and `GRPH-16` (partition by components / sparsify at low-conductance cuts) are the measurement behind `[ARCH-01]` (a service split needs a real disintegrator): the sparse cut is the disintegrator made visible.
- **High-harm automation.** `GRPH-18` (the chaining failure) borders `[SEC-05]`, which gates an LLM's irreversible actions behind a human: a borderline merge that *names* an entity is the clustering analogue of the action that rule gates. Extending the gate to non-LLM automated naming is where a future **ML/embeddings and fairness pass** attaches: per-cohort error rates and confidence-gated naming would live there, citing `GRPH-18/22` as their clustering substrate.

## Consumption

Referenced by ID at the decision point, never read front-to-back. `GRPH-01..16` and `GRPH-24..25` fire mostly at **plan/design**: when a spec has ordering, conflicts, hierarchy, retrieval, or "everything connects to everything," cite the row that names the structure. `GRPH-17..23` are the **applied core**: they fire in clustering and entity-curation code, and `GRPH-18` (`B·w`) is the one to cite on any pipeline that thresholds similarity and unions the result: it is the single rule standing between a similarity graph and a wrongly-merged identity. `GRPH-26..30` are the **control-flow core**: they fire on any state machine, agent loop, or scheduler, and `GRPH-27` is the one to cite when a dispatcher decides what an event may do: it is where an illegal-but-well-formed event is refused by construction rather than by prompt. A consuming harness inlines the trigger plus the question by phase tag and cites the ID; the argument stays here.
