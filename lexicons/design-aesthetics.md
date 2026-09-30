# Design & Aesthetics Heuristics Lexicon

## About this document

Decision rules for aesthetic direction and design mechanics: identity,
typography, colour systems and meaning, layout composition, image direction, and
brand-cultural positioning. These are the decisions above the engineering
lexicon's [`UI`](engineering.md#fam-ui) implementation rules (its `UI-*` section). Referenced, not read end
to end: a brief, comp, or design review cites a rule by ID where the direction
decision happens, and this file holds the claim behind it.

Scope boundary: engineering `UI-*` owns implementation mechanics (token scales,
spacing-signals-grouping, shade generation, elevation, WCAG floors). This
document owns *why those values*, the direction the tokens encode. Border rules
cite `↔ eng UI-xx` instead of restating.

Direction and mechanics sit on Tschichold's
[*Asymmetric Typography*](../SOURCES.md#src-asymmetric-typography), Cianci's
[*Colour Theory: Understanding and Working with Colour*](../SOURCES.md#src-colour-theory-cianci),
Scher's [*Make It Bigger*](../SOURCES.md#src-paula-scher-design), and Rutter's
[*Web Typography*](../SOURCES.md#src-web-typography), with Droste's
[*Bauhaus 1919-1933: Reform and Avant-Garde*](../SOURCES.md#src-bauhaus-droste) and
the [*Design Indaba Dialogues*](../SOURCES.md#src-design-indaba-dialogues) for
institutional and cultural identity.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. Identity & Marks](#fam-idnt)
- [2. Typography](#fam-type)
- [3. Colour & Image](#fam-col)
- [4. Layout & Composition](#fam-lay)
- [5. Brand & Cultural Positioning](#fam-brnd)
- [6. Cross-source tensions](#6-cross-source-tensions)
- [Consumption](#consumption)

<!-- END GENERATED CONTENTS -->

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[LAY-10]` |
| Trigger | observable in a mark, type choice, palette, layout, image, or brand artifact |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the direction is committed |
| T·P | tier and phase, below |
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md) |

Tier: **B**locker, **S**hould, **J**udgment. Phase: **i**dentity, **t**ype,
**c**olour, **l**ayout, **im**age, **b**rand.

## 1. Identity & Marks<a name="fam-idnt"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| IDNT-01<a name="idnt-01"></a> | identity lives only in a corner logo | **Total identity**: design the full application surface so the brand survives crop and obscuring (↔ a11y [[A11Y-06]](accessibility.md#a11y-06) a signal only in one channel vanishes when that channel is gone) | If the logo corner is covered, is the piece still ours? | B·i | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § manhattan-records](../SOURCES.md#src-paula-scher-design) |
| IDNT-02<a name="idnt-02"></a> | A logo has no association with its organization or is too complex to recognize | **Recognizable, associated logos**: redo a logo when it has no association with its organization or its form is too complex to recognize. | Can a viewer associate the mark with the organization and recognize its form? | B·i | [Paula Scher: Make It Bigger + Introduction to Graphic Design](../SOURCES.md#src-paula-scher-design) |
| IDNT-03<a name="idnt-03"></a> | mark approved off one hero surface | **Multi-platform premise**: extend to extreme scale, motion, environment, and language before approval (↔ a11y [[A11Y-08]](accessibility.md#a11y-08) signed off at one viewport, fails at extremes) | Does it still read at favicon size and on a facade? | B·i | [Design Indaba Dialogues (Saville · Scher · Pearce), § scher-arnett](../SOURCES.md#src-design-indaba-dialogues) |
| IDNT-04<a name="idnt-04"></a> | pitch promises to manufacture brand feelings | **Identity ≠ brand**: deliver recognisability systems; the audience owns the brand | Are we selling a system or a mood claim? | B·i | [Design Indaba Dialogues (Saville · Scher · Pearce), § scher-arnett](../SOURCES.md#src-design-indaba-dialogues) |
| IDNT-05<a name="idnt-05"></a> | logo brief is "freshen it" with associations intact | **Meaningful change only**: no redraw without a strategic why (↔ eng [[REF-05]](engineering.md#ref-05) change without a named problem is waste) | What breaks if we leave the mark alone? | B·i | [Design Indaba Dialogues (Saville · Scher · Pearce), § gelman-bierut](../SOURCES.md#src-design-indaba-dialogues) |
| IDNT-06<a name="idnt-06"></a> | A cultural institution reads as educational and boring to its public | **Big-type public voice**: typography itself as the identity; the words shout who we are | Does type alone say who we are, unaided? | S·i | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § the-public-theater](../SOURCES.md#src-paula-scher-design) |
| IDNT-07<a name="idnt-07"></a> | multiple names/aliases circulate publicly | **Umbrella + tokens**: one public name; sub-entities as secondary marks under it | What should a stranger call us in one word? | B·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § the-public-theater](../SOURCES.md#src-paula-scher-design) |
| IDNT-08<a name="idnt-08"></a> | name has modular structure or metaphor | **Name-gift lockup**: build the wordmark from what the name gives free (count, letterform, meaning) | What free structure does the name give us? | S·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § manhattan-records](../SOURCES.md#src-paula-scher-design) |
| IDNT-09<a name="idnt-09"></a> | product is culture but the work is only craft polish | **Cultural interpreter**: place the object in a world (instrument, gallery, street, archive); the world does half the signaling | What cultural world does this belong to? | B·i | [Design Indaba Dialogues (Saville · Scher · Pearce), § saville](../SOURCES.md#src-design-indaba-dialogues) |
| IDNT-10<a name="idnt-10"></a> | one typographic voice on the cover, another inside | **Form–content harmony**: one axial/typographic system end-to-end (↔ eng [[NAME-04]](engineering.md#name-04) consistent-and-mediocre beats good-and-inconsistent) | Does every part share one system? | S·i | [Asymmetric Typography (Jan Tschichold), § book-today](../SOURCES.md#src-asymmetric-typography) |
| IDNT-11<a name="idnt-11"></a> | product family forced into one cosmetic set look though the functions differ | **Function-discrete form**: unity is the best fulfilment of each role, not matching silhouettes; each object earns its form from use | Does each object earn its form from use, or only from the set? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p040](../SOURCES.md#src-bauhaus-droste) |
| IDNT-12<a name="idnt-12"></a> | every variant is a unique one-off tooling or bespoke build | **Modular parts kit**: a limited set of simple distinct parts combines into the product variants; variants share a part inventory | Can variants share a part inventory? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p035](../SOURCES.md#src-bauhaus-droste) |
| IDNT-13<a name="idnt-13"></a> | industrial product hides how it works behind cosmetic skin | **Reveal function**: make working parts legible and state industrial materials honestly, so a user can see how it works without a legend (↔ [[INT-01]](interaction-ux.md#int-01) an affordance shown is a function revealed; both refuse surfaces that disguise what a thing does) | Can a user see how it works without a legend? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p040](../SOURCES.md#src-bauhaus-droste) |
| IDNT-14<a name="idnt-14"></a> | mark brief starts from an illustration or mascot only | **Primitive geometric mark**: build the institutional mark from the elementary primitives the system language already uses, so the mark reuses the kit instead of inventing a one-off pictogram | Does the mark reuse the system kit, or invent a one-off pictogram? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p050](../SOURCES.md#src-bauhaus-droste) |
| IDNT-15<a name="idnt-15"></a> | prototype optimized for hand-craft ornament, not reproduction | **Machine-form economy**: a mass-production model maximizes simplicity and economy of time and material via elementary volumes; the form must hold when made by machine thousands of times | Would this form still hold if made by machine thousands of times? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p039](../SOURCES.md#src-bauhaus-droste) |
| IDNT-16<a name="idnt-16"></a> | A product catalogue contains an excessively wide range of models | **Standard-range discipline**: replace an excessively wide product range with a small number of standardized models. | Can the range be reduced to a small number of standardized models? | J·i | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p088](../SOURCES.md#src-bauhaus-droste) |

<!-- BEGIN GENERATED SECTION SOURCES fam-idnt -->

**Sources for this section**

- [asymmetric-typography](../SOURCES.md#src-asymmetric-typography)
- [bauhaus-droste](../SOURCES.md#src-bauhaus-droste)
- [design-indaba-dialogues](../SOURCES.md#src-design-indaba-dialogues)
- [paula-scher-design](../SOURCES.md#src-paula-scher-design)

<!-- END GENERATED SECTION SOURCES fam-idnt -->

## 2. Typography<a name="fam-type"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| TYPE-01<a name="type-01"></a> | prose column exceeds ~75 characters per line | **Measure cap**: liquid max ~38em; 45–75 cpl | Can the eye rejoin the next line without hunting? | B·t | [Web Typography (Richard Rutter), § designing-paragraphs-line-length](../SOURCES.md#src-web-typography) |
| TYPE-02<a name="type-02"></a> | size, face, or measure changed in isolation | **Readability stool**: size, measure, leading rebalance together, always | Did all three legs move when one did? | B·t | [Web Typography (Richard Rutter), § designing-paragraphs-line-length](../SOURCES.md#src-web-typography) |
| TYPE-03<a name="type-03"></a> | body leading left at browser default | **Screen leading floor**: start ~1.4 unitless; tune until the colour of the text block is even | Is the block's grey even, not striped? | S·t | [Web Typography (Richard Rutter), § designing-paragraphs-line-spacing](../SOURCES.md#src-web-typography) |
| TYPE-04<a name="type-04"></a> | justified body text on the web | **Hyphenate or go ragged**: justification without hyphenation makes rivers | Are there rivers or ladders? | B·t | [Web Typography (Richard Rutter), § alignment-justification-hyphenation](../SOURCES.md#src-web-typography) |
| TYPE-05<a name="type-05"></a> | ad-hoc font sizes accumulate | **Modular scale discipline**: few steps from one harmonic ladder, smallest first (↔ eng [[UI-01]](engineering.md#ui-01) stores the tokens; this rule picks the ladder) | Are sizes from one scale? | S·t | [Web Typography (Richard Rutter), § hierarchy-and-scale](../SOURCES.md#src-web-typography) |
| TYPE-06<a name="type-06"></a> | brand/display face used for long reading | **Text-face duty**: choose a body face that reduces reading friction and remains robust on screen; confine a brand face to display only when it is unfit for body reading. | Would you read 3,000 words in this face? | B·t | [Web Typography (Richard Rutter), § selecting-typefaces-body](../SOURCES.md#src-web-typography) |
| TYPE-07<a name="type-07"></a> | pairing faces by trend | **Skeleton pairing**: shared structural bones or a deliberate diagonal; never vibe-only | Do the faces share structure or only mood? | S·t | [Web Typography (Richard Rutter), § combining-typefaces](../SOURCES.md#src-web-typography) |
| TYPE-08<a name="type-08"></a> | Numerals appear in running text, headings, or columns of comparable numbers | **Numeral duty split**: prefer old-style numerals in running text, lining numerals in headings, and tabular lining numerals in columns of comparable numbers. | Are running-text figures old-style, heading figures lining, and comparable column values tabular lining? | S·t | [Web Typography (Richard Rutter), § numerals-and-tables](../SOURCES.md#src-web-typography) |
| TYPE-09<a name="type-09"></a> | webfont blocks first paint | **FOUT-friendly body**: font-display fallback + metric-compatible fallbacks; readable before the font arrives (↔ ml [[COST-10]](ml-systems.md#cost-10) when the primary path is slow, the fallback must already be usable) | Is text readable pre-webfont? | B·t | [Web Typography (Richard Rutter), § using-web-fonts](../SOURCES.md#src-web-typography) |
| TYPE-10<a name="type-10"></a> | tracking used to force a width | **Intact word shape**: never letter-space lowercase to fill; fix the structure instead | Is tracking solving a layout problem? | S·t | [Asymmetric Typography (Jan Tschichold), § the-word](../SOURCES.md#src-asymmetric-typography) |
| TYPE-11<a name="type-11"></a> | brand promise is plurality/community | **Width-as-metaphor**: mixed widths/weights can encode "many voices" deliberately | Does the lettering read as one voice or a crowd? | J·t | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § the-public-theater](../SOURCES.md#src-paula-scher-design) |
| TYPE-12<a name="type-12"></a> | An advertising brief relies on propaganda or persuasion instead of clearly presented facts | **Facts-first advertising**: present facts and economic or scientific data clearly to convince rather than using propaganda or persuasion. | Does the advertisement clearly present facts or economic and scientific data rather than rely on propaganda or persuasion? | J·t | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p110](../SOURCES.md#src-bauhaus-droste) |
| TYPE-13<a name="type-13"></a> | type locked to device-named breakpoints only | **Em-based type response**: breakpoints track root size and reading distance, not device names, so layout still reflows when the user enlarges default text (↔ [[TYPE-01]](design-aesthetics.md#type-01) both measure layout in type units so reader-chosen size still fits) | Does layout still work if user enlarges default text? | S·t | [Web Typography (Richard Rutter), § responsive-paragraphs](../SOURCES.md#src-web-typography) |

<!-- BEGIN GENERATED SECTION SOURCES fam-type -->

**Sources for this section**

- [asymmetric-typography](../SOURCES.md#src-asymmetric-typography)
- [bauhaus-droste](../SOURCES.md#src-bauhaus-droste)
- [paula-scher-design](../SOURCES.md#src-paula-scher-design)
- [web-typography](../SOURCES.md#src-web-typography)

<!-- END GENERATED SECTION SOURCES fam-type -->

## 3. Colour & Image<a name="fam-col"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| COL-01<a name="col-01"></a> | palette picked from a generator before the brief | **Concept-first palette**: scheme structure and colour roles before any hex (↔ biz [[PROD-02]](business-marketing.md#prod-02) problem before solution) | Can I state the concept without naming colours? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-02<a name="col-02"></a> | brand colour only proofed on white | **Relational proof**: adjacency and grounds change colour; proof on photo, dark UI, and busy contexts | Does the hue hold on every real ground? | B·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-03<a name="col-03"></a> | multi-colour set at equal chroma | **Harmony roles**: dominant / support / accent / neutral; one anchor | Which one colour is the identity anchor? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-04<a name="col-04"></a> | hierarchy vanishes in greyscale | **Value architecture first**: rank by value before hue exists | Does hierarchy survive desaturation? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-05<a name="col-05"></a> | neutrals default to pure grey | **Temperature-biased neutrals**: warm or cool the greys toward the identity; pure grey is an unchosen choice | Is this grey deliberately temperatured? | J·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-06<a name="col-06"></a> | paired hues mix muddy | **Temperature-matched bias**: mix within warm/cool families | Do paired hues share bias? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-07<a name="col-07"></a> | A brand deck presents a hue’s meaning, market appeal, or health effect as a universal colour-psychology fact | **No pseudo colour-psychology**: distinguish cultural symbolism, category convention, perceptual interaction, and medical physics; use category convention and perceptual interaction, plus audience-tested cultural meaning, in design rationale, and do not present Jung/MBTI colour types or chromotherapy as professional or product evidence (↔ biz [[CLM-04]](business-marketing.md#clm-04) adjectives are not evidence). | Is this a tested cultural meaning, a category convention, a perceptual interaction, or wavelength-specific medicine rather than a universal colour-personality or cure claim? | S·b | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-08<a name="col-08"></a> | sacred/political colours as decoration | **Audience-bound symbolism**: audit hue meaning per target culture | To whom does this hue already speak? | S·b | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-09<a name="col-09"></a> | second colour or rules used densely | **Thrift of accent**: sparse accent multiplies force; dense accent is noise | Is every accent structural? | J·c | [Asymmetric Typography (Jan Tschichold), § colours](../SOURCES.md#src-asymmetric-typography) |
| COL-10<a name="col-10"></a> | imagery pipeline untested across skin tones | **Inclusive grade test**: preserve detail and dignity across skin; doubly binding for an accessibility product (↔ ml [[MLDATA-06]](ml-systems.md#mldata-06) representative skin-tone labels for appearance tasks) | Whose skin was the pipeline built for? | B·im | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-11<a name="col-11"></a> | screen palette reused for print/merch | **Dual-medium spec**: plan the CMYK/gamut loss before it surprises | Where does this colour die in print? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |
| COL-12<a name="col-12"></a> | multi-color palette approved only as equal-area swatches (style tile, token strip, brand board) | **Area-proportion proof**: equal-area swatches are for comparison, not application; re-proof the set at its real area roles (large field vs button vs hairline), because the same hue reads paler and weaker at large area than on a chip (↔ [[COL-02]](design-aesthetics.md#col-02) both refuse swatch-isolation approval; that rule varies the ground, this one varies the quantity) | Did we approve this set only as equal chips, or at the areas it will actually occupy? | S·c | [Visual distillation draft: Wada Sanzo, *A Dictionary of Color Combinations* (配色事典), p024](../SOURCES.md#src-dictionary-of-color-combinations) + [Interaction of Color (Josef Albers), ch. 15](../SOURCES.md#src-interaction-of-color) |
| COL-13<a name="col-13"></a> | Furniture is being coloured without regard to whether its constructive character should be emphasized | **Constructive colour**: use clear colours on furniture to emphasize its constructive character. | Are clear colours used to emphasize the furniture’s constructive character? | J·c | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p042](../SOURCES.md#src-bauhaus-droste) |
| COL-14<a name="col-14"></a> | adjacent colours contrast strongly in hue but sit near-equal in light intensity along a sustained UI or brand edge | **Break equal-light hue edges**: avoid near-equal light intensity where contrasting hues create duplicated or triplicated contours and feel aggressive and uncomfortable; retain the effect only for an intentional screaming effect in advertising (↔ [[COL-04]](design-aesthetics.md#col-04) value at edges; ↔ [[COL-02]](design-aesthetics.md#col-02) relational change is ground-wide, this is the boundary artefact). | Is the equal-light vibration an intentional screaming effect in advertising? | J·c | [Interaction of Color (Josef Albers)](../SOURCES.md#src-interaction-of-color) |
| COL-15<a name="col-15"></a> | two adjacent neighboring colours that are not very contrasting in hue, but that must remain distinct, share equal light intensity (cards, chart segments, label-on-field, focus ring on chrome) | **Unequal light where separation must hold**: where adjacent neighboring colours that are not very contrasting in hue must stay distinct, keep their light intensity unequal; equal lightness or equivalent darkness can make their boundary practically invisible (complement of [[COL-14]](design-aesthetics.md#col-14): that row governs hue-contrast vibration/1+1=3; this row governs equal-light fusion where separation must hold; ↔ [[COL-04]](design-aesthetics.md#col-04) both make light intensity, not hue, the axis that separates or merges). | Where adjacent regions must stay distinct, are their hues not very contrasting and their light intensities unequal? | J·c | [Interaction of Color (Josef Albers)](../SOURCES.md#src-interaction-of-color) |
| COL-16<a name="col-16"></a> | one mid-tone token is expected to hold identity on two reciprocal grounds (light/dark mode, photo vs chrome, two brand fields) without reselection | **Mid-tone between reciprocal grounds**: choose the topological middle between the two grounds, or move the grounds; a mid that hugs one ground fails the other, because the same mid-tone token reads as two different colours when the ground reverses (↔ [[COL-02]](design-aesthetics.md#col-02) multi-ground proof; this row names the mid-tone selection test) | Does this mid hold identity on both grounds without reselection? | J·c | [Interaction of Color (Josef Albers)](../SOURCES.md#src-interaction-of-color) |
| COL-17<a name="col-17"></a> | overlapping or stacked colour regions meant to read as transparent layering (modals, washes, brand overlays) without a lawful mid mixture | **Lawful mid mixture for transparent layering**: place a middle mixture in the overlap with light between the parents; enlarge mixture area for a stronger transparent read; wrong mid breaks layer parse (↔ ux [[VIZ-12]](interaction-ux.md#viz-12) data-layer order; this row is brand/UI colour illusion) | Does the overlap use a mid whose light sits between the parents? | J·c | [Interaction of Color (Josef Albers)](../SOURCES.md#src-interaction-of-color) |
| COL-18<a name="col-18"></a> | physical or brand matching colours proofed under one illuminant only | **Metamerism ritual**: brand match is illuminant-qualified; multi-illuminant swatch test before lock (↔ [[COL-02]](design-aesthetics.md#col-02) both refuse single-condition match approval; that rule varies the ground, this one varies the light) | Did we check daylight and store light? | S·c | [Colour Theory: Understanding and Working with Colour (Lisa Cianci)](../SOURCES.md#src-colour-theory-cianci) |

<!-- BEGIN GENERATED SECTION SOURCES fam-col -->

**Sources for this section**

- [asymmetric-typography](../SOURCES.md#src-asymmetric-typography)
- [bauhaus-droste](../SOURCES.md#src-bauhaus-droste)
- [colour-theory-cianci](../SOURCES.md#src-colour-theory-cianci)
- [dictionary-of-color-combinations](../SOURCES.md#src-dictionary-of-color-combinations)
- [interaction-of-color](../SOURCES.md#src-interaction-of-color)

<!-- END GENERATED SECTION SOURCES fam-col -->

## 4. Layout & Composition<a name="fam-lay"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| LAY-01<a name="lay-01"></a> | all blocks carry equal visual weight | **Contrast engine / big-little law**: hierarchy via size, weight, position, silhouette; one dominant (↔ ux [[PERC-06]](interaction-ux.md#perc-06) without a dominant the eye searches linearly) | What must dominate, and what is subdued? | S·l | [Asymmetric Typography (Jan Tschichold), § use-of-space](../SOURCES.md#src-asymmetric-typography) |
| LAY-02<a name="lay-02"></a> | asymmetric composition re-centred "for balance" | **Do not centre asymmetry**: unequal margins are the design; the field is part of the composition | Are left/right margins intentionally different? | B·l | [Asymmetric Typography (Jan Tschichold), § use-of-space](../SOURCES.md#src-asymmetric-typography) |
| LAY-03<a name="lay-03"></a> | identical gaps between all content groups | **Unequal intervals**: spacing differentiates relatedness and creates tension (↔ eng [[UI-03]](engineering.md#ui-03) enforces the floor; this rule designs the rhythm) | Do intervals encode relatedness? | S·l | [Asymmetric Typography (Jan Tschichold), § use-of-space](../SOURCES.md#src-asymmetric-typography) |
| LAY-04<a name="lay-04"></a> | more than three competing units at a glance | **Three-group rule**: regroup into sense units absorbable without counting (↔ ux [[COG-01]](interaction-ux.md#cog-01) more simultaneous units than working-memory span drops the goal) | Can the structure be grasped without counting? | S·l | [Asymmetric Typography (Jan Tschichold), § leading-grouping](../SOURCES.md#src-asymmetric-typography) |
| LAY-05<a name="lay-05"></a> | white space reads as leftover | **Active white space**: place mass relative to the field; emptiness is a working material | Does moving the block 10% break or improve tension? | S·l | [Asymmetric Typography (Jan Tschichold), § use-of-space](../SOURCES.md#src-asymmetric-typography) |
| LAY-06<a name="lay-06"></a> | hierarchy depends on boxes and rules | **Hierarchy without ornament**: weight/size/position carry meaning; frames are a crutch (↔ ux [[VIZ-02]](interaction-ux.md#viz-02) rank the critical channel before decoration) | If ornament vanished, would hierarchy remain? | S·l | [Asymmetric Typography (Jan Tschichold), § decorative-typography](../SOURCES.md#src-asymmetric-typography) |
| LAY-07<a name="lay-07"></a> | brief could take classical symmetry or modern asymmetry | **Two-system choice**: symmetry when content/tradition honestly demand dignity; asymmetry for differentiated information (↔ biz [[STRAT-11]](business-marketing.md#strat-11) averaging two opposed systems produces worse than either) | Which system does the content require? | J·l | [Asymmetric Typography (Jan Tschichold), § translators-foreword](../SOURCES.md#src-asymmetric-typography) |
| LAY-08<a name="lay-08"></a> | first sketch is a style before the content exists | **Content-out**: start from the real material; a moodboard is not a structure | What is the content demanding? | S·l | [Design Indaba Dialogues (Saville · Scher · Pearce), § pearce-sankarayya](../SOURCES.md#src-design-indaba-dialogues) |
| LAY-09<a name="lay-09"></a> | A layout copies abstract-art motifs literally without grounding them in its materials or purpose | **Method, not motifs**: study the available materials and elements, use contrast to form a clearly related whole, and stay within technique and purpose rather than copying abstract forms literally. | Do the materials and contrasting elements form a related whole that stays within technique and purpose? | S·l | [Asymmetric Typography (Jan Tschichold), § abstract-art](../SOURCES.md#src-asymmetric-typography) |
| LAY-10<a name="lay-10"></a> | surface shipped on framework defaults: whitespace-only empty state (reviewable); stock accent still on browser defaults (supercharge-defaults generator, not a review criterion) | **Assembled vs designed**: the same control on browser defaults reads as boring and in a chosen brand colour reads as polished, and an empty state is a priority rather than an afterthought; every default that survives to ship must be a choice someone made (generalizes [[COL-05]](design-aesthetics.md#col-05)'s unchosen grey to the whole surface; ↔ eng [[RLSE-04]](engineering.md#rlse-04) audits the states, this rule audits the ownership) | Which of these values did a human actually choose? | S·l | [Refactoring UI, § supercharge-the-defaults](../SOURCES.md#src-refactoring-ui) + [Refactoring UI, § dont-overlook-empty-states](../SOURCES.md#src-refactoring-ui) |
| LAY-11<a name="lay-11"></a> | A room uses colourful floral wallpaper and a larger impression is desired | **Quiet field enlarges**: use barely noticeable wallpaper designs to make a room appear bigger than with colourful floral patterns. | Does a barely noticeable wallpaper design make the room appear bigger than a colourful floral pattern? | J·l | [Visual distillation draft: Magdalena Droste, *Bauhaus 1919-1933* (Taschen), p090](../SOURCES.md#src-bauhaus-droste) |
| LAY-12<a name="lay-12"></a> | equal-importance lines right-aligned in LTR | **Reading-direction align**: left-align lines of equal importance (lists, contents, verse); the eye returns to the start, and right-aligning equal LTR lines compounds the disturbance | Does the eye know where each line begins? | B·l | [Asymmetric Typography (Jan Tschichold), § leading-grouping](../SOURCES.md#src-asymmetric-typography) |

<!-- BEGIN GENERATED SECTION SOURCES fam-lay -->

**Sources for this section**

- [asymmetric-typography](../SOURCES.md#src-asymmetric-typography)
- [bauhaus-droste](../SOURCES.md#src-bauhaus-droste)
- [design-indaba-dialogues](../SOURCES.md#src-design-indaba-dialogues)
- [refactoring-ui](../SOURCES.md#src-refactoring-ui)

<!-- END GENERATED SECTION SOURCES fam-lay -->

## 5. Brand & Cultural Positioning<a name="fam-brnd"></a>

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| BRND-01<a name="brnd-01"></a> | audience framed only as conversion targets | **Audience, not punters**: design artefacts worth keeping; collectors outlast funnels | Would a fan keep this into adult life? | S·b | [Design Indaba Dialogues (Saville · Scher · Pearce), § saville](../SOURCES.md#src-design-indaba-dialogues) |
| BRND-02<a name="brnd-02"></a> | campaigns milk founding heritage for growth optics | **No family-silver melt**: founding belief is capital; seasonal extraction spends it (↔ biz [[STRAT-10]](business-marketing.md#strat-10) keep the irreplaceable rights; hire the services) | Are we spending belief or building it? | B·b | [Design Indaba Dialogues (Saville · Scher · Pearce), § saville](../SOURCES.md#src-design-indaba-dialogues) |
| BRND-03<a name="brnd-03"></a> | brief/deck has no single defendable core sentence, or form is chosen before any core sentence exists | **Emotional core first**: distil before form; the sentence the client will defend (↔ biz [[PROD-02]](business-marketing.md#prod-02) problem before solution) | One sentence we'd defend under attack? | S·b | [Design Indaba Dialogues (Saville · Scher · Pearce), § scher-arnett](../SOURCES.md#src-design-indaba-dialogues) |
| BRND-04<a name="brnd-04"></a> | attribute list contains contradictory poles | **No blanding brief**: refuse exclusive+inclusive personality mashes; singular briefs make memorable design (↔ biz [[STRAT-11]](business-marketing.md#strat-11) the middle of two poles is often worse than either) | Is the brief singular enough? | B·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § company-of-men](../SOURCES.md#src-paula-scher-design) |
| BRND-05<a name="brnd-05"></a> | market has cloned our visual language | **Break your house style**: change the system before becoming your own cliché | Are competitors speaking in our voice? | S·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § style-wars](../SOURCES.md#src-paula-scher-design) |
| BRND-06<a name="brnd-06"></a> | design ships without an internal guardian | **Strong-client only**: strong work needs someone who walks it through the building | Who defends this when attacked? | B·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, § corporate-politics-101](../SOURCES.md#src-paula-scher-design) |
| BRND-07<a name="brnd-07"></a> | taboo/stigma-adjacent category | **Need-first niche gate**: fulfill an existing need; write down who it is *not* for (↔ biz [[GTM-03]](business-marketing.md#gtm-03) niche membership before invention; ↔ biz [[STRAT-02]](business-marketing.md#strat-02) name non-X before the forward plan) | Is the excluded audience named in customer-facing language? | S·b | [Building Brand Value the Playboy Way (Gunelius), ch. 2](../SOURCES.md#src-playboy-brand-value) |
| BRND-08<a name="brnd-08"></a> | mark must work across licenses/surfaces/years | **Rabbit-head contract**: a simple, classed, consistent mark is a licensable asset; the mark's presence is a quality signature | Is this redraw still a stamp-sized contract? | B·b | [Building Brand Value the Playboy Way (Gunelius), ch. 2](../SOURCES.md#src-playboy-brand-value) + [Building Brand Value the Playboy Way (Gunelius), ch. 10](../SOURCES.md#src-playboy-brand-value) |
| BRND-09<a name="brnd-09"></a> | An extension review finds that an offering cannot carry the parent promise without apology | **Parent-promise protection**: do not put the parent mark on an offering that cannot carry the parent promise without apology; place it under a sub-brand or drop it, because the parent identity should not absorb an off-promise offer. | Can this offering carry the parent promise without apology, and if not, will it move under a sub-brand or be dropped? | B·b | [Building Brand Value the Playboy Way (Gunelius), ch. 4](../SOURCES.md#src-playboy-brand-value) |
| BRND-10<a name="brnd-10"></a> | extension/new surface proposed | **Parent-impact veto**: category fit AND parent-brand harm both assessed | Can a loyalist explain this as the same world in one sentence? | B·b | [Building Brand Value the Playboy Way (Gunelius), § defies-marketing-rules](../SOURCES.md#src-playboy-brand-value) |
| BRND-11<a name="brnd-11"></a> | A challenger attacks on a dimension outside the brand’s owned differentiation, and the proposed response would break Stability | **No Pubic Wars**: when a challenger attacks on a dimension outside the brand’s owned differentiation, do not meet them there if the response would break Stability; choose an on-promise defense, a pre-emptive or counter-offensive move, or strategic withdrawal instead. | Does the attack target a dimension outside our owned differentiation, and would matching it break Stability? | B·b | [Building Brand Value the Playboy Way (Gunelius), § competitive-attacks](../SOURCES.md#src-playboy-brand-value) |
| BRND-12<a name="brnd-12"></a> | founder is the face of taste | **Guardian beyond biography**: systemize taste control (rules, review, tokens) for succession | If the champion vanishes, who vetoes? | S·b | [Building Brand Value the Playboy Way (Gunelius), ch. 18](../SOURCES.md#src-playboy-brand-value) |
| BRND-13<a name="brnd-13"></a> | brand equity questioned via weak P&L | **Equity proxies**: recognition, loyalty, licensing margin, rebound speed; not only revenue (↔ biz [[AIPX-02]](business-marketing.md#aipx-02) the convenient proxy moved, not the outcome) | Are we measuring the asset or the quarter? | J·b | [Building Brand Value the Playboy Way (Gunelius), ch. 11](../SOURCES.md#src-playboy-brand-value) |
| BRND-14<a name="brnd-14"></a> | A client gives blank stares or does not understand the cultural work or its business relevance | **Half-responsibility translation**: build the business case for rightness in the client's language (↔ eng [[RLSE-09]](engineering.md#rlse-09) plain-English gate the decision-maker can use) | Can a non-designer repeat why this is right? | S·b | [Design Indaba Dialogues (Saville · Scher · Pearce), § saville](../SOURCES.md#src-design-indaba-dialogues) |
| BRND-15<a name="brnd-15"></a> | review meeting past first recovery after readdress | **End at peak**: stop after the first readdress recovers appreciation; a second rebuttal starts the death spiral (↔ [[BRND-06]](design-aesthetics.md#brnd-06) both protect strong work from process failure; that rule needs a guardian, this one ends the meeting before the spiral) | Are we past the recovered appreciation peak? | S·b | [Paula Scher: Make It Bigger + Introduction to Graphic Design, ch. 9](../SOURCES.md#src-paula-scher-design) |

<!-- BEGIN GENERATED SECTION SOURCES fam-brnd -->

**Sources for this section**

- [design-indaba-dialogues](../SOURCES.md#src-design-indaba-dialogues)
- [paula-scher-design](../SOURCES.md#src-paula-scher-design)
- [playboy-brand-value](../SOURCES.md#src-playboy-brand-value)

<!-- END GENERATED SECTION SOURCES fam-brnd -->

## 6. Cross-source tensions

- **Tschichold's system vs Scher's voice**: [[LAY-09]](design-aesthetics.md#lay-09) (method, not motifs) ↔ [[IDNT-06]](design-aesthetics.md#idnt-06) (big-type as brand). Resolution by surface: the *workbench* obeys Tschichold (information order first); the *marketing surface* may shout with Scher, but both from one type system [[IDNT-10]](design-aesthetics.md#idnt-10).
- **Break your style vs mark-as-contract**: [[BRND-05]](design-aesthetics.md#brnd-05) ↔ [[BRND-08]](design-aesthetics.md#brnd-08). The *mark* persists; the *campaign language* around it rotates. Playboy's rabbit survived every redesign around it.
- **Thrift of accent vs big-type exuberance**: [[COL-09]](design-aesthetics.md#col-09) ↔ [[IDNT-06]](design-aesthetics.md#idnt-06): exuberance in form, discipline in palette; Scher's Public Theater work is loud type in few colours, not many.
- **Value architecture is the accessibility engine**: [[COL-04]](design-aesthetics.md#col-04) (hierarchy survives desaturation) ↔ a11y [[A11Y-01]](accessibility.md#a11y-01) (contrast floors). A palette ranked by value before hue passes WCAG contrast by construction, so a contrast failure in review means the design step upstream was skipped. [[COL-10]](design-aesthetics.md#col-10)'s inclusive-grade test is the imaging-side twin.
- **Active white space vs unchosen defaults**: [[LAY-05]](design-aesthetics.md#lay-05) ↔ [[LAY-10]](design-aesthetics.md#lay-10). Both describe the same signal from opposite sides: space that was placed reads as intent, space that was merely left over reads as absence, and a surface built from unchosen defaults loses the user's trust before the user can say why.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[IDNT-02]`). Product-specific direction and naming decisions live in the consuming project, not here.
