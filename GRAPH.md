# Rule graph

Rules are nodes. A live `[[ID]]` cross-reference inside a rule row is
an undirected edge. The eleven files under `lexicons/` are a filing
projection over that graph: each rule lives in one file, but citations
cross file boundaries freely. This page shows the **lexicon quotient**:
one node per lexicon file, with edge weight equal to the number of
directed live cross-lexicon references between the pair.

Generated from the rule corpus on each release; do not edit by hand.
Output is byte-stable: the same corpus produces the same bytes.

## Lexicon quotient

Eleven lexicon nodes, **45** weighted edges. The heaviest edge is **business-marketing** -- **engineering** at weight **71** (directed cross-ref count).

Edge labels on the diagram are those weights. Every edge also appears
in the table below ([A11Y-02]). Node fill is a sequential rule-count
step from the shared repo palette; edge stroke colour and width encode
the same weight (see colour legend).

```mermaid
%%{init: {'themeVariables': {'fontSize': '18px'}}}%%
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
  business_marketing ---|71| engineering
  engineering ---|48| interaction_ux
  engineering ---|47| ml_systems
  engineering ---|43| epistemics
  business_marketing ---|35| interaction_ux
  business_marketing ---|32| epistemics
  interaction_ux ---|29| ml_systems
  business_marketing ---|24| ml_systems
  ml_systems ---|24| security
  engineering ---|23| security
  business_marketing ---|17| security
  engineering ---|17| graph_theory
  graph_theory ---|17| ml_systems
  accessibility ---|16| interaction_ux
  epistemics ---|14| interaction_ux
  accessibility ---|12| engineering
  design_aesthetics ---|12| engineering
  epistemics ---|11| ml_systems
  business_marketing ---|10| design_aesthetics
  interaction_ux ---|10| security
  accessibility ---|8| business_marketing
  design_aesthetics ---|8| interaction_ux
  engineering ---|6| writing
  business_marketing ---|5| writing
  graph_theory ---|5| security
  ml_systems ---|5| writing
  accessibility ---|4| design_aesthetics
  accessibility ---|4| ml_systems
  depiction ---|4| ml_systems
  depiction ---|4| writing
  graph_theory ---|4| interaction_ux
  accessibility ---|3| epistemics
  accessibility ---|3| security
  design_aesthetics ---|3| writing
  epistemics ---|3| writing
  business_marketing ---|2| depiction
  business_marketing ---|2| graph_theory
  depiction ---|2| epistemics
  depiction ---|2| interaction_ux
  design_aesthetics ---|2| ml_systems
  interaction_ux ---|2| writing
  security ---|2| writing
  accessibility ---|1| depiction
  epistemics ---|1| graph_theory
  epistemics ---|1| security
  classDef seq_0 fill:#938FA3,color:#111111,stroke:#938FA3
  classDef seq_1 fill:#817C96,color:#111111,stroke:#817C96
  classDef seq_2 fill:#736C8C,color:#FFFFFF,stroke:#736C8C
  classDef seq_3 fill:#655D82,color:#FFFFFF,stroke:#655D82
  class depiction,graph_theory,writing seq_0
  class accessibility,design_aesthetics,epistemics seq_1
  class business_marketing,interaction_ux,security seq_2
  class engineering,ml_systems seq_3
  linkStyle 0 stroke:#655D82,stroke-width:4px
  linkStyle 1,2,3 stroke:#736C8C,stroke-width:3px
  linkStyle 4,5,6,7,8,9,10,11,12,13,14 stroke:#817C96,stroke-width:2px
  linkStyle 15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44 stroke:#938FA3,stroke-width:1px
```

### Colour legend

Lexicon node fill and edge stroke both use a four-step **sequential** OKLCH magnitude ramp (fixed hue far from force hues, monotone OKLab lightness): lightest = fewest rules / lighter weights, darkest = most rules / heavier weights. Edge weight is also the edge label and a table column; stroke width is a second non-colour channel. Tier is also legible from the per-lexicon node counts in the table below.

| Step | Fill | OKLCH (L, C, h) | Rule-count rank |
|---:|---|---|---|
| 0 | `#938FA3` | 0.66, 0.030, 295° | fewest rules (e.g. depiction, graph-theory, writing) |
| 1 | `#817C96` | 0.60, 0.040, 295° | lower mid (e.g. accessibility, design-aesthetics, epistemics) |
| 2 | `#736C8C` | 0.55, 0.050, 295° | upper mid (e.g. business-marketing, interaction-ux, security) |
| 3 | `#655D82` | 0.50, 0.060, 295° | most rules (e.g. engineering, ml-systems) |

### Weighted edges

| lexicon A | lexicon B | directed cross-ref weight |
|---|---|---|
| business-marketing | engineering | 71 |
| engineering | interaction-ux | 48 |
| engineering | ml-systems | 47 |
| engineering | epistemics | 43 |
| business-marketing | interaction-ux | 35 |
| business-marketing | epistemics | 32 |
| interaction-ux | ml-systems | 29 |
| business-marketing | ml-systems | 24 |
| ml-systems | security | 24 |
| engineering | security | 23 |
| business-marketing | security | 17 |
| engineering | graph-theory | 17 |
| graph-theory | ml-systems | 17 |
| accessibility | interaction-ux | 16 |
| epistemics | interaction-ux | 14 |
| accessibility | engineering | 12 |
| design-aesthetics | engineering | 12 |
| epistemics | ml-systems | 11 |
| business-marketing | design-aesthetics | 10 |
| interaction-ux | security | 10 |
| accessibility | business-marketing | 8 |
| design-aesthetics | interaction-ux | 8 |
| engineering | writing | 6 |
| business-marketing | writing | 5 |
| graph-theory | security | 5 |
| ml-systems | writing | 5 |
| accessibility | design-aesthetics | 4 |
| accessibility | ml-systems | 4 |
| depiction | ml-systems | 4 |
| depiction | writing | 4 |
| graph-theory | interaction-ux | 4 |
| accessibility | epistemics | 3 |
| accessibility | security | 3 |
| design-aesthetics | writing | 3 |
| epistemics | writing | 3 |
| business-marketing | depiction | 2 |
| business-marketing | graph-theory | 2 |
| depiction | epistemics | 2 |
| depiction | interaction-ux | 2 |
| design-aesthetics | ml-systems | 2 |
| interaction-ux | writing | 2 |
| security | writing | 2 |
| accessibility | depiction | 1 |
| epistemics | graph-theory | 1 |
| epistemics | security | 1 |

## Intra-lexicon vs cross-lexicon edges

Of **1061** simple undirected edges among rules, **493** stay inside one lexicon file and **568** cross a file boundary (cut ratio **0.54** = cross / (intra + cross)).

**Reading A.** If the eleven lexicons were natural communities of the
citation graph, most edges would fall inside files. A cut ratio of 0.54
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

| lexicon | rule nodes | internal edges | external edges | cut ratio |
|---|---|---|---|---|
| accessibility | 54 | 23 | 48 | 0.68 |
| business-marketing | 109 | 34 | 187 | 0.85 |
| depiction | 15 | 9 | 15 | 0.62 |
| design-aesthetics | 74 | 12 | 39 | 0.76 |
| engineering | 301 | 138 | 257 | 0.65 |
| epistemics | 83 | 41 | 110 | 0.73 |
| graph-theory | 39 | 16 | 46 | 0.74 |
| interaction-ux | 91 | 33 | 157 | 0.83 |
| ml-systems | 208 | 109 | 167 | 0.61 |
| security | 122 | 76 | 80 | 0.51 |
| writing | 46 | 2 | 30 | 0.94 |

Internal and external counts are over simple undirected rule edges.
Cut ratio is external / (internal + external) for that lexicon's
incident edges.

Underlying rule graph (not drawn here): **1142** rule nodes, **1061** distinct undirected edges (simple 1061 + self-loops 0).

