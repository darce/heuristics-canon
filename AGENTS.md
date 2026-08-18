# Agent guide

This repository is a citation target, not an instruction to load every rule into
every task. Retrieve only rules whose triggers match the artifact being changed.

Human overview: [README.md](README.md). Card format (sections and link rules):
[reasoning/CONTRACT.md](reasoning/CONTRACT.md). Card inventory and human
orientation: [reasoning/README.md](reasoning/README.md).

## Consumer contract

- IDs are the API. `[FAM-NN]` is immutable once published and disappears only
  in a breaking release.
- Pin a tag, not `main`, and verify lexicon and (when present) `reasoning/`
  SHA-256 values against
  [`meta/release-manifest.json`](meta/release-manifest.json). The current
  schema is `heuristics-canon/release@4`; tags cut before it carry `release@1`
  or `release@2` and stay verifiable the same way.
- Semver: removal of a published rule ID or reasoning card is breaking;
  addition is minor; same-path content change is patch.
- Tier controls force: `B` blocks, `S` is a strong default with named
  exemptions, and `J` requires context. A context-poor agent escalates a J rule
  rather than treating it as optional.
- Rules are evidence-backed defaults, not authority that overrides the task,
  observed facts, or a documented exemption.

## Progressive retrieval

Default depth is the rule row. Cards are optional intermediate depth above the
row. [SOURCES.md](SOURCES.md) is a bibliography registry (identity of the work
and what it feeds), not a substitute for the original.

```text
rule row  ->  reasoning card  ->  original source
 (lexicon)     (reasoning/)        (publisher copy)
```

1. Rule row (default). Route the artifact, keep rows whose triggers fire,
   read exemptions and tier. Cite `[FAM-NN]`.
2. Reasoning card. For every retained rule ID, open **every** mechanism
   card that lists that ID in its `## Rule IDs` section, **once each**, in
   deterministic ascending slug order. Do not stop at the first match. A
   principle join is a reason to open, not a checklist to satisfy. Use each
   card's verification section. Cite rule IDs in the durable record, not the
   card slug alone. On every card, Rule ID mentions and Evidence slugs are
   Markdown links to lexicon anchors and `SOURCES.md` rows.
3. Original source. Last resort for primary text. Obtain the work through
   ordinary legal channels.

A card without a firing trigger is inert. Cards are selective; they do not
cover every principle.

## Lexicons

<!-- BEGIN GENERATED LEXICONS -->

| Lexicon | Rule families |
|---|---|
| [`lexicons/accessibility.md`](lexicons/accessibility.md) | [A11Y](lexicons/accessibility.md#fam-a11y) |
| [`lexicons/business-marketing.md`](lexicons/business-marketing.md) | [STRAT](lexicons/business-marketing.md#fam-strat) · [PROD](lexicons/business-marketing.md#fam-prod) · [AIPX](lexicons/business-marketing.md#fam-aipx) · [GTM](lexicons/business-marketing.md#fam-gtm) · [NEG](lexicons/business-marketing.md#fam-neg) · [OPS](lexicons/business-marketing.md#fam-ops) · [BOOT](lexicons/business-marketing.md#fam-boot) · [CLM](lexicons/business-marketing.md#fam-clm) |
| [`lexicons/depiction.md`](lexicons/depiction.md) | [ATTRIB](lexicons/depiction.md#fam-attrib) · [BOUND](lexicons/depiction.md#fam-bound) |
| [`lexicons/design-aesthetics.md`](lexicons/design-aesthetics.md) | [IDNT](lexicons/design-aesthetics.md#fam-idnt) · [TYPE](lexicons/design-aesthetics.md#fam-type) · [COL](lexicons/design-aesthetics.md#fam-col) · [LAY](lexicons/design-aesthetics.md#fam-lay) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| [`lexicons/engineering.md`](lexicons/engineering.md) | [AGT](lexicons/engineering.md#fam-agt) · [RES](lexicons/engineering.md#fam-res) · [CON](lexicons/engineering.md#fam-con) · [DATA](lexicons/engineering.md#fam-data) · [MODEL](lexicons/engineering.md#fam-model) · [STOR](lexicons/engineering.md#fam-stor) · [FLOW](lexicons/engineering.md#fam-flow) · [PERF](lexicons/engineering.md#fam-perf) · [REF](lexicons/engineering.md#fam-ref) · [TEST](lexicons/engineering.md#fam-test) · [DBG](lexicons/engineering.md#fam-dbg) · [DIAG](lexicons/engineering.md#fam-diag) · [OBS](lexicons/engineering.md#fam-obs) · [API](lexicons/engineering.md#fam-api) · [DOM](lexicons/engineering.md#fam-dom) · [ARCH](lexicons/engineering.md#fam-arch) · [TEAM](lexicons/engineering.md#fam-team) · [ALG](lexicons/engineering.md#fam-alg) · [NAME](lexicons/engineering.md#fam-name) · [UI](lexicons/engineering.md#fam-ui) · [RLSE](lexicons/engineering.md#fam-rlse) |
| [`lexicons/epistemics.md`](lexicons/epistemics.md) | [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [RSCH](lexicons/epistemics.md#fam-rsch) · [MEAS](lexicons/epistemics.md#fam-meas) · [EXP](lexicons/epistemics.md#fam-exp) |
| [`lexicons/graph-theory.md`](lexicons/graph-theory.md) | [GRPH](lexicons/graph-theory.md#fam-grph) |
| [`lexicons/interaction-ux.md`](lexicons/interaction-ux.md) | [PERC](lexicons/interaction-ux.md#fam-perc) · [COG](lexicons/interaction-ux.md#fam-cog) · [NAV](lexicons/interaction-ux.md#fam-nav) · [INT](lexicons/interaction-ux.md#fam-int) · [FORM](lexicons/interaction-ux.md#fam-form) · [HAI](lexicons/interaction-ux.md#fam-hai) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [UXR](lexicons/interaction-ux.md#fam-uxr) |
| [`lexicons/ml-systems.md`](lexicons/ml-systems.md) | [MLDATA](lexicons/ml-systems.md#fam-mldata) · [EMB](lexicons/ml-systems.md#fam-emb) · [IDX](lexicons/ml-systems.md#fam-idx) · [EVAL](lexicons/ml-systems.md#fam-eval) · [AUDIT](lexicons/ml-systems.md#fam-audit) · [CAL](lexicons/ml-systems.md#fam-cal) · [DRIFT](lexicons/ml-systems.md#fam-drift) · [SERVE](lexicons/ml-systems.md#fam-serve) · [FAIR](lexicons/ml-systems.md#fam-fair) · [PROV](lexicons/ml-systems.md#fam-prov) · [HITL](lexicons/ml-systems.md#fam-hitl) · [TRACK](lexicons/ml-systems.md#fam-track) · [VSEG](lexicons/ml-systems.md#fam-vseg) · [COST](lexicons/ml-systems.md#fam-cost) · [FM](lexicons/ml-systems.md#fam-fm) · [RAG](lexicons/ml-systems.md#fam-rag) |
| [`lexicons/security.md`](lexicons/security.md) | [SEC](lexicons/security.md#fam-sec) · [WEB](lexicons/security.md#fam-web) · [PHP](lexicons/security.md#fam-php) · [WP](lexicons/security.md#fam-wp) · [PG](lexicons/security.md#fam-pg) · [SECD](lexicons/security.md#fam-secd) |
| [`lexicons/writing.md`](lexicons/writing.md) | [WRIT](lexicons/writing.md#fam-writ) |

<!-- END GENERATED LEXICONS -->

## Phase codes

Phase codes are per lexicon; use the buckets (plan / write / review / ship)
unless you mean one lexicon's code.

<!-- BEGIN GENERATED PHASES -->

| Lexicon | Codes (label → bucket) |
|---|---|
| accessibility | p plan→plan · w write→write · r review→review · g gtm→ship |
| business-marketing | s strategy→plan · p product→plan · g gtm→ship · o ops→ship |
| depiction | d draft→write · e edit→review · v verify→review |
| design-aesthetics | i identity→plan · b brand→plan · t type→write · c colour→write · l layout→write · im image→write |
| engineering | p plan→plan · w write→write · r review→review |
| graph-theory | p plan→plan · w write→write · r review→review |
| interaction-ux | p plan→plan · w write→write · r review→review |
| ml-systems | p plan→plan · w write→write · r review→review |
| security | p plan→plan · w write→write · r review→review |
| writing | d draft→write · e edit→review · v verify→review |
| epistemics | p plan→plan · e estimate→write · r review→review |

<!-- END GENERATED PHASES -->

## Routing by artifact

A rule fires on the artifact that changed, not merely its file type.

<!-- BEGIN GENERATED ROUTES -->

| Changed artifact | Consult families |
|---|---|
| database schema or migration | [MODEL](lexicons/engineering.md#fam-model) · [DATA](lexicons/engineering.md#fam-data) · [STOR](lexicons/engineering.md#fam-stor) · [PG](lexicons/security.md#fam-pg) |
| index or query change | [STOR](lexicons/engineering.md#fam-stor) · [DATA](lexicons/engineering.md#fam-data) · [PERF](lexicons/engineering.md#fam-perf) |
| batch or stream worker | [FLOW](lexicons/engineering.md#fam-flow) · [RES](lexicons/engineering.md#fam-res) · [OBS](lexicons/engineering.md#fam-obs) · [COST](lexicons/ml-systems.md#fam-cost) |
| architecture proposal or adr | [ARCH](lexicons/engineering.md#fam-arch) · [DOM](lexicons/engineering.md#fam-dom) · [TEAM](lexicons/engineering.md#fam-team) · [PERF](lexicons/engineering.md#fam-perf) · [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| codeowners or service catalog or org change | [TEAM](lexicons/engineering.md#fam-team) · [ARCH](lexicons/engineering.md#fam-arch) · [DOM](lexicons/engineering.md#fam-dom) |
| concurrency or async code | [CON](lexicons/engineering.md#fam-con) · [DATA](lexicons/engineering.md#fam-data) · [RES](lexicons/engineering.md#fam-res) |
| security sensitive change | [SEC](lexicons/security.md#fam-sec) · [WEB](lexicons/security.md#fam-web) · [SECD](lexicons/security.md#fam-secd) · [PG](lexicons/security.md#fam-pg) |
| ui or frontend change | [PERC](lexicons/interaction-ux.md#fam-perc) · [COG](lexicons/interaction-ux.md#fam-cog) · [NAV](lexicons/interaction-ux.md#fam-nav) · [INT](lexicons/interaction-ux.md#fam-int) · [FORM](lexicons/interaction-ux.md#fam-form) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [A11Y](lexicons/accessibility.md#fam-a11y) · [UI](lexicons/engineering.md#fam-ui) |
| embedding or face recognition change | [EMB](lexicons/ml-systems.md#fam-emb) · [CAL](lexicons/ml-systems.md#fam-cal) · [FAIR](lexicons/ml-systems.md#fam-fair) · [PROV](lexicons/ml-systems.md#fam-prov) · [TRACK](lexicons/ml-systems.md#fam-track) · [GRPH](lexicons/graph-theory.md#fam-grph) · [COST](lexicons/ml-systems.md#fam-cost) · [SEC](lexicons/security.md#fam-sec) · [IDX](lexicons/ml-systems.md#fam-idx) |
| video timeline segmentation change | [VSEG](lexicons/ml-systems.md#fam-vseg) · [TRACK](lexicons/ml-systems.md#fam-track) · [EVAL](lexicons/ml-systems.md#fam-eval) · [COST](lexicons/ml-systems.md#fam-cost) · [PERF](lexicons/engineering.md#fam-perf) |
| model weights or training change | [MLDATA](lexicons/ml-systems.md#fam-mldata) · [EVAL](lexicons/ml-systems.md#fam-eval) · [CAL](lexicons/ml-systems.md#fam-cal) · [FAIR](lexicons/ml-systems.md#fam-fair) · [PROV](lexicons/ml-systems.md#fam-prov) · [SERVE](lexicons/ml-systems.md#fam-serve) · [DRIFT](lexicons/ml-systems.md#fam-drift) · [SEC](lexicons/security.md#fam-sec) |
| prompt or generation contract change | [FM](lexicons/ml-systems.md#fam-fm) · [EVAL](lexicons/ml-systems.md#fam-eval) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) |
| rag corpus or index change | [RAG](lexicons/ml-systems.md#fam-rag) · [EMB](lexicons/ml-systems.md#fam-emb) · [DRIFT](lexicons/ml-systems.md#fam-drift) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [IDX](lexicons/ml-systems.md#fam-idx) · [GRPH](lexicons/graph-theory.md#fam-grph) |
| rag retrieval or reranking change | [RAG](lexicons/ml-systems.md#fam-rag) · [EVAL](lexicons/ml-systems.md#fam-eval) · [EMB](lexicons/ml-systems.md#fam-emb) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [IDX](lexicons/ml-systems.md#fam-idx) · [GRPH](lexicons/graph-theory.md#fam-grph) |
| agent loop change | [FM](lexicons/ml-systems.md#fam-fm) · [RES](lexicons/engineering.md#fam-res) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) · [GRPH](lexicons/graph-theory.md#fam-grph) |
| agent tool side effect change | [FM](lexicons/ml-systems.md#fam-fm) · [SEC](lexicons/security.md#fam-sec) · [DATA](lexicons/engineering.md#fam-data) · [API](lexicons/engineering.md#fam-api) · [SERVE](lexicons/ml-systems.md#fam-serve) · [HAI](lexicons/interaction-ux.md#fam-hai) · [PROV](lexicons/ml-systems.md#fam-prov) |
| ai review or curation ui | [HAI](lexicons/interaction-ux.md#fam-hai) · [HITL](lexicons/ml-systems.md#fam-hitl) · [CAL](lexicons/ml-systems.md#fam-cal) · [PROV](lexicons/ml-systems.md#fam-prov) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [PERC](lexicons/interaction-ux.md#fam-perc) · [A11Y](lexicons/accessibility.md#fam-a11y) |
| agent session or skill change | [AGT](lexicons/engineering.md#fam-agt) · [FM](lexicons/ml-systems.md#fam-fm) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) |
| failing test or incident investigation | [DBG](lexicons/engineering.md#fam-dbg) · [DIAG](lexicons/engineering.md#fam-diag) · [OBS](lexicons/engineering.md#fam-obs) · [TEST](lexicons/engineering.md#fam-test) · [RES](lexicons/engineering.md#fam-res) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| release or deploy change | [RLSE](lexicons/engineering.md#fam-rlse) · [OPS](lexicons/business-marketing.md#fam-ops) · [OBS](lexicons/engineering.md#fam-obs) · [TEST](lexicons/engineering.md#fam-test) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| public naming or api surface | [NAME](lexicons/engineering.md#fam-name) · [API](lexicons/engineering.md#fam-api) · [DOM](lexicons/engineering.md#fam-dom) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| algorithm or data structure choice | [ALG](lexicons/engineering.md#fam-alg) · [PERF](lexicons/engineering.md#fam-perf) · [GRPH](lexicons/graph-theory.md#fam-grph) · [DATA](lexicons/engineering.md#fam-data) |
| prose or documentation change | [WRIT](lexicons/writing.md#fam-writ) · [CLM](lexicons/business-marketing.md#fam-clm) |
| image description or alt text change | [ATTRIB](lexicons/depiction.md#fam-attrib) · [BOUND](lexicons/depiction.md#fam-bound) · [A11Y](lexicons/accessibility.md#fam-a11y) · [WRIT](lexicons/writing.md#fam-writ) · [CLM](lexicons/business-marketing.md#fam-clm) · [PROV](lexicons/ml-systems.md#fam-prov) |
| archival description or catalogue change | [ATTRIB](lexicons/depiction.md#fam-attrib) · [WRIT](lexicons/writing.md#fam-writ) · [CLM](lexicons/business-marketing.md#fam-clm) · [PROV](lexicons/ml-systems.md#fam-prov) · [FM](lexicons/ml-systems.md#fam-fm) |
| strategy or product bet | [STRAT](lexicons/business-marketing.md#fam-strat) · [PROD](lexicons/business-marketing.md#fam-prod) · [AIPX](lexicons/business-marketing.md#fam-aipx) · [BOOT](lexicons/business-marketing.md#fam-boot) · [NEG](lexicons/business-marketing.md#fam-neg) · [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [RSCH](lexicons/epistemics.md#fam-rsch) · [HAI](lexicons/interaction-ux.md#fam-hai) |
| estimate or forecast in a plan | [FORE](lexicons/epistemics.md#fam-fore) · [STRAT](lexicons/business-marketing.md#fam-strat) · [EVAL](lexicons/ml-systems.md#fam-eval) · [CAL](lexicons/ml-systems.md#fam-cal) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [MEAS](lexicons/epistemics.md#fam-meas) |
| choosing a problem or research direction | [RSCH](lexicons/epistemics.md#fam-rsch) · [STRAT](lexicons/business-marketing.md#fam-strat) · [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| data analysis or experiment | [EXP](lexicons/epistemics.md#fam-exp) · [MEAS](lexicons/epistemics.md#fam-meas) · [EVAL](lexicons/ml-systems.md#fam-eval) · [FORE](lexicons/epistemics.md#fam-fore) · [BIAS](lexicons/epistemics.md#fam-bias) · [MLDATA](lexicons/ml-systems.md#fam-mldata) · [AUDIT](lexicons/ml-systems.md#fam-audit) |
| corpus audit or population rate claim | [AUDIT](lexicons/ml-systems.md#fam-audit) · [EVAL](lexicons/ml-systems.md#fam-eval) · [CAL](lexicons/ml-systems.md#fam-cal) · [MLDATA](lexicons/ml-systems.md#fam-mldata) · [FAIR](lexicons/ml-systems.md#fam-fair) · [MEAS](lexicons/epistemics.md#fam-meas) |
| pricing positioning or launch | [GTM](lexicons/business-marketing.md#fam-gtm) · [CLM](lexicons/business-marketing.md#fam-clm) · [PROD](lexicons/business-marketing.md#fam-prod) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| brand or visual identity change | [IDNT](lexicons/design-aesthetics.md#fam-idnt) · [BRND](lexicons/design-aesthetics.md#fam-brnd) · [TYPE](lexicons/design-aesthetics.md#fam-type) · [COL](lexicons/design-aesthetics.md#fam-col) · [LAY](lexicons/design-aesthetics.md#fam-lay) |
| php or wordpress change | [PHP](lexicons/security.md#fam-php) · [WP](lexicons/security.md#fam-wp) · [SEC](lexicons/security.md#fam-sec) · [WEB](lexicons/security.md#fam-web) |
| usability evaluation or metric | [UXR](lexicons/interaction-ux.md#fam-uxr) · [HAI](lexicons/interaction-ux.md#fam-hai) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [PERC](lexicons/interaction-ux.md#fam-perc) |
| generated rule index or registry change | [REF](lexicons/engineering.md#fam-ref) · [DATA](lexicons/engineering.md#fam-data) · [STOR](lexicons/engineering.md#fam-stor) · [PROV](lexicons/ml-systems.md#fam-prov) · [FM](lexicons/ml-systems.md#fam-fm) · [PERF](lexicons/engineering.md#fam-perf) · [TEST](lexicons/engineering.md#fam-test) |
| canon rule or card change | [WRIT](lexicons/writing.md#fam-writ) · [CLM](lexicons/business-marketing.md#fam-clm) · [PROV](lexicons/ml-systems.md#fam-prov) · [ATTRIB](lexicons/depiction.md#fam-attrib) · [DOM](lexicons/engineering.md#fam-dom) · [API](lexicons/engineering.md#fam-api) · [FM](lexicons/ml-systems.md#fam-fm) |

<!-- END GENERATED ROUTES -->

## Apply rules under a context budget

1. Match the changed artifact to the routing table above.
2. Open only the listed family anchors. Filter by
   plan/write/review/ship phase when useful.
3. Keep a rule only when its Trigger is observable. Read the complete row,
   especially exemptions and tier. If the source is unwalkable or does not
   support the mechanism, report a corpus defect instead of invoking authority.
4. If `PRINCIPLES.md` cites the rule, retrieve its siblings from unrelated
   domains. They are mechanism checks, not votes. Prefer the document's
   [Agent application](PRINCIPLES.md#agent-application) section for the
   compact protocol.
5. Partition opposed rules by surface, object, or sequence. If no partition
   works, record a contextual judgment; do not average the rules. Keep both
   rules when they inspect the same failure at earlier and later stages.
6. For each retained rule ID, open every reasoning card that lists it, once
   each, in ascending slug order; apply each card's verification. Principle
   membership joins related IDs; it is not a gate that must be fully checked.
7. Cite the applied IDs beside the decision and name the evidence.
8. Stop retrieval when every applicable blocker and strong default is
   satisfied, exempted with evidence, or explicitly escalated.

Do not open every lexicon for a single change. Do not cite rules whose
triggers did not fire. Citation count is not review quality.

## Retrieve rules

Every rule is one Markdown table row:

```sh
grep '^| RES-' lexicons/engineering.md
grep -h '^| [A-Z][A-Z0-9]*-' lexicons/*.md | wc -l
```

A `Src` slug resolves in [SOURCES.md](SOURCES.md). Deep-link a row as
`lexicons/engineering.md#res-02` when the reader needs the full trigger text.

## Read and cite a row

```text
| RES-02 | Connect/read/pool-checkout/HTTP client with no timeout | Timeout on every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

The columns are ID, Trigger, Rule, Answers, tier/phase, and source. Cite
`[RES-02]`. The Answers cell is the cheapest useful inline review prompt.

## Use principles without flattening them

`PRINCIPLES.md` maps a fired rule to independent cross-domain arrivals. Use the
siblings to look for the same mechanism in a different material, not to inflate
the citation count. When rules disagree, use surface, object, and sequence
partitions. When they watch the same failure at different stages, apply both.

## Pin and verify

```sh
git fetch --tags
git checkout <version-tag>
shasum -a 256 lexicons/*.md
find reasoning -type f 2>/dev/null | sort | xargs shasum -a 256
```

Compare the output with `meta/release-manifest.json` (schema
`heuristics-canon/release@4`; older tags carry `@1` or `@2`). The manifest
carries the full rule-ID set, per-file digests for lexicons and reasoning
cards, and from `@4` a map of withdrawn rule IDs to their successors, so
contract drift is checkable offline.
