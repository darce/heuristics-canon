# Source note: `hubbard-measure-anything-cybersecurity`

## Identity

- Slug: `hubbard-measure-anything-cybersecurity`
- Citation: Douglas W. Hubbard and Richard Seiersen. *How to Measure Anything
  in Cybersecurity Risk*. 2nd ed., Wiley, 2023.
- Canon registry: [SOURCES.md](../SOURCES.md#src-hubbard-measure-anything-cybersecurity)

## Rights posture

> This note identifies a third-party work for citation and evidence
> calibration. The work remains the property of its authors and publishers.
> Citation is not a license to reproduce expression. The private corpus may
> hold research copies under its own `NOTICE.md`; those copies and any
> chapter-level distillations do not ship in the public projection. This note
> makes no determination about fair use, secondary liability, or downstream
> redistribution rights.

## Narrow question

For the MEAS family rows that cite this work, does the source carry the stated
mechanism (uncertainty reduction, ordinal refusal, calibrated intervals, VoI
prioritization, sparse-sample baselines), or only adjacent motivation?

## Verdicts

Rows are grouped by decision mechanism, not by ascending chapter tour.
Pointers reuse chapter anchors already present in rule `Src` cells. They are
navigation aids for a reader with the book, not a substitute for the text.

### What counts as measurement

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [MEAS-02] | support | ch-2 | Measurement as quantitative uncertainty reduction, including partial information |
| [MEAS-11] | support | ch-2 | Operational definition and decision purpose before instrument shopping |
| [MEAS-08] | support | ch-2 | Sparse samples and reference-class baselines before declaring "no data" |

### Ordinal refusal

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [MEAS-01] | support | ch-3 | Restate ordered likelihood/impact cells as period probability and monetary loss interval |
| [MEAS-05] | support | ch-5 | No meaningful arithmetic on pure ordinals; ranking instability under rescaling |

### Distribution and control economics

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [MEAS-03] | support | ch-3 | Loss-exceedance style communication over single cell or single expected-loss scores |
| [MEAS-04] | support | ch-3 | Control spend judged by monetized loss reduction, not colour movement |

### Model quality and method proof

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [MEAS-09] | support | ch-6 | Factors need definition, observable, and decision consequence |
| [MEAS-10] | partial | ch-4 | Theme that workshops raise confidence without accuracy is present; rule's outcome-comparison checklist is canon packaging |
| [MEAS-12] | support | ch-5 | Compare measurement error to the real alternative decision process |

### Elicitation and measurement prioritization

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [MEAS-06] | support | ch-7 | Calibration and stake-indifference checks on stated intervals |
| [MEAS-07] | support | ch-9 | Rank measurement work by value of information for a pending decision |

## Limitations and obsolescence

- Domain voice is cybersecurity risk and quantitative decision analysis. The
  mechanisms transfer; the examples and industry threat enumerations age and
  should not be treated as current intel.
- The work argues for quantitative methods against qualitative matrices. It is
  not a primary source for load-test coordinated omission, biometric
  denominators, or accessibility scan gaps; those arrivals live on other slugs
  under the same principles.
- Edition sensitivity: second-edition structure is what the chapter anchors
  assume. A different edition may shift chapter numbers without killing the
  mechanism.
- Statistical depth is practitioner-facing. For formal measurement-error
  identification, the canon also uses other sources (for example
  `gustafson-misclassification` on AUDIT rows); do not stretch Hubbard to cover
  those proofs.
- Residual single-source density: all twelve MEAS rows still ground on this
  slug. That is a provenance fact, not a claim that the family is a book
  checklist. Until independent sources carry the same mechanisms under separate
  `Src` entries, consumers should treat the cluster as one author's apparatus
  restated in mechanism-native language.

## Conflicts

- Against pure "metrics are always gaming": [MEAS-02] and [MEAS-07] insist some
  quantitative narrowing is mandatory for high-stakes decisions, while
  Principle 15 and [OBS-09] insist the *frame* must sit outside the optimizer.
  Partition: measure the decision quantity; do not let the measured party edit
  the frame.
- Against expert recognition in high-validity domains ([NDM-01]): Hubbard-style
  elicitation still helps when stakes are numeric and feedback is slow; it does
  not require replacing fireground recognition with Monte Carlo mid-event.
- Against teams that treat any model as automatic truth: [MEAS-06] and
  [MEAS-12] push calibration and comparison to alternatives, which aligns with
  [FORE-03] scoring rather than with uncritical automation.

## Canon consequences

- **MEAS-family editorial substitution review:** MEAS-01..12 were re-authored
  into mechanism-native canon language. Source-packaged headings and workshop
  brand phrases (including one-for-one substitution, Rule of Five,
  analysis-placebo, return on control, clarification chain, and equivalent bet)
  were retired from public rule names and triggers. Mechanisms, stable IDs,
  tiers, phases, and `Src` chapter anchors stayed. The family is not a book
  tour and must not be re-expanded into chapter-ordered pedagogy.
- Keep all twelve MEAS rows pointed here unless a grounding pass marks a
  specific row `partial` with a tighter source. Residual limitation: single-
  slug provenance remains until independent sources absorb individual
  mechanisms.
- Reasoning card `measurement-integrity` may cite this slug for uncertainty
  reduction and ordinal refusal; it must not imply the book covers PERF/MLDATA
  apparatus failures.
- If a future edition renumbers chapters, update `Src` anchors in the lexicon
  and this note's verdict tables together; do not leave orphan pointers.
- Do not promote cybersecurity threat lists from this work into the security
  lexicon without a security-primary source.
- Verdict tables stay ordered by decision mechanism (or by rule ID within a
  mechanism cluster), never by ascending chapter number alone.

## Cannot answer

- Whether any particular organization has a license to reproduce figures,
  tables, or extended paraphrase from the book.
- Page-level proof for readers without the work; this note is not a condensation.
- Current CVE or control catalogs; the book is not a live feed.
- Whether ordinal matrices are *legally* required in a given compliance regime
  (process requirements can force a format while still being bad measurement).
- Full support map for non-MEAS rules that merely share Principle 4 or 15.
- Anything in private `distilled/` chapter maps; those do not ship.
