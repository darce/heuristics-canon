# Heuristics canon

A working corpus of more than 900 decision rules for building, running, securing, marketing, designing, writing, and shipping software. Each rule is a falsifiable condition -> action claim with a stable citation ID, a source you can check, and a tier that says how hard it binds. A review comment, plan, or skill cites the ID at the moment a decision is made: `[RES-02]` on a blocking call with no timeout, `[A11Y-01]` on a color change. One token replaces a paragraph of restated advice.

The shelf is deliberately mismatched: a distributed-systems text, a 1988 manual on gaming the UK pop charts, a WCAG standard, a labor study of the adult-content economy, a 1935 typography treatise. When two sources arrive at one mechanism from economies that share nothing, the corpus records the convergence as a first principle in [PRINCIPLES.md](PRINCIPLES.md), and a session that cites one rule retrieves the others as corroboration it would not have found alone.

## How to use it

Cheapest first.

1. Cite by ID. In a plan, a review comment, or a skill body: `see [DBG-01]`. Readers resolve it here, and each rule's section heading is a deep-link anchor.
2. Copy the tables. A consuming repo vendors `lexicons/*.md` into its own surface and pins a release tag; [`meta/release-manifest.json`](meta/release-manifest.json) carries a sha256 per lexicon so the copy verifies offline. See [Versioning](#versioning).
3. Wire an agent. [`AGENTS.md`](AGENTS.md) is the contract for automated consumers: pin, verify, retrieve, cite.

This repo is upstream. Rules flow from a private research corpus to here to consumers, never the reverse.

## What's inside

Ten lexicons, each a table of rules keyed by stable ID:

<!-- BEGIN GENERATED LEXICONS -->

| Lexicon | Governs | Rule families |
|---|---|---|
| [`lexicons/engineering.md`](lexicons/engineering.md) | building, running, debugging, shipping software | [AGT](lexicons/engineering.md#fam-agt) · [RES](lexicons/engineering.md#fam-res) · [CON](lexicons/engineering.md#fam-con) · [DATA](lexicons/engineering.md#fam-data) · [MODEL](lexicons/engineering.md#fam-model) · [STOR](lexicons/engineering.md#fam-stor) · [FLOW](lexicons/engineering.md#fam-flow) · [PERF](lexicons/engineering.md#fam-perf) · [REF](lexicons/engineering.md#fam-ref) · [TEST](lexicons/engineering.md#fam-test) · [DBG](lexicons/engineering.md#fam-dbg) · [DIAG](lexicons/engineering.md#fam-diag) · [OBS](lexicons/engineering.md#fam-obs) · [API](lexicons/engineering.md#fam-api) · [DOM](lexicons/engineering.md#fam-dom) · [ARCH](lexicons/engineering.md#fam-arch) · [TEAM](lexicons/engineering.md#fam-team) · [ALG](lexicons/engineering.md#fam-alg) · [NAME](lexicons/engineering.md#fam-name) · [UI](lexicons/engineering.md#fam-ui) · [RLSE](lexicons/engineering.md#fam-rlse) |
| [`lexicons/business-marketing.md`](lexicons/business-marketing.md) | strategy, validation, GTM, negotiation, bootstrap economics, claims | [STRAT](lexicons/business-marketing.md#fam-strat) · [PROD](lexicons/business-marketing.md#fam-prod) · [AIPX](lexicons/business-marketing.md#fam-aipx) · [GTM](lexicons/business-marketing.md#fam-gtm) · [NEG](lexicons/business-marketing.md#fam-neg) · [OPS](lexicons/business-marketing.md#fam-ops) · [BOOT](lexicons/business-marketing.md#fam-boot) · [CLM](lexicons/business-marketing.md#fam-clm) |
| [`lexicons/design-aesthetics.md`](lexicons/design-aesthetics.md) | identity, typography, colour, layout, brand | [IDNT](lexicons/design-aesthetics.md#fam-idnt) · [TYPE](lexicons/design-aesthetics.md#fam-type) · [COL](lexicons/design-aesthetics.md#fam-col) · [LAY](lexicons/design-aesthetics.md#fam-lay) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| [`lexicons/writing.md`](lexicons/writing.md) | prose that does not read as machine-generated | [WRIT](lexicons/writing.md#fam-writ) |
| [`lexicons/accessibility.md`](lexicons/accessibility.md) | WCAG 2.2 working set, conformance discipline | [A11Y](lexicons/accessibility.md#fam-a11y) |
| [`lexicons/security.md`](lexicons/security.md) | LLM/agent, web, secure-design principles, PHP, WordPress, PostgreSQL security (bootstrap pass) | [SEC](lexicons/security.md#fam-sec) · [WEB](lexicons/security.md#fam-web) · [PHP](lexicons/security.md#fam-php) · [WP](lexicons/security.md#fam-wp) · [PG](lexicons/security.md#fam-pg) · [SECD](lexicons/security.md#fam-secd) |
| [`lexicons/graph-theory.md`](lexicons/graph-theory.md) | reasoning as dependency graphs, assignment & cost, knowledge modeling, embedding & identity clustering | [GRPH](lexicons/graph-theory.md#fam-grph) |
| [`lexicons/interaction-ux.md`](lexicons/interaction-ux.md) | perception, cognition, wayfinding, interaction, forms, human-AI review, data visualization, usability measurement | [PERC](lexicons/interaction-ux.md#fam-perc) · [COG](lexicons/interaction-ux.md#fam-cog) · [NAV](lexicons/interaction-ux.md#fam-nav) · [INT](lexicons/interaction-ux.md#fam-int) · [FORM](lexicons/interaction-ux.md#fam-form) · [HAI](lexicons/interaction-ux.md#fam-hai) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [UXR](lexicons/interaction-ux.md#fam-uxr) |
| [`lexicons/ml-systems.md`](lexicons/ml-systems.md) | model evidence, embeddings, retrieval indexes, evaluation, calibration, drift, fairness, provenance, population audit, human review, video tracking, media timeline structure, serving cost, foundation-model composition, retrieval-augmented generation | [MLDATA](lexicons/ml-systems.md#fam-mldata) · [EMB](lexicons/ml-systems.md#fam-emb) · [IDX](lexicons/ml-systems.md#fam-idx) · [EVAL](lexicons/ml-systems.md#fam-eval) · [AUDIT](lexicons/ml-systems.md#fam-audit) · [CAL](lexicons/ml-systems.md#fam-cal) · [DRIFT](lexicons/ml-systems.md#fam-drift) · [SERVE](lexicons/ml-systems.md#fam-serve) · [FAIR](lexicons/ml-systems.md#fam-fair) · [PROV](lexicons/ml-systems.md#fam-prov) · [HITL](lexicons/ml-systems.md#fam-hitl) · [TRACK](lexicons/ml-systems.md#fam-track) · [VSEG](lexicons/ml-systems.md#fam-vseg) · [COST](lexicons/ml-systems.md#fam-cost) · [FM](lexicons/ml-systems.md#fam-fm) · [RAG](lexicons/ml-systems.md#fam-rag) |
| [`lexicons/epistemics.md`](lexicons/epistemics.md) | human and agent judgment under uncertainty — scorable estimates, forecasts, naturalistic decision making, controlled experiments, measurement validity, self-deception checks, and research practice | [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [RSCH](lexicons/epistemics.md#fam-rsch) · [MEAS](lexicons/epistemics.md#fam-meas) · [EXP](lexicons/epistemics.md#fam-exp) |

<!-- END GENERATED LEXICONS -->

## Reading a rule

Every row has the same shape. Here is one, from the engineering lexicon:

```
| ID | Trigger | Rule | Answers | T·P | Src |
| RES-02 | Connect/read/pool-checkout/HTTP client with no timeout | **Timeout on every blocking call** — every socket/pool/RPC/`wait()` needs a bounded timeout; defaults block forever. Exempt: in-process/in-memory calls | What bounds this wait? | B·w | release-it ch-5 |
```

- **ID** is the permanent citation key, immutable once assigned.
- **Trigger** is observable in a diff, plan, error, or metric, so a reviewer or a tool can tell when the rule fires.
- **Rule** is the falsifiable claim: condition, action, consequence.
- **Answers** is the one question to ask at the decision point.
- **T·P** is tier and phase. Tier **B**locker means correctness, data loss, or security if violated; **S**hould is a strong default with named exemptions; **J**udgment must be weighed in context, and escalates rather than simplifies, so a lane without that context routes it up. Phase codes are per-lexicon; filter by the bucket in the legend below (plan / write / review / ship) unless you mean one lexicon's code.
- **Src** is the source slug, linked to its row in [`SOURCES.md`](SOURCES.md): the full citation and what it feeds. The distillation behind it is private; rights are in [`NOTICE.md`](NOTICE.md).

<!-- BEGIN GENERATED PHASES -->

| Lexicon | Codes (label → bucket) |
|---|---|
| accessibility | p plan→plan · w write→write · r review→review · g gtm→ship |
| business-marketing | s strategy→plan · p product→plan · g gtm→ship · o ops→ship |
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

A rule fires on an artifact: a schema, a migration, a query plan, a stream-window config, an org chart, a launch plan. Map work to families by the artifact that changed, not only by file type.

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
| rag corpus or index change | [RAG](lexicons/ml-systems.md#fam-rag) · [EMB](lexicons/ml-systems.md#fam-emb) · [DRIFT](lexicons/ml-systems.md#fam-drift) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [IDX](lexicons/ml-systems.md#fam-idx) |
| rag retrieval or reranking change | [RAG](lexicons/ml-systems.md#fam-rag) · [EVAL](lexicons/ml-systems.md#fam-eval) · [EMB](lexicons/ml-systems.md#fam-emb) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [IDX](lexicons/ml-systems.md#fam-idx) |
| agent loop change | [FM](lexicons/ml-systems.md#fam-fm) · [RES](lexicons/engineering.md#fam-res) · [COST](lexicons/ml-systems.md#fam-cost) · [OBS](lexicons/engineering.md#fam-obs) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) |
| agent tool side effect change | [FM](lexicons/ml-systems.md#fam-fm) · [SEC](lexicons/security.md#fam-sec) · [DATA](lexicons/engineering.md#fam-data) · [API](lexicons/engineering.md#fam-api) · [SERVE](lexicons/ml-systems.md#fam-serve) · [HAI](lexicons/interaction-ux.md#fam-hai) · [PROV](lexicons/ml-systems.md#fam-prov) |
| ai review or curation ui | [HAI](lexicons/interaction-ux.md#fam-hai) · [HITL](lexicons/ml-systems.md#fam-hitl) · [CAL](lexicons/ml-systems.md#fam-cal) · [PROV](lexicons/ml-systems.md#fam-prov) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [PERC](lexicons/interaction-ux.md#fam-perc) · [A11Y](lexicons/accessibility.md#fam-a11y) |
| agent session or skill change | [AGT](lexicons/engineering.md#fam-agt) · [FM](lexicons/ml-systems.md#fam-fm) · [PROV](lexicons/ml-systems.md#fam-prov) · [SEC](lexicons/security.md#fam-sec) |
| failing test or incident investigation | [DBG](lexicons/engineering.md#fam-dbg) · [DIAG](lexicons/engineering.md#fam-diag) · [OBS](lexicons/engineering.md#fam-obs) · [TEST](lexicons/engineering.md#fam-test) · [RES](lexicons/engineering.md#fam-res) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| release or deploy change | [RLSE](lexicons/engineering.md#fam-rlse) · [OPS](lexicons/business-marketing.md#fam-ops) · [OBS](lexicons/engineering.md#fam-obs) · [TEST](lexicons/engineering.md#fam-test) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| public naming or api surface | [NAME](lexicons/engineering.md#fam-name) · [API](lexicons/engineering.md#fam-api) · [DOM](lexicons/engineering.md#fam-dom) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| algorithm or data structure choice | [ALG](lexicons/engineering.md#fam-alg) · [PERF](lexicons/engineering.md#fam-perf) · [GRPH](lexicons/graph-theory.md#fam-grph) · [DATA](lexicons/engineering.md#fam-data) |
| prose or documentation change | [WRIT](lexicons/writing.md#fam-writ) · [CLM](lexicons/business-marketing.md#fam-clm) |
| strategy or product bet | [STRAT](lexicons/business-marketing.md#fam-strat) · [PROD](lexicons/business-marketing.md#fam-prod) · [AIPX](lexicons/business-marketing.md#fam-aipx) · [BOOT](lexicons/business-marketing.md#fam-boot) · [NEG](lexicons/business-marketing.md#fam-neg) · [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [RSCH](lexicons/epistemics.md#fam-rsch) |
| estimate or forecast in a plan | [FORE](lexicons/epistemics.md#fam-fore) · [STRAT](lexicons/business-marketing.md#fam-strat) · [EVAL](lexicons/ml-systems.md#fam-eval) · [CAL](lexicons/ml-systems.md#fam-cal) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) · [MEAS](lexicons/epistemics.md#fam-meas) |
| choosing a problem or research direction | [RSCH](lexicons/epistemics.md#fam-rsch) · [STRAT](lexicons/business-marketing.md#fam-strat) · [FORE](lexicons/epistemics.md#fam-fore) · [NDM](lexicons/epistemics.md#fam-ndm) · [BIAS](lexicons/epistemics.md#fam-bias) |
| data analysis or experiment | [EXP](lexicons/epistemics.md#fam-exp) · [MEAS](lexicons/epistemics.md#fam-meas) · [EVAL](lexicons/ml-systems.md#fam-eval) · [FORE](lexicons/epistemics.md#fam-fore) · [BIAS](lexicons/epistemics.md#fam-bias) · [MLDATA](lexicons/ml-systems.md#fam-mldata) · [AUDIT](lexicons/ml-systems.md#fam-audit) |
| corpus audit or population rate claim | [AUDIT](lexicons/ml-systems.md#fam-audit) · [EVAL](lexicons/ml-systems.md#fam-eval) · [CAL](lexicons/ml-systems.md#fam-cal) · [MLDATA](lexicons/ml-systems.md#fam-mldata) · [FAIR](lexicons/ml-systems.md#fam-fair) · [MEAS](lexicons/epistemics.md#fam-meas) |
| pricing positioning or launch | [GTM](lexicons/business-marketing.md#fam-gtm) · [CLM](lexicons/business-marketing.md#fam-clm) · [PROD](lexicons/business-marketing.md#fam-prod) · [BRND](lexicons/design-aesthetics.md#fam-brnd) |
| brand or visual identity change | [IDNT](lexicons/design-aesthetics.md#fam-idnt) · [BRND](lexicons/design-aesthetics.md#fam-brnd) · [TYPE](lexicons/design-aesthetics.md#fam-type) · [COL](lexicons/design-aesthetics.md#fam-col) · [LAY](lexicons/design-aesthetics.md#fam-lay) |
| php or wordpress change | [PHP](lexicons/security.md#fam-php) · [WP](lexicons/security.md#fam-wp) · [SEC](lexicons/security.md#fam-sec) · [WEB](lexicons/security.md#fam-web) |
| usability evaluation or metric | [UXR](lexicons/interaction-ux.md#fam-uxr) · [HAI](lexicons/interaction-ux.md#fam-hai) · [VIZ](lexicons/interaction-ux.md#fam-viz) · [PERC](lexicons/interaction-ux.md#fam-perc) |
| generated rule index or registry change | [REF](lexicons/engineering.md#fam-ref) · [DATA](lexicons/engineering.md#fam-data) · [STOR](lexicons/engineering.md#fam-stor) · [PROV](lexicons/ml-systems.md#fam-prov) · [FM](lexicons/ml-systems.md#fam-fm) · [PERF](lexicons/engineering.md#fam-perf) · [TEST](lexicons/engineering.md#fam-test) |

<!-- END GENERATED ROUTES -->

## Cross-domain by design

Retrieval, in a person or a model, defaults to the domain of the question being asked. The connections across domains are exactly the ones an inference pass will not make on its own, so the corpus hard-codes them. A rule earns its tier when a second source reaches the same mechanism from an economy the first author never saw: pop charts, app stores, and government procurement all run on one gatekeeper contract, so citing the KLF's channel rule [[PROD-09]](lexicons/business-marketing.md#prod-09) also surfaces Fields' hostile-reader rule [[CLM-05]](lexicons/business-marketing.md#clm-05) and WCAG's scoped-claim rule [[A11Y-22]](lexicons/accessibility.md#a11y-22). [PRINCIPLES.md](PRINCIPLES.md) states each convergence as a first principle, lists the rules that back it, and records the tensions the lexicons keep on purpose.

## Versioning

Releases are annotated tags `vMAJOR.MINOR.PATCH`. Each tagged commit carries [`meta/release-manifest.json`](meta/release-manifest.json): a sha256 and rule count per lexicon file, plus the full rule-ID list, so a consumer can verify fetched bytes against the pin offline. Rule IDs are the API. A published ID disappearing is MAJOR, because every citation of it breaks; new IDs are MINOR; same-ID text changes are PATCH; a change to the consumption contract itself, such as a file moving, is also MAJOR. While the version is still 0.x, a breaking change lands in the minor slot (semver's pre-1.0 rule); 1.0.0 will be a deliberate declaration that the ID contract is stable. The level is computed from the ID diff at cut time, not chosen. Pin a tag and treat `main` as unreleased.

## Boundaries

- Project-neutral. Product opinions, roadmap judgments, and timing notes stay in consuming projects. If a change here is driven by one project's needs, it has stopped being canonical.
- Public rules, private arguments. Copyright protects a source's expression, not its ideas. The one-line rules are our own expression and ship; the chapter-level condensations behind them could substitute for their sources, so they stay in the private corpus. No distillation files are published here at all.

## Licensing

Everything published here is CC BY 4.0 ([`LICENSE`](LICENSE)). Cited sources belong to their authors and publishers; a citation is not a license. Attribution string, per-source rights, and the reasoning: [`NOTICE.md`](NOTICE.md).

## Layout

```
lexicons/                    the rules, one file per lexicon
PRINCIPLES.md                cross-domain convergences, stated as first principles
SOURCES.md                   every source slug resolved: its citation and what it feeds
meta/release-manifest.json   per-release digests and the full rule-ID list
AGENTS.md                    the agent contract (CLAUDE.md points here)
NOTICE.md                    licensing and rights, one page
LICENSE                      CC BY 4.0
```
