# Context obedience is a separate capability

Slug: `context-obedience-is-a-separate-capability`
Mechanism claim: Caption quality on a bare image and faithful use of injected context are uncorrelated capabilities, so ranking on the first and shipping into a context-dependent path selects on the wrong axis.

## Scope

Covers: model or prompt bake-offs for generation paths that inject external context (names, dates, places, retrieved passages, structured fact blocks) and then require the model to use that context in the output.
Excludes: pure no-context captioning; retrieval index design alone; fine-tuning vs retrieval ladder choices except as they change whether context must be obeyed; security injection defenses beyond treating supplied blocks as a declared authority class.

## Observable triggers

- Bake-off or ship gate reports only bare-image fluency, preference, or caption metrics while production prompts include a name/date/place or retrieved-evidence block.
- Context-assembly work is funded or shipped with no per-candidate score for insertion of supplied facts, non-contradiction, or invention of unsupplied facts.
- Winner selection cites prose quality; no two-arm table (no-context vs context-supplied) appears in the eval report.
- Downstream fusion or post-checks cannot state a mechanical subset rule on emitted fact units relative to supplied units.
- Failures are attributed to "retrieval" or "prompt wording" when the supplied block was present and the model ignored, contradicted, or embroidered it.

## Causal mechanism

Bare-image quality measures free generation under one input distribution. Context obedience measures whether the model treats a second input class as binding evidence: insert what was given, do not contradict it, and do not invent units that were never given. Those skills need not co-vary. Selecting the champion on the first metric installs a generator that is free to discard the context-assembly investment, so end-to-end quality stays flat while the assembly stage looks healthy in isolation.

## Required action

While the production path injects context that the answer must respect:

1. Run every candidate on two fixed arms with the same images and prompts except for the context block: no-context and context-supplied.
2. Score the context arm on three obedience surfaces: insertion of supplied facts, non-contradiction of supplied facts, and non-invention of facts not in the supplied set.
3. Prefer a merge-only fusion contract on structured fact units (`units_out ⊆ units_in`) so non-invention is checkable without a prose judge; validate any remaining open-ended scorer against human gold before it gates.
4. Ship or rank on the context-arm obedience scores (and end-to-end with context present), not on bare-arm fluency alone. Treat bare-arm metrics as a separate report, not the selection key.
5. When the product contract is grounding-required, refuse generation when the sufficiency policy fails rather than asking the model to invent the missing units.

## Predicted failure

The bake-off winner ships on caption or preference rank. Context assembly, retrieval packing, and prompt engineering then show no measurable lift: the model was never selected for using the block. Operators see confident prose that drops names, invents dates, or contradicts the supplied place line. Stage metrics look fine while the product metric does not move.

## Exemptions and boundaries

- No injected context at inference: bare-quality ranking may be the right gate; this card is idle.
- Systems that intentionally blend corpus evidence with parametric knowledge under a declared hybrid contract: still score non-contradiction of high-authority supplied units; do not demand pure merge-only unless the product claims corpus-bounded answers.
- Retrieval ceiling failures (needed evidence never retrieved): classify under retrieval diagnosis, not as obedience failure when the block was absent.
- Authority and injection security (untrusted text must not become policy): complementary; this card owns selection on use-of-supplied-evidence, not the full injection threat model.
- Sibling concerns such as index freshness, local vs global routing, or PEFT adaptation sit on other cards; plain-pointer only here.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | Bare-arm fluency and preference scores for no-context products and regression watch ([EVAL-01](../lexicons/ml-systems.md#eval-01), [EVAL-11](../lexicons/ml-systems.md#eval-11)) | Context-arm obedience scores for any path that injects binding evidence ([EVAL-06](../lexicons/ml-systems.md#eval-06), [EVAL-22](../lexicons/ml-systems.md#eval-22), [RAG-01](../lexicons/ml-systems.md#rag-01)) | Rank and ship on the arm that matches production inputs; never average the two into one leaderboard number |
| object | Open prose quality when many wordings are valid ([EVAL-11](../lexicons/ml-systems.md#eval-11)) | Claim support and merge-only unit subset when facts are machine-consumed or product-grounded ([FM-04](../lexicons/ml-systems.md#fm-04), [RAG-06](../lexicons/ml-systems.md#rag-06), [RAG-07](../lexicons/ml-systems.md#rag-07), [PROV-01](../lexicons/ml-systems.md#prov-01)) | Structure fact units under a schema so subset and support checks are mechanical; score remaining prose on a validated rubric only where structure ends |
| sequence | Assemble and budget context without silent truncation ([FM-02](../lexicons/ml-systems.md#fm-02), [RAG-05](../lexicons/ml-systems.md#rag-05), [RAG-09](../lexicons/ml-systems.md#rag-09)) | Score generation with that context present and attributable ([RAG-01](../lexicons/ml-systems.md#rag-01), [RAG-07](../lexicons/ml-systems.md#rag-07)) | Diagnose assembly and obedience as separate stages; a strong packer does not redeem a model that ignores the pack |
| authority class | Keep lower-authority text out of policy position ([FM-01](../lexicons/ml-systems.md#fm-01)) | Require the model to use declared evidence when the contract says the answer is evidence-bound ([RAG-06](../lexicons/ml-systems.md#rag-06), [PROV-01](../lexicons/ml-systems.md#prov-01)) | Label each block's authority; obey evidence class without elevating it to policy override |

## Disconfirmers

- On a fixed candidate set, bare-arm rank order predicts context-arm obedience order well enough that the second arm never changes the winner.
- Production paths that inject context show equal lift from assembly work for models selected only on bare quality.
- Mechanical `units_out ⊆ units_in` holds at ceiling for the bare-selected champion whenever the full unit set is present in context.
- Ablating the context block does not change claimed facts in outputs (context was never causal).

## Verification

- Eval artifact includes paired no-context and context-supplied runs for every candidate on the same item IDs.
- Context-arm report lists insertion, contradiction, and invention (or subset-violation) rates with denominators fixed outside the model.
- Structured path declares merge-only (`units_out ⊆ units_in`) and a CI or offline check fails the run on subset violation.
- Ship memo cites context-arm scores as the selection key; bare-arm numbers are labeled non-gating when production injects context.
- If an LLM judge scores any obedience surface, judge–human agreement on that surface is recorded and the judge protocol is pinned ([EVAL-12](../lexicons/ml-systems.md#eval-12), [EVAL-13](../lexicons/ml-systems.md#eval-13)).
- Grounding-required paths log abstain/clarify when sufficiency fails rather than silent invention ([RAG-06](../lexicons/ml-systems.md#rag-06)).

## Rule IDs

- [EVAL-01](../lexicons/ml-systems.md#eval-01): require a no-context (and other) baseline so the context arm's lift is interpretable
- [EVAL-06](../lexicons/ml-systems.md#eval-06): select the model that wins under the input regime production actually sends (context present), not only the clean bare arm
- [EVAL-11](../lexicons/ml-systems.md#eval-11): choose scorers that measure obedience surfaces, not sole string match or bare fluency
- [EVAL-12](../lexicons/ml-systems.md#eval-12): validate any open obedience judge against human gold before it gates
- [EVAL-13](../lexicons/ml-systems.md#eval-13): pin the judging protocol so two-arm trends stay comparable
- [EVAL-22](../lexicons/ml-systems.md#eval-22): treat bare-caption quality as an unvalidated proxy until it is shown to move the context-using product metric
- [FM-01](../lexicons/ml-systems.md#fm-01): declare authority class of injected blocks so evidence is used without becoming policy
- [FM-02](../lexicons/ml-systems.md#fm-02): budget context so obedience is not scored on a silently truncated block
- [FM-04](../lexicons/ml-systems.md#fm-04): schema-constrain fact units so merge-only subset checks are machine-consumable
- [RAG-01](../lexicons/ml-systems.md#rag-01): score retrieval/context supply separately from generation obedience
- [RAG-05](../lexicons/ml-systems.md#rag-05): select and pack evidence under a budget before blaming the generator
- [RAG-06](../lexicons/ml-systems.md#rag-06): gate grounding-required answers on sufficiency; inventing missing units is not obedience
- [RAG-07](../lexicons/ml-systems.md#rag-07): require material support for claims; unsupported embroidery fails the non-invention surface
- [RAG-09](../lexicons/ml-systems.md#rag-09): attribute flat product metrics to assembly vs obedience stage rather than one end-to-end score
- [PROV-01](../lexicons/ml-systems.md#prov-01): every emitted fact unit walks back to supplied evidence under the merge-only contract
- [HITL-03](../lexicons/ml-systems.md#hitl-03): gold-embed human checks when insertion or contradiction still needs annotator QC
- [HITL-09](../lexicons/ml-systems.md#hitl-09): treat human obedience review as a measured stage when it is part of the gate

## Principles

- 13. Evidence precedes commitment
- 18. A machine consumes contracts, not prose

## Evidence / source slugs

- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-01](../lexicons/ml-systems.md#fm-01), [FM-02](../lexicons/ml-systems.md#fm-02), [FM-04](../lexicons/ml-systems.md#fm-04), [RAG-01](../lexicons/ml-systems.md#rag-01), [RAG-05](../lexicons/ml-systems.md#rag-05), [RAG-06](../lexicons/ml-systems.md#rag-06), [RAG-07](../lexicons/ml-systems.md#rag-07), [RAG-09](../lexicons/ml-systems.md#rag-09), [EVAL-11](../lexicons/ml-systems.md#eval-11), [EVAL-12](../lexicons/ml-systems.md#eval-12), [EVAL-13](../lexicons/ml-systems.md#eval-13)
- [`designing-ml-systems`](../SOURCES.md#src-designing-ml-systems): supports [EVAL-01](../lexicons/ml-systems.md#eval-01), [EVAL-06](../lexicons/ml-systems.md#eval-06)
- [`ml-test-score`](../SOURCES.md#src-ml-test-score): supports [EVAL-22](../lexicons/ml-systems.md#eval-22)
- [`human-in-the-loop-ml`](../SOURCES.md#src-human-in-the-loop-ml): supports [HITL-03](../lexicons/ml-systems.md#hitl-03)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim to hold every important idea in its domain. It does not assert a measured correlation coefficient for any named model family, and it does not invent assessment-corpus slugs absent from SOURCES.md. It does not cover the full injection-security surface, retrieval recall ceilings, or adaptation-ladder policy beyond their effect on whether context must be scored. For bibliography identity, open SOURCES.md. For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
