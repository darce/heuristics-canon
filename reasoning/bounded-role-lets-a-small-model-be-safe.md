# Bounded role lets a small model be safe

Slug: `bounded-role-lets-a-small-model-be-safe`
ID: `CARD-19`
Mechanism claim: Evaluate each stage against its contract: validate machine-consumed output structurally, check factual compliance with an inventory-grounded scorer or validated rubric, and evaluate evidence-recovery stages on their task outcome; choose model tiers by comparative evaluation under those contracts.

## Scope

Covers: Choosing model capacity per pipeline stage when some stages emit under a closed assertable set (forensic inventory, schema-bound prose, refuse-to-invent) and other stages fuse or recover evidence whose quality must be measured.
Excludes: Training-data collection design; PEFT vs full fine-tune as the primary question; human-review staffing as the primary question; security injection defense beyond authority-classing inputs; product copywriting outside an evidence-bound access or caption contract.

## Observable triggers

- One model size, checkpoint, or API tier is named for every generation stage (captioner, summarizer, fusion, adjudicator).
- The stage brief forbids new facts, non-visible narrative, uncited identity, or free-form machine-consumed prose, yet the plan still upgrades the model "for quality."
- Caption, alt, or forensic text invents who/what/why beyond in-frame visibles while larger models are praised for "better writing."
- Cost or latency budgets concentrate spend on fluent generation and starve the stage that fuses retained observations or scores hard evidence.
- Plans treat capability as a global property of the product rather than a property of each stage's contract.

## Causal mechanism

A closed assertable set bounds what a stage may emit. Schema validation checks structure, but string fields can still contain invented names or events; factual compliance needs an inventory-grounded scorer or a rubric validated against human judgments on the task. Use functional oracles for executable outputs and task-appropriate scoring for open prose. Evidence-recovery stages need evaluation of their task outcomes. When stages have different measured cost and quality requirements, compare their costs and outcomes separately: inexpensive high-recall retrieval generates candidates, then a stronger, costlier reranker serves top-k precision. Compare cost, accuracy, coverage, and the business KPI when routing easy queries to cheaper or cached paths and hard queries to expensive models. Whether captioning and evidence fusion benefit from different model tiers remains a hypothesis to test under their contracts.

## Required action

1. Name each generation stage and its contract: forbid-new-facts vs recover-or-fuse-truth vs free interpretation.
2. For forbid-new-facts stages, bind instruction authority, schema or voice (FORENSIC vs EDITORIAL), and assertable inventory; constrain and validate machine-consumed output structurally, and check factual compliance with an inventory-grounded scorer or validated rubric. Choose a model tier by comparative evaluation under the stage contract; try cheaper prompt, retrieval, or tool interventions before fine-tuning, and escalate only against a named failure they cannot fix.
3. For recover-or-fuse-truth stages, size and evaluate for evidence quality (fusion of retained observations, calibrated unknown, end-to-end error)—not for prose style.
4. Record each stage's tier, cost, and task outcome; permit a shared tier when comparative evaluation supports it, and split tiers only when measured outcomes justify the change.

## Predicted failure

Choosing tiers without per-stage evaluation can waste budget or miss quality requirements. A schema-valid caption may invent identity or non-visible events, and fusion may fail its evidence-quality target; neither failure establishes which model size will fix it.

## Worked example

Alt text and multi-camera identity fusion share one API tier in the capacity plan because "one model is simpler to operate." Captions start inventing names for people barely in frame while fusion of badge and face misses its quality target. Compare tiers under fixed stage contracts: check caption structure and factual inventory against gold, measure fusion decision error, and record cost per accepted output. Use a smaller caption model or a larger fusion model only if those measurements support it; keep a shared tier if it meets both contracts at the preferred cost.

## Exemptions and boundaries

- Open editorial, marketing, or fiction stages with no evidence contract: this card does not force a small model; attribution and claim rules still apply where identity or harm content appears.
- Stages already proven on gold that a larger model reduces inventory error under the same closed contract: escalate with that evidence; do not re-open the assertable set.
- Pure retrieval or non-generative fusion with no language model: size the actual scorer; evaluate any later generative stage under its own contract before choosing its tier.
- Human adjudication queues: measure residual human error separately; do not treat "we have a reviewer" as license for an unbound captioner.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface (stage contract) | [BOUND-01](../lexicons/depiction.md#bound-01) [ATTRIB-01](../lexicons/depiction.md#attrib-01) [ATTRIB-03](../lexicons/depiction.md#attrib-03): closed inventory, measured factual compliance | [EMB-07](../lexicons/ml-systems.md#emb-07) [PROV-01](../lexicons/ml-systems.md#prov-01): fuse retained evidence; measure evidence-recovery quality | Compare tiers under each stage contract; split only when measured cost and quality justify it |
| object (what "better model" optimizes) | [FM-04](../lexicons/ml-systems.md#fm-04) [WRIT-26](../lexicons/writing.md#writ-26): validate structure and separately restore omitted actors when responsibility or needed attribution is concealed | [COST-07](../lexicons/ml-systems.md#cost-07) [FM-05](../lexicons/ml-systems.md#fm-05): compare path cost, accuracy, coverage, and the business KPI; test cheaper interventions before escalation | Optimize caption stages for inventory fidelity; fusion stages for decision error |
| sequence (escalate capacity) | [FM-05](../lexicons/ml-systems.md#fm-05) [COST-04](../lexicons/ml-systems.md#cost-04): measure cost per accepted output; test cheaper interventions | [CAL-02](../lexicons/ml-systems.md#cal-02) [HAI-01](../lexicons/interaction-ux.md#hai-01): unknown and evidence-before-label for non-identity AI claims beat a forced fluent answer | Choose capacity from task scores and cost; before fine-tuning, record the failure cheaper interventions could not fix |

## Disconfirmers

- Tiers selected by per-stage comparative evaluation under fixed contracts consistently lose on end-to-end decision error or cost per accepted correct output to tiers rejected by those evaluations, with the same contracts and budget.
- A closed assertable inventory, schema validation, and separate factual-compliance checks do not reduce uncited identity or non-visible claims compared with free prose on the same inputs.
- The inventory-grounded scorer or validated rubric consistently ranks a tier with more factual inventory errors above one with fewer errors on held-out gold, under the same stage contract and cost budget.
- The product has only one generation stage with one contract (no pipeline split to mis-tier).

## Verification

- Stage table lists contract class, model tier, and eval metric for every generation step; a shared default is supported by comparative evaluation for each stage.
- Caption/forensic sample: every who/identity/guilt/non-visible claim is tagged, editorial, or absent; schema validation passes without free-prose fallback, and a separate inventory-grounded scorer or validated rubric checks factual compliance.
- Ablation: compare candidate tiers for each stage with its contract held fixed; count caption inventory errors and fusion decision errors on gold alongside cost.
- Cost ledger attributes spend per stage; compare shared and split tiers against the same quality targets and budget.

## Rule IDs

- [BOUND-01](../lexicons/depiction.md#bound-01): bounds the assertable set independently of model size
- [ATTRIB-01](../lexicons/depiction.md#attrib-01): blocks person-as-owner of non-visible traits in forensic voice
- [ATTRIB-02](../lexicons/depiction.md#attrib-02): blocks uncited identity and guilt in forensic captions
- [ATTRIB-03](../lexicons/depiction.md#attrib-03): keeps non-visible narrative out of inventory voice
- [WRIT-26](../lexicons/writing.md#writ-26): restore an omitted actor when omission conceals responsibility or evades a needed attribution
- [FM-01](../lexicons/ml-systems.md#fm-01): preserve instruction-authority so the contract stays in policy position
- [FM-04](../lexicons/ml-systems.md#fm-04): schema-constrain machine-consumed stage output
- [FM-05](../lexicons/ml-systems.md#fm-05): try cheaper adaptation interventions before fine-tuning against a proven failure
- [PROV-01](../lexicons/ml-systems.md#prov-01): every retained claim walks back to evidence
- [EMB-07](../lexicons/ml-systems.md#emb-07): fusion stage fuses retained observations rather than matching on one
- [CAL-02](../lexicons/ml-systems.md#cal-02): unknown is valid when the contract cannot invent a fill
- [COST-04](../lexicons/ml-systems.md#cost-04): judge spend per accepted correct output per stage
- [COST-07](../lexicons/ml-systems.md#cost-07): route easy queries to cheaper or cached paths and hard queries to expensive models; compare cost, accuracy, coverage, and the business KPI
- [HAI-01](../lexicons/interaction-ux.md#hai-01): evidence before label for non-identity AI claims at human-facing surfaces

## Principles

- 9. A claim must walk back to what produced it
- 11. Unknown is a designed state
- 18. A machine consumes contracts, not prose

## Evidence / source slugs

- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-01](../lexicons/ml-systems.md#fm-01), [FM-04](../lexicons/ml-systems.md#fm-04), [FM-05](../lexicons/ml-systems.md#fm-05)
- [`berger-ways-of-seeing`](../SOURCES.md#src-berger-ways-of-seeing): supports [ATTRIB-01](../lexicons/depiction.md#attrib-01), [ATTRIB-03](../lexicons/depiction.md#attrib-03)
- [`sontag-on-photography`](../SOURCES.md#src-sontag-on-photography): supports [ATTRIB-01](../lexicons/depiction.md#attrib-01), [ATTRIB-03](../lexicons/depiction.md#attrib-03)
- [`sontag-regarding-the-pain-of-others`](../SOURCES.md#src-sontag-regarding-the-pain-of-others): supports [ATTRIB-02](../lexicons/depiction.md#attrib-02)
- [`barthes-image-music-text`](../SOURCES.md#src-barthes-image-music-text): supports [ATTRIB-01](../lexicons/depiction.md#attrib-01), [ATTRIB-03](../lexicons/depiction.md#attrib-03)
- [`azoulay-civil-contract-of-photography`](../SOURCES.md#src-azoulay-civil-contract-of-photography): supports [ATTRIB-01](../lexicons/depiction.md#attrib-01), [ATTRIB-03](../lexicons/depiction.md#attrib-03)
- [`model-cards`](../SOURCES.md#src-model-cards): supports [PROV-01](../lexicons/ml-systems.md#prov-01)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not prescribe a universal small-model mandate, a single fusion algorithm, or a full catalog of caption styles. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
