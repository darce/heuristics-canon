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

| Lexicon | Governs | Rule families |
|---|---|---|
| [`lexicons/engineering.md`](lexicons/engineering.md) | building, running, debugging, shipping software | AGT · RES · CON · DATA · MODEL · STOR · FLOW · PERF · REF · TEST · DBG · DIAG · OBS · API · DOM · ARCH · TEAM · ALG · NAME · UI · RLSE |
| [`lexicons/business-marketing.md`](lexicons/business-marketing.md) | strategy, validation, GTM, negotiation, bootstrap economics, claims | STRAT · PROD · AIPX · GTM · NEG · OPS · BOOT · CLM |
| [`lexicons/design-aesthetics.md`](lexicons/design-aesthetics.md) | identity, typography, colour, layout, brand | IDNT · TYPE · COL · LAY · BRND |
| [`lexicons/writing.md`](lexicons/writing.md) | prose that does not read as machine-generated | WRIT |
| [`lexicons/accessibility.md`](lexicons/accessibility.md) | WCAG 2.2 working set, conformance discipline | A11Y |
| [`lexicons/security.md`](lexicons/security.md) | LLM/agent, web, secure-design principles, PHP, WordPress, PostgreSQL security (bootstrap pass) | SEC · WEB · SECD · PHP · WP · PG |
| [`lexicons/graph-theory.md`](lexicons/graph-theory.md) | reasoning as dependency graphs, assignment & cost, knowledge modeling, embedding & identity clustering | GRPH |
| [`lexicons/interaction-ux.md`](lexicons/interaction-ux.md) | perception, cognition, wayfinding, interaction, forms, human-AI review, data visualization, usability measurement | PERC · COG · NAV · INT · FORM · HAI · VIZ · UXR |
| [`lexicons/ml-systems.md`](lexicons/ml-systems.md) | model evidence, embeddings, evaluation, calibration, drift, fairness, provenance, human review, video tracking, serving cost, foundation-model composition, retrieval-augmented generation | MLDATA · EMB · EVAL · CAL · DRIFT · SERVE · FAIR · PROV · HITL · TRACK · COST · FM · RAG |
| [`lexicons/epistemics.md`](lexicons/epistemics.md) | human and agent judgment under uncertainty — scorable estimates, forecasts, and naturalistic decision making | FORE · NDM |

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
| database schema or migration | MODEL · DATA · STOR · PG |
| index or query change | STOR · DATA · PERF |
| batch or stream worker | FLOW · RES · OBS · COST |
| architecture proposal or adr | ARCH · DOM · TEAM · PERF · FORE · NDM |
| codeowners or service catalog or org change | TEAM · ARCH · DOM |
| concurrency or async code | CON · DATA · RES |
| security sensitive change | SEC · WEB · SECD · PG |
| ui or frontend change | PERC · COG · NAV · INT · FORM · VIZ · A11Y · UI |
| embedding or face recognition change | EMB · CAL · FAIR · PROV · TRACK · GRPH · COST · SEC |
| video timeline segmentation change | VSEG · TRACK · EVAL · COST · PERF |
| model weights or training change | MLDATA · EVAL · CAL · FAIR · PROV · SERVE · DRIFT · SEC |
| prompt or generation contract change | FM · EVAL · PROV · SEC |
| rag corpus or index change | RAG · EMB · DRIFT · PROV · SEC · COST · OBS |
| rag retrieval or reranking change | RAG · EVAL · EMB · COST · OBS |
| agent loop change | FM · RES · COST · OBS · PROV · SEC |
| agent tool side effect change | FM · SEC · DATA · API · SERVE · HAI · PROV |
| ai review or curation ui | HAI · HITL · CAL · PROV · VIZ · PERC · A11Y |
| agent session or skill change | AGT · FM · PROV · SEC |
| failing test or incident investigation | DBG · DIAG · OBS · TEST · RES · NDM |
| release or deploy change | RLSE · OPS · OBS · TEST · NDM |
| public naming or api surface | NAME · API · DOM · BRND |
| algorithm or data structure choice | ALG · PERF · GRPH · DATA |
| prose or documentation change | WRIT · CLM |
| strategy or product bet | STRAT · PROD · AIPX · BOOT · NEG · FORE · NDM · RSCH |
| estimate or forecast in a plan | FORE · STRAT · EVAL · CAL · NDM · MEAS |
| choosing a problem or research direction | RSCH · STRAT · FORE · NDM |
| pricing positioning or launch | GTM · CLM · PROD · BRND |
| brand or visual identity change | IDNT · BRND · TYPE · COL · LAY |
| php or wordpress change | PHP · WP · SEC · WEB |
| usability evaluation or metric | UXR · HAI · VIZ · PERC |
| generated rule index or registry change | REF · DATA · STOR · PROV · FM · PERF · TEST |

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
