---
concept_name: "Stocks & Flows"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Architecture Debt"
  - "Onboarding Friction"
intervention_categories:
  - "Reduce the outflow"
  - "Increase the outflow"
  - "Throttle the inflow"
  - "Decouple coupled stocks"
  - "Make the flows visible"
---

# Stocks & Flows

## Explanation

A stock is an accumulation you can count at a moment in time. A flow is a rate — the speed at which something enters or leaves that stock. Water in a bathtub is a stock; the faucet and the drain are flows.

From Donella Meadows: *"A stock is the memory of the history of changing flows within the system."*

### Three properties that do all the work

**You cannot change a stock directly. You can only change its flows.** Every intervention that appears to act on a level actually acts on a rate. "We need more senior engineers" is a statement about a stock; the only available moves are hiring, growing, and retaining — all flows.

**Stocks change slowly even when flows change abruptly.** Cut hiring to zero today and headcount barely moves this month. This inertia is why systems absorb shocks, and why they keep drifting long after the decision that caused the drift was reversed.

**A stock rises when inflow exceeds outflow, and the two flows are usually controlled by different people.** Engineering managers control hiring; the market and the manager's own behavior control attrition. Product controls feature inflow; nobody in particular controls complexity outflow. This split is where most stock problems actually live.

So the question worth asking about any stock is **which flow is producing the level, and who controls that flow.**

## In Tech Contexts

### Team capacity

- **Stock:** engineers on the team, weighted by ramp
- **Inflows:** hiring, internal transfers in, returning leave
- **Outflows:** resignations, transfers out, reorg reassignment
- **Behavior:** headcount looks stable right up until it doesn't, because a hire and a departure in the same month net to zero on the chart while destroying months of context. See [Retention Problem](retention.md).

### Codebase complexity

- **Stock:** services, modules, interdependencies, configuration surface
- **Inflows:** new features, copy-pasted logic, new integrations, new services
- **Outflows:** refactoring, deletion, consolidation, decommissioning
- **Behavior:** the inflow is continuous and rewarded; the outflow requires a decision nobody is measured on. See [Architecture Debt](architecture-debt.md).

### Team knowledge

- **Stock:** who knows why the system is shaped the way it is
- **Inflows:** shipping, pairing, documentation, decision records, onboarding
- **Outflows:** departures, forgetting, code changing out from under the documentation
- **Behavior:** declines invisibly, because the loss registers only when someone needs the missing knowledge — usually during an incident. See [Onboarding Friction](onboarding-friction.md).

### Work in progress

- **Stock:** open tickets, in-flight branches, unreleased changes
- **Inflows:** requests, bug reports, discovered work
- **Outflows:** shipping, closing, explicit rejection
- **Behavior:** WIP grows until the coordination cost of holding it consumes the capacity that would drain it. See [Velocity Decline](velocity-decline.md).

### The tech-specific catch

**In software organizations, almost every stock has an automatic inflow and a manual outflow.** Code accumulates as a side effect of doing the job; deleting it requires someone to choose deletion over a feature. Tickets file themselves; closing them requires a meeting. Complexity arrives with every integration; consolidation arrives only when someone champions it. The inflow runs on the org's default incentives and the outflow runs on individual initiative, so the default trajectory of every one of these stocks is upward — including the ones you want to go down.

The mirror image holds for the stocks you want to keep. Attrition and forgetting run automatically; hiring and documentation run on effort. So headcount and knowledge drift down by default while complexity and WIP drift up by default, all from the same structural asymmetry.

## Diagnostic Questions

1. **What is the stock, in what unit, at what level right now?** If you can't state a number and a unit, you have a metaphor rather than a stock, and the intervention will be as vague as the description.

2. **Over the last two quarters, what were the inflow and outflow rates in that same unit?** Their difference gives you the direction and the magnitude. Most teams know one of these numbers and guess the other.

3. **Did the current trend begin with an inflow change or an outflow change?** "We stopped hiring" and "people started leaving" produce the same headcount curve and require opposite interventions. The sequence separates them.

4. **What's the turnover time — stock divided by outflow rate?** A team of 20 losing 5 a year turns over in four years; a backlog of 400 closing 40 a month turns over in ten months. This number is how long any flow change needs to run before the level can possibly reflect it, and it's the honest answer to "when will we see results."

5. **Which of the two flows is instrumented, and which one is estimated from memory?** The unmeasured flow is almost always the one that has been running away, because nobody has been able to see it move.

6. **If both flows stopped today, would the current level be acceptable?** Yes means your problem is the rate and you have time. No means the level itself is the emergency and flow changes will arrive too late — you need a one-time transfer as well.

## Where I'd Start

**I work the outflow first, in both directions.** For a stock that's draining (engineers, knowledge, trust), I reduce the outflow before increasing the inflow. For a stock that's filling (complexity, WIP, backlog), I increase the outflow before throttling the inflow.

The system logic: in software organizations the outflow is the unmanaged flow, so it holds the most unclaimed leverage per unit of effort, and outflow moves preserve or remove units that already carry context — a retained engineer arrives with four years of history, a deleted service takes its whole maintenance tail with it.

**Time-to-signal:** the flow itself responds in weeks and you should measure it directly. The stock responds over one turnover time, so compute that number first and commit to it out loud, because it is the interval during which someone will tell you this isn't working.

**The cost I'm accepting:** outflow work has no launch moment. Nobody announces the engineer who stayed or the service that was deleted. You are trading visible wins for compounding ones, and you should expect to have to argue for the budget twice.

**The branch:** if the outflow is already near its floor — attrition under 8%, a standing refactoring allocation that's actually being spent — then the outflow is no longer where the slack is, and the constraint is the inflow. Cap it explicitly: a hiring plan tied to onboarding capacity, or a complexity budget where a new service requires retiring one. And if the answer to question 6 was "no, the level is the emergency" — one person holds all the context for the payments system — then neither flow moves fast enough. Do a one-time stock transfer first (paired rotation, documented decision sprint, contractor backfill), then fix the flows so you don't have to do it again.

**What I would not start with:** a target for the stock level itself. "Get to 15 engineers," "get the backlog under 200" — these produce flow behavior that hits the number and then reverts, because nothing about what generates the flows changed. I also wouldn't open with a one-time drain like a debt sprint or a backlog bankruptcy. It resets the level while leaving both rates intact, which means you're back at the same level within one turnover time and you've spent the goodwill you'll need for the structural fix.

## Intervention Levers

### 1. Reduce the outflow

*For a stock you want to keep.*

**Why it works:** Every unit you retain is a unit you don't have to acquire, and retained units carry embedded structure — context, relationships, history — that new units lack entirely. A point of attrition avoided is worth more than a point of hiring gained.

**Strategy:** Find the specific exit path most units take and close that one, rather than improving conditions generally.

**Tech example:** A 40-person org at 20% annual attrition loses eight people a year. Getting to 12% saves three — roughly a quarter of recruiting spend, with none of the ramp cost. The move is narrow: exit conversations from the last year usually point at one or two repeated causes (no growth path, one specific manager, on-call load), and closing the largest one moves the rate more than a compensation adjustment across the whole org.

### 2. Increase the outflow

*For a stock that's filling past what the system can carry.*

**Why it works:** A manual outflow runs at the rate of individual initiative, which is near zero under deadline pressure. Converting it to an automatic outflow makes draining the default rather than the exception.

**Strategy:** Make the removal happen without anyone deciding to do it.

**Tech example:** Tickets untouched for 90 days close automatically with a note and a one-click reopen. Backlog outflow goes from "quarterly grooming marathon" to continuous, and the reopen rate tells you exactly how much of the backlog was real. The same pattern works on code: a standing deletion budget where every sprint retires one flag, one endpoint, or one dead module.

### 3. Throttle the inflow at the source

*When the outflow is already at its practical ceiling.*

**Why it works:** The cheapest unit of complexity is the one never added. Inflow control acts upstream of everything downstream — review, testing, operations, onboarding — so one unit prevented saves cost in every stock it would have touched.

**Strategy:** Give the inflow a hard budget with a visible owner, so that adding requires trading rather than asking.

**Tech example:** A complexity budget: a new service can be introduced when an existing one is retired. Teams stop reaching for a new service as the default answer, and the consolidation conversation happens at design time instead of two years later during an on-call postmortem.

### 4. Decouple stocks that share a flow

**Why it works:** When two stocks drain through the same pipe, fixing one appears to require fixing the other, and you end up fighting a battle you can't win to protect a stock you could have protected directly.

**Strategy:** Identify what you actually care about, then move it out of the path of the flow you can't stop.

**Tech example:** Headcount and knowledge share the departure outflow, so retention becomes the only apparent lever for knowledge. Break the coupling: recorded handoff during notice period, architecture decision records written at decision time, mandatory rotation on single-owner systems. Attrition stays where it is and knowledge stops leaving with it. This is the highest-value decoupling in most engineering orgs.

### 5. Make the stock and both flows visible on one chart

**Why it works:** People manage what they can see, and an unmeasured flow runs unopposed. Showing the rates next to the level also protects you from overcorrection, because you see the flow respond weeks before the stock does.

**Strategy:** One chart, updated monthly, showing level as a line and both flows as bars in the same unit.

**Tech example:** Headcount as a line with hires and departures as bars. Two flat quarters of net-zero headcount stop reading as stability once you can see six hires and six departures underneath them. The same chart shape works for services added versus retired, and for tickets opened versus closed.

## What Would Change This Diagnosis

- **The stock is stable and the problem is still getting worse.** Accumulation isn't the mechanism. Something is feeding back on itself. Read [Feedback Loops](feedback-loops.md).
- **You changed a flow, the flow moved, and the level hasn't — and you're about to reverse the change.** That's turnover time doing exactly what it does. Read [Delays](delays.md) before you touch anything.
- **You've changed both flows and neither one moves.** A hard cap is holding the rate: interview panel availability, one reviewer who must approve everything, a fixed budget line. Read [System Limits](limits.md).
- **Every team's stocks look healthy and the org still fails.** The stocks are fine locally and misallocated globally. Read [Hierarchy & Suboptimization](hierarchy.md).
- **The average level is fine and the system breaks at spikes.** You have a buffer sizing problem rather than a level problem. Read [Resilience](resilience.md).

## Cross-References to Problems

- [Retention Problem](retention.md) — team capacity as a stock: hiring inflow against departure outflow, with knowledge draining through the same pipe
- [Velocity Decline](velocity-decline.md) — WIP and complexity accumulate faster than they drain, and the accumulation consumes the capacity that would drain it
- [Architecture Debt](architecture-debt.md) — the canonical automatic-inflow, manual-outflow stock; complexity rises by default
- [Onboarding Friction](onboarding-friction.md) — knowledge as a stock, with mentoring capacity as the flow constraint on refilling it

---

## Summary

Stocks are levels, flows are rates, and every intervention you have acts on a rate. In software the inflows run automatically and the outflows run on somebody's initiative, so complexity and WIP drift up while headcount and knowledge drift down. Work the outflow first, measure the flow rather than the level, and compute the turnover time before you promise anyone results.
