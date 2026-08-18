# Heuristics canon

A library of short, checkable rules for building and shipping software, in
eleven domains from engineering and security to writing and judgment under
uncertainty. The rules are distilled from books, papers, and standards, and
every rule points at the work it came from (a small number, under thirty of
some 1,200, are labelled unsourced practice in the bibliography and are still
waiting for one).

Each rule is one line. It names a situation you can see (the trigger), says
what to do about it (the rule), and gives you the one question to ask at that
moment. Every rule has a permanent ID such as `RES-02`, so a person or a tool
can cite it in a review, a plan, or a commit message without restating the
argument. Two fields often describe the same failure in different words;
[PRINCIPLES.md](PRINCIPLES.md) records those meeting points, so a question
about a database schema can surface evidence written about forms, contracts,
or experiments.

## A one-minute example

You are reviewing a change that adds an HTTP client. Nothing sets a timeout.
That is a trigger you can see in the diff. The engineering lexicon has
[RES-02](lexicons/engineering.md#res-02), **timeout on every blocking call**,
tier B, which means it blocks the change until it is handled or explicitly
exempted. You set the timeout, write `[RES-02]` in the review, and move on.

If the same change also widens what the code is allowed to touch, a
[reasoning card](reasoning/) such as
[least-privilege-blast-radius](reasoning/least-privilege-blast-radius.md)
walks through the whole decision across several related rules. Cards are
optional depth. The one-line rule is the default.

## Ask an agent to use it

The canon is written for tools as much as for people. Point an agent (Claude
Code, Claude Cowork, Codex, or any assistant that can read a repository) at
this repo. The agent decides which lexicons, principles, and cards apply; you
tell it what changed and, when it helps, where to look. Set it up once:

```text
Clone https://github.com/darce/heuristics-canon next to this project and
read its AGENTS.md. Apply the canon whenever I ask you to review, plan,
or write, and cite the rule IDs you used.
```

Then ask in plain words. Three examples, each with the rules an agent would
find in a typical case.

Review a change:

```text
Review this diff against the heuristics canon.
```

The diff adds an HTTP call with a retry loop and a new index. What fires:

```text
RES-02  B  client.py:41   http.get() has no timeout        set one
RES-01  B  client.py:47   POST retried, not idempotent     add an idempotency key
API-08  S  client.py:44   fixed 1s retry, no ceiling       backoff, ~3 attempts, 5xx only
STOR-01 S  0007_orders.sql new index on a write-hot table  name the query it serves
```

Check a plan, steering the agent to one area:

```text
Check this migration plan against the canon. Focus on data and rollout.
```

The plan renames a column in place and has a runbook. What fires:

```text
DATA-04  S  step 2   rename in place under no-downtime     expand, migrate, contract
STOR-01  S  step 3   adds an index, no query named          cite the query or drop it
RLSE-11  S  step 5   manual click-path runbook, run weekly  script it
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

Good output looks like this: a handful of IDs beside concrete lines, each with
what to do. An answer that cites twenty rules for a ten-line change has read
too much; ask it to keep only the rules whose trigger it can point at.

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
verify, for one mechanism. Cards cover a few dozen hot decisions.
[SOURCES.md](SOURCES.md) lists the works behind the rules; obtain the originals
through ordinary legal channels.

## Rights and where the technical detail lives

The rule, principle, and card prose is offered under CC BY 4.0, as stated in
[NOTICE.md](NOTICE.md). That grant does not cover the third-party works listed
in SOURCES.md.

Everything a tool or an integrator needs, including the routing table and
phase codes, is in [AGENTS.md](AGENTS.md). In the published repository that
file also explains how to pin a release and verify digests.
