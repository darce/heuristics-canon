# Agent guide

This repository is a read-only citation target, not an instruction to load
1,000+ rules into every task. Retrieve only rules whose triggers match the
artifact being changed.

## Consumer contract

- IDs are the API. `[FAM-NN]` is immutable once published and disappears only
  in a breaking release.
- Pin a tag, not `main`, and verify lexicon and (when present) `reasoning/` /
  `sources/` SHA-256 values against
  [`meta/release-manifest.json`](meta/release-manifest.json)
  (`heuristics-canon/release@2`).
- Semver: removal of a published rule ID, reasoning card, or source note is
  breaking; addition is minor; same-path content change is patch.
- Tier controls force: `B` blocks, `S` is a strong default with named
  exemptions, and `J` requires context. A context-poor agent escalates a J rule
  rather than treating it as optional.
- Rules are evidence-backed defaults, not authority that overrides the task,
  observed facts, or a documented exemption.
- This projection is not edited directly. Open an issue for upstream review.

## Progressive retrieval ladder

Default depth is the rule row. Do not open the whole tree on every task.

```text
rule row  ->  reasoning card  ->  source note  ->  original source
 (lexicon)     (reasoning/)       (sources/)        (publisher copy)
```

1. **Rule row** (default). Route the artifact, keep rows whose triggers fire,
   read exemptions and tier. Cite `[FAM-NN]`.
2. **Reasoning card.** For every retained rule ID, open **every** mechanism
   card that lists that ID in its `## Rule IDs` section, **once each**, in
   deterministic ascending slug order. Do not stop at the first match. Current
   pilot overlaps (two cards each): `HAI-02`, `NDM-01`, `RLSE-07`, `SEC-05`,
   `SERVE-04`. A principle join is a reason to open, not a checklist to satisfy.
   Pilot open-when principle numbers (union of card sections): 3, 4, 7, 8,
   11–17, 19. Use [reasoning/README.md](reasoning/README.md) and each card's
   verification section. Cite rule IDs in the durable record, not the card slug
   alone.
3. **Source note.** Open only for citation audit of a `SOURCES.md` slug you
   already cite or dispute. See [sources/CONTRACT.md](sources/CONTRACT.md).
4. **Original source.** Last resort for primary text. Obtain the work through
   ordinary legal channels; this repo does not ship research copies.

A card without a firing trigger is inert. Notes do not replace reading the
source. Private distillations are intentionally absent.

## Apply rules under a context budget

1. Match the changed artifact to the README routing table.
2. Open only the listed family anchors. Filter by
   plan/write/review/ship phase when useful.
3. Keep a rule only when its Trigger is observable. Read the complete row,
   especially exemptions and tier. If the source is unwalkable or does not
   support the mechanism, report a corpus defect instead of invoking authority.
4. If `PRINCIPLES.md` cites the rule, retrieve its siblings
   from unrelated domains. They are mechanism checks, not votes.
5. Partition opposed rules by surface, object, or sequence. If no
   partition works, record a contextual judgment; do not average the rules.
   Keep both rules when they inspect the same failure upstream and downstream.
6. For each retained rule ID, open every reasoning card that lists it, once
   each, in ascending slug order; apply each card's verification. Principle
   membership joins related IDs; it is not a gate that must be fully checked.
7. Cite the applied IDs beside the decision and name the evidence.
8. Stop retrieval when every applicable blocker and strong default is
   satisfied, exempted with evidence, or explicitly escalated.

Do not open all ten lexicons for a single change. Do not cite rules whose
triggers did not fire. Citation count is not review quality.

## Retrieve rules

Every rule is one Markdown table row. The README maps artifacts to families:

```sh
grep '^| RES-' lexicons/engineering.md
grep -h '^| [A-Z][A-Z0-9]*-' lexicons/*.md | wc -l
```

Phase codes are per lexicon; use the README's phase buckets unless you mean one
lexicon's code. A `Src` slug resolves in [SOURCES.md](SOURCES.md). Private
distillations are intentionally absent.

## Read and cite a row

```text
| RES-02 | blocking call with no timeout | Timeout every blocking call … | What bounds this wait? | B·w | release-it ch-5 |
```

The columns are ID, Trigger, Rule, Answers, tier/phase, and source. Cite
`[RES-02]`; deep-link `lexicons/engineering.md#res-02` when the reader needs the
row. The Answers cell is the cheapest useful inline review prompt.

## Use principles without flattening them

`PRINCIPLES.md` maps a fired rule to independent cross-domain arrivals. Use the
siblings to look for the same mechanism in a different material, not to inflate
the citation count. When rules disagree, use the document's surface, object,
and sequence partitions. When they watch the same failure at different stages,
apply both.

## Pin and verify

```sh
git fetch --tags
git checkout <version-tag>
shasum -a 256 lexicons/*.md
find reasoning sources -type f 2>/dev/null | sort | xargs shasum -a 256
```

Compare the output with `meta/release-manifest.json` (schema
`heuristics-canon/release@2`). The manifest carries the full rule-ID set and
per-file digests for lexicons, reasoning cards, and source notes, so contract
drift is checkable offline.

## Operator gate (structural only)

Before cutting a public release from the private corpus, run the reasoning-layer
structural check (not wired into `tools/publish.py`; operator-owned preflight):

```sh
python3 tools/eval_reasoning.py --check-public --json
```

A green status means fixtures and mechanism cards are structurally sound (and,
when the live lexicon index loads, every card Rule ID resolves). It is **not**
evidence that cards improve decision quality. Arm utility needs offline scored
responses and `compare`.
