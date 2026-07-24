# Source note: `designing-data-intensive-applications`

## Identity

- Slug: `designing-data-intensive-applications`
- Citation: Martin Kleppmann. *Designing Data-Intensive Applications: The Big
  Ideas Behind Reliable, Scalable, and Maintainable Systems*. 1st ed., O'Reilly,
  2017.
- Canon registry: [SOURCES.md](../SOURCES.md#src-designing-data-intensive-applications)

## Rights posture

> This note identifies a third-party work for citation and evidence
> calibration. The work remains the property of its authors and publishers.
> Citation is not a license to reproduce expression. The private corpus may
> hold research copies under its own `NOTICE.md`; those copies and any
> chapter-level distillations do not ship in the public projection. This note
> makes no determination about fair use, secondary liability, or downstream
> redistribution rights.

## Narrow question

For the engineering rules most used by the reversibility and feedback cards
(isolation, idempotent writes, dual-write avoidance, stream completeness), does
this work support the mechanism at the cited chapter anchors, and where is the
canon packing engineering policy on top of the book's explanations?

## Verdicts

Focus set only: rules that feed the pilot reasoning cards. The slug feeds many
more DATA/STOR/FLOW rows; absence from this table is not a not-found verdict.

| Rule | Verdict | Pointer | Note |
|---|---|---|---|
| [DATA-17] | support | ch-7 | Isolation level names are not portable guarantees; engines differ in anomalies |
| [DATA-18] | support | ch-7 | Snapshot isolation leaves check-then-act races; integrity needs stronger handling or redesign |
| [DATA-19] | support | ch-7 | Multi-row reads need a consistent snapshot when the invariant spans rows |
| [DATA-20] | partial | ch-7 | Serializability tradeoffs discussed; "contention bet" framing is canon operationalization |
| [DATA-13] | support | ch-12 | End-to-end idempotency and request identity for safe retries |
| [DATA-14] | support | ch-11 | Dual writes as integrity hazard; single source / log-centric repair paths |
| [FLOW-06] | support | ch-11 | Derived stores rebuilt from log/snapshot; patching rows that skip the log fails |
| [FLOW-08] | support | ch-11 | Stream windows and late data require an explicit completeness policy |
| [RES-01] | support | ch-8 | Retries without idempotency amplify damage |
| [DATA-01] | support | ch-5 | Consistency expectations must be stated, not assumed from vendor labels |
| [DATA-10] | support | ch-5 | Durability and loss tolerance are explicit product choices |

## Limitations and obsolescence

- First edition (2017). Core concurrency and log-centric arguments remain
  durable; specific system examples and default isolation of named products
  drift. Always re-check the engine you run.
- The book teaches distributed data systems. It is not a primary source for LLM
  human-gates, least-privilege SQL grants, or accessibility claim language even
  when those share Principle 3.
- Chapter anchors above match canon `Src` cells. Other printings or
  translations may shift pagination; chapter identity is the stable pointer.
- Depth on consensus and transactions is explanatory. Production defaults still
  need engine-specific anomaly tests ([DATA-17] action), which the canon states
  more imperatively than a textbook chapter.

## Conflicts

- Against "eventual consistency is always fine": [DATA-17] and [DATA-18] force
  an invariant-by-invariant choice; Principle 3 prices weak isolation as the
  underpriced irreversible option when integrity matters.
- Against dual-write convenience in microservices: [DATA-14] and [FLOW-06]
  oppose hand-patched derived stores; some operational runbooks still do
  emergency patches, which must be followed by rebuild from source.
- Against unbounded agent retries: [RES-01] plus [RES-02] (from `release-it`)
  are an amplification pair: idempotency without timeouts still hangs; timeouts
  without idempotency still corrupt.
- Against treating the book as a complete reliability program: release rollback
  ([RLSE-08]) and human side-effect gates ([SEC-05]) are other economies.

## Canon consequences

- Keep DATA-17/18/13/14 and FLOW-06/08 pointed here; they are load-bearing for
  `reversibility-blast-radius` and parts of `feedback-bounded-waiting`.
- When packaging rules, preserve mechanism fidelity: "isolation names are not
  guarantees" must not harden into a false claim that a named engine always
  exhibits a specific anomaly.
- Re-ground any row whose `Src` claims a chapter that a future audit marks
  not-found; do not leave textbook prestige as authority.
- Do not expand this note into a full 40-rule digest; add rows only when a
  card or dispute needs them.

## Cannot answer

- License or fair-use status for diagrams, long paraphrase, or course packs.
- A chapter-by-chapter teaching outline (deliberately refused).
- Whether your specific database's default isolation matches any 2017-era
  example; measure the engine.
- Network or SRE timeout policy ([RES-02] lives primarily on `release-it`).
- Security dual-control and TCB sizing (Anderson and related slugs).
- Private distillation chapter maps or extraction hashes.
