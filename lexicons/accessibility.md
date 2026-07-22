# Accessibility Heuristics Lexicon

## About this document

Decision rules for accessibility as a spanning concern: the conformance floor
(WCAG 2.2 AA), the field-prioritized working set of failures, and the claims
discipline around the word "accessible." Referenced, not read end to end: a
plan, diff, or claim surface cites a rule by ID where the decision happens, and
this file holds the claim behind it. Accessibility earns its own lexicon because
it cuts across the other three (implementation floors in engineering `UI-02`,
inclusive direction in design `COL-04` and `COL-10`, claims exposure in
business), and a spanning concern that no lexicon owns ships broken: the WebAIM
Million 2026 found detectable failures on 95.9% of home pages.

Ordering is empirical: §1 is the WebAIM Million working set, six mechanical
failure classes that constitute 96% of detected errors on the web. A product
that only ever enforces §1 in CI is already ahead of ~96% of home pages. §§2–4
complete the AA surface by POUR principle; §5 governs process and claims.

<!-- BEGIN GENERATED CONTENTS -->

**Contents**

- [1. The Working Set (96% of shipped failures)](#1-the-working-set-96-of-shipped-failures)
- [2. Perceivable (beyond the working set)](#2-perceivable-beyond-the-working-set)
- [3. Operable](#3-operable)
- [4. Understandable & Robust](#4-understandable--robust)
- [5. Process & Claims](#5-process--claims)
- [6. Cross-lexicon amplifications](#6-cross-lexicon-amplifications)
- [Consumption](#consumption)

<!-- END GENERATED CONTENTS -->

**Reading a row**

| Column | What it holds |
|---|---|
| ID | stable citation key, immutable once assigned; cite it as `[A11Y-01]` |
| Trigger | observable in a plan, diff, rendered page, or claim surface |
| Rule | the falsifiable claim: condition, action, consequence |
| Answers | the one question to ask before the decision is made |
| T·P | tier and phase, below |
| Src | source slug, resolved in [`SOURCES.md`](../SOURCES.md); the distillation behind it stays in the private research corpus |

Tier: **B**locker (excludes a user class or creates legal exposure if violated),
**S**hould (strong default, spec-stated exemptions exist), **J**udgment. Phase:
**p**lan, **w**rite, **r**eview, **g**tm (claims and contract surfaces).

WCAG success-criterion numbers are kept in rules as shared retrieval keys.
Cross-lexicon borders cite `↔ eng/design/biz` rules instead of restating them.
## 1. The Working Set (96% of shipped failures)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-01<a name="a11y-01"></a> | text or UI colors set or changed in a diff/mockup | **Contrast floors (1.4.3/1.4.11)**: text ≥4.5:1, large text and UI component states ≥3:1; logos/incidental exempt; fails on 83.9% of pages (↔ eng [[UI-02]](engineering.md#ui-02) owns the token mechanics; ↔ design [[COL-04]](design-aesthetics.md#col-04): a value-ranked palette passes free) | Does every pair pass its ratio on every real ground? | B·w | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) + [wcag22-accessibility ch-8](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-02<a name="a11y-02"></a> | image/icon/chart added without alt text or decorative marking | **Alt serves purpose (1.1.1)**: text equivalent for the content's *purpose*, or explicit `alt=""` when decorative; filename-alts pass scanners and fail users | What must a non-seeing user get from this? | B·w | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-03<a name="a11y-03"></a> | form input without a programmatically associated visible label | **Label every input (3.3.2/1.3.1)**: `<label for>` or equivalent; placeholder is not a label (vanishes on input, skipped by some AT) | Is the label announced with the field? | B·w | [wcag22-accessibility ch-4](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-04<a name="a11y-04"></a> | link or button with empty or generic accessible name | **Name every control (2.4.4/4.1.2/2.5.3)**: name states destination/action; visible label text contained in accessible name (voice users say what they see) | What does a voice-control user say to press this? | B·w | [wcag22-accessibility ch-3](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-05<a name="a11y-05"></a> | page template or HTML shell in a diff | **Declare the language (3.1.1)**: `lang` on the document; mark language changes inline (3.1.2) | Does AT know how to pronounce this page? | B·w | [wcag22-accessibility ch-4](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-06<a name="a11y-06"></a> | status, trend, series, or validity distinguished by hue alone | **Second channel always (1.4.1)**: pair color with icon/label/weight/pattern (↔ eng [[UI-02]](engineering.md#ui-02): same rule, this row adds the criterion number and scan trigger) | Does the signal survive greyscale? | B·r | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) |

## 2. Perceivable (beyond the working set)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-07<a name="a11y-07"></a> | visual structure (headings, groups, order) not mirrored in markup | **Programmatic structure (1.3.1/1.3.2/2.4.6)**: headings marked as headings, no skipped levels (41.8% of pages skip), DOM order = reading order | Would this outline make sense read linearly? | S·r | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) + [wcag22-accessibility ch-8](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-08<a name="a11y-08"></a> | layout reviewed only at desktop width / 100% zoom | **Reflow and resize (1.4.4/1.4.10/1.4.12)**: usable at 200% zoom and 320px width without 2-D scroll; survives user-forced text spacing; 2-D-essential content (maps, tables) exempt | What breaks at 320px and 200%? | S·r | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-09<a name="a11y-09"></a> | video/audio content added | **Captions and alternatives (1.2.x)**: captions for prerecorded (A) and live (AA) audio; audio description for prerecorded video (AA); transcript for audio-only | Can this media be consumed deaf, or blind? | S·p | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-10<a name="a11y-10"></a> | tooltip/popover appears on hover or focus | **Dismissible, hoverable, persistent (1.4.13)**: Esc dismisses, pointer can enter the popup, content stays until dismissed | Can the user read the tooltip without a steady hand? | S·w | [wcag22-accessibility ch-2](../SOURCES.md#src-wcag22-accessibility) |

## 3. Operable

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-11<a name="a11y-11"></a> | new interactive flow or widget in review | **Keyboard walk (2.1.1/2.1.2/2.4.3/2.4.7)**: every function reachable by keyboard, focus visible, order preserves meaning, no traps | Can the whole flow run from the keyboard alone? | B·r | [wcag22-accessibility ch-3](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-12<a name="a11y-12"></a> | custom widget built from `<div>`/`<span>` | **Native first, ARIA last (4.1.2)**: a native element carries name/role/keyboard free; wrong ARIA overrides correct semantics (pages using ARIA average *more* errors: 59 vs 42) | Why is this not a native element? | S·r | [wcag22-accessibility ch-5](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-13<a name="a11y-13"></a> | sticky header, toast, or cookie banner added to layout | **Focus not obscured (2.4.11)**: the focused element is never entirely hidden behind author content (↔ eng [[WEB-21]](security.md#web-21) an overlay that steals the interaction surface from what the user can see) | Where is keyboard focus when the banner is up? | S·r | [wcag22-accessibility ch-6](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-14<a name="a11y-14"></a> | tap/click targets in a dense UI | **Target size (2.5.8)**: ≥24×24 CSS px effective; platform HIGs are stricter (44pt iOS / 48dp Android): apply the stricter floor | Can a tremoring thumb hit this without collateral? | S·w | [wcag22-accessibility ch-3](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-15<a name="a11y-15"></a> | drag, swipe, multipoint, or path gesture added | **Single-pointer alternative (2.5.1/2.5.7)**: click/keyboard path for every gesture unless the gesture is essential | How does this work without a drag? | S·w | [wcag22-accessibility ch-6](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-16<a name="a11y-16"></a> | carousel, auto-updating region, or author-set time limit | **User's time, user's motion (2.2.1/2.2.2/2.3.1)**: pause/stop/hide for motion >5s, adjustable timeouts, nothing flashes >3×/s (↔ ux [[INT-10]](interaction-ux.md#int-10) continuous system change needs a user stop) | Who set this tempo: the user or us? | S·w | [wcag22-accessibility ch-3](../SOURCES.md#src-wcag22-accessibility) |

## 4. Understandable & Robust

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-17<a name="a11y-17"></a> | form validation or error handling in a diff | **Errors name the field and the fix (3.3.1/3.3.3)**: detected errors identified in text at the field, corrections suggested; a bare "invalid input" toast fails (↔ product-deploy-agents-fields ch-3: specific, non-alarming, actionable) | Which field, what's wrong, how to fix: all in text? | S·w | [wcag22-accessibility ch-4](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-18<a name="a11y-18"></a> | legal, financial, or data-destroying submission flow | **Reversible, checked, or confirmed (3.3.4)**: at least one of undo / validation-with-correction / confirmation step (↔ ux [[INT-07]](interaction-ux.md#int-07) preview before a costly commit; ↔ ux [[INT-09]](interaction-ux.md#int-09) reversible command stack) | Can one mis-tap destroy something permanent? | B·r | [wcag22-accessibility ch-4](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-19<a name="a11y-19"></a> | login/auth or multi-step form in a diff | **No cognitive gate (3.3.7/3.3.8)**: paste/autofill are the mechanisms that usually satisfy 3.3.8; blocking them with no alternative method fails; data entered once is never re-typed in the same process (↔ ux [[COG-02]](interaction-ux.md#cog-02) recognition and choosers beat pure recall) | Does a password manager complete this unaided? | S·r | [wcag22-accessibility ch-6](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-20<a name="a11y-20"></a> | focus or input triggers navigation/submission | **No surprise context change (3.2.1/3.2.2)**: focusing never changes context; input changes warn first | Did the user ask to go somewhere? | S·r | [wcag22-accessibility ch-4](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-21<a name="a11y-21"></a> | async result, toast, or counter updates without focus | **Announce status (4.1.3)**: live region/`role="status"` so AT hears what sighted users see (the accessible half of "every async op has visible progress") | Does a screen reader learn this happened? | S·w | [wcag22-accessibility ch-5](../SOURCES.md#src-wcag22-accessibility) |

## 5. Process & Claims

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-22<a name="a11y-22"></a> | "accessible" / "WCAG compliant" in copy, contract, or VPAT | **Scoped conformance claims**: version + level + page scope + date; conformance attaches to full pages and *every step* of a process; one failing step falsifies the sentence (↔ biz [[CLM-01]](business-marketing.md#clm-01): a conformance claim is a claim-as-product with EAA/ADA force) | Could one failing page falsify this sentence? | B·g | [wcag22-accessibility ch-7](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-23<a name="a11y-23"></a> | accessibility verified by automated scan only | **Scanner-pass is the floor of the floor**: automation detects a minority of criteria (<4.1% of pages actually conform); keyboard walk + AT pass on primary flows required (↔ biz [[PROD-12]](business-marketing.md#prod-12): the worst-day user includes the AT user) | What did a human verify that axe cannot? | S·r | [wcag22-accessibility ch-8](../SOURCES.md#src-wcag22-accessibility) |
| A11Y-24<a name="a11y-24"></a> | screen states enumerated in a design/release review | **Every state accessible (process de-conformance)**: one inaccessible step de-conforms the process; on PDA's state matrix, loading, empty, error, offline each keep focus management, announcements, and contrast, so an accessible happy path with an inaccessible error state fails the process (↔ eng [[RLSE-04]](engineering.md#rlse-04) both fail when a state ships that was rendered but never designed) | Where does focus go when this errors? | S·r | [wcag22-accessibility ch-1](../SOURCES.md#src-wcag22-accessibility) + [product-deploy-agents-fields ch-3](../SOURCES.md#src-product-deploy-agents-fields) |
| A11Y-25<a name="a11y-25"></a> | accessibility work postponed as post-launch polish | **Retrofit costs more than the hedge**: the safe side (native elements, labels, contrast tokens) costs ~zero at write time and a rewrite later; same cost asymmetry as regulatory claims (↔ biz [[CLM-02]](business-marketing.md#clm-02) both price the cheap precaution now against the expensive reversal later) | What does doing this now actually cost? | S·p | [product-deploy-agents-fields ch-7](../SOURCES.md#src-product-deploy-agents-fields) |
| A11Y-26<a name="a11y-26"></a> | org or customer base touches Ontario | **AODA nexus check**: 1+ Ontario employee attaches duties (training, documents, web); 20+ employees or public sector adds mandatory compliance reports; fines run per-day (to $100k/day) and reach officers personally | Do we have Ontario nexus, and who owns the filing? | S·p | [aoda-ontario ch-1](../SOURCES.md#src-aoda-ontario) |
| A11Y-27<a name="a11y-27"></a> | binding WCAG version taken from a vendor page or consultant summary | **Regulation text over vendor summary**: secondary sources contradict each other on binding versions (the two AODA sources split 2.0 AA vs 2.2); build to 2.2 AA, claim per the regulation's own citation | What does the regulation itself cite? | S·r | [aoda-ontario ch-2](../SOURCES.md#src-aoda-ontario) |
| A11Y-28<a name="a11y-28"></a> | accessibility or UI-automation path recovers structure from screenshots because view hierarchy / a11y tags are missing or incomplete | **Pixel parse is proposal, not certificate**: when structure is inferred from pixels, treat the hierarchy as an assistive proposal for navigation/tooling and still require human AT verification, because detection and grouping errors leave residual barriers and the model does not certify name quality, states, or other POUR criteria (↔ [[A11Y-23]](accessibility.md#a11y-23) both refuse to certify from a surface the assistive contract does not actually expose) | What residual detection/group errors remain, and what did a human AT pass still check? | J·r | [screen-parsing](../SOURCES.md#src-screen-parsing) |
| A11Y-29<a name="a11y-29"></a> | visual layout or pixel model groups controls one way while the accessibility tree, focus order, or interaction wiring groups them another | **Visual group must match enforced a11y structure**: when the eye or a screenshot parser invents a group, verify the platform accessibility tree and focus order enforce the same boundary, because a perceived group the system does not wire is a navigation/name lie (↔ ux [[PERC-03]](interaction-ux.md#perc-03) the visual grouping and the wired structure are audited as one claim; Principle 10's perceived-vs-enforced cut) | Does the a11y tree enforce the same groups the pixels imply? | J·r | [screen-parsing](../SOURCES.md#src-screen-parsing) |
| A11Y-30<a name="a11y-30"></a> | accessibility evidence is a pile of per-screen scanner dumps or a crawl with near-duplicate screens | **Whole-app de-duped report**: when auditing more than one screen, group same screens and match UI elements so each unique issue is counted once with category totals, because scan-by-scan review redoes overlapping work and hides app-wide patterns (↔ [[A11Y-23]](accessibility.md#a11y-23) on scanner limits) | Is there one de-duped app report with per-category counts? | J·r | [accessibility-report-generation](../SOURCES.md#src-accessibility-report-generation) |
| A11Y-31<a name="a11y-31"></a> | the same false positive, wont-fix, or already-addressed finding reappears on every scan | **Ignore memory across scans**: when humans triage scanner output, persist ignore decisions keyed to screen and element identity and re-apply them on later runs (and filter issues with no visible matched element as likely FP), because tools with no memory force endless re-triage and bury new regressions | Do known FPs/wont-fix stay suppressed without hiding new issues? | J·w | [accessibility-report-generation](../SOURCES.md#src-accessibility-report-generation) |
| A11Y-32<a name="a11y-32"></a> | an automated accessibility report is used as a CI or release gate | **Report is triage input, not sole gate**: when a whole-app accessibility report gates ship or CI, require human prioritization of high-count/high-impact findings plus AT or manual checks on primary flows, because automated tools will not find all issue types and crawler coverage is incomplete (↔ [[A11Y-23]](accessibility.md#a11y-23); ↔ HITL review-queue rules) | What did a human and an AT pass still verify beyond the report? | J·g | [accessibility-report-generation](../SOURCES.md#src-accessibility-report-generation) |
| A11Y-33<a name="a11y-33"></a> | CMS editor, rich-text field, design tool, template picker, or content-generation surface (including AI generators as modern auto-generation UIs) under product review | **Authoring UI is for authors (Part A)**: when the surface creates or modifies content for others, require Part A floors: web-based UI meets WCAG (A.1.1.1); all authoring functions keyboard-operable without traps (A.3.1.1 Level A, A.3.1.2); non-web UI follows platform a11y services (A.1.2), because authors with disabilities cannot produce content if the tool excludes them (↔ [[A11Y-11]](accessibility.md#a11y-11) keyboard walk on product UI; this row scopes ATAG's authoring-tool duty) | Can an author complete primary create/edit flows by keyboard on this tool UI alone? | B·r | [atag20](../SOURCES.md#src-atag20) |
| A11Y-34<a name="a11y-34"></a> | tool automatically generates web content during or after an authoring session (templates auto-selected, wizards, scripts, generated pages; treat AI generation as auto-generation when the tool specifies the process) | **Auto-specified content is accessible (B.1.1)**: when the developer-specified path auto-generates content, ensure at least one of: output meets WCAG without author input; prompt for required accessibility information during generation; automatic accessibility checking after; or prompt authors to check (B.1.1.1/B.1.1.2, Level A for WCAG A), because auto-produced problems impose repair on authors and ship barriers to end users | After auto-generation, what required a11y info was prompted or checked? | B·w | [atag20](../SOURCES.md#src-atag20) |
| A11Y-35<a name="a11y-35"></a> | restructuring, recoding, optimizing transform, or structured copy-paste inside the authoring tool | **Preserve accessibility information (B.1.2)**: when equivalent mechanisms exist in the output technology, preserve accessibility information (including text alternatives for preserved non-text) or default-warn / check (B.1.2.1-B.1.2.4); optimizations must preserve (B.1.2.3 Level A), because transforms silently strip the accessible layer between input and output | Does the transform keep alts, names, and structure, or warn before loss? | S·w | [atag20](../SOURCES.md#src-atag20) |
| A11Y-36<a name="a11y-36"></a> | insert non-text content, choose among authoring actions for the same outcome, set content properties, or offer templates / pre-authored content | **Guide accessible production (B.2)**: make accessible options at least as prominent as inaccessible ones (B.2.2.1); provide mechanisms to set accessibility properties (B.2.2.2); keep text alternatives editable (B.2.3.1); never auto-insert generic or filename alts without author accept/modify/reject (B.2.3.2); offer accessible templates for a range of uses (B.2.4.1) (↔ [[A11Y-02]](accessibility.md#a11y-02) owns content alt quality; this row is the tool's prompt/edit/default-path duty) | Is the accessible path as visible as the inaccessible one, and can authors edit alts? | S·w | [atag20](../SOURCES.md#src-atag20) |
| A11Y-37<a name="a11y-37"></a> | authoring tool lets authors add or modify content in ways that can violate a WCAG success criterion | **In-tool check and repair (B.3)**: provide accessibility checking for those criteria (manual checking is the minimum; B.3.1.1) with locate and decide help (B.3.1.2/B.3.1.3), and when a check can detect failure provide repair suggestions (B.3.2.1); treat status reports as triage input not sole conformance (↔ [[A11Y-23]](accessibility.md#a11y-23) scanner floor; ↔ [[A11Y-32]](accessibility.md#a11y-32) report is not sole gate; [[A11Y-30]](accessibility.md#a11y-30)/[[A11Y-31]](accessibility.md#a11y-31) own post-hoc whole-app report ops, not this authoring-time duty) | For each SC this tool can break, where is check + repair in the authoring flow? | S·r | [atag20](../SOURCES.md#src-atag20) |
| A11Y-38<a name="a11y-38"></a> | accessible content support features (checking, prompts, repair, a11y property fields) ship off by default or less prominent than spelling/grammar/syntax checks | **A11y support on and prominent by default (B.4.1)**: turn all accessible content support features on by default (B.4.1.1 Level A), keep them reactivatable if off (B.4.1.2), and at least as prominent as invalid-markup/spelling/grammar features (B.4.1.4 Level AA), because ATAG requires accessible support as the default workflow (Principle 6 arrival: unchosen off is neglect; ↔ [[LAY-10]](design-aesthetics.md#lay-10) unchosen surface defaults; ↔ [[RLSE-04]](engineering.md#rlse-04) undesigned state, different surface) | Are a11y checks/prompts on by default and as visible as spellcheck? | S·p | [atag20](../SOURCES.md#src-atag20) |

## 6. Cross-lexicon amplifications

This rubric's rules strengthen the other lexicons' rules, and the reverse also holds:

- **Contrast is designed upstream**: design [[COL-04]](design-aesthetics.md#col-04) (value architecture before hue) makes [[A11Y-01]](accessibility.md#a11y-01) pass by construction; [[A11Y-01]](accessibility.md#a11y-01) is the measurable readout that [[COL-04]](design-aesthetics.md#col-04) was actually followed. A team failing contrast in review skipped a design step, not an engineering one.
- **The state matrix has an accessibility dimension**: eng [[RLSE-04]](engineering.md#rlse-04) (undesigned state is a bug) × [[A11Y-24]](accessibility.md#a11y-24): a state isn't designed until its focus order and announcements are. PDA's UX lens and WCAG conformance audit the same states from two threat models.
- **Claims discipline transfers whole**: [[A11Y-22]](accessibility.md#a11y-22) is [[CLM-01]](business-marketing.md#clm-01)/[[CLM-04]](business-marketing.md#clm-04) instantiated: "accessible" is an adjective-without-mechanism exactly like "encrypted", and the EAA/ADA give it the same enforcement asymmetry [[CLM-02]](business-marketing.md#clm-02) describes.
- **Exclusion is a brand decision**: design [[BRND-07]](design-aesthetics.md#brnd-07) requires naming who a product is *not* for; an inaccessible flow silently makes that decision without anyone signing it. If an audience is to be excluded, that decision belongs in the brief, not in a `<div onclick>`.
- **Platform floor vs spec floor**: [[A11Y-14]](accessibility.md#a11y-14) (24px) vs platform HIG (44pt/48dp): always the stricter; the same "stricter-of-two-gatekeepers" logic as biz [[PROD-09]](business-marketing.md#prod-09) channel contracts.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[A11Y-01]`). CI-enforceable rows (§1 especially) are designed to be wired into automated checks; §5 rows fire in review and go-to-market surfaces. Product-specific conformance targets (which pages, which level, by when) live in the consuming project, not here.
