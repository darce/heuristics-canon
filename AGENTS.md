# Agent guide

This repository is a citation target, not a codebase. It holds decision rules, each a
falsifiable condition -> action claim with a stable ID, that you cite at the moment a
decision is made: `[RES-02]` on a blocking call with no timeout, `[A11Y-01]` on a color
change. Cite the ID instead of restating the advice.

## The contract

- IDs are the API. `[FAM-NN]` is immutable once assigned. A published ID only disappears
  in a MAJOR release; if a citation stops resolving after an upgrade, read the new
  [`meta/release-manifest.json`](meta/release-manifest.json) before assuming a typo.
- Tier tells you how hard a rule binds. `B`locker: correctness, data loss, or security
  if violated. `S`hould: strong default with named exemptions. `J`udgment: weigh in
  context. Judgment escalates rather than simplifies, so a lane without the context
  routes a J rule up instead of treating it as optional.
- Cite against a tag, not `main`. Rule text can change under the same ID in a PATCH
  release, so a citation pinned to a tag stays reproducible while `main` advances. Verify
  digests (below).
- Nothing here is editable. Rules are authored in a private research corpus and
  projected in; there is no tooling in this repo and pull requests are not taken. If a
  rule looks wrong, open an issue.

## Pin and verify

```sh
git fetch --tags && git checkout v0.1.0        # or the latest tag
shasum -a 256 lexicons/*.md                    # compare against meta/release-manifest.json
```

Fetching files without a checkout: take `meta/release-manifest.json` at the tag and
compare each lexicon's sha256 before using it. A mismatch means you do not have the
release you think you have. The manifest also carries the full rule-ID list, so "did the
ID contract change" is answerable offline.

## Retrieve rules

The lexicons are the payload; read them directly. Every rule is one table row starting
with its ID, so family retrieval is a text match:

```sh
grep '^| RES-' lexicons/engineering.md         # one family
grep -h '^| [A-Z]*-' lexicons/*.md | wc -l     # every rule
```

- The README's [routing table](README.md#routing-by-artifact) maps a changed artifact to
  the families to consult. Retrieve by artifact, not by loading everything.
- Phase codes are per-lexicon; the README's [phases legend](README.md#reading-a-rule)
  maps each code to a bucket (plan / write / review / ship).
- A rule's `Src` slug resolves in [`SOURCES.md`](SOURCES.md): what the source feeds and
  its rights posture. The distillation behind it is private; do not expect a file.

## Reading a row

```
| RES-02 | Connect/read/… with no timeout | **Timeout on every blocking call** — … | What bounds this wait? | B·w | release-it ch-5 |
```

Trigger (observable in a diff, plan, or metric) · Rule (the falsifiable claim) · Answers
(the one question to ask) · tier·phase · source. The Answers column is the cheapest
thing to inline in a review comment next to the ID.

## Deep-link a rule

Every rule row carries an anchor, so a citation can point at the exact rule, not the top
of a file: `lexicons/business-marketing.md#clm-05` opens the rendered table scrolled to
CLM-05. Use this in review comments and docs so a reader lands on the rule itself.

## Corroboration

When you cite a rule, [`PRINCIPLES.md`](PRINCIPLES.md) may hold its cross-domain
siblings: independent sources that reached the same mechanism. Citing `[PROD-09]` and
adding its principle's other arrivals (`[CLM-05]`, `[A11Y-22]`) is stronger than any one
of them.
