# Design & Aesthetics Heuristics Lexicon

## About this document

Decision rules for aesthetic direction and design mechanics: identity,
typography, colour systems and meaning, layout composition, image direction, and
brand-cultural positioning. These are the decisions above the engineering
lexicon's UI implementation rules (its `UI-*` section). Referenced, not read end
to end: a brief, comp, or design review cites a rule by ID where the direction
decision happens, and this file holds the claim behind it.

Scope boundary: engineering `UI-*` owns implementation mechanics (token scales,
spacing-signals-grouping, shade generation, elevation, WCAG floors). This
document owns *why those values*, the direction the tokens encode. Border rules
cite `↔ eng UI-xx` instead of restating.

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[LAY-10]` |
| Trigger | observable in a mark, type choice, palette, layout, image, or brand artifact |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the direction is committed |
| T·P | tier and phase, below |
| Src | source slug, resolved in the Sources section at the end of this file; the distillation behind it stays in the private research corpus |

Tier: **B**locker, **S**hould, **J**udgment. Phase: **i**dentity, **t**ype,
**c**olour, **l**ayout, **im**age, **b**rand.

## 1. Identity & Marks

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| IDNT-01 | identity lives only in a corner logo | **Total identity** — design the full application surface so the brand survives crop and obscuring (↔ a11y [[A11Y-06]](accessibility.md?plain=1#L46) a signal only in one channel vanishes when that channel is gone) | If the logo corner is covered, is the piece still ours? | B·i | paula-scher-design ch-5 |
| IDNT-02 | logo fails recognition, readability, or joy | **Three logo fails** — unrelated, unreadable, or joyless → redo; no fourth category of acceptable failure | Can a stranger match mark to org and remember it? | B·i | paula-scher-design ch-4 |
| IDNT-03 | mark approved off one hero surface | **Multi-platform premise** — extend to extreme scale, motion, environment, and language before approval (↔ a11y [[A11Y-08]](accessibility.md?plain=1#L53) signed off at one viewport, fails at extremes) | Does it still read at favicon size and on a facade? | B·i | design-indaba-dialogues ch-7 |
| IDNT-04 | pitch promises to manufacture brand feelings | **Identity ≠ brand** — deliver recognisability systems; the audience owns the brand | Are we selling a system or a mood claim? | B·i | design-indaba-dialogues ch-7 |
| IDNT-05 | logo brief is "freshen it" with associations intact | **Meaningful change only** — no redraw without a strategic why (↔ eng [[REF-05]](engineering.md?plain=1#L181) change without a named problem is waste) | What breaks if we leave the mark alone? | B·i | design-indaba-dialogues ch-6 |
| IDNT-06 | institution/product reads elite or boring to its public | **Big-type public voice** — typography itself as the identity; the words shout who we are | Does type alone say who we are, unaided? | S·i | paula-scher-design ch-6 |
| IDNT-07 | multiple names/aliases circulate publicly | **Umbrella + tokens** — one public name; sub-entities as secondary marks under it | What should a stranger call us in one word? | B·b | paula-scher-design ch-6 |
| IDNT-08 | name has modular structure or metaphor | **Name-gift lockup** — build the wordmark from what the name gives free (count, letterform, meaning) | What free structure does the name give us? | S·b | paula-scher-design ch-8 |
| IDNT-09 | product is culture but the work is only craft polish | **Cultural interpreter** — place the object in a world (instrument, gallery, street, archive); the world does half the signaling | What cultural world does this belong to? | B·i | design-indaba-dialogues ch-2 |
| IDNT-10 | one typographic voice on the cover, another inside | **Form–content harmony** — one axial/typographic system end-to-end (↔ eng [[NAME-04]](engineering.md?plain=1#L357) consistent-and-mediocre beats good-and-inconsistent) | Does every part share one system? | S·i | asymmetric-typography ch-4 |
| IDNT-11 | product family forced into one cosmetic set look though the functions differ | **Function-discrete form** — unity is the best fulfilment of each role, not matching silhouettes; each object earns its form from use | Does each object earn its form from use, or only from the set? | J·i | bauhaus-droste p040 |
| IDNT-12 | every variant is a unique one-off tooling or bespoke build | **Modular parts kit** — a limited set of simple distinct parts combines into the product variants; variants share a part inventory | Can variants share a part inventory? | J·i | bauhaus-droste p035 |
| IDNT-13 | industrial product hides how it works behind cosmetic skin | **Reveal function** — make working parts legible and state industrial materials honestly, so a user can see how it works without a legend (↔ [[INT-01]](interaction-ux.md?plain=1#L111) an affordance shown is a function revealed; both refuse surfaces that disguise what a thing does) | Can a user see how it works without a legend? | J·i | bauhaus-droste p040 |
| IDNT-14 | mark brief starts from an illustration or mascot only | **Primitive geometric mark** — build the institutional mark from the elementary primitives the system language already uses, so the mark reuses the kit instead of inventing a one-off pictogram | Does the mark reuse the system kit, or invent a one-off pictogram? | J·i | bauhaus-droste p050 |
| IDNT-15 | prototype optimized for hand-craft ornament, not reproduction | **Machine-form economy** — a mass-production model maximizes simplicity and economy of time and material via elementary volumes; the form must hold when made by machine thousands of times | Would this form still hold if made by machine thousands of times? | J·i | bauhaus-droste p039 |
| IDNT-16 | catalogue sprawls into vanity variants, or the brand hero is a bespoke showpiece no SKU carries | **Standard-range discipline** — replace an excessive range with a small number of standardized models, and let the quiet repeatable product carry the identity rather than the exhibition piece (↔ [[BRND-12]](design-aesthetics.md?plain=1#L118) both make the repeatable system, not the one-off, the thing that outlives its author) | Which models are necessary, and what is our standard product rather than our showpiece? | J·i | bauhaus-droste p088 |

## 2. Typography

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| TYPE-01 | prose column exceeds ~75 characters per line | **Measure cap** — liquid max ~38em; 45–75 cpl | Can the eye rejoin the next line without hunting? | B·t | web-typography ch-5 |
| TYPE-02 | size, face, or measure changed in isolation | **Readability stool** — size, measure, leading rebalance together, always | Did all three legs move when one did? | B·t | web-typography ch-5 |
| TYPE-03 | body leading left at browser default | **Screen leading floor** — start ~1.4 unitless; tune until the colour of the text block is even | Is the block's grey even, not striped? | S·t | web-typography ch-5 |
| TYPE-04 | justified body text on the web | **Hyphenate or go ragged** — justification without hyphenation makes rivers | Are there rivers or ladders? | B·t | web-typography ch-6 |
| TYPE-05 | ad-hoc font sizes accumulate | **Modular scale discipline** — few steps from one harmonic ladder, smallest first (↔ eng [[UI-01]](engineering.md?plain=1#L365) stores the tokens; this rule picks the ladder) | Are sizes from one scale? | S·t | web-typography ch-8 |
| TYPE-06 | brand/display face used for long reading | **Text-face duty** — reading text gets a robust screen text face; the brand face is for display | Would you read 3,000 words in this face? | B·t | web-typography ch-14 |
| TYPE-07 | pairing faces by trend | **Skeleton pairing** — shared structural bones or a deliberate diagonal; never vibe-only | Do the faces share structure or only mood? | S·t | web-typography ch-14 |
| TYPE-08 | numerals in prose vs tables | **Numeral duty split** — old-style in running text, tabular-lining in tables | Do figures shout louder than words? | S·t | web-typography ch-10 |
| TYPE-09 | webfont blocks first paint | **FOUT-friendly body** — font-display fallback + metric-compatible fallbacks; readable before the font arrives (↔ ml [[COST-10]](ml-systems.md?plain=1#L271) when the primary path is slow, the fallback must already be usable) | Is text readable pre-webfont? | B·t | web-typography ch-15 |
| TYPE-10 | tracking used to force a width | **Intact word shape** — never letter-space lowercase to fill; fix the structure instead | Is tracking solving a layout problem? | S·t | asymmetric-typography ch-9 |
| TYPE-11 | brand promise is plurality/community | **Width-as-metaphor** — mixed widths/weights can encode "many voices" deliberately | Does the lettering read as one voice or a crowd? | J·t | paula-scher-design ch-2 |
| TYPE-12 | advertising or landing lettering sells by persuasion tone or slogan density | **Facts-first advertising type** — convince through clear presentation of facts and data, not propaganda; if the hype words are stripped, the type must still deliver the claim (↔ [[WRIT-28]](writing.md?plain=1#L82) both replace prestige noise with a named, checkable effect) | If we strip the hype words, does the type still deliver the claim? | J·t | bauhaus-droste p110 |

## 3. Colour & Image

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| COL-01 | palette picked from a generator before the brief | **Concept-first palette** — scheme structure and colour roles before any hex (↔ biz [[PROD-02]](business-marketing.md?plain=1#L52) problem before solution) | Can I state the concept without naming colours? | S·c | colour-theory-cianci ch-14 |
| COL-02 | brand colour only proofed on white | **Relational proof** — adjacency and grounds change colour; proof on photo, dark UI, and busy contexts | Does the hue hold on every real ground? | B·c | colour-theory-cianci ch-7 |
| COL-03 | multi-colour set at equal chroma | **Harmony roles** — dominant / support / accent / neutral; one anchor | Which one colour is the identity anchor? | S·c | colour-theory-cianci ch-5 |
| COL-04 | hierarchy vanishes in greyscale | **Value architecture first** — rank by value before hue exists | Does hierarchy survive desaturation? | S·c | colour-theory-cianci ch-2 |
| COL-05 | neutrals default to pure grey | **Temperature-biased neutrals** — warm or cool the greys toward the identity; pure grey is an unchosen choice | Is this grey deliberately temperatured? | J·c | colour-theory-cianci ch-4 |
| COL-06 | paired hues mix muddy | **Temperature-matched bias** — mix within warm/cool families | Do paired hues share bias? | S·c | colour-theory-cianci ch-6 |
| COL-07 | brand deck cites colour-psychology tests | **No pseudo colour-psychology** — culture and perception claims only, testable in market (↔ biz [[CLM-04]](business-marketing.md?plain=1#L161) adjectives are not evidence) | Is the claim testable? | S·b | colour-theory-cianci ch-10 |
| COL-08 | sacred/political colours as decoration | **Audience-bound symbolism** — audit hue meaning per target culture | To whom does this hue already speak? | S·b | colour-theory-cianci ch-8 |
| COL-09 | second colour or rules used densely | **Thrift of accent** — sparse accent multiplies force; dense accent is noise | Is every accent structural? | J·c | asymmetric-typography ch-11 |
| COL-10 | imagery pipeline untested across skin tones | **Inclusive grade test** — preserve detail and dignity across skin; doubly binding for an accessibility product (↔ ml [[MLDATA-06]](ml-systems.md?plain=1#L85) representative skin-tone labels for appearance tasks) | Whose skin was the pipeline built for? | B·im | colour-theory-cianci ch-15 |
| COL-11 | screen palette reused for print/merch | **Dual-medium spec** — plan the CMYK/gamut loss before it surprises | Where does this colour die in print? | S·c | colour-theory-cianci ch-12 |
| COL-12 | multi-color palette approved only as equal-area swatches (style tile, token strip, brand board) | **Area-proportion proof** — equal-area swatches are for comparison, not application; Wada's method page says equal-quantity use should normally be avoided and that colours at large area read much paler than chips, so re-proof the set at its real area roles (large field vs button vs hairline) (↔ [[COL-02]](design-aesthetics.md?plain=1#L74) both refuse swatch-isolation approval; that rule varies the ground, this one varies the quantity) | Did we approve this set only as equal chips, or at the areas it will actually occupy? | J·c | dictionary-of-color-combinations p024 |
| COL-13 | structure or furniture coloured to decorate rather than to clarify joints and planes | **Constructive colour** — use clear colour to emphasize constructive character, never as applied ornament; the colour should explain the structure (↔ [[COL-01]](design-aesthetics.md?plain=1#L73) both put the palette's job before its taste) | Does the colour explain the structure? | J·c | bauhaus-droste p042 |

## 4. Layout & Composition

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| LAY-01 | all blocks carry equal visual weight | **Contrast engine / big-little law** — hierarchy via size, weight, position, silhouette; one dominant (↔ ux [[PERC-06]](interaction-ux.md?plain=1#L79) without a dominant the eye searches linearly) | What must dominate, and what is subdued? | S·l | asymmetric-typography ch-5 |
| LAY-02 | asymmetric composition re-centred "for balance" | **Do not centre asymmetry** — unequal margins are the design; the field is part of the composition | Are left/right margins intentionally different? | B·l | asymmetric-typography ch-6 |
| LAY-03 | identical gaps between all content groups | **Unequal intervals** — spacing differentiates relatedness and creates tension (↔ eng [[UI-03]](engineering.md?plain=1#L367) enforces the floor; this rule designs the rhythm) | Do intervals encode relatedness? | S·l | asymmetric-typography ch-6 |
| LAY-04 | more than three competing units at a glance | **Three-group rule** — regroup into sense units absorbable without counting (↔ ux [[COG-01]](interaction-ux.md?plain=1#L86) more simultaneous units than working-memory span drops the goal) | Can the structure be grasped without counting? | S·l | asymmetric-typography ch-8 |
| LAY-05 | white space reads as leftover | **Active white space** — place mass relative to the field; emptiness is a working material | Does moving the block 10% break or improve tension? | S·l | asymmetric-typography ch-6 |
| LAY-06 | hierarchy depends on boxes and rules | **Hierarchy without ornament** — weight/size/position carry meaning; frames are a crutch (↔ ux [[VIZ-02]](interaction-ux.md?plain=1#L164) rank the critical channel before decoration) | If ornament vanished, would hierarchy remain? | S·l | asymmetric-typography ch-2 |
| LAY-07 | brief could take classical symmetry or modern asymmetry | **Two-system choice** — symmetry when content/tradition honestly demand dignity; asymmetry for differentiated information (↔ biz [[STRAT-11]](business-marketing.md?plain=1#L41) averaging two opposed systems produces worse than either) | Which system does the content require? | J·l | asymmetric-typography ch-4 |
| LAY-08 | first sketch is a style before the content exists | **Content-out** — start from the real material; a moodboard is not a structure | What is the content demanding? | S·l | design-indaba-dialogues ch-9 |
| LAY-09 | composition apes modernist looks | **Method, not motifs** — asymmetry serves reading order; "looking Bauhaus" is ornament by other means | Is this order serving reading? | S·l | asymmetric-typography ch-13 |
| LAY-10 | surface shipped on framework defaults — stock accent, linear easing, whitespace-only empty state | **Assembled vs designed** — users can't articulate unchosen details but stop trusting because of them; every default that survives must be a choice (generalizes [[COL-05]](design-aesthetics.md?plain=1#L77)'s unchosen grey to the whole surface; ↔ eng [[RLSE-04]](engineering.md?plain=1#L383) audits the states, this rule audits the ownership) | Which of these values did a human actually choose? | S·l | product-deploy-agents-fields ch-3 |
| LAY-11 | a large field or background pattern is loud, figurative, or high-contrast by default | **Quiet field enlarges** — barely noticeable texture makes the field recede and the space read larger; a loud field competes with the content sitting on it | Does the field recede, or compete with what sits on it? | J·l | bauhaus-droste p090 |

## 5. Brand & Cultural Positioning

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| BRND-01 | audience framed only as conversion targets | **Audience, not punters** — design artefacts worth keeping; collectors outlast funnels | Would a fan keep this into adult life? | S·b | design-indaba-dialogues ch-2 |
| BRND-02 | campaigns milk founding heritage for growth optics | **No family-silver melt** — founding belief is capital; seasonal extraction spends it (↔ biz [[STRAT-10]](business-marketing.md?plain=1#L40) keep the irreplaceable rights; hire the services) | Are we spending belief or building it? | B·b | design-indaba-dialogues ch-3 |
| BRND-03 | cannot state what the org feels like in one sentence | **Emotional core first** — distil before form; the sentence the client will defend (↔ biz [[PROD-02]](business-marketing.md?plain=1#L52) problem before solution) | One sentence we'd defend under attack? | S·b | design-indaba-dialogues ch-7 |
| BRND-04 | attribute list contains contradictory poles | **No blanding brief** — refuse exclusive+inclusive personality mashes; singular briefs make memorable design (↔ biz [[STRAT-11]](business-marketing.md?plain=1#L41) the middle of two poles is often worse than either) | Is the brief singular enough? | B·b | paula-scher-design ch-9 |
| BRND-05 | market has cloned our visual language | **Break your house style** — change the system before becoming your own cliché | Are competitors speaking in our voice? | S·b | paula-scher-design ch-11 |
| BRND-06 | design ships without an internal guardian | **Strong-client only** — strong work needs someone who walks it through the building | Who defends this when attacked? | B·b | paula-scher-design ch-10 |
| BRND-07 | taboo/stigma-adjacent category | **Need-first niche gate** — fulfill an existing need; write down who it is *not* for (↔ biz [[GTM-03]](business-marketing.md?plain=1#L90) niche membership before invention; ↔ biz [[STRAT-02]](business-marketing.md?plain=1#L32) name non-X before the forward plan) | Is the excluded audience named in customer-facing language? | S·b | playboy-brand-value ch-2 |
| BRND-08 | mark must work across licenses/surfaces/years | **Rabbit-head contract** — a simple, classed, consistent mark is a licensable asset; the mark's presence is a quality signature | Is this redraw still a stamp-sized contract? | B·b | playboy-brand-value ch-2 |
| BRND-09 | revenue conflicts with identity taste | **Refuse off-promise money** — dollars that require being someone else tax equity | Does this dollar require us to be someone else? | B·b | playboy-brand-value ch-3 |
| BRND-10 | extension/new surface proposed | **Parent-impact veto** — category fit AND parent-brand harm both assessed | Can a loyalist explain this as the same world in one sentence? | B·b | playboy-brand-value ch-5 |
| BRND-11 | challenger wins by degrading a dimension | **No Pubic Wars** — never break what loyalists feel secure about to match an attacker | Does this response destroy our stability promise? | B·b | playboy-brand-value ch-9 |
| BRND-12 | founder is the face of taste | **Guardian beyond biography** — systemize taste control (rules, review, tokens) for succession | If the champion vanishes, who vetoes? | S·b | playboy-brand-value ch-8 |
| BRND-13 | brand equity questioned via weak P&L | **Equity proxies** — recognition, loyalty, licensing margin, rebound speed; not only revenue (↔ biz [[AIPX-02]](business-marketing.md?plain=1#L71) the convenient proxy moved, not the outcome) | Are we measuring the asset or the quarter? | J·b | playboy-brand-value ch-11 |
| BRND-14 | designer awaits client's cultural direction | **Half-responsibility translation** — build the business case for rightness in the client's language (↔ eng [[RLSE-09]](engineering.md?plain=1#L388) plain-English gate the decision-maker can use) | Can a non-designer repeat why this is right? | S·b | design-indaba-dialogues ch-5 |

## 6. Cross-source tensions

- **Tschichold's system vs Scher's voice**: [[LAY-09]](design-aesthetics.md?plain=1#L99) (method, not motifs) ↔ [[IDNT-06]](design-aesthetics.md?plain=1#L40) (big-type as brand). Resolution by surface: the *workbench* obeys Tschichold (information order first); the *marketing surface* may shout with Scher, but both from one type system [[IDNT-10]](design-aesthetics.md?plain=1#L44).
- **Break your style vs mark-as-contract**: [[BRND-05]](design-aesthetics.md?plain=1#L111) ↔ [[BRND-08]](design-aesthetics.md?plain=1#L114). The *mark* persists; the *campaign language* around it rotates. Playboy's rabbit survived every redesign around it.
- **Thrift of accent vs big-type exuberance**: [[COL-09]](design-aesthetics.md?plain=1#L81) ↔ [[IDNT-06]](design-aesthetics.md?plain=1#L40): exuberance in form, discipline in palette; Scher's Public Theater work is loud type in few colours, not many.
- **Value architecture is the accessibility engine**: [[COL-04]](design-aesthetics.md?plain=1#L76) (hierarchy survives desaturation) ↔ a11y [[A11Y-01]](accessibility.md?plain=1#L41) (contrast floors). A palette ranked by value before hue passes WCAG contrast by construction, so a contrast failure in review means the design step upstream was skipped. [[COL-10]](design-aesthetics.md?plain=1#L82)'s inclusive-grade test is the imaging-side twin.
- **The Ive test vs active white space**: product-deploy-agents-fields ch-3 (would this detail survive a five-second pause?) ↔ [[LAY-05]](design-aesthetics.md?plain=1#L95)/[[LAY-10]](design-aesthetics.md?plain=1#L100). Both describe the same signal: a surface built from unchosen defaults loses the user's trust before the user can say why.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[IDNT-02]`). Product-specific direction and naming decisions live in the consuming project, not here.

<!-- BEGIN GENERATED SOURCES -->

## Sources

Every `Src` cell above names one of these. The citation is the work itself; the distillation behind it stays in the private research corpus.

| Src | Source | Rules here |
|---|---|---|
| `asymmetric-typography` | Jan Tschichold, *Asymmetric Typography* (Faber & Faber / Cooper & Beatty, 1967 English ed.; integral translation of *Typographische Gestaltung*, Basle 1935; tr. Ruari McLean, author-approved) | 11 |
| `bauhaus-droste` | bauhaus-droste | 9 |
| `colour-theory-cianci` | Dr Lisa Cianci, *Colour Theory: Understanding and Working with Colour* (RMIT Open Press, 2023; CC BY-NC 4.0) | 10 |
| `design-indaba-dialogues` | *Design Indaba Dialogues* (Times Media Books / Design Indaba, 2014 e-book of interviews originally 2001–2011) | 9 |
| `dictionary-of-color-combinations` | dictionary-of-color-combinations | 1 |
| `paula-scher-design` | Paula Scher, *Make It Bigger* (Princeton Architectural Press, 2005 pbk) + BBC Maestro *An Introduction to Graphic Design* course notes | 9 |
| `playboy-brand-value` | Susan Gunelius, *Building Brand Value the Playboy Way* (Palgrave Macmillan, 2009) | 7 |
| `product-deploy-agents-fields` | Jason Fields, *Product Deploy Agents* (github.com/fasonista71/product-deploy-agents), v2.0, 2026 | 1 |
| `web-typography` | Richard Rutter, *Web Typography: A handbook for designing beautiful and effective responsive typography* (Ampersand Type, Brighton, 2017) | 9 |

<!-- END GENERATED SOURCES -->
