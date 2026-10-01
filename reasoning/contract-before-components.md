# Contract before components

Slug: `contract-before-components`
ID: `CARD-01`
Mechanism claim: For products with explicit channel-format constraints, write
the format contract before filling in components. Other gatekeeper and
compliance contexts need their own source-backed requirements.

## Scope

Covers: channel and store guidelines; accessibility conformance claims;
security policy before controls; release and expert gates; completion claims
that name evidence; schema for machine-consumed generation.

Excludes: pure taste without a gatekeeper or compliance claim; measurement
apparatus integrity (see [measurement-integrity](measurement-integrity.md)); privilege sizing alone
(see [least-privilege-blast-radius](least-privilege-blast-radius.md)).

## Observable triggers

- Work starts on UI, copy, song, model, or feature before the acceptance
  checklist exists in checkable form.
- A claim ("accessible", "secure", "done", "compliant") has no step-by-step
  falsifier a hostile reader can run.
- Rejection from a store, gate, or reviewer is treated as a cosmetic obstacle
  rather than the named missing condition.
- Expert sign-off is asked for jargon without exact strings or yes/no questions.
- Machine consumers must parse free prose for status, schema, or outcome.

## Causal mechanism

A product built without its known channel limits may need revision to fit
them. Writing those format constraints first gives component construction a
known container. The cited passage supports format-first construction; it does
not establish that late constraints always make a surface expensive to change.

## Required action

1. Name the gatekeeper (channel, store, regulator, compliance officer, release
   checklist, machine consumer) and the written contract it will apply
   ([PROD-09](../lexicons/business-marketing.md#prod-09), [CLM-05](../lexicons/business-marketing.md#clm-05),
   [SECD-01](../lexicons/security.md#secd-01)).
2. Make the claim falsifiable step by step before shipping language that
   asserts it ([A11Y-22](../lexicons/accessibility.md#a11y-22)).
3. Treat the broader gate policies in
   [AGT-08](../lexicons/engineering.md#agt-08) and
   [RLSE-02](../lexicons/engineering.md#rlse-02) as hypotheses pending grounding:
   satisfying a rejection's named condition or escalating with evidence, and
   refusing release past any unresolved gate verdict, may be useful policies,
   but their cited passages do not establish them as requirements.

   These current row summaries are distinct from the narrower source guidance
   awaiting coordinated row revisions. *The Pragmatic Programmer: Your Journey
   to Mastery* supports checking documented preconditions at the caller when
   the language checks them before routine entry, or bracketing the call with
   an assertion-checking preamble or postamble without that support.
   *Release It! Design and Deploy Production-Ready Software* supports refusing
   approval before QA has finished testing merely to meet an arbitrary date;
   it does not establish the broader unresolved-gate policy.
4. Give experts exact quoted strings and yes/no questions
   ([RLSE-09](../lexicons/engineering.md#rlse-09)).
5. Machine-facing outcomes are schema, status, or named evidence, not prose
   ([FM-04](../lexicons/ml-systems.md#fm-04), [AGT-04](../lexicons/engineering.md#agt-04),
   [AGT-21](../lexicons/engineering.md#agt-21)).

## Predicted failure

Charts and stores reject late. Accessibility claims fail audit after launch.
Security theatre: mechanisms without a policy sentence. Teams argue past gates
instead of meeting them. "Done" cannot be verified. Downstream parsers invent
structure from banners and narrative.

## Worked example

A redesign starts by picking a chart library before writing the checkable contract the dashboard gate will enforce (metric definitions, empty states, refresh SLA). The trigger is components first, gate second. Write the acceptance checks as named assertions, then choose the library that can meet them. Without the contract, the team swaps components twice and still cannot say when the board is done.

## Exemptions and boundaries

- Exploratory spikes may precede a contract if they do not ship claims or bind
  customers; the card fires when the artifact will face a gate or assert a claim.
- Living contracts may iterate; each ship still needs the version of the
  contract that gate will use *for that ship*.
- Substance-before-style (Principle 5) ranks content structure; this card ranks
  the *acceptance* contract. Both can apply.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [PROD-09](../lexicons/business-marketing.md#prod-09) contract before components | [GTM-08](../lexicons/business-marketing.md#gtm-08) launch novelty when discovery requires a first look | novelty may lead marketing surface; gate contracts still bind claim and ship surfaces |
| object | [SECD-01](../lexicons/security.md#secd-01) policy before mechanisms | [SECD-02](../lexicons/security.md#secd-02) least privilege on grants | write the policy; then size grants so compromise cannot exceed it |
| surface | [A11Y-22](../lexicons/accessibility.md#a11y-22) falsifiable accessibility process | [CLM-05](../lexicons/business-marketing.md#clm-05) hostile commercial reader | same contract-first reflex on compliance vs store/legal readers |

## Disconfirmers

- A hostile reader runs the written checklist and cannot find a step the
  artifact fails while a non-checklist review still rejects it (contract was
  incomplete).
- Shipping without the checklist did not increase rework or rejection rate
  under controlled comparison (mechanism not load-bearing here).
- Machine consumer validates schema without regex over prose (contract is
  structural).

## Verification

- Contract artifact exists before component work is marked done: named file,
  checklist, or schema with version.
- Every shipped claim maps to a step a third party can fail.
- Completion records cite file:line, test, or decisive output
  ([AGT-04](../lexicons/engineering.md#agt-04)).

## Rule IDs

- [PROD-09](../lexicons/business-marketing.md#prod-09): channel contract before the product surface
- [CLM-05](../lexicons/business-marketing.md#clm-05): write for the hostile literal reader
- [A11Y-22](../lexicons/accessibility.md#a11y-22): accessibility as falsifiable process
- [RLSE-09](../lexicons/engineering.md#rlse-09): expert sign-off as exact questions
- [RLSE-02](../lexicons/engineering.md#rlse-02): broader unresolved-gate policy is a hypothesis pending grounding; [*Release It! Design and Deploy Production-Ready Software*](../SOURCES.md#src-release-it) supports refusing approval before QA finishes merely to meet an arbitrary date, not that broader policy
- [AGT-08](../lexicons/engineering.md#agt-08): broader rejection policy is a hypothesis pending grounding; [*The Pragmatic Programmer: Your Journey to Mastery*](../SOURCES.md#src-pragmatic-programmer) supports caller precondition checks, not that broader policy
- [SECD-01](../lexicons/security.md#secd-01): policy paragraph before mechanisms
- [AGT-04](../lexicons/engineering.md#agt-04): done names evidence
- [AGT-21](../lexicons/engineering.md#agt-21): exit status is the machine contract
- [FM-04](../lexicons/ml-systems.md#fm-04): schema-constrained generation for machines

## Principles

- 1. Author the contract before the components
- 18. A machine consumes contracts, not prose

## Evidence / source slugs

- [`klf-the-manual`](../SOURCES.md#src-klf-the-manual): supports [PROD-09](../lexicons/business-marketing.md#prod-09)
- [`bootstrap`](../SOURCES.md#src-bootstrap): supports [CLM-05](../lexicons/business-marketing.md#clm-05), [RLSE-09](../lexicons/engineering.md#rlse-09), [AGT-04](../lexicons/engineering.md#agt-04)
- [`wcag22-accessibility`](../SOURCES.md#src-wcag22-accessibility): supports [A11Y-22](../lexicons/accessibility.md#a11y-22)
- [`anderson-security-engineering`](../SOURCES.md#src-anderson-security-engineering): supports [SECD-01](../lexicons/security.md#secd-01)
- [`ai-engineering`](../SOURCES.md#src-ai-engineering): supports [FM-04](../lexicons/ml-systems.md#fm-04)
- [`unix-programming-environment`](../SOURCES.md#src-unix-programming-environment): supports [AGT-21](../lexicons/engineering.md#agt-21)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to hold every compliance or release-engineering idea. Open the rule rows for
triggers and tiers. [SOURCES.md](../SOURCES.md) is a bibliography registry, not
a substitute for the original works.
