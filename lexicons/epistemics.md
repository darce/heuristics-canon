# Epistemics Heuristics Lexicon

## About this document

Decision rules for human and agent judgment under uncertainty: how a plan,
estimate, or forecast is framed, written as a number that can be scored,
updated, and reviewed. Referenced, not read end to end: a plan, estimate, or
review cites a rule by ID where the judgment is committed, and this file holds
the claim behind it. It begins where machine calibration ends: `[CAL-*]` and
`[EVAL-*]` govern model scores and thresholds; this lexicon governs the
subjective *p* a person or agent puts on a claim before any model is involved.

What it covers, two populated families:

- **FORE**: forecasting, human and agent probabilistic judgment (resolvable
  questions, numeric probability, outside view, fermi decomposition, incremental
  belief updates, proper scoring, post-mortems)
- **NDM**: naturalistic decision making (recognition-primed decisions, mental
  simulation, pre-mortem, intent and common ground, de-minimis errors, and the
  validity–feedback gate that partitions expert recognition from scored
  estimation)

Scope boundary: decision heuristics for scorable judgment and for recognitional
judgment under time pressure, not a cognitive-science textbook. FORE
applicability is bounded where Tetlock's evidence comes from (resolvable ~1–12
month questions; long horizons, one-shots, self-fulfilling forecasts, fat tails
are exemptions). NDM applicability is bounded where Klein's evidence comes from
(high-validity domains with rapid feedback: fireground, NICU, C2, chess);
low-validity or slow-feedback domains route to FORE, not to "trust the expert."
The tension between FORE and NDM is documented, not averaged.

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[FORE-01]` |
| Trigger | observable in a plan, estimate, forecast, or review artifact |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask, answerable from the plan, estimate, and outcome notes |
| T·P | tier and phase, below |
| Src | source slug, resolved in the Sources section at the end of this file; the distillation behind it stays in the private research corpus |

Tier: **B**locker (a wrong answer corrupts correctness, ships real-world harm,
or breaks security), **S**hould (strong default), **J**udgment. Phase: **p**lan
(frame the claim), **e**stimate (author the number), **r**eview (score, update,
or gate). Cross-lexicon borders cite `↔ [ID]` rather than restating them.

Provenance: every row cites a primary source, chapter-traced in its
distillation. Tetlock & Gardner, *Superforecasting* (2015); Gary Klein, *Sources
of Power* (20th ann. 2017). Repo-derived rules enter at tier J with occurrence
provenance and are promoted by independent convergence. This file is the
canonical source: consuming repos inline cues by phase tag and cite rules by ID,
never copying row bodies.

## 1. FORE: Forecasting / human·agent probabilistic judgment

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| FORE-01 | estimate or risk is stated only in vague words (`likely`, `significant risk`, `serious possibility`, `may well`) with no number | **Numeric probability required** — words hide 20–80% disagreement and cannot be scored; force a number and defined terms (↔ [[CAL-02]](ml-systems.md) unknown is a valid result; ↔ [[HAI-08]](interaction-ux.md) uncertainty at decision granularity; ↔ [[CLM-04]](business-marketing.md) bare adjectives; ↔ [[CAL-03]](ml-systems.md) when *p* is consumed as a rate — that row is machine calibration, this is authoring a subjective *p*) | What exact probability (0–1) am I willing to put on this by date D? | S·e | superforecasting ch-3 |
| FORE-02 | forecast or success claim has no resolution date and/or no observable resolution criterion | **Resolvable forecast contract** — if it cannot resolve, it cannot train judgment or prove you wrong; rewrite until scorable (↔ [[STRAT-02]](business-marketing.md) inversion; ↔ [[PROD-04]](business-marketing.md) kill-criteria; ↔ [[TEST-06]](engineering.md) a test never observed failing; ↔ [[RLSE-06]](engineering.md) adverse-condition audit) | On what date, by what observable criterion, is this true or false? | B·p | superforecasting ch-3 |
| FORE-03 | a prediction was committed (numeric or verbal) and the outcome is known, but no score or track record is recorded | **Score the forecast** — apply a proper score (**Brier** or agreed equivalent); unscored judgment is the **illusion of a stopped clock** (↔ [[DBG-06]](engineering.md) re-run the original claim; ↔ [[TEST-06]](engineering.md) prove the green can go red; ↔ [[EVAL-01]](ml-systems.md) baselines without which a number is uninterpretable) | Where is the Brier (or score) for this call, and the running track record? | S·r | superforecasting ch-3 |
| FORE-04 | a single probabilistic forecast is marked "wrong" or "right" solely because the outcome fell on the other/same side of 50% | **Wrong-side-of-maybe ban** — one outcome does not grade one probability; grade calibration across a set (↔ [[CAL-03]](ml-systems.md) reliability diagram; ↔ [[DBG-06]](engineering.md) wrong test of verification; ↔ [[EVAL-01]](ml-systems.md) baselines over a set, not one lucky hit) | Are we grading a reliability diagram / set of calls, or litigating one unlucky 65%? | S·r | superforecasting ch-3 |
| FORE-05 | estimate or plan opens with case-specific narrative and never cites a base rate / reference class | **Outside view first** — start from how often this *class* happens, then adjust with the **inside view** (↔ [[STRAT-02]](business-marketing.md) disconfirmers before forward plan; ↔ [[PROD-02]](business-marketing.md) restate the problem before the solution; ↔ [[UXR-01]](interaction-ux.md) match claim to validation level) | What is the base rate for things of this sort, before our story? | S·p | superforecasting ch-5 |
| FORE-06 | a point probability or magnitude is given with no decomposition into sub-estimates and stated assumptions | **Fermi-ize** — break into tractable sub-questions; expose knowable vs unknowable; no black-box precision (↔ [[GRPH-14]](graph-theory.md) claim walks back to ancestors; ↔ [[PROV-02]](ml-systems.md) derived claims name their inputs; ↔ [[AGT-04]](engineering.md) evidence verbatim) | Which assumptions multiply to this number, and which are pure guesses? | S·e | superforecasting ch-5 |
| FORE-07 | an estimate revises in a large step (e.g. 30%→80%) on a single ordinary/non-diagnostic data point, or stays frozen after clearly diagnostic news | **Incremental belief updating** — default small moves that blend prior and likelihood; jump only on diagnostic signals; never freeze after hard news (↔ [[STRAT-02]](business-marketing.md) look for disconfirmers; ↔ [[PROD-04]](business-marketing.md) evidence kills darlings; ↔ [[DBG-03]](engineering.md)/[[DBG-04]](engineering.md) one change at a time / back out bad experiments) | What was the prior, how diagnostic is this signal, and why this step size? | S·r | superforecasting ch-7 |
| FORE-08 | probabilities are only coarse (`50/50`, `likely/unlikely`, or a 3-setting dial) when the decision is sensitive to finer odds | **Granularity** — distinguish degrees of doubt the problem permits; 63% vs 65% can be real skill (↔ [[CAL-02]](ml-systems.md) designed unknown; ↔ [[HAI-08]](interaction-ux.md) uncertainty at decision granularity; ↔ [[HITL-08]](ml-systems.md) name the uncertainty score; ↔ [[FORE-01]](epistemics.md) force a number, not three bins) | Could a 10-point swing change the decision — and did we resolve that coarse? | J·e | superforecasting ch-6 |
| FORE-09 | plan or estimate states a probability but lists no observations that would raise or lower it | **Pre-commit probability movers** — write what evidence would move *p* up/down (and what would kill the thesis) before new data arrives (↔ [[STRAT-02]](business-marketing.md) invert the thesis; ↔ [[PROD-04]](business-marketing.md) name the kill result; ↔ [[DBG-01]](engineering.md) reproduce failure first; ↔ [[TEST-06]](engineering.md) predict the failure message) | What would I see that would force a 10+ point update either way? | B·p | superforecasting ch-7 |
| FORE-10 | the same probability is assigned across materially different scopes (time windows, magnitudes, counts) without re-derivation | **Scope sensitivity** — re-estimate when scope changes; ban copy-paste *p* (↔ [[STRAT-02]](business-marketing.md) a new claim needs new disconfirmers; ↔ [[HAI-08]](interaction-ux.md) uncertainty matches the decision's scope; ↔ [[EVAL-04]](ml-systems.md) slice-based gate when aggregates hide scope) | If I double the time window, why is *p* unchanged? | S·r | superforecasting ch-11 |
| FORE-11 | outcome of a forecast is known but there is no process post-mortem (or contemporaneous notes cannot reconstruct why *p* was set) | **Forecast post-mortem** — reconstruct reasoning for hits and misses; keep perpetual-beta notes from forecast time (↔ [[DBG-06]](engineering.md) verify against the original claim; ↔ [[AGT-07]](engineering.md) externalize at discovery; ↔ [[ARCH-07]](engineering.md) ADR outlives the author) | Can I explain *why* the number was what it was, not only that it hit or missed? | S·r | superforecasting ch-8 |
| FORE-12 | a forecast is publicly or identity-committed and subsequent evidence is rationalized without moving *p* | **Ego-cost firewall** — separate advocacy from forecasting; allow private re-estimates; treat freeze after hard news as a defect (↔ [[STRAT-02]](business-marketing.md) commitment blocks disconfirmers; ↔ [[OPS-01]](business-marketing.md) you get the incentive you pay for; ↔ [[PROD-04]](business-marketing.md) evidence over darlings; tension with [[STRAT-07]](business-marketing.md): conviction is for values/mission, not for freezing empirical *p*) | If this number were anonymous, would it still be the same today? | S·r | superforecasting ch-7 |
| FORE-13 | every forecast is generated from one Big Idea / single framework with no competing model's probability | **Fox, not hedgehog** — force at least two causal models before locking *p*; hedgehogs lose calibration and resolution (↔ [[STRAT-01]](business-marketing.md) latticework over one Big Idea; ↔ [[STRAT-02]](business-marketing.md) rival models supply disconfirmers; ↔ [[PROD-04]](business-marketing.md) kill criteria from more than one story) | What would a smart rival model forecast, and how did we blend? | S·p | superforecasting ch-3 |

## 2. NDM: Naturalistic decision making

Recognition-primed and field decision discipline for time pressure, expertise, and plans about to commit. Complements FORE: when the domain is high-validity with rapid feedback, skilled recognition plus mental simulation is the right source of power; otherwise number and score. Do not average the two ([[STRAT-11]](business-marketing.md)).

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| NDM-01 | plan treats expert recognition/gut as authoritative, or forces multi-option analysis on a time-pressured expert call, without stating whether the domain has high-validity learnable cues and rapid unambiguous feedback | **Validity–feedback gate** — trust **RPD** only when both conditions hold; otherwise decompose, number, and score (↔ [[FORE-01]](epistemics.md) numeric *p*; ↔ [[FORE-05]](epistemics.md) outside view; ↔ [[FORE-09]](epistemics.md) pre-commit movers; ↔ [[COG-04]](interaction-ux.md) deliberate comparison when time allows; ↔ [[HAI-05]](interaction-ux.md) do not name expertise beyond the envelope; ↔ [[STRAT-11]](business-marketing.md) do not average opposed goods) | High-validity cues *and* fast feedback — yes or no? Which source of power does that select? | B·p | sources-of-power ch-7 |
| NDM-02 | plan or decision is about to be committed with no written failure analysis (no "why it failed" pass) | **Pre-mortem** — assume it is months later and the plan failed outright; each person writes why before commit (↔ [[STRAT-02]](business-marketing.md) invert; ↔ [[PROD-04]](business-marketing.md) kill result; ↔ [[FORE-09]](epistemics.md) pre-commit movers; ↔ [[RLSE-06]](engineering.md) adverse-condition audit; ↔ [[RLSE-08]](engineering.md) rollback before ship; ↔ [[TEST-06]](engineering.md) predict the failure) | What failure causes would make us say "of course it wasn't going to work"? | B·p | sources-of-power ch-5 |
| NDM-03 | time-critical incident or ops decision process requires a multi-attribute option-comparison matrix before first action when an experienced operator already has a recognized workable option | **RPD / singular evaluation** — evaluate the first workable option via **mental simulation**; do not force comparative matrix under time pressure when experience is high (↔ [[COG-04]](interaction-ux.md) comparison when deliberation is available — surface partition, not average; ↔ [[DIAG-01]](engineering.md) facts before locking a hypothesis; ↔ [[NDM-01]](epistemics.md) validity gate first; ↔ [[STRAT-11]](business-marketing.md) opposed goods) | Is time short, experience high, and a workable option recognized — or do we still need a matrix? | S·p | sources-of-power ch-3 |
| NDM-04 | first recognized course of action is committed with no walkthrough of barriers or failure modes | **Mental simulation of the first option** — run the action forward for barriers; if broken, modify or generate the next option before commit (↔ [[RLSE-06]](engineering.md) adverse conditions; ↔ [[FORE-09]](epistemics.md) what would break the claim; ↔ [[STRAT-02]](business-marketing.md) failure anatomy; ↔ [[RLSE-08]](engineering.md) design the escape before ship) | What breaks if we run this option forward in our heads? | S·p | sources-of-power ch-5 |
| NDM-05 | multiple early-warning cues each receive a separate benign local explanation, and no alternate diagnosis is considered | **De-minimis error ban** — do not explain away the set one cue at a time; treat the composite as anomaly and force an alternate diagnosis (**crystal ball**) (↔ [[STRAT-02]](business-marketing.md) disconfirmers; ↔ [[PROD-04]](business-marketing.md) evidence over the darling diagnosis; ↔ [[DBG-01]](engineering.md) reproduce/face the failure; ↔ [[DIAG-01]](engineering.md) facts before hypothesis; ↔ [[FORE-09]](epistemics.md) killers listed in advance; ↔ [[OBS-07]](engineering.md) page on the symptom cluster) | If the crystal ball says this story is wrong, what is the next best explanation of the same cues? | S·r | sources-of-power ch-5 |
| NDM-06 | plan or incident log shows expectancies / predicted observations violated, but execution continues without re-size-up | **Expectancy-violation stop** — when the pattern breaks, stop and re-diagnose; do not press the original recognition (↔ [[DBG-01]](engineering.md) make the anomaly fail the current story; ↔ [[DIAG-01]](engineering.md) facts before hypothesis; ↔ [[OBS-07]](engineering.md) the symptom is the page; ↔ [[FORE-07]](epistemics.md) hard news must move the call) | Which expectancy failed, and what situation does that imply instead? | S·r | sources-of-power ch-4 |
| NDM-07 | task handoff, agent instruction, or order lists steps only — no goal, priorities, constraints, or forbidden moves | **Intent on the wire** — state purpose, priorities, constraints, and forbidden moves so the executor can improvise and catch errors (**common ground**) (↔ [[HAI-04]](interaction-ux.md) intent feedback on automation; ↔ [[HAI-05]](interaction-ux.md) do not claim autonomy beyond stated envelope; ↔ [[AGT-07]](engineering.md) externalize at handoff; ↔ [[ARCH-07]](engineering.md) decision/intent outlives the author; ↔ [[TEAM-01]](engineering.md) communication path must match the work) | If they must improvise, do they know what success and failure look like? | S·p | sources-of-power ch-13 |
| NDM-08 | team is about to make an irreversible call while members hold materially different situation pictures, or private diagnoses never enter the shared record | **Team-mind merge** — force a shared situation picture and shared intent before the irreversible call (↔ [[TEAM-01]](engineering.md) align communication with the decision boundary; ↔ [[AGT-07]](engineering.md) externalize private knowledge; ↔ [[ARCH-07]](engineering.md) record the diagnosis; ↔ [[HAI-06]](interaction-ux.md) durable decision log) | Can each member state the same diagnosis and intent in one sentence? | S·p | sources-of-power ch-14 |
| NDM-09 | analysis continues after options are already near-ties with no remaining decision-critical difference | **Zone of indifference** — when options are that close, pick a workable one and move on; stop optimizing (↔ [[STRAT-11]](business-marketing.md) do not grind opposed near-equals into mush; ↔ [[FORE-08]](epistemics.md) granularity only where the decision is sensitive; ↔ [[COG-04]](interaction-ux.md) comparison earns its keep when frames differ) | If the delta no longer changes the decision, why are we still scoring? | J·r | sources-of-power ch-7 |
| NDM-10 | multi-stakeholder conflict or formal justification is required, but the record has only a singular RPD narrative with no option comparison | **Comparative evaluation when required** — use option comparison for justification and conflict resolution (Table 7.1) (↔ [[COG-04]](interaction-ux.md) compute the comparison for the deliberate mind; ↔ [[ARCH-07]](engineering.md) ADR records alternatives; ↔ [[CLM-05]](business-marketing.md) gatekeeper must be able to check the choice; ↔ [[FORE-13]](epistemics.md) rival models before lock-in; ↔ [[NDM-03]](epistemics.md) singular evaluation keeps the other boundary) | Do we need a defensible comparison for stakeholders, or only a workable first option? | S·p | sources-of-power ch-7 |
| NDM-11 | decision process demands pure multiattribute rational analysis for every call, including time-critical expert recognition in a domain that already passes the validity–feedback gate | **Hyperrationality ban** — analysis is a source of power with limits; do not make it the only legal move (↔ [[NDM-01]](epistemics.md) gate first; ↔ [[NDM-03]](epistemics.md) singular evaluation when the table says so; ↔ [[COG-04]](interaction-ux.md) comparison when deliberation is the point; ↔ [[STRAT-11]](business-marketing.md) opposed goods stay partitioned) | Are we analyzing because the boundary table says so, or because analysis is our only ritual? | S·r | sources-of-power ch-15 |

<!-- BEGIN GENERATED SOURCES -->

## Sources

Every `Src` cell above names one of these. The citation is the work itself; the distillation behind it stays in the private research corpus.

| Src | Source | Rules here |
|---|---|---|
| `sources-of-power` | Gary Klein, *Sources of Power: How People Make Decisions*, 20th Anniversary Edition (MIT Press, 2017) | 11 |
| `superforecasting` | Philip E. Tetlock & Dan Gardner, *Superforecasting: The Art and Science of Prediction*, 1st ed. 2015 | 13 |

<!-- END GENERATED SOURCES -->
