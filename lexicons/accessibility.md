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
| Src | source slug, resolved in the Sources section at the end of this file; the distillation behind it stays in the private research corpus |

Tier: **B**locker (excludes a user class or creates legal exposure if violated),
**S**hould (strong default, spec-stated exemptions exist), **J**udgment. Phase:
**p**lan, **w**rite, **r**eview, **g**tm (claims and contract surfaces).

WCAG success-criterion numbers are kept in rules as shared retrieval keys.
Cross-lexicon borders cite `↔ eng/design/biz` rules instead of restating them.
## 1. The Working Set (96% of shipped failures)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-01<a name="a11y-01"></a> | text or UI colors set or changed in a diff/mockup | **Contrast floors (1.4.3/1.4.11)** — text ≥4.5:1, large text and UI component states ≥3:1; logos/incidental exempt; fails on 83.9% of pages (↔ eng [[UI-02]](engineering.md#ui-02) owns the token mechanics; ↔ design [[COL-04]](design-aesthetics.md#col-04): a value-ranked palette passes free) | Does every pair pass its ratio on every real ground? | B·w | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |
| A11Y-02<a name="a11y-02"></a> | image/icon/chart added without alt text or decorative marking | **Alt serves purpose (1.1.1)** — text equivalent for the content's *purpose*, or explicit `alt=""` when decorative; filename-alts pass scanners and fail users | What must a non-seeing user get from this? | B·w | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |
| A11Y-03<a name="a11y-03"></a> | form input without a programmatically associated visible label | **Label every input (3.3.2/1.3.1)** — `<label for>` or equivalent; placeholder is not a label (vanishes on input, skipped by some AT) | Is the label announced with the field? | B·w | [wcag22-accessibility ch-4](#src-wcag22-accessibility) |
| A11Y-04<a name="a11y-04"></a> | link or button with empty or generic accessible name | **Name every control (2.4.4/4.1.2/2.5.3)** — name states destination/action; visible label text contained in accessible name (voice users say what they see) | What does a voice-control user say to press this? | B·w | [wcag22-accessibility ch-3](#src-wcag22-accessibility) |
| A11Y-05<a name="a11y-05"></a> | page template or HTML shell in a diff | **Declare the language (3.1.1)** — `lang` on the document; mark language changes inline (3.1.2) | Does AT know how to pronounce this page? | B·w | [wcag22-accessibility ch-4](#src-wcag22-accessibility) |
| A11Y-06<a name="a11y-06"></a> | status, trend, series, or validity distinguished by hue alone | **Second channel always (1.4.1)** — pair color with icon/label/weight/pattern (↔ eng [[UI-02]](engineering.md#ui-02) — same rule, this row adds the criterion number and scan trigger) | Does the signal survive greyscale? | B·r | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |

## 2. Perceivable (beyond the working set)

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-07<a name="a11y-07"></a> | visual structure (headings, groups, order) not mirrored in markup | **Programmatic structure (1.3.1/1.3.2/2.4.6)** — headings marked as headings, no skipped levels (41.8% of pages skip), DOM order = reading order | Would this outline make sense read linearly? | S·r | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |
| A11Y-08<a name="a11y-08"></a> | layout reviewed only at desktop width / 100% zoom | **Reflow and resize (1.4.4/1.4.10/1.4.12)** — usable at 200% zoom and 320px width without 2-D scroll; survives user-forced text spacing; 2-D-essential content (maps, tables) exempt | What breaks at 320px and 200%? | S·r | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |
| A11Y-09<a name="a11y-09"></a> | video/audio content added | **Captions and alternatives (1.2.x)** — captions for prerecorded (A) and live (AA) audio; audio description for prerecorded video (AA); transcript for audio-only | Can this media be consumed deaf, or blind? | S·p | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |
| A11Y-10<a name="a11y-10"></a> | tooltip/popover appears on hover or focus | **Dismissible, hoverable, persistent (1.4.13)** — Esc dismisses, pointer can enter the popup, content stays until dismissed | Can the user read the tooltip without a steady hand? | S·w | [wcag22-accessibility ch-2](#src-wcag22-accessibility) |

## 3. Operable

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-11<a name="a11y-11"></a> | new interactive flow or widget in review | **Keyboard walk (2.1.1/2.1.2/2.4.3/2.4.7)** — every function reachable by keyboard, focus visible, order preserves meaning, no traps | Can the whole flow run from the keyboard alone? | B·r | [wcag22-accessibility ch-3](#src-wcag22-accessibility) |
| A11Y-12<a name="a11y-12"></a> | custom widget built from `<div>`/`<span>` | **Native first, ARIA last (4.1.2)** — a native element carries name/role/keyboard free; wrong ARIA overrides correct semantics (pages using ARIA average *more* errors: 59 vs 42) | Why is this not a native element? | S·r | [wcag22-accessibility ch-5](#src-wcag22-accessibility) |
| A11Y-13<a name="a11y-13"></a> | sticky header, toast, or cookie banner added to layout | **Focus not obscured (2.4.11)** — the focused element is never entirely hidden behind author content (↔ eng [[WEB-21]](security.md#web-21) an overlay that steals the interaction surface from what the user can see) | Where is keyboard focus when the banner is up? | S·r | [wcag22-accessibility ch-6](#src-wcag22-accessibility) |
| A11Y-14<a name="a11y-14"></a> | tap/click targets in a dense UI | **Target size (2.5.8)** — ≥24×24 CSS px effective; platform HIGs are stricter (44pt iOS / 48dp Android) — apply the stricter floor | Can a tremoring thumb hit this without collateral? | S·w | [wcag22-accessibility ch-3](#src-wcag22-accessibility) |
| A11Y-15<a name="a11y-15"></a> | drag, swipe, multipoint, or path gesture added | **Single-pointer alternative (2.5.1/2.5.7)** — click/keyboard path for every gesture unless the gesture is essential | How does this work without a drag? | S·w | [wcag22-accessibility ch-6](#src-wcag22-accessibility) |
| A11Y-16<a name="a11y-16"></a> | carousel, auto-updating region, or author-set time limit | **User's time, user's motion (2.2.1/2.2.2/2.3.1)** — pause/stop/hide for motion >5s, adjustable timeouts, nothing flashes >3×/s; honoring `prefers-reduced-motion` also covers AAA 2.3.3 as a near-free default (↔ ux [[INT-10]](interaction-ux.md#int-10) continuous system change needs a user stop) | Who set this tempo — the user or us? | S·w | [wcag22-accessibility ch-3](#src-wcag22-accessibility) |

## 4. Understandable & Robust

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-17<a name="a11y-17"></a> | form validation or error handling in a diff | **Errors name the field and the fix (3.3.1/3.3.3)** — detected errors identified in text at the field, corrections suggested; a bare "invalid input" toast fails (↔ product-deploy-agents-fields ch-3: specific, non-alarming, actionable) | Which field, what's wrong, how to fix — all in text? | S·w | [wcag22-accessibility ch-4](#src-wcag22-accessibility) |
| A11Y-18<a name="a11y-18"></a> | legal, financial, or data-destroying submission flow | **Reversible, checked, or confirmed (3.3.4)** — at least one of undo / validation-with-correction / confirmation step (↔ ux [[INT-07]](interaction-ux.md#int-07) preview before a costly commit; ↔ ux [[INT-09]](interaction-ux.md#int-09) reversible command stack) | Can one mis-tap destroy something permanent? | B·r | [wcag22-accessibility ch-4](#src-wcag22-accessibility) |
| A11Y-19<a name="a11y-19"></a> | login/auth or multi-step form in a diff | **No cognitive gate (3.3.7/3.3.8)** — paste/autofill are the mechanisms that usually satisfy 3.3.8; blocking them with no alternative method fails; data entered once is never re-typed in the same process (↔ ux [[COG-02]](interaction-ux.md#cog-02) recognition and choosers beat pure recall) | Does a password manager complete this unaided? | S·r | [wcag22-accessibility ch-6](#src-wcag22-accessibility) |
| A11Y-20<a name="a11y-20"></a> | focus or input triggers navigation/submission | **No surprise context change (3.2.1/3.2.2)** — focusing never changes context; input changes warn first | Did the user ask to go somewhere? | S·r | [wcag22-accessibility ch-4](#src-wcag22-accessibility) |
| A11Y-21<a name="a11y-21"></a> | async result, toast, or counter updates without focus | **Announce status (4.1.3)** — live region/`role="status"` so AT hears what sighted users see (the accessible half of "every async op has visible progress") | Does a screen reader learn this happened? | S·w | [wcag22-accessibility ch-5](#src-wcag22-accessibility) |

## 5. Process & Claims

| ID | Trigger | Rule | Answers | T·P | Src |
| --- | --- | --- | --- | --- | --- |
| A11Y-22<a name="a11y-22"></a> | "accessible" / "WCAG compliant" in copy, contract, or VPAT | **Scoped conformance claims** — version + level + page scope + date; conformance attaches to full pages and *every step* of a process; one failing step falsifies the sentence (↔ biz [[CLM-01]](business-marketing.md#clm-01): a conformance claim is a claim-as-product with EAA/ADA force) | Could one failing page falsify this sentence? | B·g | [wcag22-accessibility ch-7](#src-wcag22-accessibility) |
| A11Y-23<a name="a11y-23"></a> | accessibility verified by automated scan only | **Scanner-pass is the floor of the floor** — automation detects a minority of criteria (<4.1% of pages actually conform); keyboard walk + AT pass on primary flows required (↔ biz [[PROD-12]](business-marketing.md#prod-12): the worst-day user includes the AT user) | What did a human verify that axe cannot? | S·r | [wcag22-accessibility ch-8](#src-wcag22-accessibility) |
| A11Y-24<a name="a11y-24"></a> | screen states enumerated in a design/release review | **Every state accessible (state-matrix join)** — loading, empty, error, offline each keep focus management, announcements, and contrast; an accessible happy path with an inaccessible error state fails the process (↔ eng [[RLSE-04]](engineering.md#rlse-04) both fail when a state ships that was rendered but never designed) | Where does focus go when this errors? | S·r | [wcag22-accessibility ch-1](#src-wcag22-accessibility) + [product-deploy-agents-fields ch-3](#src-product-deploy-agents-fields) |
| A11Y-25<a name="a11y-25"></a> | accessibility work postponed as post-launch polish | **Retrofit costs more than the hedge** — the safe side (native elements, labels, contrast tokens) costs ~zero at write time and a rewrite later; same cost asymmetry as regulatory claims (↔ biz [[CLM-02]](business-marketing.md#clm-02) both price the cheap precaution now against the expensive reversal later) | What does doing this now actually cost? | S·p | [product-deploy-agents-fields ch-7](#src-product-deploy-agents-fields) |
| A11Y-26<a name="a11y-26"></a> | org or customer base touches Ontario | **AODA nexus check** — 1+ Ontario employee attaches duties (training, documents, web); 20+ employees or public sector adds mandatory compliance reports; fines run per-day (to $100k/day) and reach officers personally | Do we have Ontario nexus, and who owns the filing? | S·p | [aoda-ontario ch-1](#src-aoda-ontario) |
| A11Y-27<a name="a11y-27"></a> | binding WCAG version taken from a vendor page or consultant summary | **Regulation text over vendor summary** — secondary sources contradict each other on binding versions (the two AODA sources split 2.0 AA vs 2.2); build to 2.2 AA, claim per the regulation's own citation | What does the regulation itself cite? | S·r | [aoda-ontario ch-2](#src-aoda-ontario) |

## 6. Cross-lexicon amplifications

This rubric's rules strengthen the other lexicons' rules, and the reverse also holds:

- **Contrast is designed upstream**: design [[COL-04]](design-aesthetics.md#col-04) (value architecture before hue) makes [[A11Y-01]](accessibility.md#a11y-01) pass by construction; [[A11Y-01]](accessibility.md#a11y-01) is the measurable readout that [[COL-04]](design-aesthetics.md#col-04) was actually followed. A team failing contrast in review skipped a design step, not an engineering one.
- **The state matrix has an accessibility dimension**: eng [[RLSE-04]](engineering.md#rlse-04) (undesigned state is a bug) × [[A11Y-24]](accessibility.md#a11y-24): a state isn't designed until its focus order and announcements are. PDA's UX lens and WCAG audit the same seven states from two threat models.
- **Claims discipline transfers whole**: [[A11Y-22]](accessibility.md#a11y-22) is [[CLM-01]](business-marketing.md#clm-01)/[[CLM-04]](business-marketing.md#clm-04) instantiated: "accessible" is an adjective-without-mechanism exactly like "encrypted", and the EAA/ADA give it the same enforcement asymmetry [[CLM-02]](business-marketing.md#clm-02) describes.
- **Exclusion is a brand decision**: design [[BRND-07]](design-aesthetics.md#brnd-07) requires naming who a product is *not* for; an inaccessible flow silently makes that decision without anyone signing it. If an audience is to be excluded, that decision belongs in the brief, not in a `<div onclick>`.
- **Platform floor vs spec floor**: [[A11Y-14]](accessibility.md#a11y-14) (24px) vs platform HIG (44pt/48dp): always the stricter; the same "stricter-of-two-gatekeepers" logic as biz [[PROD-09]](business-marketing.md#prod-09) channel contracts.

## Consumption

Canonical source. Consuming repos sync this file and cite rules by ID (`[A11Y-01]`). CI-enforceable rows (§1 especially) are designed to be wired into automated checks; §5 rows fire in review and go-to-market surfaces. Product-specific conformance targets (which pages, which level, by when) live in the consuming project, not here.

<!-- BEGIN GENERATED SOURCES -->

## Sources

Every `Src` cell above names one of these. The citation is the work itself; the distillation behind it stays in the private research corpus.

| Src | Source | Rules here |
|---|---|---|
| <a name="src-aoda-ontario"></a>`aoda-ontario` | wcag.com. "AODA Compliance." *wcag.com*, Dec. 2024. accessibilitychecker.org. "AODA Guide." *accessibilitychecker.org*, Aug. 2024 | 2 |
| <a name="src-product-deploy-agents-fields"></a>`product-deploy-agents-fields` | Fields, Jason. "Product Deploy Agents." *GitHub*, version 2.0, 2026, github.com/fasonista71/product-deploy-agents | 1 |
| <a name="src-wcag22-accessibility"></a>`wcag22-accessibility` | W3C Web Accessibility Initiative. *Web Content Accessibility Guidelines 2.2*. n.d. WebAIM. *The WebAIM Million*. 2026 | 23 |
| <a name="src-wcag22-accessibility-ch-1-product-deploy-agents-fields"></a>`wcag22-accessibility-ch-1-product-deploy-agents-fields` | W3C Web Accessibility Initiative. *Web Content Accessibility Guidelines 2.2*. n.d. WebAIM. *The WebAIM Million*. 2026 | 1 |

<!-- END GENERATED SOURCES -->
