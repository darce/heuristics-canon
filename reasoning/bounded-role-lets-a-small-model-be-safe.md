# Bounded role lets a small model be safe

Slug: `bounded-role-lets-a-small-model-be-safe`
ID: `CARD-19`
Mechanism claim: When a stage's contract forbids introducing new facts, model capability mainly buys fluent invention so a small model is correct; when a stage must recover truth from hard evidence, capability is required—so one model tier for the whole pipeline is the wrong decision.

## Scope

Covers: Choosing model capacity per pipeline stage when some stages emit under a closed assertable set (forensic inventory, schema-bound prose, refuse-to-invent) and other stages fuse or recover evidence where quality tracks capability.
Excludes: Training-data collection design; PEFT vs full fine-tune as the primary question; human-review staffing as the primary question; security injection defense beyond authority-classing inputs; product copywriting outside an evidence-bound access or caption contract.

## Observable triggers

- One model size, checkpoint, or API tier is named for every generation stage (captioner, summarizer, fusion, adjudicator).
- The stage brief forbids new facts, non-visible narrative, uncited identity, or free-form machine-consumed prose, yet the plan still upgrades the model "for quality."
- Caption, alt, or forensic text invents who/what/why beyond in-frame visibles while larger models are praised for "better writing."
- Cost or latency budgets concentrate spend on fluent generation and starve the stage that fuses retained observations or scores hard evidence.
- Plans treat capability as a global property of the product rather than a property of each stage's contract.

## Causal mechanism

A closed assertable set turns generation into constrained rephrasing of allowed inputs. Under that contract, extra parameters buy smoother wording and plausible fills, not verifiable truth; the larger model is more likely to re-author the frame. A stage whose job is to recover or fuse evidence from weak or multi-source signal is the opposite: error falls when capacity, coverage, or dedicated fusion improves the decision. Uniform tiering therefore misprices both ends—over-paying where fluency is the failure mode, under-paying where capability is the truth mechanism.

## Required action

1. Name each generation stage and its contract: forbid-new-facts vs recover-or-fuse-truth vs free interpretation.
2. For forbid-new-facts stages, bind instruction authority, schema or voice (FORENSIC vs EDITORIAL), and assertable inventory; pick the smallest model that meets structured validation and gold inventory checks; treat fluent elaboration as a regression.
3. For recover-or-fuse-truth stages, size and evaluate for evidence quality (fusion of retained observations, calibrated unknown, end-to-end error)—not for prose style.
4. Refuse a single default tier "for the pipeline"; record the per-stage tier and the failure the cheaper tier could not fix when escalating.

## Predicted failure

One model tier for the whole pipeline: over-pay and over-fluent at the captioner (invented identity, non-visible plot, secured full meaning) while under-paying at fusion or hard evidence recovery, so end-to-end cost rises and truth falls in different places for the same wrong reason.

## Worked example

Alt text and multi-camera identity fusion share one API tier in the capacity plan because "one model is simpler to operate." Captions start inventing names for people barely in frame while fusion of badge and face still runs on leftover budget. Put a small model plus schema check on captions; spend the large tier only where fusion error drops. One tier for both jobs overpays fluency and underpays truth.

## Exemptions and boundaries

- Open editorial, marketing, or fiction stages with no evidence contract: this card does not force a small model; attribution and claim rules still apply where identity or harm content appears.
- Stages already proven on gold that a larger model reduces inventory error under the same closed contract: escalate with that evidence; do not re-open the assertable set.
- Pure retrieval or non-generative fusion with no language model: size the actual scorer; the uniform-tier failure still applies if a generative model is later inserted without a role split.
- Human adjudication queues: measure residual human error separately; do not treat "we have a reviewer" as license for an unbound captioner.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface (stage contract) | [BOUND-01](../lexicons/depiction.md#bound-01) [ATTRIB-01](../lexicons/depiction.md#attrib-01) [ATTRIB-03](../lexicons/depiction.md#attrib-03): closed inventory, small fluent model | [EMB-07](../lexicons/ml-systems.md#emb-07) [PROV-01](../lexicons/ml-systems.md#prov-01): fuse retained evidence; capability where truth tracks capacity | Split tiers by stage contract, not by product brand |
| object (what "better model" optimizes) | [FM-04](../lexicons/ml-systems.md#fm-04) [WRIT-26](../lexicons/writing.md#writ-26): schema pass and sourced claims beat stylish prose | [COST-07](../lexicons/ml-systems.md#cost-07) [FM-05](../lexicons/ml-systems.md#fm-05): pay for quality only where eval proves the cheaper layer fails | Optimize caption stages for inventory fidelity; fusion stages for decision error |
| sequence (escalate capacity) | [FM-05](../lexicons/ml-systems.md#fm-05) [COST-04](../lexicons/ml-systems.md#cost-04): cheapest adequate per accepted output | [CAL-02](../lexicons/ml-systems.md#cal-02) [HAI-01](../lexicons/interaction-ux.md#hai-01): unknown and evidence-before-label beat a forced fluent answer | Escalate only after gold shows the small model fails the stage contract, not after subjective "thin" wording |

## Disconfirmers

- Under a fixed closed contract and gold inventory scorer, larger models systematically reduce factual inventory error rather than only increasing fluent non-visible content.
- A single mid-tier model matches split-tier cost-per-accepted-correct on both caption inventory and fusion decision error within the same budget.
- Fusion quality is insensitive to capacity once inputs are fixed, so under-paying fusion never moves the end-to-end metric.
- The product has only one generation stage with one contract (no pipeline split to mis-tier).

## Verification

- Stage table lists contract class, model tier, and eval metric for every generation step; no orphan "default model" global.
- Caption/forensic sample: every who/identity/guilt/non-visible claim is tagged, editorial, or absent; schema validation passes without free-prose fallback.
- Ablation: swap captioner up a tier with contract held fixed—count invented non-visibles and identity labels; swap fusion down a tier—count decision error on gold.
- Cost ledger attributes spend per stage; fusion and captioner are not forced to the same unit price without a written exemption.

## Rule IDs

- [BOUND-01](../lexicons/depiction.md#bound-01): names the closed assertable set that makes small models safe
- [ATTRIB-01](../lexicons/depiction.md#attrib-01): blocks person-as-owner of non-visible traits in forensic voice
- [ATTRIB-02](../lexicons/depiction.md#attrib-02): blocks uncited identity and guilt in forensic captions
- [ATTRIB-03](../lexicons/depiction.md#attrib-03): keeps non-visible narrative out of inventory voice
- [WRIT-26](../lexicons/writing.md#writ-26): name the source or cut the claim under the closed contract
- [FM-01](../lexicons/ml-systems.md#fm-01): preserve instruction-authority so the contract stays in policy position
- [FM-04](../lexicons/ml-systems.md#fm-04): schema-constrain machine-consumed stage output
- [FM-05](../lexicons/ml-systems.md#fm-05): escalate capacity only after cheaper layer is proven insufficient
- [PROV-01](../lexicons/ml-systems.md#prov-01): every retained claim walks back to evidence
- [EMB-07](../lexicons/ml-systems.md#emb-07): fusion stage fuses retained observations rather than matching on one
- [CAL-02](../lexicons/ml-systems.md#cal-02): unknown is valid when the contract cannot invent a fill
- [COST-04](../lexicons/ml-systems.md#cost-04): judge spend per accepted correct output per stage
- [COST-07](../lexicons/ml-systems.md#cost-07): explicit quality–cost–coverage trade across stages
- [HAI-01](../lexicons/interaction-ux.md#hai-01): evidence before label at human-facing claim surfaces

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
