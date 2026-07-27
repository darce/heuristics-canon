# Fail loudly, succeed quietly

Slug: `fail-loudly-succeed-quietly`
Mechanism claim: Design the success and failure channels so failure is
impossible to miss and success is impossible to confuse with noise.

## Scope

Covers: telemetry and alert channels where silence must not read as health;
ERROR and page severity that imply operator action; program I/O where stdout is
data and diagnostics stay on the human-only channel.

Excludes: timeouts and queue bounds that make stalls detectable at all (see
`feedback-bounded-waiting`); plan and rollout step size (see
`step-size-by-feedback`); pure measurement-frame integrity (see
`measurement-integrity`); correction reaching source of truth (see
`correction-at-source`).

## Observable triggers

- Dashboards treat silence as health; dead instrumentation does not break.
- ERROR lines or pages do not mean on-call action; false positives train ignore.
- A program whose stdout is piped or parsed prints banners, progress, or
  diagnostics on the success path.

## Causal mechanism

Operators and parsers treat a channel as a sensor. A sensor that stays quiet
when broken reports health by absence. A sensor that chatters on every success
trains readers to ignore it. Keep rare, actionable failure signals on the loud
path, and keep success quiet on the data path so neither people nor machines
confuse decoration for payload.

## Required action

1. Treat silence as a failure class for instrumented paths; dead capture must
   break loudly ([OBS-08](../lexicons/engineering.md#obs-08), Principle 16).
2. Reserve ERROR and pages for conditions that require operator action
   ([OBS-04](../lexicons/engineering.md#obs-04)).
3. Keep success quiet on the data path; send diagnostics and progress to the
   human-only channel ([AGT-15](../lexicons/engineering.md#agt-15)).
4. Never swallow exceptions without a named policy — empty catch blocks are
   silent lies ([REF-37](../lexicons/engineering.md#ref-37)).

## Predicted failure

On-call staff ignore alerts; silent dashboards hide dead instrumentation.
Pipelines mis-parse banners as payload when success chatters on stdout.
Real failures arrive too late because the loud channel already trained
everyone to look away.

## Exemptions and boundaries

- In-process debug noise on a developer machine is fine; the card fires when
  a production consumer, parser, or on-call path can confuse chatter with
  payload or health.
- A deliberate quiet success channel still needs a separate dead-man's path
  for capture health (Principle 16 via [OBS-08](../lexicons/engineering.md#obs-08)).
- Bounding the wait so a failure can occur at all is owned by
  `feedback-bounded-waiting`; this card owns where that failure is reported.
- Step size of plans and rollouts is owned by `step-size-by-feedback`
  (Principle 19); plain pointer only.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| object | [OBS-08](../lexicons/engineering.md#obs-08) silence is not success | [OBS-04](../lexicons/engineering.md#obs-04) ERROR means action | make dead capture loud; keep the loud channel scarce so it stays trusted |
| surface | [AGT-15](../lexicons/engineering.md#agt-15) stdout is data | human-facing progress and diagnostics | same split: payload channel stays quiet; human channel carries the story |

## Disconfirmers

- On-call drill: silence produces a dead-man's alert; ERROR always has an owner.
- Piped or parsed success path stays undecorated under a banner-injection test.
- Reducing false ERROR volume improves response time to real pages (channel
  trust was the bottleneck).

## Verification

- Alert policy: ERROR implies runbook; absence of telemetry is itself an alert.
- Piped or parsed success path is undecorated data; diagnostics go to stderr
  (or the equivalent human-only channel).
- Freshness or heartbeat gate exists for each critical instrumented stream.

## Rule IDs

- [OBS-08](../lexicons/engineering.md#obs-08): silence is not success
- [OBS-04](../lexicons/engineering.md#obs-04): ERROR means action
- [AGT-15](../lexicons/engineering.md#agt-15): stdout is data, stderr is for humans
- [REF-37](../lexicons/engineering.md#ref-37): no empty exception blocks
- [RLSE-05](../lexicons/engineering.md#rlse-05): silent failure is the worst failure

## Principles

- 16. Fail loudly, succeed quietly

## Evidence / source slugs

- [`observability-engineering`](../SOURCES.md#src-observability-engineering): supports [OBS-08](../lexicons/engineering.md#obs-08)
- [`release-it`](../SOURCES.md#src-release-it): supports [OBS-04](../lexicons/engineering.md#obs-04)
- [`art-of-unix-programming`](../SOURCES.md#src-art-of-unix-programming): supports [AGT-15](../lexicons/engineering.md#agt-15)
- [`unix-programming-environment`](../SOURCES.md#src-unix-programming-environment): supports [AGT-15](../lexicons/engineering.md#agt-15)
- [`clean-code-cookbook`](../SOURCES.md#src-clean-code-cookbook): supports [REF-37](../lexicons/engineering.md#ref-37)
- [`product-deploy-agents-fields`](../SOURCES.md#src-product-deploy-agents-fields): supports [RLSE-05](../lexicons/engineering.md#rlse-05)

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to cover every alerting or CLI convention. It is a decision aid over existing
rule IDs. [SOURCES.md](../SOURCES.md) is a bibliography registry, not a substitute
for the original works.
