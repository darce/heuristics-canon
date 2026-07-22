# First principles

The lexicons hold rules. This document holds the mechanisms underneath them.

A claim earns a place in a lexicon when it is useful in its own domain. It earns a *tier* when a second source (from an economy the first author never saw) arrives at the same mechanism by a different road. Those independent arrivals are the corpus's most valuable output, because they are the connections retrieval will not make on its own: a person or a model answering a question defaults to the domain of the question, and the pop-charts rule never surfaces while you are debugging a race. So the convergences are written down and stated as principles, each with the arrivals that back it, the author who arrived there, and the rule IDs to cite.

Read this file to understand how the corpus thinks. Cite a principle when a single-domain rule fires and you want its cross-domain corroboration: a session that reaches for [[PROD-09]](lexicons/business-marketing.md#prod-09) should also get [[CLM-05]](lexicons/business-marketing.md#clm-05) and [[A11Y-22]](lexicons/accessibility.md#a11y-22), because they are one rule wearing three uniforms.

---

## 1. Author the contract before the components

Distribution almost never runs straight to the audience. It passes through a reader (a playlist committee, a store reviewer, a compliance officer) who checks the artifact against a written spec and fades, demotes, or rejects whatever fails it. The spec exists before your work does, so the work is built to it first.

- The KLF, in *The Manual*, learned that a record ignoring radio-edit and playlist rules never charts, however good it is, so the channel contract gets written before the song [[PROD-09]](lexicons/business-marketing.md#prod-09).
- Jason Fields, in *Product Deploy Agents*, ships iOS apps past a review team paid to read every claim literally, and counts the store guidelines, the regulator, and a future plaintiff's attorney among three hostile readers [[CLM-05]](lexicons/business-marketing.md#clm-05).
- The W3C's WCAG makes "accessible" a falsifiable sentence a compliance officer tests page by page; one failing step falsifies the claim [[A11Y-22]](lexicons/accessibility.md#a11y-22).
- Fields again, on the expert sign-off: give the clinician or lawyer exact quoted strings and specific yes/no questions, a five-minute read, not jargon that shifts liability without informing [[RLSE-09]](lexicons/engineering.md#rlse-09).
- The same author's release gates make proximity a defect: CONDITIONAL is red, not yellow, because the shipping team is the worst judge of shipping [[RLSE-02]](lexicons/engineering.md#rlse-02); and his gate discipline reads a rejection as the named contract to satisfy, never a cosmetic obstacle to argue past [[AGT-08]](lexicons/engineering.md#agt-08).
- Ross Anderson makes the security form exact: write in one paragraph what must not happen and who may do what before choosing mechanisms, because a protection claim without a falsifiable policy is theatre [[SECD-01]](lexicons/security.md#secd-01).

Pop charts, app stores, government procurement, release gates, and security policies run on one mechanism: author the contract the gatekeeper reads, and let no claim ship that the gatekeeper can falsify. A session citing [[PROD-09]](lexicons/business-marketing.md#prod-09) should surface [[CLM-05]](lexicons/business-marketing.md#clm-05), [[A11Y-22]](lexicons/accessibility.md#a11y-22), [[RLSE-09]](lexicons/engineering.md#rlse-09), [[RLSE-02]](lexicons/engineering.md#rlse-02), [[AGT-08]](lexicons/engineering.md#agt-08), and [[SECD-01]](lexicons/security.md#secd-01) as corroboration from economies its prompt never mentioned.

## 2. Specify what would prove you wrong

A claim nobody has tried to break is a guess wearing a conclusion's clothes. The discipline is the same whether the claim is a strategy, a feature, a diagnosis, or a passing test: name the observation that would make you wrong, then go looking for it.

- Charlie Munger, in *Poor Charlie's Almanack*, inverts every thesis: define non-X and the disconfirmers before the forward plan, and ask where the bet dies [[STRAT-02]](lexicons/business-marketing.md#strat-02).
- Gothelf and Seiden's *Lean UX* names the result that would kill the darling and treats seeing it as the win; taste is not evidence [[PROD-04]](lexicons/business-marketing.md#prod-04).
- David Agans reproduces the failure before anyone proposes a fix [[DBG-01]](lexicons/engineering.md#dbg-01); Andreas Zeller establishes a cause only when its absence makes the failure vanish [[DBG-11]](lexicons/engineering.md#dbg-11); Agans again refuses to call a fix verified until the exact repro that failed now passes [[DBG-06]](lexicons/engineering.md#dbg-06).
- Dave Farley will not trust a test never observed failing, its message predicted in advance, because it may assert nothing at all [[TEST-06]](lexicons/engineering.md#test-06).
- Fields' pre-release audit enumerates action against adverse condition and timing: the disconfirming inputs the happy path is built to hide [[RLSE-06]](lexicons/engineering.md#rlse-06).
- Tetlock & Gardner's *Superforecasting* makes the same reflex numeric: a forecast with no resolution date or criterion cannot prove you wrong [[FORE-02]](lexicons/epistemics.md#fore-02); the probability's movers and killers are written before new data arrives [[FORE-09]](lexicons/epistemics.md#fore-09); and after the outcome, a proper score (Brier) is how you verify the original claim rather than reframe the hits [[FORE-03]](lexicons/epistemics.md#fore-03).
- Gary Klein's *Sources of Power* runs the same reflex on plans and diagnoses: a **pre-mortem** assumes the plan has already failed and writes the causes before commit [[NDM-02]](lexicons/epistemics.md#ndm-02); a **de-minimis** diagnosis that explains away each early-warning cue is the refusal to let disconfirmers kill the story [[NDM-05]](lexicons/epistemics.md#ndm-05).
- Zeller's diagnosis posture names it for engineering fixes: a proposed approach is a **falsifiable hypothesis**; define how you will evaluate before you run it [[DIAG-03]](lexicons/engineering.md#diag-03).
- Tim Ferriss's fear-setting converts vague dread into named worst cases and repair paths before a reversible decision freezes [[STRAT-14]](lexicons/business-marketing.md#strat-14).
- Anderson's threat model is the security twin: list the ways the policy dies (including insiders and supply chain) before buying controls, because malice forces the least-convenient failure [[SECD-07]](lexicons/security.md#secd-07).

The same reflex runs under all of them: replace "this looks right" with a stated way to find out it is not.

## 3. The safe side is cheap; the wrong side is not

When one option is reversible and the other is not, the reversible one is almost always underpriced at the moment you choose. The cautious version costs a softer verb or an hour now; crossing the line costs a rewrite, a recall, or a regulator later.

- Fields makes the cost asymmetry of a claim absolute: the safe phrasing loses a little conversion, the aggressive phrasing risks orders of magnitude, so no aggressive claim is worth the exposure [[CLM-02]](lexicons/business-marketing.md#clm-02).
- The accessibility lexicon runs the same trade late, also from Fields: native elements, labels, and contrast tokens cost roughly zero at write time and a rewrite after launch [[A11Y-25]](lexicons/accessibility.md#a11y-25).
- The same author's rollback plan is written before ship, because at 2am you execute a plan, you do not design one [[RLSE-08]](lexicons/engineering.md#rlse-08).
- Steve Wilson's least privilege and human-in-the-loop gate cost a scope narrowing now; a jailbroken agent holding broad scope costs everything it can reach [[SEC-04]](lexicons/security.md#sec-04), [[SEC-05]](lexicons/security.md#sec-05).
- Kleppmann makes the concurrency version exact: a weaker isolation level looks free at write time, but the write skew or lost update it admits commits with no error and surfaces as a data-integrity incident later, so choosing it is the underpriced-irreversible side. Record the engine's real anomaly behaviour and test each invariant against it before defaulting to weak isolation [[DATA-17]](lexicons/engineering.md#data-17), [[DATA-18]](lexicons/engineering.md#data-18).
- Ameisen and Yang make the product form of the same gate: when a model output can drive irreversible harm, a human or external check layer is the cheap side; unsupervised accept is the expensive one [[AIPX-09]](lexicons/business-marketing.md#aipx-09).

The accessibility and claims lexicons already cross-link on this, and it generalizes: pay the small certain cost of the reversible side, and treat "we can fix it after launch" as the expensive answer it usually is.

## 4. You get the number you pay for, not the outcome you want

Any proxy drifts from its target under pressure, and once the proxy becomes a target it gets gamed. The fix is to anchor on the outcome you actually want and to instrument the node where that outcome is really counted.

- Munger puts incentives before everything: a metric pays for the behavior it rewards at 2am with no witnesses, not the behavior you meant [[OPS-01]](lexicons/business-marketing.md#ops-01).
- Gothelf and Seiden ship what changes valuable behavior [[PROD-01]](lexicons/business-marketing.md#prod-01), and Emmanuel Ameisen reads an offline score that rises while user acceptance stays flat as the proxy moving, not the product [[AIPX-02]](lexicons/business-marketing.md#aipx-02).
- Farley finds coverage gameable; change-failure rate measures the thing you wanted coverage to stand in for [[TEST-11]](lexicons/engineering.md#test-11).
- The *Observability Engineering* authors page on degraded user experience, not on a CPU threshold that has benign explanations [[OBS-07]](lexicons/engineering.md#obs-07).
- The KLF spends where the number is actually typed and counted [[GTM-06]](lexicons/business-marketing.md#gtm-06), and Heather Berg optimizes payers per thousand rather than reach [[BOOT-08]](lexicons/business-marketing.md#boot-08).
- Albert & Tullis measure the decision variable, not the convenient one: an optimistic self-report on a safety-critical task, or a composite UX score that "wins" while task success collapses, is the proxy moving, not the product [[UXR-03]](lexicons/interaction-ux.md#uxr-03), [[UXR-15]](lexicons/interaction-ux.md#uxr-15). Munzner adds the level check: a downstream success (a fast algorithm, a polished chart) is never evidence for the upstream claim it did not test [[UXR-01]](lexicons/interaction-ux.md#uxr-01), the visualization twin of reading the offline score, not the outcome.
- Chen, Murphy, Parisa and Sculley make the serving budget the same discipline: if a quality, freshness, or cost target is not an SLI with an owner, no one is paying for it on purpose, and hardware busy-ness optimizes the wrong number [[COST-01]](lexicons/ml-systems.md#cost-01). Gregg's completion accounting says the same downstream: pay per output the product actually accepts, folding in the retries and timeouts hidden behind a green utilization gauge [[COST-04]](lexicons/ml-systems.md#cost-04).
- Tetlock: if accuracy is not the measured number, narrative confidence and status are; unscored forecasts manufacture the illusion of a stopped clock [[FORE-03]](lexicons/epistemics.md#fore-03); and when identity commitment punishes an update, the paid behavior is a frozen *p* [[FORE-12]](lexicons/epistemics.md#fore-12).
- Ben Larbi's tropes corpus and Wikipedia's editors catch the prose form of the same drift: "drew wide attention" and "widely praised" are prestige proxies that stand in for a named, measurable effect; the coverage number moved, not the outcome [[WRIT-28]](lexicons/writing.md#writ-28).
- Latency work has the same trap: a wait-then-send benchmark **coordinates omission** and undersamples the slow responses; the green average moved, not the tail the user feels [[PERF-03]](lexicons/engineering.md#perf-03).
- Meadows names the slow form from systems theory: a performance goal set as a trailing function of recent performance erodes under each bad season, the drift-to-low-performance loop, so the reference must be absolute or owned outside the loop that chases it [[OBS-11]](lexicons/engineering.md#obs-11).
- Munger again on the quote: a market price or hype spike used as proof of quality is Mr. Market's mood standing in for intrinsic value; the number moved, not the asset [[STRAT-12]](lexicons/business-marketing.md#strat-12).
- Ameisen's ship review makes the cohort form exact: aggregate accuracy that clears while a user or content slice fails is the headline proxy, not the product [[AIPX-04]](lexicons/business-marketing.md#aipx-04).
- Adversarial ML makes the same cut on model promotion: clean test accuracy is the number you paid for; a **backdoor** that flips class under a fixed trigger was never in that number [[SEC-12]](lexicons/security.md#sec-12).

The measured proxy and the real goal come apart exactly when the stakes rise, which is precisely when someone starts optimizing the proxy.

## 5. Rank the substance before you style it

Order the underlying thing first and the surface decisions fall out correctly, often passing their own checks for free. Reverse the order and you re-litigate every surface value and still fail the audit.

- Cianci ranks a palette by value before hue exists; hierarchy that survives greyscale is the real hierarchy [[COL-04]](lexicons/design-aesthetics.md#col-04).
- That same value-ranked palette clears the W3C's WCAG contrast floor by construction, so a contrast failure in review means the design step upstream was skipped, not that engineering missed a token [[A11Y-01]](lexicons/accessibility.md#a11y-01).
- Gothelf and Seiden restate the solution brief as a measurable problem before designing a solution to it [[PROD-02]](lexicons/business-marketing.md#prod-02).
- The Design Indaba designers start layout from the real content; a moodboard is not a structure [[LAY-08]](lexicons/design-aesthetics.md#lay-08).
- Ware and Munzner rank the encoding before the decoration: the effectiveness principle gives the most accurate channel (position, then length) to the most important attribute before any colour or 3D styling, so a chart that reads wrong was mis-*ranked* upstream, not mis-coloured [[VIZ-02]](lexicons/interaction-ux.md#viz-02).
- Fairbanks ranks architecture the same way: structure is justified by its quality-attribute risks (latency, security, modifiability), not by feature decomposition, because functionality runs on almost any architecture and the quality attributes are what a skeleton enables or forecloses [[ARCH-12]](lexicons/engineering.md#arch-12).

Decide the structure before the decoration, and the decoration has nothing left to argue about.

## 6. An unchosen default is a defect the user feels before they can name it

Every value that ships should be one a human chose on purpose. A default that survives review reads as neglect, and neglect is legible even when the specific default is not: the user stops trusting the surface without being able to say which pixel did it.

- Fields flags a surface assembled from framework defaults (stock accent, linear easing, an empty state that is only whitespace) as one that loses trust before the user can articulate why [[LAY-10]](lexicons/design-aesthetics.md#lay-10).
- Cianci calls pure grey an unchosen choice; temperature the neutrals toward the identity [[COL-05]](lexicons/design-aesthetics.md#col-05).
- Fields again: loading, empty, error, offline, and first-time each get designed, or the screen ships a state that merely renders [[RLSE-04]](lexicons/engineering.md#rlse-04).
- The W3C's ATAG makes it normative for the tools that make content: accessible-content support features must be active by default and at least as prominent as the spelling checker, because a support feature shipped off is a default nobody chose on the author's behalf [[A11Y-38]](lexicons/accessibility.md#a11y-38).
- Felienne Hermans matches the codebase's existing convention over your own taste, because consistent-and-mediocre outperforms good-and-inconsistent [[NAME-04]](lexicons/engineering.md#name-04).

Design and release engineering audit the same signal from two sides: the difference between a surface that was assembled and one that was chosen.

## 7. Write it where it outlives the person who knows it

Knowledge held only in a head, a session, or a founder dies at the next compaction or succession. The cheap insurance is to record it where the next reader will find it, before the person who knows it is gone.

- Felienne Hermans persists the plan, the path verdicts, and the model into notes at the moment of discovery, because externalized working memory survives the context loss that wipes the in-head version [[AGT-07]](lexicons/engineering.md#agt-07).
- Ford and Richards keep context, decision, and consequences in an architecture decision record, past the author who made them [[ARCH-07]](lexicons/engineering.md#arch-07).
- Michael Nygard puts a correlation ID on every log line, turning the post-mortem into a grep instead of an excavation [[OBS-03]](lexicons/engineering.md#obs-03).
- Susan Gunelius systemizes the founder's taste into rules and review so the brand outlives the founder [[BRND-12]](lexicons/design-aesthetics.md#brnd-12), and Tim Ferriss writes down the authority so the business runs without you for thirty days [[OPS-08]](lexicons/business-marketing.md#ops-08).
- Munger restates Braun: an order or plan that omits who/what/when/where/why must be rewritten, because a smart skeptic cannot comply without the rationale [[OPS-13]](lexicons/business-marketing.md#ops-13).

A session, an author, and a founder all leave; only what they wrote down stays.

## 8. Assume a hostile landlord and keep a second exit

Any single point of external control eventually turns against you, whether it is a platform, a dependency, or a model that has been talked out of its instructions. Design as if the counterparty is adversarial, and keep the switch to an alternative cheap enough to actually throw.

- Heather Berg warns that one ToS change can zero a creator's revenue overnight, so multi-home the masters and the rails before you need to [[BOOT-07]](lexicons/business-marketing.md#boot-07).
- The same source's first move is ownership before polish: rights, name, and a direct contact path are the residual if the platform dies; polish comes after that residual exists [[BOOT-01]](lexicons/business-marketing.md#boot-01).
- The KLF rents the distribution muscle under its own label instead of waiting on one platform's blessing [[GTM-04]](lexicons/business-marketing.md#gtm-04).
- Steve Wilson notes that trust changes at every boundary, so grant the minimum scope: a compromised component exercises everything it holds [[SEC-01]](lexicons/security.md#sec-01), [[SEC-04]](lexicons/security.md#sec-04).
- Dave Farley wraps the third party behind an adapter; every hard-coded library call is a forfeited exit [[REF-15]](lexicons/engineering.md#ref-15).

No external party (platform, dependency, or jailbroken model) should get a hold on you that you cannot survive losing.

## 9. A claim must walk back to what produced it

Every artifact is derived from inputs, and the derivation is the part that decays first. Attach the pointer at creation time, so an audit follows pointers instead of reconstructing them. Principle 7 records knowledge so it survives its author; this one records derivation so a reader can verify it: a note can outlive everyone and still be untraceable.

- Barrasa, Natarajan and Webber, in *Building Knowledge Graphs*, store provenance as a directed citation graph: every artifact points at the inputs that produced it, and an audit walks ancestors where a filename cannot [[GRPH-14]](lexicons/graph-theory.md#grph-14).
- Steve Wilson pins the exact revision of any model or dataset pulled from a hub, because unpinned weights are an unauditable dependency [[SEC-10]](lexicons/security.md#sec-10).
- Ossama Ben Larbi's tropes corpus and Wikipedia's editors make it a blocker in prose: name the source or cut the claim [[WRIT-26]](lexicons/writing.md#writ-26), and a citation that cannot be followed is worse than none [[WRIT-41]](lexicons/writing.md#writ-41).
- Two vendor summaries of Ontario's AODA contradict each other on which WCAG version binds, so the accessibility lexicon reads the regulation itself; a claim's authority is its primary ancestor, not a derived copy [[A11Y-27]](lexicons/accessibility.md#a11y-27).
- Tetlock's fermi-izing is the same audit for a number: a point probability with no decomposition has no walkable ancestors; break it into sub-estimates and stated assumptions, or the figure is untraceable [[FORE-06]](lexicons/epistemics.md#fore-06).
- Agans sends the debugger to the manual instead of the memory of it: look it up, don't guess. Applied to citations, every path and symbol is read before it is asserted, and a missing referent is a finding [[AGT-02]](lexicons/engineering.md#agt-02).
- Wilson's hallucinated-dependency gate is the package form: a model-invented package name is not a package until owner and history resolve; attackers register malware under names models invent [[SEC-09]](lexicons/security.md#sec-09).

A knowledge graph, a model registry, an editor, a regulator, a coding session, and a dependency manifest run the same audit: walk backward from the claim, and if the walk breaks, the claim breaks with it.

## 10. Perceived boundaries must match enforced boundaries

A grouping the surface implies but the system does not enforce is a lie the user believes. Gestalt grouping, DOM structure, IA categories, authorization scopes, cluster membership, and an automation's operating envelope all fail the same way: the eye or the mental model reads one boundary while the machine honours another.

- Johnson's Gestalt audit checks a laid-out group for the relations proximity and similarity *imply* against the ones the code actually wires [[PERC-03]](lexicons/interaction-ux.md#perc-03), and Tidwell's MECE categories fail when a label promises one home for a thing the system files in two [[NAV-05]](lexicons/interaction-ux.md#nav-05).
- The DIMACS chaining failure is the computational twin: a borderline similarity edge that *names* an entity asserts a boundary the data never enforced [[GRPH-18]](lexicons/graph-theory.md#grph-18), and Wilson's trust that changes at every crossing says an unenforced boundary (a prediction read by an undeclared consumer [[PROV-05]](lexicons/ml-systems.md#prov-05)) exists only in the mind [[SEC-01]](lexicons/security.md#sec-01).
- Shneiderman makes it lethal: naming full autonomy beyond the tested envelope, or hiding that AI is acting at all, is a perceived boundary the system does not hold, the failure behind the 737 MAX and misused Autopilot [[HAI-05]](lexicons/interaction-ux.md#hai-05).
- Fields makes the legal-document form exact: a privacy policy or ToS is a promise, and shipping it against a divergent implementation is the same lie; audit claim-by-claim and never let the two contradict [[CLM-03]](lexicons/business-marketing.md#clm-03).
- Yang and Ameisen's commercial surface: AI content that could pass as human must be labeled as synthetic, or the perceived human boundary is one the system does not hold [[AIPX-13]](lexicons/business-marketing.md#aipx-13), [[HAI-14]](lexicons/interaction-ux.md#hai-14).

- Skelton and Pais give it an organizational form: an architectural boundary the org does not actually communicate across is a boundary only on the diagram (the communication structure wins) so a software split must be a team split first [[TEAM-01]](lexicons/engineering.md#team-01); Fairbanks adds the structural form: a property left to "everyone will be careful" is perceived, not enforced, until the architecture itself guarantees it [[ARCH-13]](lexicons/engineering.md#arch-13).
- Hermans's linguistic antipatterns are the naming form of the same lie: an `is*` that is not Boolean, or a getter with side effects, promises a type and behaviour the code does not hold [[NAME-03]](lexicons/engineering.md#name-03).
- Web authorization and multi-tenant storage arrive at the same structural cut: a route check that does not authorize the object leaves IDOR open [[WEB-08]](lexicons/security.md#web-08); app `WHERE` clauses without RLS leave tenant isolation to every developer's vigilance [[PG-02]](lexicons/security.md#pg-02); and a framed UI that steals the victim's clicks delivers ambient authority to a target the eye never chose [[WEB-21]](lexicons/security.md#web-21).

Pixels, DOM nodes, nav labels, similarity edges, trust boundaries, autonomy claims, identifier names, policy sentences, synthetic authorship, object IDs, tenant rows, and click targets run one audit: draw the boundary the user perceives, then prove the system enforces exactly that one.

## 11. Unknown is a designed state

Forced certainty manufactures a false identity, a false merge, a misleading progress bar, and a silent failure. *Unknown*, *pending*, *disputed*, and *insufficient-evidence* must exist as first-class states in the data model and the UI, or the system fabricates an answer where it owed a question.

- Two unrelated recognition sources arrive at abstention as a decision: Huyen sets a below-threshold action, and NIST keeps an investigation mode where the machine does not decide (*unknown is a valid result*) [[CAL-02]](lexicons/ml-systems.md#cal-02); AdaFace makes the training-time analogue, de-emphasising the identity-void image rather than forcing it to a face [[EMB-04]](lexicons/ml-systems.md#emb-04).
- Monarch routes the item the model is least sure of to a human instead of guessing [[HITL-07]](lexicons/ml-systems.md#hitl-07); Shneiderman keeps an override for when the automation's intent is unmet [[HAI-04]](lexicons/interaction-ux.md#hai-04).
- Fields audits the empty, error, and offline states as designed screens rather than defaults [[RLSE-04]](lexicons/engineering.md#rlse-04), and Tidwell designs the first-run "now what?" and the dead-end so they are entry points, not voids [[NAV-08]](lexicons/interaction-ux.md#nav-08).
- Tetlock designs graded uncertainty the same way: refuse vague words that fake crispness; force a number the decision can use [[FORE-01]](lexicons/epistemics.md#fore-01); and when the decision is sensitive to finer odds, refuse a coarse dial that collapses doubt into three bins [[FORE-08]](lexicons/epistemics.md#fore-08).
- Ben Larbi and Wikipedia's editors refuse the same forced label on authorship: one stylistic tell or a detector score is not proof; treat it as scrutiny, not a binary AI/human call, because a single cue under weak evidence is an *unknown*, and only a dense cluster is a signal [[WRIT-43]](lexicons/writing.md#writ-43).
- Stream processing and HTTP design reach the same designed third state: a window that looks complete without a late-event policy fabricates certainty about stragglers [[FLOW-08]](lexicons/engineering.md#flow-08); an empty search match is a successful answer (`200`), not a missing resource (`404`) [[API-06]](lexicons/engineering.md#api-06).
- Ameisen's guidance product prefers silence to wrong advice: coverage that forces a confident answer is the failure, and precision-first guidance designs the abstention [[AIPX-07]](lexicons/business-marketing.md#aipx-07); imperfect-model UX adds confidence gates so low evidence is a state, not a polished guess [[AIPX-14]](lexicons/business-marketing.md#aipx-14).
- Munger's circle of competence puts the same third state on strategy: yes / no / **too-tough** baskets, so unknown edge is a designed refusal rather than fake fluency [[STRAT-03]](lexicons/business-marketing.md#strat-03).

Calibration, annotation, automation control, release engineering, information architecture, prose detection, stream windows, query results, product guidance, and competence boundaries each refuse the same shortcut: when the evidence runs out, ship the designed unknown, not a confident wrong answer.

## 12. Correction must reach the source

Changing a label without changing the cluster, the model input, the rule, or the state transition that produced it only hides the error until the next recomputation restores it. A correction is real only when it reaches the thing that was wrong.

- On the review surface, a human edit must update the underlying model or graph, preserve provenance, and be reversible, or the same machine claim returns after recompute [[HAI-02]](lexicons/interaction-ux.md#hai-02); Monarch closes the loop by retraining on the correction before the same error is served again [[HITL-01]](lexicons/ml-systems.md#hitl-01).
- Tidwell models the edit as a discrete reversible operation on the real data, not a cosmetic overwrite [[INT-09]](lexicons/interaction-ux.md#int-09), and Sculley refuses the post-hoc corrector stacked on a frozen model's output: the cascade that deadlocks improvement because the source of error never updates [[SERVE-04]](lexicons/ml-systems.md#serve-04).
- The provenance authority is why: a correction that does not reach the single source of truth is just a divergent copy [[GRPH-14]](lexicons/graph-theory.md#grph-14), [[DATA-14]](lexicons/engineering.md#data-14).
- Kleppmann's dataflow makes it operational: a wrong derived store is repaired by reprocessing the retained log into a fresh view and cutting over, not by hand-patching rows, and a new view is bootstrapped from a snapshot pinned to a log offset. The log is the source, the store is a recomputable copy, so a patch that skips the log is undone by the next rebuild [[FLOW-06]](lexicons/engineering.md#flow-06).
- The writing lexicon states the same discipline for edit passes: swapping the flagged phrase while leaving the inflation, vagueness, or template intact only launders the tell; the next draft restores the defect unless the underlying problem is fixed [[WRIT-44]](lexicons/writing.md#writ-44).
- Fowler/Beck and Kleppmann name the code and storage twins: a field that mirrors other state drifts until it lies [[REF-09]](lexicons/engineering.md#ref-09); a precomputed cube is an optimization with a freshness SLO, not a source you can drop the raw facts for [[STOR-07]](lexicons/engineering.md#stor-07).
- Ameisen's product flywheel is the training form: accept/edit instrumentation makes production use the label source, so the next training run can consume the correction rather than re-serve the same error [[AIPX-03]](lexicons/business-marketing.md#aipx-03), [[HITL-01]](lexicons/ml-systems.md#hitl-01).

A review UI, an annotation loop, an undo stack, a model pipeline, a provenance graph, a prose edit pass, a derived field, a materialized view, and a production-label flywheel agree: edit the source, or you have edited nothing.

## 13. Evidence precedes commitment

A model label, an architecture decision, a UX claim, a purchase, and an agent's "done" all become durable state the moment they are committed, and each needs inspectable evidence *before* that moment, not after the harm. This is Principle 2's disconfirmer and Principle 9's traceable ancestor placed on a clock: the evidence must exist and be legible *first*, before the number, the identity, or the order is real.

- Suitability is earned before deployment, not discovered in the field: a model card's disaggregated analysis [[PROV-02]](lexicons/ml-systems.md#prov-02), Gender Shades' intersectional table [[FAIR-02]](lexicons/ml-systems.md#fair-02), NIST's differential outcomes at the operating threshold [[FAIR-03]](lexicons/ml-systems.md#fair-03), and Huyen's baselines that make a metric mean anything [[EVAL-01]](lexicons/ml-systems.md#eval-01).
- On the human surface, Tidwell shows the outcome before the costly commit [[INT-07]](lexicons/interaction-ux.md#int-07) and Johnson computes the comparison for the deliberate mind before a high-stakes choice [[COG-04]](lexicons/interaction-ux.md#cog-04); Monarch accepts a training label against embedded gold, treating annotator agreement as a diagnostic rather than truth [[HITL-05]](lexicons/ml-systems.md#hitl-05).
- The same reflex runs in older economies: Munger's disconfirmers before the forward plan [[STRAT-02]](lexicons/business-marketing.md#strat-02) and Fields' hostile reader who must be able to check the claim before it ships [[CLM-05]](lexicons/business-marketing.md#clm-05).
- Tetlock's outside view is the cheap prior before narrative lock-in: start from the base rate for this *class* of things, then adjust with the inside view; evidence before the story commits the estimate [[FORE-05]](lexicons/epistemics.md#fore-05).
- Feathers makes the legacy-code form exact: pin actual current behaviour with a characterization test before the edit commits a new contract [[TEST-03]](lexicons/engineering.md#test-03).
- Fields applies it to the smallest commitment there is, the word "done": a completion claim carries the command and the decisive output line, or it is not a claim [[AGT-04]](lexicons/engineering.md#agt-04).
- Ferriss makes the commercial form exact: "users said they'd buy" is not demand; only a costly action (purchase, preorder, deposit) is evidence before the inventory or capability commitment [[GTM-01]](lexicons/business-marketing.md#gtm-01).
- Ameisen refuses the model commitment without a deterministic baseline first: the heuristic is the evidence that the ML path has anything to beat [[AIPX-01]](lexicons/business-marketing.md#aipx-01), [[EVAL-01]](lexicons/ml-systems.md#eval-01).
- Gothelf and Seiden's Truth Curve scales fidelity to market evidence: a high-fidelity plan without the evidence to support it is a commitment the validation level cannot yet justify [[PROD-05]](lexicons/business-marketing.md#prod-05).

Deploy, merge, buy, label, complete, refactor, staff a model, and scale fidelity are all commitments; each is cheap to gate with evidence beforehand and expensive to reverse once it is durable state.

## 14. Grant the least privilege; minimize what a compromise reaches

Every component, credential, and role is a blast radius: whoever takes it inherits exactly what it could reach. The durable defense is not a taller wall but a smaller grant: give each principal only what its named function needs, and keep the set whose compromise is fatal as small as possible.

- Ross Anderson makes this the spine of access control and names the target directly: shrink the **trusted computing base** (the set whose failure breaks the policy) and grant least privilege by default, because a fat TCB makes every bug fatal [[SECD-02]](lexicons/security.md#secd-02).
- The same rule arrives independently in three economies the classic-security author never wrote for: Steve Wilson bounds an LLM agent's tools and scopes so a jailbreak exercises little [[SEC-04]](lexicons/security.md#sec-04); the PostgreSQL rule runs the app as a non-superuser so an injection is not a cluster takeover [[PG-01]](lexicons/security.md#pg-01); and the ML-security rule splits train / promote / serve rights so no single identity can silently swap the production weights [[SEC-16]](lexicons/security.md#sec-16). (Checking *every access* is a different discipline, complete mediation [[SECD-03]](lexicons/security.md#secd-03), not least privilege.)
- Two further PostgreSQL grants make the blast-radius cut concrete: `GRANT … TO PUBLIC` hands every role unintended DML [[PG-06]](lexicons/security.md#pg-06), and a backup or replication role with write privileges beyond need expands the radius of a stolen ops credential [[PG-14]](lexicons/security.md#pg-14).
- It is the inward twin of Principle 8: that principle keeps a second exit so no *external* landlord's hold is fatal [[BOOT-07]](lexicons/business-marketing.md#boot-07); this one keeps every *internal* grant small so no single compromise is. Both size the damage one failure can do, before it happens.

Agents, databases, ML pipelines, and classic security engineering each reached it alone: assume the component *will* be compromised, and make sure that when it is, it holds almost nothing.

---

## 15. A measurement the measured party can shape is not a measurement

Every number in this corpus is produced by an apparatus, and the apparatus is usually built by the same people the number judges. Where the measured system can decide which cases enter the sample, or how large the divisor grows, the metric stops reporting the world and starts reporting the arrangement. The failure never looks like a failure: the number improves. What makes this a first principle rather than a statistics footnote is that the correction is identical in every economy: fix the sampling frame or the denominator *outside* the system under test, then re-read the number.

- Load testing found it first and named it: **coordinated omission** [[PERF-03]](lexicons/engineering.md#perf-03). A wait-then-send benchmark pauses when the system stalls, so the requests that would have been slow are never issued: the apparatus deletes exactly the observations it exists to capture, and the latency histogram comes back clean.
- Dataset construction arrives at the same mechanism from the opposite end. A quality-control filter that strips extreme pose, occlusion, and low resolution from a corpus whose claim covers those conditions [[MLDATA-09]](lexicons/ml-systems.md#mldata-09) deletes the regime under test; the benchmark goes green because the cases that would have moved it are gone. Its sibling [[MLDATA-08]](lexicons/ml-systems.md#mldata-08) is the passive form: a set harvested by a detector inherits that detector's blind spots as the benchmark's.
- Biometric evaluation supplies the denominator version. Where a false-positive rate is normalized by a count the system itself emits, loosening the upstream stage mints extra searches and the reported rate falls while every operator's workload rises [[EVAL-19]](lexicons/ml-systems.md#eval-19). Usability research had already required the denominator be predefined [[UXR-07]](lexicons/interaction-ux.md#uxr-07); the biometric case adds *by whom*.
- Business operations states the incentive plainly (you get the number you pay for [[OPS-01]](lexicons/business-marketing.md#ops-01)) and testing states the artifact: coverage is a number a team can raise without improving anything, so measure stability instead [[TEST-11]](lexicons/engineering.md#test-11). Both are this principle read as a management problem rather than an instrument problem.
- Meadows supplies the structural fix the others imply: the watcher must sit outside the optimizer's reach, because a loop that can edit its own success metric, sample frame, or threshold is measuring its arrangement, not the world [[OBS-09]](lexicons/engineering.md#obs-09).
- The tension worth keeping: the fix is not "never let the team build the instrument", which no organization can afford. It is that the *sampling frame and the divisor* must be fixed outside the system, while the measurement itself may stay in-house.

Performance engineering, dataset construction, biometric evaluation, usability research, testing, and operations each arrived alone, from instruments that share no vocabulary: ask what the system under test could do to make this number better without doing anything better.

## 16. Fail loudly, succeed quietly

An outcome channel earns trust in both directions at once: failure must be impossible to miss, and success must be impossible to confuse with noise. Systems break this symmetry two ways, and both corrupt the channel: chatter on the success path buries the one line that matters, and a swallowed failure converts an error into a silent lie. The discipline is one mechanism seen from both sides: keep the success path clean enough that any output means something, and make every failure surface where its consumer actually looks.

- Kernighan and Pike built the split into the operating system: stderr exists because error messages "did start disappearing into pipelines", and the composable program stays silent on success [[AGT-15]](lexicons/engineering.md#agt-15); its outcome is an exit status a caller can branch on without parsing prose [[AGT-21]](lexicons/engineering.md#agt-21).
- Raymond states the repair rule two decades later, and Fields arrives from shipping products: when you must fail, fail noisily and as soon as possible, because a crash is honest and a silent wrong answer is not [[AGT-10]](lexicons/engineering.md#agt-10), [[RLSE-05]](lexicons/engineering.md#rlse-05).
- The observability authors run the same audit on telemetry: silence is not success, and dead instrumentation must break loudly, because a quiet dashboard and a healthy system are indistinguishable until you enforce the difference [[OBS-08]](lexicons/engineering.md#obs-08).
- The converse guard keeps the loud side honest: an ERROR that does not require operator action trains operators to ignore ERROR, which is how the loud channel goes quiet in the reader instead of the emitter [[OBS-04]](lexicons/engineering.md#obs-04).

Unix stream design, product release engineering, and production observability arrived separately: a channel where success chatters or failure whispers is not reporting the system, and the fix is symmetrical silence discipline, not more logging.

---

## When two rules point the other way

Not every cross-source pair agrees. Some rules pull in opposite directions, and the lexicons keep those pairs on purpose. The corpus applies Voss's [[STRAT-11]](lexicons/business-marketing.md#strat-11) to itself: averaging two good opposed rules produces a rule worse than either parent. Resolution means finding the partition on which each rule is fully right, and the recorded tensions use three.

- A **surface** partition separates where each rule applies. The workbench obeys Tschichold's reading order [[LAY-09]](lexicons/design-aesthetics.md#lay-09) while the marketing surface may shout with Scher [[IDNT-06]](lexicons/design-aesthetics.md#idnt-06), both drawn from one Tschichold type system [[IDNT-10]](lexicons/design-aesthetics.md#idnt-10). The same cut holds for shipping: Fields keeps the release process boring [[RLSE-07]](lexicons/engineering.md#rlse-07) while the KLF keeps the launch stunt loud [[GTM-08]](lexicons/business-marketing.md#gtm-08).
- An **object** partition gives each rule its own asset. Gunelius's mark persists as a contract [[BRND-08]](lexicons/design-aesthetics.md#brnd-08) while Scher rotates the campaign language around it [[BRND-05]](lexicons/design-aesthetics.md#brnd-05); Karp runs values on conviction [[STRAT-07]](lexicons/business-marketing.md#strat-07) while Lean UX runs funnels on falsification [[PROD-04]](lexicons/business-marketing.md#prod-04).
- A **sequence** partition orders them in time. The KLF's first exposure can lead with novelty [[GTM-08]](lexicons/business-marketing.md#gtm-08) while Fields keeps the claim inside the package on the safe side of the regulatory line at every moment [[CLM-02]](lexicons/business-marketing.md#clm-02).
- A **surface** partition also settles the corpus's sharpest epistemics tension. Klein's recognition-primed decisions under time pressure [[NDM-03]](lexicons/epistemics.md#ndm-03) and Tetlock's scored, decomposed probabilities [[FORE-01]](lexicons/epistemics.md#fore-01), [[FORE-05]](lexicons/epistemics.md#fore-05), [[FORE-09]](lexicons/epistemics.md#fore-09) look like a war between gut and Brier. They are not. Intuitive expertise is trustworthy only when the environment is **high-validity** (regular, learnable cues) *and* the person had prolonged practice with **rapid, unambiguous feedback**, the Kahneman–Klein conditions, operationalized as the validity–feedback gate [[NDM-01]](lexicons/epistemics.md#ndm-01). Fireground, NICU, chess, and many C2 calls can pass that gate; novel product bets, geopolitics, and slow-feedback strategy often fail it. When the gate passes, forced multi-attribute analysis can make experts worse ([[NDM-11]](lexicons/epistemics.md#ndm-11), and the tension with [[COG-04]](lexicons/interaction-ux.md#cog-04) is the same cut: deliberate comparison when time and framing demand it; singular evaluation when time is short and the cue library is real). When the gate fails, recognition is confidence, not expertise: number the claim, take the outside view, and score it. Do not average the two into mush [[STRAT-11]](lexicons/business-marketing.md#strat-11).

A pair no partition can split is a genuine judgment call: it stays at tier J and gets decided in context, with the reasoning recorded in Ford and Richards' ADR [[ARCH-07]](lexicons/engineering.md#arch-07).

## When two rules watch the same failure

An amplification is the opposite of a tension: two sources watch one failure from different lanes, one naming the upstream cause and the other the downstream check. These stay wired rather than partitioned, so each source catches the step the other skipped.

- Cianci's value-first palette [[COL-04]](lexicons/design-aesthetics.md#col-04) makes the W3C's WCAG contrast floor [[A11Y-01]](lexicons/accessibility.md#a11y-01) pass by construction: the design habit and the legal check are the same event seen upstream and downstream.
- Fields' undesigned-state audit [[RLSE-04]](lexicons/engineering.md#rlse-04) and the W3C's per-state conformance [[A11Y-24]](lexicons/accessibility.md#a11y-24) read the same seven screen states from a UX threat model and an accessibility one.
- Fields' Ive five-second test (*Product Deploy Agents* ch-3) and Tschichold's active white space [[LAY-05]](lexicons/design-aesthetics.md#lay-05) both fire on a surface built from unchosen defaults, one asking whether a detail was chosen and the other whether the emptiness is working.
- Wilson's trust that changes at every crossing [[SEC-01]](lexicons/security.md#sec-01) and the DIMACS chaining failure [[GRPH-18]](lexicons/graph-theory.md#grph-18) refuse one shortcut from two lanes: a relation verified pairwise (trust at a boundary, similarity at an edge) does not compose across a chain no one re-checked.
- Bondy and Murty's articulation point [[GRPH-05]](lexicons/graph-theory.md#grph-05) is Heather Berg's hostile landlord [[BOOT-07]](lexicons/business-marketing.md#boot-07) met before the adversary shows up: the graph text supplies the detection (if this node dies, how many components remain?) and the labor study the response (multi-home until the platform stops being a bridge).
- Johnson's seven-principle Gestalt audit [[PERC-03]](lexicons/interaction-ux.md#perc-03) and the DIMACS partition-plus-verification [[GRPH-22]](lexicons/graph-theory.md#grph-22) run one check in two materials: a card that visually merges two interface concepts and a similarity chain that merges two identities are the same false grouping, caught by proposing the structure and then verifying it invents no relation; pixels upstream, entities downstream.

## How these earn their place

A convergence is the mechanism by which a rule is promoted. A claim enters a lexicon at the lowest tier with its observed outcome as provenance; it climbs when a second, unrelated source is found to have reached it independently. So this file is not a summary of the lexicons: it is the evidence for their tiers, and the index a reader uses to pull a rule's cross-domain siblings into a decision that only named one domain.
