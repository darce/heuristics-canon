# Business & Marketing Heuristics Lexicon

## About this document

Decision rules for strategy, product validation, go-to-market, negotiation, bootstrap
economics, and claims. Referenced, not read end to end: a roadmap, scope, pricing page,
or outbound sequence cites a rule by ID where the decision happens, and this file holds
the claim behind it.

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[STRAT-02]` |
| Trigger | observable in a roadmap, metric, conversation, or market signal |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the decision is made |
| T·P | tier and phase, below |
| Src | source slug, resolved in the Sources section at the end of this file; the distillation behind it stays in the private research corpus |

Tier: **B**locker (existential or irreversible if violated), **S**hould (strong default
with named exemptions), **J**udgment (weigh in context, and escalate when the context is
missing). Phase: **s**trategy, **p**roduct, **g**tm, **o**ps.

A new rule from a lived outcome enters at tier J with the outcome as its provenance.

## 1. Strategy & Bets

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| STRAT-01 | strategy uses one framework for a multi-causal bet | **Latticework required** — hang the decision on multiple discipline models or refuse certainty | Which three non-native models change the conclusion? | B·s | poor-charlies-almanack ch-2 |
| STRAT-02 | plan only shows the path to win, no failure anatomy | **Invert, always invert** — define non-X and disconfirmers before the forward plan (↔ ml [[FAIR-02]](ml-systems.md?plain=1#L183)/[[FAIR-03]](ml-systems.md?plain=1#L184) disaggregated evidence before deploy; ↔ ml [[HITL-05]](ml-systems.md?plain=1#L216) agreement is not truth before the label commits; ↔ ux [[INT-07]](interaction-ux.md?plain=1#L117) preview before costly commit; ↔ ml [[EVAL-01]](ml-systems.md?plain=1#L117)/[[TEST-03]](engineering.md?plain=1#L208) baseline and characterization before the new contract) | Where do we die, and what evidence would kill this thesis? | B·s | poor-charlies-almanack ch-5 |
| STRAT-03 | team enters a domain where the edge boundary is unknown | **Circle of competence** — yes / no / too-tough baskets; no fake fluency (↔ epi [[NDM-01]](epistemics.md?plain=1#L79) trust expertise only when validity and feedback hold; ↔ ux [[HAI-05]](interaction-ux.md?plain=1#L142) do not name capability beyond the tested envelope; ↔ ml [[CAL-02]](ml-systems.md?plain=1#L146) unknown is a valid result; ↔ ml [[EMB-04]](ml-systems.md?plain=1#L105) de-emphasise the identity-void rather than force a face; ↔ ml [[HITL-07]](ml-systems.md?plain=1#L218) escalate the unsure item to a human) | If the next hard question comes, are we Planck or the chauffeur? | B·s | poor-charlies-almanack ch-3 |
| STRAT-04 | rare clear edge appears with favorable odds | **Load the boat** — bet seldom, bet big when mispriced; pair with [[OPS-02]](business-marketing.md?plain=1#L120) sit-on-your-hands | If we only get 20 punches lifetime, is this punch-worthy? | S·s | poor-charlies-almanack ch-8 |
| STRAT-05 | a product bet is justified mainly by a competitor's launch, raise, valuation, executive attention, or peer adoption | **Mimetic-convergence audit** — separate independently observed customer evidence from desire *mediated* by a competitor or status model; imitation makes many firms converge on one object without proving it is valuable to *this* firm | Would we choose this bet if the competitor's activity were hidden? | S·p | deceit-desire-and-novel |
| STRAT-06 | roadmap fills with consumer conveniences | **Consequential over trivial** — allocate talent to problems that still matter in a decade | If this wins, what capability exists that didn't? | S·s | technological-republic ch-1 |
| STRAT-07 | strategy flipped after a pile-on / backlash | **Conviction over crowd veto** — backlash is input, not board | What did we believe last quarter that evidence still supports? | J·s | technological-republic ch-3 |
| STRAT-08 | planning a debut mass-market win as if it funds five years | **Spike is not a business model** — extract rights and cash from a spike; don't staff for automatic repeat | What survives if the spike never happens again? | B·s | klf-the-manual ch-1 |
| STRAT-09 | post-hit plan is to rerun the exact exploit | **One-time hole** — systems close visible hacks; change formula or accept nostalgia | What breaks if the platform adapts tomorrow? | S·s | klf-the-manual ch-14 |
| STRAT-10 | vendor offers free work for equity/rights or "I'll intro the majors" | **Keep the rights; hire the services** — flattery trades are how spikes lose their only real money | Who owns the IP if this works? | B·s | klf-the-manual ch-9 |
| STRAT-11 | pressure to split the difference on price/terms | **Never split the difference** — the middle is often the worst design; repackage instead | Is there a package that beats 50/50? | S·s | never-split-the-difference ch-6 |
| STRAT-12 | market price/hype spike used as validation of quality | **Price ≠ value** — intrinsic math over Mr. Market mood | What is the value if the quote were unavailable for a year? | S·s | poor-charlies-almanack ch-2 |
| STRAT-13 | comparing options by revenue alone | **Relative income** — dollars without time/mobility are a false wealth score | What is the per-founder-hour value, and which levers do we control? | S·s | four-hour-workweek ch-1 |
| STRAT-14 | big reversible decision frozen by dread | **Fear-setting** — named worst cases become repair plans; vague fear freezes (↔ epi [[NDM-02]](epistemics.md?plain=1#L80) pre-mortem names the failure modes before commit; ↔ eng [[RLSE-08]](engineering.md?plain=1#L387) write the recovery before ship) | Worst case, repair path, and the 10-year cost of inaction? | S·s | four-hour-workweek ch-3 |
| STRAT-15 | leaders/deciders carry no downside | **Ownership society** — stake in success and failure for whoever decides | What do decision-makers lose if this fails? | B·s | technological-republic ch-18 |

## 2. Product & Validation

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| PROD-01 | feature request without an outcome metric | **Outcome over output** — ship only what changes valuable behavior (↔ [[OPS-01]](business-marketing.md?plain=1#L119) you get the incentive you pay for, not the outcome you meant; ↔ eng [[TEST-11]](engineering.md?plain=1#L216) stability over gameable coverage; ↔ ux [[UXR-03]](interaction-ux.md?plain=1#L188) a metric that cannot decide the goal is the wrong number; ↔ writ [[WRIT-28]](writing.md?plain=1#L82) prestige proxies are not named effects) | What human behavior must change, by how much? | B·p | lean-ux ch-3 |
| PROD-02 | long PRD / solution brief arrives first | **Problem before solution** — restate as a business problem with measurable adverse effect | What adverse effect and behavior define success? | B·s | lean-ux ch-5 |
| PROD-03 | expensive feature debate | **Cheapest learning first** — landing page / fake door / Wizard-of-Oz before build | What's the least work to learn the riskiest unknown? | S·p | lean-ux ch-12 |
| PROD-04 | experiment fails but the team loves the design | **Falsification wins** — kill or pivot; taste isn't evidence (↔ [[STRAT-02]](business-marketing.md?plain=1#L32) define the disconfirmers before the plan; ↔ eng [[DBG-06]](engineering.md?plain=1#L231)/[[DBG-11]](engineering.md?plain=1#L236) a fix is real only when the cause's absence kills the failure; ↔ sec [[SECD-07]](security.md?plain=1#L198) threat-model the ways it dies before buying controls; ↔ epi [[FORE-03]](epistemics.md?plain=1#L61) score the forecast, do not reframe hits) | What result would make us wrong — and did we see it? | B·p | lean-ux ch-12 |
| PROD-05 | low evidence, high-fidelity plan | **Truth Curve** — investment proportional to market evidence (↔ ux [[UXR-01]](interaction-ux.md?plain=1#L186) the method must be able to support the claim's level; ↔ [[STRAT-02]](business-marketing.md?plain=1#L32) evidence before the commitment; ↔ ml [[PROV-02]](ml-systems.md?plain=1#L196) model card before release; ↔ ux [[INT-07]](interaction-ux.md?plain=1#L117) preview before the costly commit) | What evidence justifies this fidelity? | S·p | lean-ux ch-12 |
| PROD-06 | "we know our users" with no recent contact | **Persona three gates** — exist, need, switch value; recruit to prove | Can we recruit them, confirm the pain, and beat the incumbent? | B·p | lean-ux ch-7 |
| PROD-07 | roadmap is a feature timeline | **Outcome roadmap** — leadership sets metrics; the team chooses features | Why this work, and how will we know we did a good job? | B·s | lean-ux ch-17 |
| PROD-08 | product designed from taste or golden-age references | **Study the Top, not your era** — current mass winners share more with each other than with their genre roots | What are this month's winners doing that ours refuses to do? | S·p | klf-the-manual ch-3 |
| PROD-09 | feature ignores hard channel constraints (length, hook, review rules) | **Format-first construction** — write the channel contract before the components (↔ [[CLM-05]](business-marketing.md?plain=1#L162) three hostile readers of the claim; ↔ eng [[RLSE-09]](engineering.md?plain=1#L388) plain-English expert gate; ↔ sec [[SECD-01]](security.md?plain=1#L192) write the policy before the mechanism; ↔ eng [[AGT-08]](engineering.md?plain=1#L41) a guard rejection is the named contract to satisfy) | What will the gatekeeper fade, skip, or demote? | B·p | klf-the-manual ch-4 |
| PROD-10 | team blocked seeking the never-seen | **Magpie assembly** — recombine proven parts; personality rides the collage | Which past winners can we legally recombine this week? | S·p | klf-the-manual ch-5 |
| PROD-11 | efficiency investment in a commodity-like offer | **Second-step test** — do the savings stick to us or flow to customers? | After competitors copy this tool, who keeps the margin? | S·p | poor-charlies-almanack ch-7 |
| PROD-12 | builders never meet the operational user on the real workflow | **Builder–user proximity** — continuous first-hand contact with the person who runs the product on their worst day; a requirements doc is not a substitute for getting out of the building (↔ a11y [[A11Y-23]](accessibility.md?plain=1#L83): the worst-day user includes the AT user) | Would a field user trust this UI on their worst day? | S·p | lean-ux ch-7 |
| PROD-13 | "we build because we can" | **What/why before can** — purpose precedes capability demos | Who is harmed if we never ship this — and served if we do? | S·p | technological-republic ch-6 |
| PROD-14 | UI quality never revisited after v1 | **UX debt is debt** — track and pay down like tech debt | Where does the current journey diverge from the ideal? | J·p | lean-ux ch-17 |

## 3. AI-Product Craft

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| AIPX-01 | "we need a model for this" before rules tried | **Heuristic before ML** — ship the deterministic baseline first (↔ ml [[EVAL-01]](ml-systems.md?plain=1#L117) without the heuristic baseline the model metric is uninterpretable; ↔ [[STRAT-02]](business-marketing.md?plain=1#L32) evidence before the commitment) | Can a maintainable rule deliver the value? | B·p | building-ml-powered-applications ch-1 |
| AIPX-02 | offline metric up, user acceptance flat | **Product-metric sovereignty** — offline scores are proxies; the user behavior is the metric (↔ [[OPS-01]](business-marketing.md?plain=1#L119) you get the number you pay for; ↔ [[PROD-01]](business-marketing.md?plain=1#L51) ship the outcome, not the offline score) | Which user behavior proves this model helped? | B·p | building-ml-powered-applications ch-2 |
| AIPX-03 | no accept/edit instrumentation on model output | **Instrument the flywheel** — production use is the label source (↔ ml [[HITL-01]](ml-systems.md?plain=1#L212) each train run must consume a new human-label batch; ↔ eng [[DATA-14]](engineering.md?plain=1#L115) no dual writes of the truth; ↔ ux [[HAI-02]](interaction-ux.md?plain=1#L139) correction must reach the source; ↔ ml [[SERVE-04]](ml-systems.md?plain=1#L171) no post-hoc correction cascade; ↔ ux [[INT-09]](interaction-ux.md?plain=1#L119) edit is a reversible command on the real data; ↔ eng [[REF-09]](engineering.md?plain=1#L185) a derived field that skips the source drifts) | Where does the next training label come from? | B·p | building-ml-powered-applications ch-4 |
| AIPX-04 | only aggregate accuracy at ship review | **Slice before ship** — per-cohort and failure-mode checks (↔ ml [[FAIR-02]](ml-systems.md?plain=1#L183) intersectional slices expose the compound cell the aggregate cleared; ↔ [[OPS-01]](business-marketing.md?plain=1#L119) the headline number is not the outcome; ↔ [[PROD-01]](business-marketing.md?plain=1#L51) outcome over the cleared aggregate) | On which user/content slice would we be embarrassed? | B·p | building-ml-powered-applications ch-5 |
| AIPX-05 | model path with no fallback | **Heuristic fallback required** — fail closed to a safe deterministic path | What do we show when confidence is low or input is garbage? | B·o | building-ml-powered-applications ch-10 |
| AIPX-06 | new model to 100% of traffic | **Shadow then canary** — prove production parity before cutover | Have we compared on live traffic without burning users? | S·o | building-ml-powered-applications ch-11 |
| AIPX-07 | advice/description feature tuned for coverage | **Precision-first guidance** — wrong advice costs more than silence (↔ ml [[CAL-02]](ml-systems.md?plain=1#L146) abstention is safer than a forced wrong class; ↔ [[STRAT-03]](business-marketing.md?plain=1#L33) too-tough is a designed basket; ↔ eng [[RLSE-04]](engineering.md?plain=1#L383) empty/error/offline are designed states) | What happens to trust the first time we're wrong? | S·p | building-ml-powered-applications ch-7 |
| AIPX-08 | generative output presented as complete | **Output is not the answer** — design for interpretation, edit, and next action (↔ ux [[HAI-01]](interaction-ux.md?plain=1#L138) a machine claim without inspectable evidence is uncalibrated reliance) | Will the user treat this as verified truth? | B·p | designing-ai-interfaces ch-5 |
| AIPX-09 | objective claim drives real action | **Secondary verification for stakes** — high-stakes outputs need a human or external check layer (↔ sec [[SEC-05]](security.md?plain=1#L68) human approves before the side effect executes; ↔ eng [[DATA-18]](engineering.md?plain=1#L119) check-then-act under weak isolation is the irreversible side; ↔ a11y [[A11Y-25]](accessibility.md?plain=1#L85) retrofit costs more than the hedge at write time) | Can a wrong accept cause irreversible harm? | B·p | designing-ai-interfaces ch-5 |
| AIPX-10 | request for a model-confidence badge | **No confidence theater** — sources, hedges, and validation paths over self-reported % | Can the user validate without trusting a score? | S·p | designing-ai-interfaces ch-5 |
| AIPX-11 | AI fluent but possibly wrong | **User as error detector** — afford double-check, edit, and source paths when the system can't self-flag (↔ ux [[HAI-01]](interaction-ux.md?plain=1#L138) every machine claim links to inspectable evidence) | Is failure detectable by the system, or only by the user? | B·p | designing-ai-interfaces ch-4 |
| AIPX-13 | humanlike AI in a commercial surface | **Disclose AI early** — synthetic nature labeled as an understanding aid (↔ ux [[HAI-14]](interaction-ux.md?plain=1#L151) label AI content that could pass as human; ↔ grph [[GRPH-18]](graph-theory.md?plain=1#L97) a named similarity boundary the data never enforced; ↔ sec [[WEB-21]](security.md?plain=1#L111) ambient authority the eye never chose; ↔ eng [[NAME-03]](engineering.md?plain=1#L356) a name that promises a type the code does not hold) | Could a user reasonably think this is a human? | B·g | designing-ai-interfaces ch-5 |
| AIPX-14 | perfect accuracy assumed in UX copy | **Design for imperfect models** — confidence gates and human override in the flow (↔ ux [[HAI-04]](interaction-ux.md?plain=1#L141) user must be able to stop and steer; ↔ ml [[CAL-02]](ml-systems.md?plain=1#L146) below-threshold is a designed state; ↔ [[STRAT-03]](business-marketing.md?plain=1#L33) too-tough over fake fluency; ↔ eng [[RLSE-04]](engineering.md?plain=1#L383) undesigned empty/error is a bug) | What is the worst wrong output a user might see? | B·p | building-ml-powered-applications ch-2 |

## 4. Go-to-Market & Distribution

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| GTM-01 | "users said they'd buy" without money | **Ask them to buy** — only paid intent validates (↔ ux [[UXR-03]](interaction-ux.md?plain=1#L188) a metric that cannot decide the goal is the wrong number; stated intent cannot decide paid demand; ↔ [[STRAT-02]](business-marketing.md?plain=1#L32) evidence before the inventory commitment) | What costly action (purchase, preorder, deposit) proves demand? | B·g | four-hour-workweek ch-10 |
| GTM-02 | building capability/inventory pre-demand | **Micro-test the offer** — measure conversion at target price before committing | Can we measure conversion before we build? | B·g | four-hour-workweek ch-10 |
| GTM-03 | product idea without a reachable tribe | **Niche-first** — market membership before invention | Which group do we already understand that spends and is reachable affordably? | S·g | four-hour-workweek ch-9 |
| GTM-04 | plan waits on a major platform/partner for distribution | **Distribution-as-product via service stack** — rent the infrastructure under your own label (↔ eng [[REF-15]](engineering.md?plain=1#L191) every hard-coded dependency is a forfeited exit) | Can we rent the muscle without selling the company? | S·g | klf-the-manual ch-10 |
| GTM-05 | awareness funded before conversion infrastructure | **Plugger-path before vanity press** — reach the ranking/conversion nodes, then press | Who gets us heard *and* who writes the ranking signal? | S·g | klf-the-manual ch-11 |
| GTM-06 | heat is high but the ranked/instrumented number is flat | **Resource the ranking nodes** — spend where the number is actually typed, scanned, counted (↔ [[OPS-01]](business-marketing.md?plain=1#L119) pay for the node that records the outcome; ↔ [[PROD-01]](business-marketing.md?plain=1#L51) heat is not valuable behavior change) | Where is the number actually recorded? | B·g | klf-the-manual ch-12 |
| GTM-07 | mass-market name/title is witty or needs explanation | **Title = emotional first line** — one basic feeling; clever caps at cult | Can a stranger repeat the meaning after one exposure? | S·g | klf-the-manual ch-6 |
| GTM-08 | debut leads with craft excellence, no novelty package | **Novelty beats craft on first exposure** — strangers can't judge quality yet | What is newsworthy in one scroll? | S·g | klf-the-manual ch-7 |
| GTM-09 | drafting any outbound message | **Research × personalization × relevance** — all three or silence | What is uniquely true about *them* in the first line? | B·g | linkedin-messaging-guide ch-5 |
| GTM-10 | first outbound asks for a meeting | **Soft CTA / foot-in-door** — earn call rights; never cold-Calendly | Have they agreed a conversation exists? | B·g | linkedin-messaging-guide ch-7 |
| GTM-11 | no reply after a written touch | **Rotate the format** — audio/video/other channel after 5–7 days, not bump #2 | Which untried door remains? | S·g | linkedin-messaging-guide ch-6 |
| GTM-12 | pipeline counted as quota-matching opportunities | **Inverse close-rate pipeline** — 2–4× closes as live opps; always prospecting | Do we have the multiple? | B·o | linkedin-messaging-guide ch-27 |
| GTM-13 | packaging/stunts multiply after the product converts | **Brown-bag test** — if it works bare, stop funding lore | Would this still win without the stunt budget? | J·g | klf-the-manual ch-13 |

## 5. Negotiation & Sales Conversations

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| NEG-01 | unreasonable demand / hard no on terms | **Calibrated How** — force them to solve your constraint under the illusion of control | "How am I supposed to do that?" | S·g | never-split-the-difference ch-7 |
| NEG-02 | pre-meeting dread / bad-news call | **Accusation audit** — name the worst charges first | What's the nastiest true thing they could say about us? | S·g | never-split-the-difference ch-3 |
| NEG-03 | counterpart emotion spikes | **Label, then pause** — daylight on fear beats argument | "It seems like you're worried about ___?" | S·g | never-split-the-difference ch-3 |
| NEG-04 | early smooth yes | **Three-yes test** — counterfeit commitment detector; hunt "that's right", not "yes" | Can they affirm it three different ways, including a How? | B·g | never-split-the-difference ch-8 |
| NEG-05 | haggle phase opens | **Ackerman ladder** — 65/85/95/100 with an odd final + nonmonetary chip | Target, 65% open, and the last chip? | S·g | never-split-the-difference ch-9 |
| NEG-06 | only the champion is engaged | **Behind-the-table map** — deal-killers outrank deal-makers | How on board is everyone *not* on this call? | B·g | never-split-the-difference ch-8 |
| NEG-07 | radio silence | **"Have you given up on this?"** — loss framing + autonomy reopens | Sent the no-oriented reopen? | S·g | never-split-the-difference ch-4 |
| NEG-08 | "they're irrational" | **Black Swan hunt** — hidden constraints/info/interests make their move rational | What would have to be true for their move to be rational? | J·s | never-split-the-difference ch-10 |

## 6. Operations & Incentives

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| OPS-01 | KPI/comp/pricing plan can be gamed or pays for the wrong output | **Incentives first** — never think about anything else before incentives are right (↔ ml [[COST-01]](ml-systems.md?plain=1#L262) if the target is not an owned SLI, no one is paying for it; ↔ ml [[COST-04]](ml-systems.md?plain=1#L265) pay per accepted output, not busy hardware; ↔ epi [[FORE-03]](epistemics.md?plain=1#L61) unscored forecasts pay for narrative confidence; ↔ eng [[OBS-07]](engineering.md?plain=1#L264) page on user symptoms, not a CPU proxy; ↔ eng [[PERF-03]](engineering.md?plain=1#L164) green averages that omit the slow tail; ↔ sec [[SEC-12]](security.md?plain=1#L75) clean accuracy is not a backdoor probe) | What behavior does this pay for at 2 a.m. with no witnesses? | B·o | poor-charlies-almanack ch-10 |
| OPS-02 | calendar fills with mediocre initiatives to reduce anxiety | **Sit on your hands** — explicit no-swing criteria; swing only at fat pitches | What is the "no swing" criterion this week? | S·o | poor-charlies-almanack ch-4 |
| OPS-03 | vendor/agency advice coincides with their upsell | **Incentive-caused-bias discount** — especially fear advice that's good for the advisor | Who gets paid if we say yes? | S·o | poor-charlies-almanack ch-10 |
| OPS-04 | only good news reaches the operator | **Welcome bad news promptly** — kill messenger-shooting structurally | What bad news arrived last, and who brought it safely? | S·o | poor-charlies-almanack ch-10 |
| OPS-05 | hiring or automating a mess | **Eliminate before automate/delegate** — never scale waste | What can we delete before we build or pay? | B·o | four-hour-workweek ch-8 |
| OPS-06 | calendar full, outcomes flat | **80/20 elimination** — cut the sources of 80% of pain; clone the 20% of gain | Which 20% creates the profit, and which creates the misery? | B·o | four-hour-workweek ch-5 |
| OPS-07 | endless inputs while shipping stalls | **Low-information diet** — just-in-time inputs; attention is inventory | Will I use this immediately, or is it just-in-case? | S·o | four-hour-workweek ch-6 |
| OPS-08 | founder is the bottleneck after sales exist | **Management by absence** — written authority and rules beat heroics (↔ [[OPS-13]](business-marketing.md?plain=1#L131) who/what/when/where/why or rewrite; ↔ eng [[AGT-07]](engineering.md?plain=1#L40) externalize at discovery before compaction; ↔ des [[BRND-12]](design-aesthetics.md?plain=1#L118) systemize taste so the brand outlives the founder) | What written rule would let this run without me for 30 days? | S·o | four-hour-workweek ch-11 |
| OPS-09 | launch team is a committee with >2 equal votes | **Pair, not crew** — one rudder; factions kill timelines | Who can say no without a meeting? | S·o | klf-the-manual ch-2 |
| OPS-10 | founder deep in specialist execution while the channel goal drifts | **Hold the rudder** — specify and accept/reject; don't become crew | Does this decision still aim at the harbor metric? | S·o | klf-the-manual ch-8 |
| OPS-11 | postmortem stops at "operator error" | **Five Whys into incentives** — chase the structure that made the miss rational | What org/pricing incentive made this rational? | S·o | technological-republic ch-14 |
| OPS-12 | hiring/partnering on charisma | **Record over presence** — underweight the interview, overweight the track record | What would the dossier say with the charm muted? | S·o | poor-charlies-almanack ch-10 |
| OPS-13 | order/plan omits rationale | **Braun why-rule** — who/what/when/where/why or rewrite (↔ eng [[ARCH-07]](engineering.md?plain=1#L310) context, decision, and consequences must outlive the author) | Why would a smart skeptic comply? | S·o | poor-charlies-almanack ch-6 |

## 7. Bootstrap Brand Economics

> Source: Berg, *Porn Work* (scholarly labor study of the adult-content economy), distilled for its transferable zero-capital creator mechanics: how workers build income under stigma, platform hostility, and no funding. The rules generalize to any bootstrap product; the distillation stays in the private research corpus.

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| BOOT-01 | zero-capital brand building | **Own before polish** — the first assets are rights, name, and a direct contact path; polish comes after ownership (↔ eng [[REF-15]](engineering.md?plain=1#L191) every hard-coded dependency is a forfeited exit) | If the platform dies tomorrow, what residual remains? | B·s | porn-work ch-3 |
| BOOT-02 | work sold once with no rights retained | **Scene-as-ad** — treat each visible unit as promotional labor for owned recurring streams | What owned product does this unit sell? | S·g | porn-work ch-4 |
| BOOT-03 | partner/platform pushes costs onto the creator | **Turn forced cost into product** — recapture imposed costs as fan-facing offerings under your own name | Does this cost build their equity or ours? | S·o | porn-work ch-4 |
| BOOT-04 | pricing your own labor/service | **Eyes-closed rate floor** — below the feel-good price the asset burns out; resentment compounds | Would I resent this rate after the platform's cut? | B·o | porn-work ch-7 |
| BOOT-05 | intimacy/access/attention as the product | **Bounded authenticity** — real connection, metered and calendared; the boundary is what makes it sustainable | Where does the performance end on the calendar? | S·o | porn-work ch-8 |
| BOOT-06 | free samples/tiers offered | **Freemium kill switch** — free exists only with a stated conversion hypothesis | What paid action does this free unit force? | S·g | porn-work ch-10 |
| BOOT-07 | one platform carries the revenue | **Hostile-landlord assumption** — multi-home the masters and the rails before you need to (↔ [[GTM-04]](business-marketing.md?plain=1#L91) rent muscle under your own label; ↔ sec [[SEC-04]](security.md?plain=1#L67) least-privilege agency so a jailbreak reaches little) | Can a ToS change kill >50% of revenue in a week? | B·s | porn-work ch-9 |
| BOOT-08 | follower counts as KPIs | **Payers per 1k followers** — optimize paid conversion, not reach (↔ [[OPS-01]](business-marketing.md?plain=1#L119) the reach number is not the paid outcome; ↔ [[PROD-01]](business-marketing.md?plain=1#L51) payers are the behavior change) | How many payers per thousand? | S·g | porn-work ch-9 |
| BOOT-09 | collab/trade arrangements | **Symmetric residual trade** — refuse partners who keep the files and the larger paid audience | Who owns the files, and whose list grows? | S·g | porn-work ch-6 |
| BOOT-10 | always-on hustle as the plan | **Rest as COGS** — recovery is a cost of goods; price and schedule it | Is recovery costed into the rate card? | S·o | porn-work ch-10 |
| BOOT-11 | scope changes mid-delivery | **Renegotiate on change** — new deliverable, new deal; silence re-prices you at zero | Did terms change without a new price? | B·o | porn-work ch-11 |
| BOOT-12 | "just refuse bad clients" advice | **Stratified refusal power** — build the alternate stream before moralizing about walking away | Who in this market can actually walk? | J·s | porn-work ch-5 |

## 8. Claims & Regulatory Surface

> Added 2026-07-11. Source: Fields, *Product Deploy Agents* compliance lens (CC BY 4.0, Jason Fields, jasonpfields.com, @fasonista); provenance in `distilled/engineering/product-deploy-agents-fields.md` ch-7. The premise is that in any regulated or platform-gated space, the language describing a product receives the same scrutiny as the product: a claim, not a sensor, decides which regulatory regime applies.

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| CLM-01 | user-facing copy describes a capability in a regulated domain | **Claims are products** — the same capability framed two ways lives in opposite regulatory universes ("supports stress awareness" vs "treats anxiety disorder"; "educational content" vs "investment advice") | Which side of the line does a *literal* reading land on? | B·g | product-deploy-agents-fields ch-7 |
| CLM-02 | stronger claim proposed because it converts better | **The cost asymmetry is absolute** — the safe side costs a softer verb or a hedge; crossing costs orders of magnitude; no aggressive claim is worth the exposure (↔ [[AIPX-09]](business-marketing.md?plain=1#L78) high-stakes accept needs a check layer; ↔ eng [[RLSE-08]](engineering.md?plain=1#L387) write the rollback before ship; ↔ eng [[DATA-17]](engineering.md?plain=1#L118) weak isolation looks free and costs integrity later; ↔ sec [[SEC-04]](security.md?plain=1#L67) narrow scope now, not after the jailbreak) | What does the cautious phrasing actually lose? | B·g | product-deploy-agents-fields ch-7 |
| CLM-03 | privacy policy (or ToS) and implementation drift apart | **The policy is a contract** — every statement is a promise; audit claim-by-claim; usually the policy is the stale side; never ship them in contradiction (↔ a11y [[A11Y-22]](accessibility.md?plain=1#L82) one failing step falsifies the claim; ↔ [[AIPX-13]](business-marketing.md?plain=1#L81) synthetic labeled as human is a boundary the system does not hold; ↔ sec [[SEC-01]](security.md?plain=1#L64) trust that changes at every crossing; ↔ eng [[ARCH-13]](engineering.md?plain=1#L316) a property left to "everyone will be careful" is only perceived; ↔ ux [[HAI-14]](interaction-ux.md?plain=1#L151) disclose the synthetic hand; ↔ eng [[NAME-03]](engineering.md?plain=1#L356) names that lie about the type) | Which policy sentence does this diff falsify? | B·o | product-deploy-agents-fields ch-7 |
| CLM-04 | "encrypted", "compliant", "secure", "accessible" as bare adjectives | **Adjectives are not evidence** — the full claim is mechanism + location + failure behavior; anything less is assertion (↔ ux [[HAI-08]](interaction-ux.md?plain=1#L145) uncertainty at the decision granularity; ↔ a11y [[A11Y-22]](accessibility.md?plain=1#L82) for "accessible") | What completes this claim? | B·o | product-deploy-agents-fields ch-7 |
| CLM-05 | copy reviewed only by its author's intent | **Three hostile readers** — the regulator, the platform review team, and the plaintiff's attorney in three years; read literally, not charitably (the platform reviewer is [[BOOT-07]](business-marketing.md?plain=1#L145)'s hostile landlord wearing a badge; ↔ [[STRAT-02]](business-marketing.md?plain=1#L32) the claim must survive its disconfirmers before it ships; ↔ eng [[RLSE-09]](engineering.md?plain=1#L388) plain-English expert gate, not liability-shifting jargon) | Who profits from reading this against us, and what do they find? | S·g | product-deploy-agents-fields ch-7 |

## 9. Cross-source tensions worth keeping

- **Conviction vs falsification**: [[STRAT-07]](business-marketing.md?plain=1#L37) (Karp: don't let the crowd veto) ↔ [[PROD-04]](business-marketing.md?plain=1#L54) (Lean UX: evidence kills darlings). Resolution by object: *values and positioning* run on conviction; *features and funnels* run on falsification.
- **Novelty vs precision**: [[GTM-08]](business-marketing.md?plain=1#L95) (KLF: novelty wins first exposure) ↔ [[AIPX-07]](business-marketing.md?plain=1#L76) (Ameisen: precision-first for advice products). First exposure can be novel; the *output* can never be sloppy in a trust product.
- **Niche membership vs consequential problems**: [[GTM-03]](business-marketing.md?plain=1#L90) (Ferriss: sell to a tribe you belong to) ↔ [[STRAT-06]](business-marketing.md?plain=1#L36) (Karp: work on what matters). A rare wedge satisfies both; hunt for it.
- **Novelty vs the regulatory line**: [[GTM-08]](business-marketing.md?plain=1#L95) (KLF: novelty beats craft at first exposure) ↔ [[CLM-02]](business-marketing.md?plain=1#L159) (Fields: the cost asymmetry is absolute). The hook can be as loud as the campaign wants; the claim inside it stays on the safe side of the line. The novelty lives in the packaging, not in the claim.
- **Channel contract vs claims review**: [[PROD-09]](business-marketing.md?plain=1#L59) (KLF: write the gatekeeper's contract before the components) and [[CLM-05]](business-marketing.md?plain=1#L162) (three hostile readers) are the same move at different stakes: App Store guidelines, FDA wellness lines, and radio-edit rules are all channel contracts read by someone paid to find violations. KLF learned it from playlist committees; Fields from app review.
- **Boring releases vs loud launches**: [[GTM-08]](business-marketing.md?plain=1#L95)/[[GTM-13]](business-marketing.md?plain=1#L100) stunts ↔ eng [[RLSE-07]](engineering.md?plain=1#L386) (phased rollout, stop criteria). The marketing moment can be theatrical, but the rollout percentage is set by the monitoring plan, never by the stunt calendar.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[STRAT-02]`) in their own planning, review, and design docs. Product-specific opinions and execution-timing notes are kept in the consuming project, never here; this file stays reusable across projects.

<!-- BEGIN GENERATED SOURCES -->

## Sources

Every `Src` cell above names one of these. The citation is the work itself; the distillation behind it stays in the private research corpus.

| Src | Source | Rules here |
|---|---|---|
| `building-ml-powered-applications` | Emmanuel Ameisen, *Building Machine Learning Powered Applications: Going from Idea to Product* (O’Reilly, 2020) | 8 |
| `deceit-desire-and-novel` | deceit-desire-and-novel | 1 |
| `designing-ai-interfaces` | Louise Macfadyen, *Designing AI Interfaces: Design Principles for Creative and Autonomous AI* (O’Reilly, 2026) | 5 |
| `four-hour-workweek` | Timothy Ferriss, *The 4-Hour Workweek* (Crown, 2007; expanded/updated ed. 2009) | 9 |
| `klf-the-manual` | The KLF / The Timelords (Bill Drummond & Jimmy Cauty), *The Manual (How to Have a Number One the Easy Way)*, KLF Publications 1988 | 14 |
| `lean-ux` | Jeff Gothelf & Josh Seiden, *Lean UX: Designing Great Products with Agile Teams*, 3rd ed. (O’Reilly) | 9 |
| `linkedin-messaging-guide` | Daniel Disney, *The Ultimate LinkedIn Messaging Guide: How to Use Written, Audio, Video and InMail Messages to Start More Conversations and Increase Sales* (Wiley, 2023) | 4 |
| `never-split-the-difference` | Chris Voss with Tahl Raz, *Never Split the Difference: Negotiating As If Your Life Depended On It* (HarperBusiness, 2016) | 9 |
| `poor-charlies-almanack` | Charles T. Munger / Peter D. Kaufman (ed.), *Poor Charlie's Almanack: The Wit and Wisdom of Charles T. Munger* (expanded 3rd ed.) | 12 |
| `porn-work` | Heather Berg, *Porn Work: Sex, Labor, and Late Capitalism* (University of North Carolina Press, 2021) | 12 |
| `product-deploy-agents-fields` | Jason Fields, *Product Deploy Agents* (github.com/fasonista71/product-deploy-agents), v2.0, 2026 | 5 |
| `technological-republic` | Alexander C. Karp & Nicholas W. Zamiska, *The Technological Republic: Hard Power, Soft Belief, and the Future of the West* (Crown Currency, 2025) | 5 |

<!-- END GENERATED SOURCES -->
