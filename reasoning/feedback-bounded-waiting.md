# Feedback and bounded waiting

Slug: `feedback-bounded-waiting`
Mechanism claim: Bound every wait and every step by the feedback that can catch
failure before the next commitment; silence is not success.

## Scope

Covers: timeouts and queue bounds; agent and automation loops; rollout step
size; delayed labels and feedback-loop training; human correction paths;
validity of expert recognition under time pressure; logging and alert channels
that must surface error.

Excludes: pure measurement-frame integrity (see `measurement-integrity`); pure
privilege sizing (see `reversibility-blast-radius`) except where unbounded
autonomy *is* the blast radius; long-horizon strategy without an operational
loop (still needs forecasts with resolution criteria, not this card alone).

## Observable triggers

- Connect, read, pool checkout, RPC, or `wait()` with no timeout; queues or
  result sets without capacity bounds.
- A model- or agent-driven loop runs "until done" with no max steps, tokens,
  spend, or repeated-state stop.
- A plan's next increment is larger than any near feedback channel can observe.
- Rollout jumps 0→100% without named stop criteria.
- Negatives are recorded after a fixed window while true positives still arrive
  later; the model trains on its own served diet without exploration.
- Human edits fix a surface without updating the model, graph, or log that
  will recompute the claim.
- Dashboards treat silence as health; ERROR lines do not mean operator action.
- Expertise is trusted in a low-validity or slow-feedback environment.

## Causal mechanism

Control requires a loop: act, observe, correct, within a deadline. Unbounded
waits convert local stalls into system-wide hangs. Steps larger than their
feedback loop are unsupervised bets. Delayed or self-generated labels teach
the past policy, not the world. Corrections that never reach the source are
undone by the next recompute. Quiet success channels and chatty false ERROR
both destroy the only path operators have to see failure.

Separately, human recognition works only where cues are valid *and* feedback
was fast and clear for long practice. Outside that gate, confidence is not
expertise; scored, decomposed judgment is required.

## Required action

1. Timeout every blocking call; bound pools, queues, and result sets; fail
   fast when slow failure would cascade ([RES-02], [RES-03], [RES-05],
   [RES-14]).
2. Declare agent loops as state machines with explicit limits and a terminal
   failure result ([FM-08]); irreversible tools still need [SEC-05].
3. Keep step size inside what feedback can catch: small replaceable steps,
   cheapest falsifying artifact first, shadow/canary before cutover, phased
   rollout with pre-named stops ([REF-28], [PROD-03], [AIPX-06], [RLSE-07]).
4. Window delayed labels honestly; price exploration when serving shapes
   future training ([MLDATA-05], [COST-14]).
5. Route corrections to the source of truth and the next training or recompute
   path ([HITL-01], [HAI-02], [SERVE-04], Principle 12).
6. Keep success quiet and failure loud where the consumer looks; ERROR means
   action ([OBS-08], [OBS-04], Principle 16).
7. Apply the validity-feedback gate before trusting recognition-primed calls
   ([NDM-01]); otherwise number, outside-view, and score.

## Predicted failure

Thread pools exhaust on eternal waits. Agents loop until budget death or false
completion. Large releases discover failure only after full exposure. Models
learn their own recommendations and mark late converters as permanent
negatives. UI fixes recur after retrain. Operators ignore alerts; silent
dashboards hide dead instrumentation. Teams treat gut calls in novel domains
as expertise and lose to base rates.

## Exemptions and boundaries

- In-process memory calls may omit network timeouts; they do not omit
  application-level deadlines for user-visible operations.
- One-shot offline batch jobs still need wall-clock and cost bounds if they
  can starve shared systems.
- High-validity expert domains (after [NDM-01]) may skip forced multi-attribute
  analysis under time pressure ([NDM-11]); they still need a later review loop
  when stakes are durable.
- Bounded waiting is necessary but not sufficient for measurement integrity:
  a timed-out load test can still coordinate omission if arrivals pause.

## Tensions

| Partition | Side A (keep fully) | Side B (keep fully) | Cut |
|---|---|---|---|
| surface | [NDM-03] recognition under time pressure | [FORE-01] / [FORE-05] scored, outside-view probabilities | use recognition only when [NDM-01] validity and feedback both hold |
| sequence | [REF-28] / [RLSE-07] small steps and phased exposure | single-moment launches when coordination demands it | bound the *risk radius* even if the calendar shows one date; stop criteria still required |
| object | [RES-02] timeout every wait | [RES-06] queue-and-retry, answer fast | timeout the wait; still return a controlled async path rather than blocking the caller forever |
| sequence | [HITL-01] fresh labels into the next train | [MLDATA-05] wait long enough for delayed truth | close the loop, but do not cut the label window shorter than the feedback process |

## Disconfirmers

- Fault injection: a stuck dependency surfaces as timeout and shed load, not
  global hang.
- A canary stop criterion fires in rehearsal on synthetic degradation.
- Post-window label audit shows residual positives below an accepted bound.
- Edit then recompute: the wrong claim does not return.
- On-call drill: silence produces a dead-man's alert; ERROR always has an owner.

## Verification

- Config grep (or equivalent) for client timeouts on every egress.
- Loop policy lists max steps, tokens, spend, repeated-state count, terminal
  failure.
- Rollout plan names metric, window, and pause rule before traffic moves.
- Label policy documents feedback-loop length and exploration budget.
- Alert policy: ERROR implies runbook; absence of telemetry is itself an alert.

## Rule IDs

- [RES-02]: timeout every blocking call
- [RES-03]: slow failure worse than fast failure
- [RES-05]: unbounded result sets
- [RES-14]: handshaking and pending-work bounds
- [RES-06]: queue-and-retry, answer fast
- [FM-08]: agent loops must be bounded
- [SEC-05]: human gate on irreversible tools
- [REF-28]: do not outrun your headlights
- [PROD-03]: cheapest falsifying artifact first
- [AIPX-06]: shadow, canary, then cutover
- [RLSE-07]: phased rollout with stop criteria
- [MLDATA-05]: window delayed feedback
- [COST-14]: feedback-loop economics and exploration
- [HITL-01]: fresh human labels into training
- [HAI-02]: correction reaches source, reversible
- [SERVE-04]: no post-hoc corrector cascade
- [OBS-08] / [OBS-04]: silence is not success; ERROR means action
- [FLOW-08]: late-event policy for "complete" windows
- [NDM-01]: validity-feedback gate
- [NDM-03] / [NDM-11]: recognition vs forced analysis (tension pair)
- [FORE-01] / [FORE-05]: numeric claims and outside view when the gate fails

## Principles

- 7. Write it where it outlives the person who knows it (handoff intent as
  feedback for the next actor)
- 12. Correction must reach the source
- 16. Fail loudly, succeed quietly
- 19. Step size is bounded by the feedback that can catch it

Also load Principle 13 when the step is a durable commit, not only a size
question.

## Evidence / source slugs

- `release-it`: timeouts, pools, queues, ERROR discipline
- `ai-engineering`: bounded agent loops
- `pragmatic-programmer`: headlights / step size
- `lean-ux`: cheapest learning first
- `building-ml-powered-applications`: staged model traffic
- `product-deploy-agents-fields`: phased rollout stops
- `designing-ml-systems`: delayed feedback windows
- `reliable-machine-learning`: exploration under feedback loops
- `human-in-the-loop-ml`: labels and correction into the next run
- `hidden-technical-debt-ml`: corrector cascades
- `observability-engineering`: silence vs success
- `designing-data-intensive-applications`: stream completeness and late data
- `sources-of-power`: recognition and feedback conditions
- `kahneman-thinking-fast-slow`: co-arrival on validity/feedback
- `superforecasting`: scored judgment when recognition is untrusted
- `llm-security-playbook`: tool side-effect gates inside loops

## Non-claims

This card does not reconstruct any source's structure, quote its text, or claim
to cover every control-theory or SRE pattern. It is a decision aid over existing
rule IDs. Private distillations are not published.
