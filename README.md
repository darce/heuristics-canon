# Heuristics canon

A library of more than 1,800 short, checkable rules for software work and for
the writing, marketing, and decisions around it. Nearly every rule is distilled
from a book, paper, or standard, and cites it. The few with no source yet,
fewer than thirty, are labelled unsourced practice until a source is found.

That makes the canon a grounding layer for planning, writing, and review. It
holds the cited evidence a decision can be checked against, so a
recommendation rests on a source you can open rather than on someone's say-so.
It does not run the work, pick your tools, or decide for you. The person or
agent doing the work still chooses which rules apply.

A rule names something you can see in the work, says what to do about it, and
gives you one question to ask. Every rule has a permanent ID, such as
`RES-02`, so a person or a tool can cite it in a review, a plan, or a commit
message instead of restating the argument.

## A rule at work

You are reading a marketing brief before it goes to an agency. Its proof of
demand is a survey in which people said they would buy. That matches
[GTM-01](lexicons/business-marketing.md#gtm-01), **ask them to buy**: stated
intent is not demand. GTM-01 is tier B, so the brief waits until it shows paid
intent, such as a pre-order or a paid pilot, or carries a written exemption.
You write `[GTM-01]` in the margin and move on to the next line.

## Reading a rule

Each lexicon is a Markdown table, and each row is one rule:

```text
| RES-02 | Connect/read/pool-checkout/HTTP client with no timeout | Timeout on every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

| Column | What it holds |
|---|---|
| ID | The permanent ID; the row's anchor is `#res-02` |
| Trigger | What you can see in the work when the rule applies |
| Rule | The rule's name in bold, then what to do and why |
| Answers | The question to ask when the trigger appears |
| Tier·phase | How hard the rule is, and when in the work it tends to apply |
| Source | The work behind the rule, listed in [SOURCES.md](SOURCES.md) |

The tier sets how hard a rule is:

- **B** blocks the work until the issue is handled or explicitly exempted.
- **S** is a strong default with named exemptions.
- **J** calls for your judgment.

Across lexicons, these labels keep the same action meaning, but the consequence
bar that separates B from S is domain-specific. The security lexicon uses B for
an omission that is exploitable or causes data loss or an authorization bypass;
business and marketing uses B for a violation that is existential or
irreversible. When a route crosses lexicons, read each rule against the Tier
bar in its owning lexicon. A B in one domain is a blocker under that domain's
bar, not a cross-domain severity ranking.

Rules are evidence-backed defaults. They do not override your judgment, the
facts in front of you, or a documented exemption.

## Using it with an agent

Any assistant that can read a web page or a repository can use the canon:
Claude Code, Claude Cowork, Codex, or another. Nothing needs installing. Tell
it once:

```text
Read the heuristics canon at https://github.com/darce/heuristics-canon,
starting with AGENTS.md. Whenever I ask you to review, plan, or write,
apply the canon and cite the rule IDs you used.
```

If your tool reads local files but not web pages, clone the repository next
to your project and point the agent at the copy.

A review then goes like this:

```text
  you                        the agent
  ---                        ---------
  "Review this brief."  -->  reads it
                             finds the rules whose trigger appears in the text
                             edits the brief where a rule applies
                        <--  the edited brief and a short list:
                             each change, and the rule ID behind it
  you read the list and
  keep or undo each change
```

The list is what makes the review checkable. An agent can miss a trigger, or
apply a rule to a case its exemptions cover. With the ID, you can open the
rule and decide in under a minute.

You say what the work is and, if it helps, where to look. The agent chooses
which rules to read. Here are three requests, each with the rules an agent
might cite on a typical draft.

**A campaign brief** that promises awareness, leans on a survey, and has a
clever tagline:

```text
Review this campaign brief against the heuristics canon.
```

```text
STRAT-20  B  goals section    lists targets, never names the obstacle   say what stands in the way
GTM-01    B  "demand" section survey says people would buy              get a paid pre-order first
GTM-05    S  media plan       press spend before a way to convert       build the path, then buy press
GTM-07    S  tagline          pun that needs explaining                 one feeling, said plainly
CLM-04    B  claims           "secure" and "compliant" as adjectives    say how, where, and what fails
```

**A launch plan** that shows only the path to a win and copies a rival's move:

```text
Check this launch plan against the canon. Focus on what could go wrong.
```

```text
STRAT-02  B  whole plan   no section on how it fails            write the failure case first
STRAT-05  S  rationale    "because the competitor just did it"  separate their reasons from ours
STRAT-28  S  tactics      no guess at how the rival responds    write their likely reaction
```

**A blog post** with the usual tells of machine-written prose:

```text
Edit this post with the canon's writing rules. Keep my argument.
```

```text
WRIT-30  S  27 em dashes                          vary the punctuation
WRIT-07  B  three "not X, it's Y" pivots          keep one
WRIT-05  S  "crucial, pivotal, evolving" cluster  one concrete claim
CLM-04   B  "secure" as a bare adjective          mechanism, location, failure
```

A good answer cites a handful of IDs, each beside a concrete line, and says
what changed and why. Twenty rules for a one-page brief means the agent read
too much. Ask it to keep only the rules whose trigger it can point to.

## What is inside

| Path | What it is |
|---|---|
| [lexicons/](lexicons/) | The rules: one file per domain, grouped by family, keyed by ID |
| [PRINCIPLES.md](PRINCIPLES.md) | Failures that rules from unrelated fields describe in different words |
| [reasoning/](reasoning/) | Reasoning cards: optional depth for one shared decision |
| [SOURCES.md](SOURCES.md) | The bibliography: every work a rule cites |
| [GRAPH.md](GRAPH.md) | A picture of how the lexicons refer to each other |
| [AGENTS.md](AGENTS.md) | The guide for tools: routing, phases, and retrieval |
| [NOTICE.md](NOTICE.md) | What is licensed, and on what terms |

The eleven lexicons cover accessibility; business and marketing; depiction
(what a description may claim about what it depicts); design; engineering;
epistemics (judgment under uncertainty); graph theory; interaction and UX;
ML systems; security; and writing. Within a lexicon, rules are grouped into
families with short prefixes, such as
[`RES`](lexicons/engineering.md#fam-res) for resilience or
[`WRIT`](lexicons/writing.md#fam-writ) for writing.

## Principles and reasoning cards

The one-line rule is the default. Two optional layers add depth when a
decision needs it.

- **Principles.** [PRINCIPLES.md](PRINCIPLES.md) records failures that rules
  from unrelated fields describe in different words. When a rule you applied
  appears there, the rules beside it are independent checks of the same
  failure, so a question about a database schema can draw on evidence about
  forms, contracts, or experiments. Treat them as a second opinion, not as
  extra citations.
- **Reasoning cards.** A card in [reasoning/](reasoning/) covers one decision
  that several rules share. It sets out the triggers, the failure, the action,
  the tensions, and how to verify the result. There are about thirty.

For any change that edits [PRINCIPLES.md](PRINCIPLES.md), use the canon's
`eval --compare <base> <head>` with the commits before and after the change,
then review its new asserted, prose-only, and wired pair counts.

## Licence and sources

The text of the rules, principles, and cards is licensed under CC BY 4.0, as
[NOTICE.md](NOTICE.md) explains. The licence does not cover the works listed
in [SOURCES.md](SOURCES.md); obtain those through ordinary legal channels.

Tools and integrators should read [AGENTS.md](AGENTS.md). It holds the routing
table and phase codes and, for teams that need a review to be repeatable,
explains how to pin a release and verify its digests.
