# Heuristics canon

A shared set of decision rules for software, product, design, security,
research, and operations. Each rule is a stable ID with an observable trigger,
a falsifiable action, a question, a tier, and a citable source.

Rules exist so people and tools can cite a short claim without restating the
whole argument. Texts from different fields sometimes describe the same causal
mechanism; [PRINCIPLES.md](PRINCIPLES.md) joins those rules so a question in one
domain can surface evidence another domain would miss.

## A concrete example

You are reviewing a service change that adds an HTTP client. The client has no
timeout. The engineering lexicon has [RES-02](lexicons/engineering.md#res-02):
**timeout every blocking call**. You cite `[RES-02]`, set the timeout, and move
on. If the same change also grows irreversible blast radius, open a
[reasoning card](reasoning/) such as `least-privilege-blast-radius` for the joined
decision. The rule row is the default depth; the card is optional.

## How to use it

1. **Name what changed** (schema, plan, UI, model, incident, launch).
2. **Open only the relevant families.** A **family** is a short prefix group
   inside a lexicon (for example `RES` resilience, `SEC` security, `FORE`
   forecasting). Use the sketch below, the routing table in
   [AGENTS.md](AGENTS.md), or a lexicon table of contents.
3. **Keep rules whose trigger you can observe.** Read exemptions and tier.
4. **Cite by ID and stop** when applicable blockers and strong defaults are
   handled.

Agents and integrators: follow the full contract in [AGENTS.md](AGENTS.md)
(pin a release tag, verify digests, progressive card retrieval).

### Common artifacts → where to look

Sketch only; not the full route table.

| If you changed… | Start here (lexicon · families) |
|---|---|
| Schema, migration, storage | [engineering](lexicons/engineering.md) · MODEL, DATA, STOR · [security](lexicons/security.md) · PG |
| API or public name | engineering · API, NAME · [design](lexicons/design-aesthetics.md) · BRND |
| Concurrent or async code | engineering · CON, DATA, RES |
| Release, deploy, rollback | engineering · RLSE, OBS, TEST |
| UI, form, navigation | [interaction-ux](lexicons/interaction-ux.md) · PERC, COG, NAV, INT, FORM · [accessibility](lexicons/accessibility.md) · A11Y |
| Auth, tenancy, web threat | [security](lexicons/security.md) · SEC, WEB, SECD, PG |
| Model eval, RAG, agent loop | [ml-systems](lexicons/ml-systems.md) · EVAL, RAG, FM, COST · engineering · RES, OBS |
| Forecast, experiment, metric | [epistemics](lexicons/epistemics.md) · FORE, EXP, MEAS, BIAS |
| Product bet, pricing, launch | [business-marketing](lexicons/business-marketing.md) · STRAT, PROD, GTM, CLM |
| Prose or docs | [writing](lexicons/writing.md) · WRIT |

## What is inside

| Path | What it is |
|---|---|
| [lexicons/](lexicons/) | Decision rules by domain and family |
| [PRINCIPLES.md](PRINCIPLES.md) | Cross-domain mechanisms that join rules |
| [SOURCES.md](SOURCES.md) | Bibliography registry for every cited work |
| [reasoning/](reasoning/) | Mechanism cards (optional decision depth) |
| [AGENTS.md](AGENTS.md) | Technical consumer contract |
| [NOTICE.md](NOTICE.md) | Rights boundary and CC BY scope |
| `meta/release-manifest.json` | Per-release digests and published rule IDs |

### Reading a rule

```text
| RES-02 | blocking call with no timeout | Timeout every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

- **ID** is the permanent citation key (`[RES-02]`, anchor `#res-02`).
- **Trigger** is observable in an artifact, plan, error, or metric.
- **Rule** is the condition, action, and consequence.
- **Answers** is the decision-point question.
- **T·P** is tier and phase (`B` blocks, `S` strong default, `J` needs judgment;
  phase buckets are plan / write / review / ship; see AGENTS).
- **Src** resolves through [SOURCES.md](SOURCES.md).

## Principles and reasoning cards

**Principles** surface the same mechanism in another material. Use siblings as
independent checks, not as a citation quota. They are grouped into four forces
(contracts, evidence, reversibility, feedback) for navigation; the numbered
principles stay separate.

**Reasoning cards** rebuild a multi-rule decision: what to notice, why it fails,
what to do, and how to check. Open a card when several retained rules share one
mechanism. Cards are optional depth above the row and selective pilots, not
full coverage. [SOURCES.md](SOURCES.md) is the complete registry of cited
works; it is not a substitute for reading the originals through ordinary legal
channels.

## Rights

Original rule, principle, and card prose is offered under CC BY 4.0 as stated in
[NOTICE.md](NOTICE.md). That grant does not cover third-party works listed in
SOURCES.md.

Integrity, versioning, routing tables, and card-open rules live in
[AGENTS.md](AGENTS.md).
