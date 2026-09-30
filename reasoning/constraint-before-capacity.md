# Name the limiting stage before adding capacity

Slug: `constraint-before-capacity`
ID: `CARD-33`
Mechanism claim: Throughput of a chain is set by its limiting stage, so improving any other stage, or adding capacity in general, does not raise it and can raise queues.

## Scope

Covers: a proposal to parallelize, scale out, buy hardware, fill utilization, or add a standing gate or manual sign-off in order to raise throughput or cut delay, when the path is a chain of stages.

Excludes: geography and per-hop latency floors ([PERF-09](../lexicons/engineering.md#perf-09)); percentiles as the reporting form ([PERF-01](../lexicons/engineering.md#perf-01)); job order on one already-named worker ([PERF-11](../lexicons/engineering.md#perf-11) stays in force once the stage is named); timeouts and pending-work bounds ([feedback-bounded-waiting](feedback-bounded-waiting.md)); whether a service split is actually independent ([REF-14](../lexicons/engineering.md#ref-14)); end-to-end tests as the whole verification strategy ([TEST-10](../lexicons/engineering.md#test-10)).

## Observable triggers

- A plan proposes more parallelism, replicas, hardware, or a scale-out, and no stage is named as the limit.
- A capacity or autoscale target aims at near-full average utilization with no per-stage queue reading.
- A latency fix starts without saying whether propagation, transmission, processing, or queuing dominates.
- A standing QA or DevOps gate, or a manual release sign-off, is added on the delivery path.
- Spend continues on a link that is not the limit while the chain still misses its throughput.

## Causal mechanism

A chain's completed throughput equals the throughput of its slowest stage. Work added upstream of that stage waits. Work sped up downstream has nothing extra to take. Capacity that is not on the limiting stage therefore does not raise completed throughput, and the extra arrivals show up as queue. Order is part of the mechanism: measure which stage limits, use the capacity that stage already has, hold every other stage to what that stage can absorb, and only then add capacity there. After the add, the limit moves, so the same order starts again.

## Required action

While a proposal would add parallelism, hardware, scale-out, fuller utilization, or a gate in order to raise throughput, do these in order:

1. Identify the constraint by measurement. Record queue length, utilization of each stage, and which delay component dominates.
2. Exploit the constraint. Remove waste on it, keep it fed, and protect it with a small ready buffer.
3. Subordinate everything else. Limit work in progress and intake to what the constraint can absorb. A numeric cap that does not change flow is not this step.
4. Elevate the constraint, and only now. Add capacity at the named stage after steps 1 to 3.
5. Return to step 1. The constraint moves.

## Predicted failure

Parallelism, hardware, and extra gates land on stages that were not the limit. Completed throughput stays flat. Queues grow in front of the unnamed stage. The next plan buys more of the same, because the first add did not move the number, and lead time rises with the queue.

## Worked example

A release review sees a green build followed by a manual sign-off, and the latency plan asks for more compile workers plus a second cluster. Stage timings show compile and test mostly idle, the sign-off queue holds every change, and the deploy queue is near empty. Name the sign-off as the limiting stage. Remove avoidable approvers, keep a small pile of already-tested builds ready for the people who still must sign, and stop starting features that sign-off cannot clear. Only if that stage is still the limit after the waste is gone, add review capacity. If the next measurement shows deploy is now the long queue, repeat on deploy instead of hiring more reviewers. Without that order the team buys compile workers, the sign-off queue lengthens, and lead time does not fall.

## Exemptions and boundaries

- Does not apply when no stage holds a continuing queue and improving any stage raises completed throughput.
- A geography or hop-count floor ([PERF-09](../lexicons/engineering.md#perf-09)) is not a stage to elevate.
- Timeouts, shed load, and pending-work bounds stay with [feedback-bounded-waiting](feedback-bounded-waiting.md). This card does not restate those bounds.
- [RLSE-12](../lexicons/engineering.md#rlse-12) still requires that green mean deployable. This card only orders the extra manual gate against the limiting stage.
- A one-off blocked item is an issue, not proof of a capacity constraint.
- Shared-pool capacity, where adding capacity on any drawing stage moves the total, is a disconfirmer below, not a reason to skip measurement.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| sequence | [STRAT-22](../lexicons/business-marketing.md#strat-22) identify the limiting link and fund it before other spends | [COST-06](../lexicons/ml-systems.md#cost-06), [ARCH-09](../lexicons/engineering.md#arch-09), and [PERF-04](../lexicons/engineering.md#perf-04) buy hardware, scale out, or parallelize when that is the real lever | Name, exploit, and subordinate first; the capacity rules stay fully right only as the elevate step |
| object | [OPS-27](../lexicons/business-marketing.md#ops-27) keep a small ready buffer in front of the scarce stage | [PERF-13](../lexicons/engineering.md#perf-13) operate left of saturation so queuing delay does not dominate | The buffer belongs only at the constraint; headroom remains the operating point everywhere else |
| surface | [TEAM-06](../lexicons/engineering.md#team-06) and [RLSE-12](../lexicons/engineering.md#rlse-12) a standing gate or manual sign-off on the delivery path | [PERF-16](../lexicons/engineering.md#perf-16) name which delay component dominates a request path | A hand-off queue and a propagation or processing delay are different surfaces; name the limit on the surface about to change |
| object | [PERF-11](../lexicons/engineering.md#perf-11) order jobs on a shared worker by the declared objective | [STRAT-22](../lexicons/business-marketing.md#strat-22) the chain limit may be a different stage than that worker | Apply the sort only at the stage already identified; a local order does not replace the chain limit |

## Disconfirmers

- Queue length and utilization stay even across stages, and improving a stage that is not the busiest raises end-to-end throughput by about as much as improving the busiest stage. The chain has no persistent constraint.
- Capacity is shared across stages, and adding it at any stage that draws on the pool raises completed throughput even when no single stage queue dominates. Stage-level improvement moves the total.
- One blocked item clears when its issue is fixed, and that stage's queue does not reform. There was no continuing constraint.

## Verification

- The plan names one limiting stage and the measurement used: queue length, per-stage utilization, or the dominant delay component.
- Waste removed at that stage, and a ready buffer where upstream can stall it, are recorded before any capacity purchase.
- Intake or work in progress is capped to what that stage completes.
- Any capacity add is on the named stage and is dated after the exploit and subordinate steps.
- A follow-up measurement is scheduled, because the constraint can move.

## Rule IDs

- [PERF-04](../lexicons/engineering.md#perf-04): parallelism for a fixed workload, after the limiting stage is named
- [PERF-06](../lexicons/engineering.md#perf-06): measure before calling a hotspot the constraint
- [PERF-13](../lexicons/engineering.md#perf-13): headroom against saturation, distinct from the constraint's ready buffer
- [PERF-16](../lexicons/engineering.md#perf-16): name the dominant delay component before speeding a path
- [COST-03](../lexicons/ml-systems.md#cost-03): read queue and saturation before a spend decision
- [COST-05](../lexicons/ml-systems.md#cost-05): size to the knee only after the limiting stage is known
- [COST-06](../lexicons/ml-systems.md#cost-06): remove work and name the limit before buying hardware
- [ARCH-08](../lexicons/engineering.md#arch-08): do not add a stack until a stated scale limit forces it
- [ARCH-09](../lexicons/engineering.md#arch-09): quantify load, then still name the limiting stage before scale-out
- [TEAM-06](../lexicons/engineering.md#team-06): a standing hand-off gate is not capacity
- [RLSE-12](../lexicons/engineering.md#rlse-12): a manual sign-off after green is a stage, not proof the pipeline is the limit
- [STRAT-22](../lexicons/business-marketing.md#strat-22): fund the limiting link first
- [OPS-27](../lexicons/business-marketing.md#ops-27): small ready buffer in front of the scarce stage
- [PERF-11](../lexicons/engineering.md#perf-11): order work at an identified shared worker, not instead of naming the stage

## Principles

No exclusive principle claim. This decision sequences a capacity add behind a measured limiting stage. It does not own a numbered entry in PRINCIPLES.md.

## Evidence / source slugs

- [`good-strategy-bad-strategy`](../SOURCES.md#src-good-strategy-bad-strategy): supports [STRAT-22](../lexicons/business-marketing.md#strat-22)
- [`pinedo-scheduling`](../SOURCES.md#src-pinedo-scheduling): supports [OPS-27](../lexicons/business-marketing.md#ops-27), [PERF-11](../lexicons/engineering.md#perf-11)
- [`latency-reduce-delay-in-software-systems`](../SOURCES.md#src-latency-reduce-delay-in-software-systems): supports [PERF-04](../lexicons/engineering.md#perf-04), [PERF-13](../lexicons/engineering.md#perf-13), [PERF-16](../lexicons/engineering.md#perf-16)
- [`philosophy-of-software-design`](../SOURCES.md#src-philosophy-of-software-design): supports [PERF-06](../lexicons/engineering.md#perf-06)
- [`systems-performance-gregg`](../SOURCES.md#src-systems-performance-gregg): supports [COST-03](../lexicons/ml-systems.md#cost-03), [COST-05](../lexicons/ml-systems.md#cost-05), [COST-06](../lexicons/ml-systems.md#cost-06)
- [`observability-engineering`](../SOURCES.md#src-observability-engineering): supports [ARCH-08](../lexicons/engineering.md#arch-08)
- [`designing-data-intensive-applications`](../SOURCES.md#src-designing-data-intensive-applications): supports [ARCH-08](../lexicons/engineering.md#arch-08), [ARCH-09](../lexicons/engineering.md#arch-09)
- [`team-topologies`](../SOURCES.md#src-team-topologies): supports [TEAM-06](../lexicons/engineering.md#team-06)
- [`modern-software-engineering`](../SOURCES.md#src-modern-software-engineering): supports [RLSE-12](../lexicons/engineering.md#rlse-12)

## Non-claims

This card does not reconstruct any source's structure, tour its chapters, or claim to hold every important idea in its domain. Short phrases in Required action anchor the ordered steps to the mechanism records; they are not a substitute for the works. For bibliography identity, open [SOURCES.md](../SOURCES.md). For the full rule row, open the lexicon. SOURCES.md is not a substitute for the original work.
