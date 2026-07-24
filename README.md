# Heuristics canon

A versioned corpus of 1,000+ decision rules for software, product, design,
security, research, and operations. Each rule is a stable ID attached to an
observable trigger, a falsifiable action, a question, a tier, and a citable
source.

The distinctive output is cross-domain reasoning. When unrelated sources reach
the same causal mechanism, [PRINCIPLES.md](PRINCIPLES.md) joins their rules so
an agent working in one domain retrieves evidence its native vocabulary would
not surface.

## Apply the canon

Do not load every lexicon.

1. Match the changed artifact to the [routing table](#routing-by-artifact).
2. Open only the listed family anchors; narrow by plan/write/review/ship phase
   when useful.
3. Keep a rule only when its trigger is observed. Read its exemptions and tier;
   report an unwalkable or non-authoritative source rather than borrowing its
   authority.
4. If the rule appears in `PRINCIPLES.md`, load its cross-domain siblings as
   independent mechanism checks, not votes.
5. Partition opposed rules by surface, object, or sequence. Keep upstream and
   downstream rules wired when they watch the same failure.
6. Decide, cite `[ID]`, and stop when no applicable blocker or strong default
   remains unresolved.

For the complete automated-consumer contract, see [AGENTS.md](AGENTS.md).

## Progressive retrieval ladder

Rule rows are the default depth. Open more only when the decision is still
under-specified:

```text
rule row  ->  reasoning card  ->  source note  ->  original source
 (lexicon)     (reasoning/)       (sources/)        (publisher copy)
```

1. **Rule row** (default). Match the artifact, keep rows whose triggers fire,
   read tier and exemptions. Cite `[FAM-NN]`.
2. **Reasoning card.** Open a card only when several retained rules share one
   mechanism, or a principle joins cross-domain siblings. Cards rebuild the
   decision (triggers, action, failure, tensions, verification), not a book.
   See [reasoning/README.md](reasoning/README.md).
3. **Source note.** Open a note only for citation audit: how hard a `SOURCES.md`
   slug works for the rules that cite it. See [sources/CONTRACT.md](sources/CONTRACT.md).
4. **Original source.** Last. Obtain the work through ordinary legal channels.
   This repo never ships research copies or chapter condensations.

Cards and notes are pilots for hot mechanisms; they are not coverage of the
whole canon. A card without a firing trigger is inert.

## What's inside

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

```text
| RES-02 | blocking call with no timeout | Timeout every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

- **ID** is the permanent citation key.
- **Trigger** is observable in an artifact, plan, error, or metric.
- **Rule** is the condition, action, and consequence.
- **Answers** is the decision-point question.
- **T·P** is tier and phase. `B` blocks; `S` is a strong default with
  exemptions; `J` requires contextual judgment and escalation when context is
  absent. Phase codes map to the buckets below.
- **Src** resolves through [SOURCES.md](SOURCES.md). The underlying
  distillations remain private.

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

## Why principles matter

Ordinary retrieval stays inside the question's domain. The principles encode
independent arrivals that expose hidden gatekeepers, denominators, blast radii,
feedback delays, and source-of-truth errors across domains.

The 19 mechanisms remain separate because overlap in theme is not identity of
trigger, cause, and action. Wrong proxy differs from a shaped sample; least
privilege differs from dual control; falsification differs from evidence timing;
a commit gate differs from step size. `PRINCIPLES.md` also records how opposed
rules partition and how complementary rules amplify one another.

## Versioning and integrity

Pin an annotated `vMAJOR.MINOR.PATCH` tag. Its
[`meta/release-manifest.json`](meta/release-manifest.json) uses schema
`heuristics-canon/release@2` and records:

- every published rule ID;
- SHA-256 for each lexicon file;
- SHA-256 for every file under `reasoning/` and `sources/` (when present).

Semver for the published surface (rule IDs, reasoning cards, and source notes):

| Change | Level |
|---|---|
| Removal of a published rule ID, lexicon file, reasoning card, or source note | **breaking** (MAJOR; on 0.x lands in the minor slot per pre-1.0 practice) |
| Addition of a rule ID, lexicon, card, or note | **minor** |
| Same-ID / same-path content change only | **patch** |

Treat `main` as unreleased. Verify offline:

```sh
git fetch --tags
git checkout <version-tag>
shasum -a 256 lexicons/*.md
# when present:
find reasoning sources -type f 2>/dev/null | sort | xargs shasum -a 256
```

Compare digests with `meta/release-manifest.json`. The manifest also carries
the full rule-ID set, so contract drift is checkable without network access.

## Boundaries and licensing

This repository is a read-only projection of a private research corpus. Rules,
principles, reasoning cards, and source notes are authored upstream; open an
issue here rather than a pull request. The projection publishes operational
rules and intermediate decision aids, not source excerpts; quoted or
source-adjacent expression is a defect to report. Chapter-level distillations
and research-copy source text are never published.

Original rule, principle, card, and note prose is offered under CC BY 4.0 as
stated in [NOTICE.md](NOTICE.md). That grant does not cover third-party works
identified in `SOURCES.md` or in source notes; citation is not a license. See
NOTICE for the precise scope and exclusions. This README states no legal
conclusion about fair use or downstream rights.

## Layout

```text
lexicons/                    rules, grouped by domain and family
PRINCIPLES.md                cross-domain convergences and tensions
SOURCES.md                   source identities and what each feeds
reasoning/                   progressive mechanism cards (pilot depth)
  CONTRACT.md                card schema and anti-reconstruction rules
  README.md                  retrieval ladder and how to open a card
  *.md                       mechanism cards (slug-named)
sources/                     critical source notes (citation audit)
  CONTRACT.md                note schema; no legal conclusions
  <slug>.md                  notes keyed by SOURCES.md slug
meta/release-manifest.json   release@2 digests and stable rule-ID set
AGENTS.md                    automated-consumer contract
NOTICE.md                    rights boundary and CC BY scope
```
