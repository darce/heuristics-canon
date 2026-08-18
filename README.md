# Heuristics canon

A library of short, checkable rules for software work and the writing,
marketing, and decisions around it, in eleven domains including engineering,
security, business, writing, and judgment under uncertainty. The rules are
distilled from books, papers, and standards, and each one points at the work
it came from. Twenty-eight of some 1,200 are labelled unsourced practice in
the bibliography and are still waiting for a source.

Each rule is one line. It names a situation you can see (the trigger), says
what to do about it (the rule), and gives you the one question to ask at that
moment. Every rule has a permanent ID such as `RES-02`, so a person or a tool
can cite it in a review, a plan, or a commit message without restating the
argument. Two fields often describe the same failure in different words;
[PRINCIPLES.md](PRINCIPLES.md) records those meeting points, so a question
about a database schema can surface evidence written about forms, contracts,
or experiments.

## A one-minute example

You are reading a marketing brief before it goes to an agency. It says the
campaign will "build awareness", the tagline is a pun that needs a footnote,
and the proof of demand is a survey where people said they would buy. Each of
those is a trigger you can see on the page. The business lexicon has
[GTM-01](lexicons/business-marketing.md#gtm-01), **ask them to buy**, tier B:
stated intent is not demand, so the brief cannot go out until there is paid
intent or an explicit exemption. You write `[GTM-01]` in the margin, ask for a
pre-order or a paid pilot, and move on to the next line.

If several rules that fired share one decision, a [reasoning card](reasoning/)
walks through the whole decision. Cards are optional depth. The one-line rule
is the default.

## Ask an agent to use it

The canon is written for tools as much as for people. Any assistant that can
read a web page or a repository (Claude Code, Claude Cowork, Codex, or another)
can use it. Nothing needs installing. Tell it once:

```text
Read the heuristics canon at https://github.com/darce/heuristics-canon,
starting with AGENTS.md. Whenever I ask you to review, plan, or write,
apply the canon and cite the rule IDs you used.
```

If your tool reads local files but not web pages, clone the repository next
to your project and point the agent at that instead.

When you then ask for a review, this is the exchange:

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

The list is what makes this checkable. An agent can miss a trigger, or apply
a rule to a case the rule's own exemptions cover; the ID lets you open the
rule and decide in under a minute. The agent picks which rules to read. You
say what the thing is and, if it helps, where to look. Three examples in plain
words, each with rules an agent might find in a typical case.

Review a marketing brief:

```text
Review this campaign brief against the heuristics canon.
```

The brief promises awareness, leans on a survey, and has a clever tagline.
What fires:

```text
STRAT-20  B  goals section    lists targets, never names the obstacle   say what stands in the way
GTM-01    B  "demand" section survey says people would buy              get a paid pre-order first
GTM-05    S  media plan       press spend before a way to convert       build the path, then buy press
GTM-07    S  tagline          pun that needs explaining                 one feeling, said plainly
CLM-04    B  claims           "secure" and "compliant" as adjectives    say how, where, and what fails
```

Check a launch plan, steering the agent to one area:

```text
Check this launch plan against the canon. Focus on what could go wrong.
```

The plan shows only the path to a win and copies a rival's move. What fires:

```text
STRAT-02  B  whole plan   no section on how it fails            write the failure case first
STRAT-05  S  rationale    "because the competitor just did it"  separate their reasons from ours
STRAT-28  S  tactics      no guess at how the rival responds    write their likely reaction
```

Edit prose:

```text
Edit this post with the canon's writing rules. Keep my argument.
```

What fires on a draft with the usual tells:

```text
WRIT-30  S  27 em dashes                          vary the punctuation
WRIT-07  B  three "not X, it's Y" pivots          keep one
WRIT-05  S  "crucial, pivotal, evolving" cluster  one concrete claim
CLM-04   B  "secure" as a bare adjective          mechanism, location, failure
```

Good output looks like this: a handful of IDs beside concrete lines, each
with what changed and why. An answer that cites twenty rules for a one-page
brief has read too much; ask it to keep only the rules whose trigger it can
point at.

## What is inside

| Path | What it is |
|---|---|
| [lexicons/](lexicons/) | The rules, one file per domain, grouped by family, keyed by ID |
| [PRINCIPLES.md](PRINCIPLES.md) | Cross-domain mechanisms that join rules from unrelated sources |
| [reasoning/](reasoning/) | Mechanism cards: optional decision depth above the one-line rule |
| [SOURCES.md](SOURCES.md) | The bibliography: every work a rule cites |
| [GRAPH.md](GRAPH.md) | A picture of how the lexicons reference each other |
| [AGENTS.md](AGENTS.md) | The contract for tools: routing, phases, retrieval |
| [NOTICE.md](NOTICE.md) | What is licensed and what never ships |

The eleven lexicons cover engineering, security, business and marketing,
design, writing, depiction (what a description may claim about what it
depicts), accessibility, graph theory, interaction and UX, ML systems, and
epistemics (judgment under uncertainty). Reading by hand works too: each
lexicon is a Markdown table grouped into families with short prefixes such as
[`RES`](lexicons/engineering.md#fam-res) (resilience) or
[`WRIT`](lexicons/writing.md#fam-writ) (writing).

## Reading a rule

```text
| RES-02 | Connect/read/pool-checkout/HTTP client with no timeout | Timeout on every blocking call ... | What bounds this wait? | B·w | release-it ch-5 |
```

The columns are the ID, the trigger, the rule, the question it answers, the
tier and phase, and the source. The ID is permanent and anchors as `#res-02`.
The tier says how hard the rule is: B blocks until it is handled or explicitly
exempted, S is a strong default with named exemptions, J needs your judgment.
Rules are evidence-backed defaults, not an authority that overrides your
judgment, the facts in front of you, or a documented exemption. The phase
letter says when in the work the rule tends to bite; the source resolves in
[SOURCES.md](SOURCES.md).

## Principles and cards

A principle answers "this failure has the same shape in another field". When a
rule that fired appears in [PRINCIPLES.md](PRINCIPLES.md), the rules listed
beside it are independent checks of the same mechanism from other domains.
Read them as a second opinion, not as extra citations.

A reasoning card answers "several rules that fired share one decision". A card
rebuilds the triggers, the failure, the action, the tensions, and how to
verify, for one mechanism. There are about thirty cards.
[SOURCES.md](SOURCES.md) lists the works behind the rules; obtain the originals
through ordinary legal channels.

## Rights and where the technical detail lives

The rule, principle, and card prose is offered under CC BY 4.0, as stated in
[NOTICE.md](NOTICE.md). That grant does not cover the third-party works listed
in SOURCES.md.

Everything a tool or an integrator needs, including the routing table and
phase codes, is in [AGENTS.md](AGENTS.md). In the published repository that
file also explains how to pin a release and verify digests, for teams that
need a review to be repeatable rather than current.
