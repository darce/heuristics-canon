# Rule graph

Rules are nodes. A live `[[ID]]` cross-reference inside a rule row is
an undirected edge. The eleven files under `lexicons/` are a filing
projection over that graph: each rule lives in one file, but citations
cross file boundaries freely. This page shows the **lexicon quotient**:
one node per lexicon file, with each edge weighted by how many rule
citations run between that pair of files (see *Weighted edges*).

Generated from the rule corpus on each release; do not edit by hand.
Output is byte-stable: the same corpus produces the same bytes.

## Lexicon quotient

Eleven lexicon nodes, **45** weighted edges. The heaviest edge is **business-marketing** -- **engineering**, with **71** citations between them.

Each edge weight is a **circle** on the path between two lexicon
**rectangles** (mermaid has no circular edge-label form on GitHub).
Every edge also appears in the table below ([A11Y-02]). Lexicon fill is
a sequential rule-count step from the shared repo palette; weight-circle
fill, edge stroke colour, and stroke width encode the same weight (see
colour legend). All **45** weighted pairs are drawn — nothing is omitted.

```mermaid
%%{init: {'themeVariables': {'fontSize': '22px'}}}%%
graph LR
  accessibility["accessibility"]
  business_marketing["business-marketing"]
  depiction["depiction"]
  design_aesthetics["design-aesthetics"]
  engineering["engineering"]
  epistemics["epistemics"]
  graph_theory["graph-theory"]
  interaction_ux["interaction-ux"]
  ml_systems["ml-systems"]
  security["security"]
  writing["writing"]
  business_marketing --- W_business_marketing__engineering((71))
  W_business_marketing__engineering --- engineering
  engineering --- W_engineering__interaction_ux((48))
  W_engineering__interaction_ux --- interaction_ux
  engineering --- W_engineering__ml_systems((47))
  W_engineering__ml_systems --- ml_systems
  engineering --- W_engineering__epistemics((43))
  W_engineering__epistemics --- epistemics
  business_marketing --- W_business_marketing__interaction_ux((35))
  W_business_marketing__interaction_ux --- interaction_ux
  business_marketing --- W_business_marketing__epistemics((32))
  W_business_marketing__epistemics --- epistemics
  interaction_ux --- W_interaction_ux__ml_systems((29))
  W_interaction_ux__ml_systems --- ml_systems
  business_marketing --- W_business_marketing__ml_systems((24))
  W_business_marketing__ml_systems --- ml_systems
  ml_systems --- W_ml_systems__security((24))
  W_ml_systems__security --- security
  engineering --- W_engineering__security((23))
  W_engineering__security --- security
  business_marketing --- W_business_marketing__security((17))
  W_business_marketing__security --- security
  engineering --- W_engineering__graph_theory((17))
  W_engineering__graph_theory --- graph_theory
  graph_theory --- W_graph_theory__ml_systems((17))
  W_graph_theory__ml_systems --- ml_systems
  accessibility --- W_accessibility__interaction_ux((16))
  W_accessibility__interaction_ux --- interaction_ux
  epistemics --- W_epistemics__interaction_ux((14))
  W_epistemics__interaction_ux --- interaction_ux
  accessibility --- W_accessibility__engineering((12))
  W_accessibility__engineering --- engineering
  design_aesthetics --- W_design_aesthetics__engineering((12))
  W_design_aesthetics__engineering --- engineering
  epistemics --- W_epistemics__ml_systems((11))
  W_epistemics__ml_systems --- ml_systems
  business_marketing --- W_business_marketing__design_aesthetics((10))
  W_business_marketing__design_aesthetics --- design_aesthetics
  interaction_ux --- W_interaction_ux__security((10))
  W_interaction_ux__security --- security
  accessibility --- W_accessibility__business_marketing((8))
  W_accessibility__business_marketing --- business_marketing
  design_aesthetics --- W_design_aesthetics__interaction_ux((8))
  W_design_aesthetics__interaction_ux --- interaction_ux
  engineering --- W_engineering__writing((6))
  W_engineering__writing --- writing
  business_marketing --- W_business_marketing__writing((5))
  W_business_marketing__writing --- writing
  graph_theory --- W_graph_theory__security((5))
  W_graph_theory__security --- security
  ml_systems --- W_ml_systems__writing((5))
  W_ml_systems__writing --- writing
  accessibility --- W_accessibility__design_aesthetics((4))
  W_accessibility__design_aesthetics --- design_aesthetics
  accessibility --- W_accessibility__ml_systems((4))
  W_accessibility__ml_systems --- ml_systems
  depiction --- W_depiction__ml_systems((4))
  W_depiction__ml_systems --- ml_systems
  depiction --- W_depiction__writing((4))
  W_depiction__writing --- writing
  graph_theory --- W_graph_theory__interaction_ux((4))
  W_graph_theory__interaction_ux --- interaction_ux
  accessibility --- W_accessibility__epistemics((3))
  W_accessibility__epistemics --- epistemics
  accessibility --- W_accessibility__security((3))
  W_accessibility__security --- security
  design_aesthetics --- W_design_aesthetics__writing((3))
  W_design_aesthetics__writing --- writing
  epistemics --- W_epistemics__writing((3))
  W_epistemics__writing --- writing
  business_marketing --- W_business_marketing__depiction((2))
  W_business_marketing__depiction --- depiction
  business_marketing --- W_business_marketing__graph_theory((2))
  W_business_marketing__graph_theory --- graph_theory
  depiction --- W_depiction__epistemics((2))
  W_depiction__epistemics --- epistemics
  depiction --- W_depiction__interaction_ux((2))
  W_depiction__interaction_ux --- interaction_ux
  design_aesthetics --- W_design_aesthetics__ml_systems((2))
  W_design_aesthetics__ml_systems --- ml_systems
  interaction_ux --- W_interaction_ux__writing((2))
  W_interaction_ux__writing --- writing
  security --- W_security__writing((2))
  W_security__writing --- writing
  accessibility --- W_accessibility__depiction((1))
  W_accessibility__depiction --- depiction
  epistemics --- W_epistemics__graph_theory((1))
  W_epistemics__graph_theory --- graph_theory
  epistemics --- W_epistemics__security((1))
  W_epistemics__security --- security
  classDef seq_0 fill:#B68477,color:#111111,stroke:#B68477
  classDef seq_1 fill:#B4668B,color:#111111,stroke:#B4668B
  classDef seq_2 fill:#8D57BA,color:#FFFFFF,stroke:#8D57BA
  classDef seq_3 fill:#225AD6,color:#FFFFFF,stroke:#225AD6
  class depiction,graph_theory,writing,W_accessibility__engineering,W_design_aesthetics__engineering,W_epistemics__ml_systems,W_business_marketing__design_aesthetics,W_interaction_ux__security,W_accessibility__business_marketing,W_design_aesthetics__interaction_ux,W_engineering__writing,W_business_marketing__writing,W_graph_theory__security,W_ml_systems__writing,W_accessibility__design_aesthetics,W_accessibility__ml_systems,W_depiction__ml_systems,W_depiction__writing,W_graph_theory__interaction_ux,W_accessibility__epistemics,W_accessibility__security,W_design_aesthetics__writing,W_epistemics__writing,W_business_marketing__depiction,W_business_marketing__graph_theory,W_depiction__epistemics,W_depiction__interaction_ux,W_design_aesthetics__ml_systems,W_interaction_ux__writing,W_security__writing,W_accessibility__depiction,W_epistemics__graph_theory,W_epistemics__security seq_0
  class accessibility,design_aesthetics,epistemics,W_business_marketing__interaction_ux,W_business_marketing__epistemics,W_interaction_ux__ml_systems,W_business_marketing__ml_systems,W_ml_systems__security,W_engineering__security,W_business_marketing__security,W_engineering__graph_theory,W_graph_theory__ml_systems,W_accessibility__interaction_ux,W_epistemics__interaction_ux seq_1
  class business_marketing,interaction_ux,security,W_engineering__interaction_ux,W_engineering__ml_systems,W_engineering__epistemics seq_2
  class engineering,ml_systems,W_business_marketing__engineering seq_3
  linkStyle 0,1 stroke:#225AD6,stroke-width:4px
  linkStyle 2,3,4,5,6,7 stroke:#8D57BA,stroke-width:3px
  linkStyle 8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29 stroke:#B4668B,stroke-width:2px
  linkStyle 30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89 stroke:#B68477,stroke-width:1px
```

### Colour legend

Lexicon node fill, weight-circle fill, and edge stroke share one four-step **sequential** ramp: lightest = fewest rules / lighter edge weights, darkest = most rules / heavier weights. **Rectangles** are lexicon nodes; **circles** on a path are edge weights (citation counts). The swatches below are painted by the same `classDef` lines the diagram uses, so they are the colours, not a description of them.

```mermaid
%%{init: {'themeVariables': {'fontSize': '22px'}}}%%
flowchart LR
  SW0["step 0 — fewest rules / lightest weight<br/>depiction, graph-theory, writing"]
  SW1["step 1 — lower mid / lighter weight<br/>accessibility, design-aesthetics, epistemics"]
  SW2["step 2 — upper mid / heavier weight<br/>business-marketing, interaction-ux, security"]
  SW3["step 3 — most rules / heaviest weight<br/>engineering, ml-systems"]
  classDef seq_0 fill:#B68477,color:#111111,stroke:#B68477
  classDef seq_1 fill:#B4668B,color:#111111,stroke:#B4668B
  classDef seq_2 fill:#8D57BA,color:#FFFFFF,stroke:#8D57BA
  classDef seq_3 fill:#225AD6,color:#FFFFFF,stroke:#225AD6
  class SW0 seq_0
  class SW1 seq_1
  class SW2 seq_2
  class SW3 seq_3
```

**Colour is never the only channel.** Every edge weight is also printed inside its circle and listed in the table below, and stroke width carries it a third time; every lexicon node's tier is recoverable from the rule counts in *Per-lexicon counts*. Delete the colour and the page loses no information ([A11Y-02]).

The ramp is derived, not picked: OKLab lightness starts at 0.66 and falls by 0.05 per step; chroma starts at 0.065 and rises by 0.045; hue starts at 35° and turns -44° per step (132° arc). Falling lightness is what makes the order survive greyscale and colour-vision deficiency — the hue rotation rides on top of a value scale rather than carrying the ordering itself.

### Weighted edges

**What the weight counts.** Every `[[ID]]` written inside a rule row is
one citation, and a citation points somewhere: the rule that contains it
names the rule it depends on. An edge weight here is simply **how many
of those citations run between the two files**, counted in both
directions and added together.

The heaviest edge, `business-marketing` -- `engineering` at **71**, therefore says: 71 separate `[[ID]]` citations sit in one of those two files and name a rule in the other.

"Directed" is doing one job in that sentence: if two rules cite *each
other*, that is **two** citations, not one. They arrived at each other
independently, from opposite sides, and the weight says so.

That is the whole reason two numbers on this page disagree. There are **598** cross-lexicon citations but only **568** cross-lexicon *edges*, because **30** pairs of rules cite each other — one edge, two citations. 568 + 30 = 598, exactly.

**How to read a heavy edge.** It is not a defect and not a merge
candidate. A heavy edge means two domains keep reaching for each other's
rules — the cross-domain convergence this corpus exists to surface. A
light edge means the two vocabularies are largely independent, which is
equally informative and much less common.

| lexicon A | lexicon B | citations between them |
|---|---|---:|
| [business-marketing](lexicons/business-marketing.md) | [engineering](lexicons/engineering.md) | 71 |
| [engineering](lexicons/engineering.md) | [interaction-ux](lexicons/interaction-ux.md) | 48 |
| [engineering](lexicons/engineering.md) | [ml-systems](lexicons/ml-systems.md) | 47 |
| [engineering](lexicons/engineering.md) | [epistemics](lexicons/epistemics.md) | 43 |
| [business-marketing](lexicons/business-marketing.md) | [interaction-ux](lexicons/interaction-ux.md) | 35 |
| [business-marketing](lexicons/business-marketing.md) | [epistemics](lexicons/epistemics.md) | 32 |
| [interaction-ux](lexicons/interaction-ux.md) | [ml-systems](lexicons/ml-systems.md) | 29 |
| [business-marketing](lexicons/business-marketing.md) | [ml-systems](lexicons/ml-systems.md) | 24 |
| [ml-systems](lexicons/ml-systems.md) | [security](lexicons/security.md) | 24 |
| [engineering](lexicons/engineering.md) | [security](lexicons/security.md) | 23 |
| [business-marketing](lexicons/business-marketing.md) | [security](lexicons/security.md) | 17 |
| [engineering](lexicons/engineering.md) | [graph-theory](lexicons/graph-theory.md) | 17 |
| [graph-theory](lexicons/graph-theory.md) | [ml-systems](lexicons/ml-systems.md) | 17 |
| [accessibility](lexicons/accessibility.md) | [interaction-ux](lexicons/interaction-ux.md) | 16 |
| [epistemics](lexicons/epistemics.md) | [interaction-ux](lexicons/interaction-ux.md) | 14 |
| [accessibility](lexicons/accessibility.md) | [engineering](lexicons/engineering.md) | 12 |
| [design-aesthetics](lexicons/design-aesthetics.md) | [engineering](lexicons/engineering.md) | 12 |
| [epistemics](lexicons/epistemics.md) | [ml-systems](lexicons/ml-systems.md) | 11 |
| [business-marketing](lexicons/business-marketing.md) | [design-aesthetics](lexicons/design-aesthetics.md) | 10 |
| [interaction-ux](lexicons/interaction-ux.md) | [security](lexicons/security.md) | 10 |
| [accessibility](lexicons/accessibility.md) | [business-marketing](lexicons/business-marketing.md) | 8 |
| [design-aesthetics](lexicons/design-aesthetics.md) | [interaction-ux](lexicons/interaction-ux.md) | 8 |
| [engineering](lexicons/engineering.md) | [writing](lexicons/writing.md) | 6 |
| [business-marketing](lexicons/business-marketing.md) | [writing](lexicons/writing.md) | 5 |
| [graph-theory](lexicons/graph-theory.md) | [security](lexicons/security.md) | 5 |
| [ml-systems](lexicons/ml-systems.md) | [writing](lexicons/writing.md) | 5 |
| [accessibility](lexicons/accessibility.md) | [design-aesthetics](lexicons/design-aesthetics.md) | 4 |
| [accessibility](lexicons/accessibility.md) | [ml-systems](lexicons/ml-systems.md) | 4 |
| [depiction](lexicons/depiction.md) | [ml-systems](lexicons/ml-systems.md) | 4 |
| [depiction](lexicons/depiction.md) | [writing](lexicons/writing.md) | 4 |
| [graph-theory](lexicons/graph-theory.md) | [interaction-ux](lexicons/interaction-ux.md) | 4 |
| [accessibility](lexicons/accessibility.md) | [epistemics](lexicons/epistemics.md) | 3 |
| [accessibility](lexicons/accessibility.md) | [security](lexicons/security.md) | 3 |
| [design-aesthetics](lexicons/design-aesthetics.md) | [writing](lexicons/writing.md) | 3 |
| [epistemics](lexicons/epistemics.md) | [writing](lexicons/writing.md) | 3 |
| [business-marketing](lexicons/business-marketing.md) | [depiction](lexicons/depiction.md) | 2 |
| [business-marketing](lexicons/business-marketing.md) | [graph-theory](lexicons/graph-theory.md) | 2 |
| [depiction](lexicons/depiction.md) | [epistemics](lexicons/epistemics.md) | 2 |
| [depiction](lexicons/depiction.md) | [interaction-ux](lexicons/interaction-ux.md) | 2 |
| [design-aesthetics](lexicons/design-aesthetics.md) | [ml-systems](lexicons/ml-systems.md) | 2 |
| [interaction-ux](lexicons/interaction-ux.md) | [writing](lexicons/writing.md) | 2 |
| [security](lexicons/security.md) | [writing](lexicons/writing.md) | 2 |
| [accessibility](lexicons/accessibility.md) | [depiction](lexicons/depiction.md) | 1 |
| [epistemics](lexicons/epistemics.md) | [graph-theory](lexicons/graph-theory.md) | 1 |
| [epistemics](lexicons/epistemics.md) | [security](lexicons/security.md) | 1 |

## Intra-lexicon vs cross-lexicon edges

Of **1068** simple undirected edges among rules, **500** stay inside one lexicon file and **568** cross a file boundary (cut ratio **0.53** = cross / (intra + cross)).

**Reading A.** If the eleven lexicons were natural communities of the
citation graph, most edges would fall inside files. A cut ratio of 0.53
says they are not: the file partition is not a low-conductance community
partition. Read alone, that can look like a filing error.

**Reading B (preferred).** This corpus exists to surface cross-domain
convergence. Independent arrivals at the same mechanism are its most
valuable output. Lexicons are a **retrieval** partition, driven by how
agents and people look up rules, not a community partition of the
citation graph. A cut ratio above 0.5 is that purpose showing up in
topology: rules are filed by domain of first arrival and linked by
mechanism. Re-partitioning the files to minimise the cut would hide
the convergences the corpus is built to expose.

## Per-lexicon counts

One row per file. Read across:

- **rule nodes** — how many rules the file holds.
- **internal edges** — links from one of its rules to another of its
  own. High means the file is a self-contained body of practice.
- **external edges** — links between one of its rules and a rule in
  some other file. High means the file is a hub.
- **cut ratio** — external / (internal + external): the share of this
  file's links that leave it. **0.00** would be an island, **1.00** a
  file whose rules only ever connect outward and never to each other.

Both edge columns count undirected pairs, so a mutual citation is one
edge here (unlike the weights above). An edge between two files is
counted once in each file's external column, which is why the external
column sums to twice the cross-edge total rather than to it.

| lexicon | rule nodes | internal edges | external edges | cut ratio |
|---|---:|---:|---:|---:|
| [accessibility](lexicons/accessibility.md) | 59 | 30 | 48 | 0.62 |
| [business-marketing](lexicons/business-marketing.md) | 127 | 34 | 187 | 0.85 |
| [depiction](lexicons/depiction.md) | 15 | 9 | 15 | 0.62 |
| [design-aesthetics](lexicons/design-aesthetics.md) | 74 | 12 | 39 | 0.76 |
| [engineering](lexicons/engineering.md) | 311 | 138 | 257 | 0.65 |
| [epistemics](lexicons/epistemics.md) | 84 | 41 | 110 | 0.73 |
| [graph-theory](lexicons/graph-theory.md) | 39 | 16 | 46 | 0.74 |
| [interaction-ux](lexicons/interaction-ux.md) | 100 | 33 | 157 | 0.83 |
| [ml-systems](lexicons/ml-systems.md) | 208 | 109 | 167 | 0.61 |
| [security](lexicons/security.md) | 122 | 76 | 80 | 0.51 |
| [writing](lexicons/writing.md) | 46 | 2 | 30 | 0.94 |

Underlying rule graph (not drawn here): **1185** rule nodes, **1068** distinct undirected edges (simple 1068 + self-loops 0).

