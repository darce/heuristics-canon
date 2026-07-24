# Public reasoning layer

Progressive retrieval for agents and humans. Start narrow; open more only when
the decision is still under-specified. The same ladder is linked from the
repository [README](../README.md#progressive-retrieval-ladder) and
[AGENTS.md](../AGENTS.md#progressive-retrieval-ladder).

## Retrieval ladder

```text
rule row  ->  reasoning card  ->  source note  ->  original source
 (lexicon)     (this tree)       (../sources)       (publisher copy)
```

1. **Rule row.** Match the changed artifact, keep rows whose triggers fire, read
   tier and exemptions. Cite `[FAM-NN]`. This is the default depth.
2. **Reasoning card.** For each retained rule ID, open **every** card whose
   `## Rule IDs` section lists that ID, **once each**, in deterministic
   ascending slug order. Do not keep only the first match. Cards rebuild the
   *decision*: triggers, action, failure, tensions, verification. Current pilot
   overlaps (two cards each): `HAI-02`, `NDM-01`, `RLSE-07`, `SEC-05`,
   `SERVE-04`.
3. **Source note.** Open only for citation audit: how hard a `SOURCES.md` slug
   works for the rules that cite it. Notes give support / partial / not-found
   verdicts, not book reports.
4. **Original source.** Last. Only when the note or dispute requires primary
   text. Obtain the work through ordinary legal channels. The public repo never
   ships research copies or chapter condensations.

Private `distilled/` is the authoring argument behind many rows. It does not
publish. If a card ever reads like a chapter tour, it is a defect: rewrite as
mechanism or delete.

## What ships here

| Path | Role |
|---|---|
| [CONTRACT.md](CONTRACT.md) | Card schema, anti-reconstruction rules, template |
| [measurement-integrity.md](measurement-integrity.md) | Pilot card: honest meters and unshaped frames |
| [reversibility-blast-radius.md](reversibility-blast-radius.md) | Pilot card: cheap safe side; small compromise radius |
| [feedback-bounded-waiting.md](feedback-bounded-waiting.md) | Pilot card: timeouts, step size, correction loops |
| [../sources/CONTRACT.md](../sources/CONTRACT.md) | Critical note schema |
| [../sources/](../sources/) | Pilot notes keyed by source slug |

## How to use a card in a session

1. Route and select rules as in the root agent contract.
2. Open every card that lists any retained rule ID (once each, ascending slug
   order). A principle is a *join* across domains, not a checklist: when a
   retained ID sits under the pilot open-when set (Principles **3, 4, 7, 8,
   11–17, 19**, the union of the three pilot cards' Principles sections), that
   is one reason to open; matching a pilot theme is another. Never require the
   whole principle set before opening.
3. Apply each card's required action and verification; cite rule IDs, not the
   card slug alone, in the durable decision record.
4. Partition tensions; do not average opposed rules.
5. Stop when blockers and strong defaults are satisfied, exempted with
   evidence, or escalated.

Cards do not replace rows. A card without a firing trigger is inert.

## Operator gate (structural only)

Upstream release preflight (private corpus; not part of `tools/publish.py`):

```sh
python3 tools/eval_reasoning.py --check-public --json
```

Structural fitness of fixtures and cards only. Not proof that cards improve
reasoning.

## How to use a source note

1. Open a note only for slugs you already cite or dispute.
2. Read the narrow question and the verdict table for your rule IDs.
3. Treat `partial` and `not-found` as corpus risk: re-ground upstream, do not
   paper over with prestige.
4. Never paste private distillation text into public notes.

## Authoring constraints (summary)

- Existing rule IDs, principle numbers, and source slugs only.
- No quotations, no chapter-order walkthroughs, no "complete guide" claims.
- Criticism over summary in `public/sources/`.
- `WRIT` discipline on prose (sparse markup, few em dashes, plain diction).

## Pilots only

Three cards and two notes are pilots for the progressive layer. They are not
coverage of the whole canon. Prefer depth on hot mechanisms over a thin card
per principle.
