---
concept_name: "Delays"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Architecture Debt"
  - "Onboarding Friction"
  - "Cross-Team Communication"
intervention_categories:
  - "Shorten the information delay"
  - "Dampen the response"
  - "Steer by the forecast"
  - "Delete a delay leg"
  - "Publish the lag"
---

# Delays

## Explanation

A delay is the lag between a cause and its observable effect. Every real system has them, and they are the reason systems overshoot, oscillate, and punish decisive people.

From Donella Meadows: *"Delays are pervasive in systems, and they are strong determinants of behavior. Changing the length of a delay may — or may not, depending on the type of delay and the relative lengths of other delays — utterly change behavior."*

### Three kinds worth separating

**Information delay** — time between the condition changing and you knowing. A defect shipped in March, discovered in May.

**Decision and action delay** — time between knowing and the response actually being in the system. You know in May, headcount is approved in July, the recruiter starts in August.

**Effect delay** — time between the response landing and the outcome moving. The new engineer starts in October and is productive in January.

These add. Nobody experiences the sum, because each leg has a different owner and each owner sees only their own leg as reasonable.

### The dynamic that matters: oscillation

**A balancing loop with a long delay does not settle — it oscillates.** The classic demonstration is a shower with slow pipes: you turn the handle, feel nothing, turn it further, get scalded, crank it back, freeze, and so on. Every correction is a correct response to information that describes a system state you have already left.

Two things set the size of the swings: the length of the delay, and the aggressiveness of each correction. You can't always shorten the delay. You can always make the correction smaller. That single trade is the most useful practical consequence of this concept, and most organizations get it backwards — they respond to visible oscillation by correcting harder and faster, which is precisely what amplifies it.

## In Tech Contexts

### Information delays

- **Defect escape:** merged Tuesday, surfaces in production six weeks later, attributed to whoever touched the file most recently.
- **Attrition:** an engineer disengages in January and resigns in June. The observable event trails the decision by months. See [Retention Problem](retention.md).
- **Debt:** complexity accumulates for a year with no visible cost, then shows up all at once as an estimate that tripled. See [Architecture Debt](architecture-debt.md).
- **Cross-team drift:** two teams diverge on an interface assumption in week 1 and discover it in integration week 9. See [Cross-Team Communication](cross-team-communication.md).

### Decision and action delays

- **Headcount approval:** the req waits for the next planning cycle, which averages half a quarter of pure queueing.
- **Prioritization inertia:** a critical issue arrives mid-sprint and the team redirects at the next boundary. A two-week sprint puts an average one-week delay on every redirect, by construction.
- **Release batching:** the fix is written Monday and ships with the Thursday-after-next train.

### Effect delays

- **New hire ramp:** three to six months to full contribution, longer on a system with thin documentation.
- **Refactoring:** the payoff shows up in estimates for work that hasn't been scoped yet, which means a quarter or two before the delivery curve moves. See [Velocity Decline](velocity-decline.md).
- **Onboarding process changes:** you change the program in Q1 and the first cohort that experienced it is only measurable in Q3. See [Onboarding Friction](onboarding-friction.md).

### Stacked delay: hiring

Take an engineer who resigns in month 0.

| Leg | Duration |
|---|---|
| Knowledge loss becomes visible as reduced throughput | 2 months |
| Case built, req approved, budget confirmed | 1.5 months |
| Sourcing, interviewing, offer, notice period | 3 months |
| New hire ramps to the departed engineer's output | 4 months |

**Total: roughly ten months.** Every leg is defended by someone as reasonable, and it is — locally. The consequence is that the team is below capacity for most of a year, which raises load on the people remaining, which raises attrition, which restarts the clock. The delay is what converts a single departure into a spiral, because the reinforcing loop cycles faster than the correction can land.

### Stacked delay: code quality feedback

You want the team to learn which practices reduce defects. The chain: a practice changes in week 1, code written under it merges over weeks 2–8, defects escape to production across weeks 8–20, incidents get triaged and attributed over weeks 20–24. By the time the signal arrives it is six months old, mixed with three other changes, and attributed to whoever was on call rather than to the practice.

That feedback is too slow and too scrambled to teach anything. So teams adopt quality practices by fashion and abandon them by fatigue, and both decisions feel evidence-based at the time. The fix is to move the measurement upstream to something with a one-week lag, where the signal still points at a cause.

### The oscillation signature

- **Hire, freeze, hire, freeze** on roughly annual cycles, each swing justified with fresh reasoning.
- **Quality crackdown, gradual relaxation, incident, crackdown.**
- **Centralize the platform team, complain about the bottleneck, embed the engineers, complain about the duplication, centralize again** — typically an 18-month period.

The tell is two or more reversals on the same axis. Two reversals mean the delay is unaccounted for, rather than the earlier decisions having been wrong.

## Diagnostic Questions

1. **For the most recent instance of this problem, write four dates: when the condition actually started, when you knew, when you decided, when the effect landed.** The four gaps are your delay budget, and the largest one is where an intervention is worth paying for. Most teams have never written these down and are surprised by which leg dominates.

2. **How long is the total delay compared with how often you revisit the decision?** Reviewing more often than the delay guarantees overcorrection, because every review acts on a state the system has already left. This one question explains most hiring whiplash.

3. **Has the organization reversed direction on this at least twice?** Two reversals is oscillation, and it means the lag is the problem rather than the judgment of the people who made the calls.

4. **What signal are you steering by, and how old is it when it reaches you?** A stale outcome metric and a fresh leading indicator call for opposite fixes — instrument something new versus wait longer on what you have.

5. **The last time you changed something and saw nothing, how long did you wait before changing again?** If that interval was shorter than the known effect delay, you never actually tested the intervention, and whatever you concluded from it is unsupported.

6. **Who owns the total elapsed time, end to end?** If the answer is nobody, each leg will stay locally reasonable and the sum will stay absurd. A ten-month hiring loop is what "nobody" looks like.

## Where I'd Start

**I write the delay budget for one real recent instance, and then I shorten the information delay first.**

The system logic: information delay is the only leg that makes every downstream decision act on stale state. Shorten it and every subsequent choice improves, including the ones you haven't thought of. Shortening the effect delay costs real money and is bounded by physics; shortening the decision delay only makes a poorly-informed decision arrive faster.

**Time-to-signal:** the delay budget takes an afternoon and usually changes the conversation on its own. Instrumenting a leading indicator takes two to four weeks. The oscillation damping shows up over one full cycle of whatever loop you're in — for hiring, about two quarters.

**The cost I'm accepting:** leading indicators are noisier than outcomes. You will act on signals that turn out to be nothing. That's the trade — you accept a higher false-positive rate to get out of the regime where you're steering entirely blind, and you manage the noise with lever 2 rather than by going back to slow, certain data.

**The branch:** if the information delay is already short — the dashboards exist, people can see the state weekly, and the org still swings — then the data is not the constraint and the response policy is. Go straight to damping: make each correction smaller than the gap appears to justify, and hold it for one full delay period before adjusting again. And if you genuinely don't know how long any of the legs are, measure before you intervene at all; an intervention sized against a guessed delay is how oscillation starts.

**What I would not start with:** compressing the effect delay. Accelerating onboarding ramp or forcing a refactor to pay off sooner is the most expensive leg, the most physically constrained, and the least improvable — you might get 20% and you'll spend a quarter getting it. I also wouldn't start by building a faster escalation path. That shortens the decision leg while the dominant lag sits elsewhere, and its actual effect is more reversals per year, which is the failure mode you were trying to fix.

## Intervention Levers

### 1. Shorten the information delay

**Why it works:** Every decision downstream of a measurement inherits that measurement's age. Cutting the lag between condition and observation improves the whole chain at once, and it's usually the cheapest leg to change because it's instrumentation rather than physics.

**Strategy:** Replace the trailing outcome metric with a leading indicator that sits earlier in the same causal chain, and accept that it's noisier.

**Tech example:** For code quality, stop steering by production defect rate — a six-month signal. Steer by review latency, PR size distribution, coverage on changed lines, and flaky-test rate, all measurable weekly. These move first and they move for the same reasons defects eventually will, so the team gets feedback while the practice change is still fresh enough to attribute.

### 2. Dampen the response

**Why it works:** Oscillation amplitude is a product of the delay length and the size of each correction. When the delay is fixed, the correction size is the only variable left, and it's fully under your control.

**Strategy:** Make each adjustment deliberately smaller than the observed gap suggests, then hold it for one full delay period before adjusting again. Write the hold period down in advance, because the pressure to adjust early arrives on schedule.

**Tech example:** Two engineers resign in a quarter and the instinct is to open six reqs — two backfills plus buffer for the departures you expect next. Open two, hold for two quarters, then reassess. The overshoot you avoid is the one where five people start in the same month against a team that has capacity to onboard two, which produces the slow ramps and frustration that generate the next round of departures.

### 3. Steer by the forecast rather than the level

**Why it works:** With a known effect delay, the correct control input is the state the system will be in when your action lands. Steering by the current level guarantees you're always one delay period behind.

**Strategy:** Take the observed rate, project it forward by the length of the delay, and act against that projection.

**Tech example:** Backfill against projected attrition instead of observed vacancy. If you lose eight a year and hiring takes seven months, you should have roughly five reqs open continuously regardless of how many seats are empty today. The same logic applies to refactoring: start when the leading indicators drift, not when the delivery curve drops, because the drop is the point at which the fix takes a year.

### 4. Delete a delay leg instead of shortening it

**Why it works:** Some legs are pure queueing — waiting for a cycle, a meeting, an approval — and queueing time can be removed entirely rather than optimized. This is where the largest single reductions live.

**Strategy:** Find the legs that consist of waiting rather than working, and convert them to a standing decision or a continuous process.

**Tech example:** Standing backfill authorization removes the approval leg completely: a resignation triggers an open req the same day, no case, no cycle. Trunk-based continuous deployment removes the release-train leg, taking fix-to-production from two weeks to hours. Asynchronous design review with a 48-hour SLA removes the wait for the weekly architecture meeting.

### 5. Publish the lag before you start

**Why it works:** A large share of oscillation is impatience with an intervention that is still inside its own delay. Stating the lag in advance converts "this isn't working" from a live conclusion into a scheduled checkpoint.

**Strategy:** When launching an intervention, announce the expected time-to-signal and the interim leading indicators, in writing, before there is any pressure on it.

**Tech example:** Starting a six-month platform migration, state up front that delivery velocity will be flat or slightly down for two quarters, and name what to watch at weeks 4 and 8 — services migrated, build times, incident counts on the migrated path. Without this, the quarterly review lands mid-lag, the migration reads as a failure, and it gets halted at the point of maximum cost and zero payoff.

## What Would Change This Diagnosis

- **Feedback is fast, response is immediate, and the problem still accelerates.** Nothing is lagging; something is compounding. Read [Feedback Loops](feedback-loops.md).
- **You can see the effect happening in real time and the level still takes months to move.** That's accumulation inertia rather than a lag — the flow responded and the stock is doing what stocks do. Read [Stocks & Flows](stocks-and-flows.md).
- **Everyone knows the delays, plans around them correctly, and the system still fails under load spikes.** You're short on buffer, not short on speed. Read [Resilience](resilience.md).
- **Faster feedback changes nothing because one resource is saturated the whole time.** Better information doesn't relieve a hard cap. Read [System Limits](limits.md).
- **The delays appear only at handoffs between teams on different cadences and incentives.** The lag is a symptom of structure, and the structure is the intervention. Read [Hierarchy & Suboptimization](hierarchy.md).

## Cross-References to Problems

- [Retention Problem](retention.md) — the ten-month stacked hiring delay is what turns one departure into a spiral, because the reinforcing loop cycles faster than the correction lands
- [Velocity Decline](velocity-decline.md) — debt costs arrive a year after the decisions that created them, so the team is always paying for a quarter it can no longer identify
- [Architecture Debt](architecture-debt.md) — refactoring pays off two quarters out, which is exactly long enough to get it cancelled at the first review
- [Onboarding Friction](onboarding-friction.md) — process changes take two cohorts to become measurable, so onboarding programs get rewritten before any version is ever evaluated
- [Cross-Team Communication](cross-team-communication.md) — divergent assumptions surface at integration, weeks after the cheap moment to correct them has passed

---

## Summary

Delays turn correct decisions into oscillation, because every correction responds to a system state that has already changed. Separate the information, decision, and effect legs, write down how long each one is, and shorten the information leg first — it's the cheapest and it improves everything downstream. When the delay can't be shortened, shrink the correction instead and hold it for one full delay period before touching it again.
