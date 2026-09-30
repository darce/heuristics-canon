# Agent guide

This repository is a citation target. Retrieve only the rules whose triggers
appear in the artifact you are changing; never load every rule into a task.

For people: [README.md](README.md). Card format:
[reasoning/CONTRACT.md](reasoning/CONTRACT.md). Card inventory:
[reasoning/README.md](reasoning/README.md).

## Consumer contract

- IDs are the API. A published `[FAM-NN]` never changes meaning, and it is
  removed only in a breaking release.
- Pin a release tag, not `main`, and verify its digests against
  [`meta/release-manifest.json`](meta/release-manifest.json) (see
  [Pin and verify](#pin-and-verify)).
- Semver: removing a published rule ID or reasoning card is a major change;
  adding one is minor; changing content at the same path is a patch.
- The tier sets a rule's force. `B` blocks; `S` is a strong default with
  named exemptions; `J` needs context. A context-poor agent escalates a `J`
  rule; it does not skip it.
- Rules are evidence-backed defaults. They do not override the task, observed
  facts, or a documented exemption.

## Apply the canon

Go deeper only when the decision needs it:

```text
rule row  ->  reasoning card  ->  original source
(lexicons/)   (reasoning/)        (publisher's copy)
```

1. **Route.** Match the changed artifact to the [routing table](#routing-by-artifact).
   A rule fires on what changed, not on its file type.
2. **Open only the listed families.** Follow the family anchors from the
   route, and filter by phase bucket when that helps. Do not open every
   lexicon for one change.
3. **Keep the rows that fire.** Keep a rule only when its trigger is
   observable in the artifact. Read the whole row, especially the exemptions
   and tier. If the source cannot be traced or does not support the
   mechanism, report a corpus defect instead of citing the rule as authority.
4. **Check principles.** If [PRINCIPLES.md](PRINCIPLES.md) lists a kept rule,
   retrieve its siblings from unrelated domains and look for the same
   mechanism in the new material. Siblings are mechanism checks, not votes and
   not a checklist. The [Agent application](PRINCIPLES.md#agent-application)
   section gives the compact protocol.
5. **Open cards.** For each kept rule ID, open every reasoning card whose
   `## Rule IDs` section lists it, once each, in ascending slug order. Do not
   stop at the first match. Apply each card's verification section. A card
   whose trigger did not fire is inert, and cards do not cover every
   principle.
6. **Resolve conflicts.** When two rules pull in opposite directions,
   partition them by surface, object, or sequence. If no partition works,
   record a contextual judgment; do not average the rules. When two rules
   watch the same failure at different stages, apply both.
7. **Cite.** Put `[FAM-NN]` beside each decision it supports and name the
   evidence. Cite rule IDs, not card slugs alone. Do not cite rules whose
   triggers did not fire; the number of citations is not a measure of review
   quality.
8. **Stop** when every applicable `B` and `S` rule is satisfied, exempted with
   evidence, or explicitly escalated.

Original sources are the last resort. [SOURCES.md](SOURCES.md) identifies each
work and what it feeds; it does not replace the work. Obtain originals through
ordinary legal channels.

## Read and cite a row

Every rule is one Markdown table row:

```text
| RES-02 | Connect/read/pool-checkout/HTTP client with no timeout | Timeout on every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

The columns are ID, Trigger, Rule, Answers, Tier·phase, and Source. Cite
`[RES-02]`, and deep-link the row as `lexicons/engineering.md#res-02` when the
reader needs its full text. The Answers cell is the cheapest useful review
prompt. The source slug resolves in [SOURCES.md](SOURCES.md). On a card, rule
IDs and evidence slugs are links to lexicon anchors and `SOURCES.md` rows.

To pull rows from the command line:

```sh
grep '^| RES-' lexicons/engineering.md
grep -h '^| [A-Z][A-Z0-9]*-' lexicons/*.md | wc -l
```

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

Each lexicon has its own phase letters. This table maps them to four shared
buckets: plan, write, review, and ship. Use the bucket unless you mean one
lexicon's code.

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
| ui or frontend change | [PERC](lexicons/interaction-ux.md#fam-perc) · [COG](lexicons/interaction-ux.md#fam-cog) · [NAV](lexicons/interaction-ux.md#fam-nav) · [INT](lexicons/interaction-ux.md#fam-int) · [FORM](lexicons/interaction-ux.md#fam-form) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [A11Y](lexicons/accessibility.md#fam-a11y) · [UI](lexicons/engineering.md#fam-ui) · [TYPE](lexicons/design-aesthetics.md#fam-type) · [LAY](lexicons/design-aesthetics.md#fam-lay) · [COL](lexicons/design-aesthetics.md#fam-col) |
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

## Pin and verify

```sh
git fetch --tags
git checkout <version-tag>
shasum -a 256 lexicons/*.md
find reasoning -type f 2>/dev/null | sort | xargs shasum -a 256
```

Compare the output with `meta/release-manifest.json`. The current schema is
`heuristics-canon/release@4`; older tags carry `@1` or `@2` and verify the
same way. The manifest lists the full rule-ID set and per-file digests for
lexicons and reasoning cards. From `@4` it also maps each withdrawn rule ID to
its successor, so contract drift can be checked offline.
