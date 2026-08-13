---
concept_name: "Hierarchy & Suboptimization"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Architecture Debt"
  - "Cross-Team Communication"
intervention_categories:
  - "Change what the subsystem is measured on"
  - "Route the consequence back to the decision"
  - "Define the goal one level up"
  - "Move the boundary"
---

# Hierarchy & Suboptimization

## Explanation

Hierarchy is how complex systems stay manageable. A system organized into subsystems — teams, services, departments, individuals — lets each part handle its own decisions without every part tracking every other part. That's the whole point: hierarchy reduces the amount of information any one node has to process.

From Donella Meadows: *"Hierarchical systems evolve from the bottom up. The purpose of the upper layers of the hierarchy is to serve the purposes of the lower layers."*

The failure mode is built into the same structure. Each subsystem has a goal, and the goal is local. When a subsystem pursues its local goal well enough to damage the whole, Meadows calls it **suboptimization**: *"When a subsystem's goals dominate at the expense of the total system's goals, the resulting behavior is called suboptimization."*

### The insight that makes this useful

**A locally rational actor produces a globally bad outcome.** Every person in the story is doing their job correctly. The platform team that refuses the risky migration is protecting uptime, which is what they're paged on. The product team pushing the feature past code freeze is protecting the quarter's commitments, which is what they're reviewed on. Neither is confused, lazy, or political. Both are responding accurately to the signal they receive.

This has a hard consequence: **arguing with the actor never works.** Explanations, escalations, alignment offsites, and appeals to "what's best for the company" all target the actor's understanding, and understanding was never the constraint. The subsystem's behavior is produced by what it is measured on, paged on, promoted for, and blamed for. Change the measure and behavior changes within a cycle. Leave the measure in place and the behavior returns the moment attention moves elsewhere — usually with the same people, now quietly resentful about the meeting.

The diagnostic move is to stop asking *why are they behaving this way* and start asking *what would a rational actor do given the scoreboard they can see.* If the observed behavior is the correct answer to that question, you have suboptimization, and the scoreboard is the intervention point.

## In Tech Contexts

### Team-level

- **Product and Engineering over debt.** Product is measured on shipped features per quarter; Engineering is measured on incident count and code health. Refactoring costs Product its scoreboard and buys Engineering theirs. The argument recurs every planning cycle because the structure regenerates it. See [Architecture Debt](architecture-debt.md).
- **Frontend and Backend over API shape.** Frontend is measured on interaction latency and ships whatever gets the page fast; Backend is measured on data correctness and consistency guarantees. The API lands wherever the more senior party wins, and neither team owns the resulting mismatch.
- **Your team and the shared codebase.** Every team is measured on its own delivery. The shared service is nobody's scoreboard, so every team takes the change that is cheapest for them and most expensive for the file. Shared code degrades fastest in orgs with the cleanest per-team metrics. See [Cross-Team Communication](cross-team-communication.md).

### Department-level

- **Sales and Engineering.** Sales is compensated on closed deals; Engineering absorbs the commitments. A one-off promised in a deal is free to the subsystem that made it and expensive to the subsystem that keeps it, so promises accumulate.
- **Finance and Engineering.** Finance is measured on cost per unit of output and holds headcount flat. The saving is immediate and legible; the cost — slower delivery, a thinner bus factor, departures — arrives two quarters later against a different owner's number. See [Velocity Decline](velocity-decline.md).
- **Security and everyone.** Security is measured on vulnerabilities admitted, never on delivery slowed. A review gate with no latency budget is the correct move for that subsystem and a tax on every other one.

### Individual-level

- **Growth and coverage.** An engineer is promoted for visible scope, so they take the greenfield service and leave the migration, the flaky test suite, and the on-call runbook to whoever is least able to refuse. The promo packet rewards exactly this. See [Retention Problem](retention.md).
- **Indispensability and maintainability.** An engineer's job security rises with how much only they understand. Nothing forces sabotage; simply skipping the documentation and taking the review shortcuts they can hold in their head is enough. The team wants legibility, the individual is rewarded for being load-bearing.
- **Manager headcount and org throughput.** Managers are evaluated on the size and importance of what they own, which makes giving a project away a personal loss and taking one on a personal gain. Ownership migrates toward whoever wants it rather than whoever is closest to the work.

### The tech-specific catch

**Software organizations measure subsystems far more precisely than they measure the whole.** Per-team velocity, per-service SLOs, per-department budget, and per-person promo criteria are all instrumented, dashboarded, and reviewed on a cadence. "Does the product get better for users at a sustainable cost" has no dashboard and no weekly owner. Precision on the parts plus vagueness on the whole is the exact condition under which suboptimization gets rewarded — the local metric is the only signal anyone can actually defend in a review.

## Diagnostic Questions

1. **For each subsystem involved, what number determines whether they had a good quarter?** Write the actual operative metric — the one that appears in reviews and promo packets — rather than the stated mission. Divergence between the two is where the behavior lives.

2. **Does the behavior you're frustrated by make the actor's number go up?** If yes, you're looking at suboptimization and no amount of explaining will move it. If the behavior *hurts* their number too, this is confusion or a capability gap, and information will actually help.

3. **Who bears the cost of the decision, and are they the ones making it?** When the decider and the payer are different subsystems, expect the cost to grow without bound. Name the specific separation.

4. **If each subsystem hit its target perfectly, would the whole system be in good shape?** If perfect local performance still produces a bad outcome, the goals themselves are misspecified. That rules out "execute harder" entirely.

5. **How long has this conflict recurred, and does it come back with different people in the seats?** A conflict that survives a full turnover of participants is structural. A conflict that leaves with one person was personal.

6. **What happened the last time someone did the globally right thing?** Ask for a specific instance. If they absorbed the cost quietly and got nothing, everyone else has already learned the lesson and you're watching them apply it.

## Where I'd Start

**I'd change what one subsystem is measured on — specifically, the subsystem whose local optimum is furthest from the global one — and I'd change it in the review that people actually care about, not in a document.**

The system logic: subsystem behavior is a control loop tracking a target. Escalation adds a one-time push against a loop that runs continuously, so the loop wins by default. Moving the target redirects the same loop, and it keeps working after you stop paying attention.

Concretely: pick the single most costly recurring conflict. Write down what each side is measured on. Find the one metric that, if changed, would make the globally good behavior also locally good — usually by adding a term that captures the cost currently being exported. A platform team paged on uptime and nothing else will refuse migrations forever; add "unblocked consumer teams" to their scorecard and the same team starts scheduling migrations without being asked. Then say it out loud in the forum where performance is judged, because that is the only place a metric becomes real.

**Time-to-signal:** one review or planning cycle, typically four to eight weeks. Behavior shifts fast once the scoreboard changes; the second cycle tells you whether it held.

**The cost I'd accept:** the new metric will be fuzzier and harder to attribute than the one it replaces, and the subsystem loses a clean number it could defend. Some of that team's genuine wins become invisible. That's the price of measuring something closer to the truth, and you should say so directly rather than pretending the new metric is rigorous.

**The branch:** if both subsystems are already measured on the same outcome and still conflict, this is not a goal problem. Either they can't see what the other is absorbing — go to lever 2, route the consequence back — or they're fighting over a genuinely scarce resource, which is a constraint problem, and I'd read [System Limits](limits.md) instead.

**What I would not start with:** a reorg. Moving boxes changes who reports where without changing what anyone is measured on, so the same conflict reappears across the new boundary in a quarter, and you've paid three months of churn for it. I also wouldn't start with a cross-team alignment meeting or a shared doc of principles. Both make the conflict polite. Neither makes it stop.

## Intervention Levers

### 1. Change what the subsystem is measured on

*The default. For conflicts that recur across personnel changes.*

**Why it works:** A subsystem is a balancing loop holding to a target. Redefine the target and the loop's full machinery — planning, prioritization, individual judgment calls — realigns without anyone being persuaded of anything.

**Strategy:** Add a term to the local metric that captures the cost being exported, and put it in the same review as the existing metric. A metric announced anywhere else is a suggestion.

**Tech example:** An infrastructure team measured purely on uptime blocks every risky migration, and product teams route around them with shadow infrastructure. Add "consumer teams unblocked per quarter" alongside availability. The team now proposes migration windows, and the shadow systems get absorbed rather than multiplying. Uptime dips slightly; the org stops maintaining four parallel deployment paths.

### 2. Route the consequence back to the decision

*When a subsystem exports a cost it never experiences.*

**Why it works:** Suboptimization needs an asymmetry — benefit local, cost elsewhere. Close the loop between decision and consequence and the local calculation changes on its own, with no new metric and no negotiation.

**Strategy:** Find where the cost lands and connect it back to the decider directly. Ownership beats reporting; feeling beats knowing.

**Tech example:** A team ships a service and hands operations to a central on-call rotation. Defect rates stay high because the pain lands on strangers. Move the team onto its own pager. Reliability work appears in their backlog within two sprints, unprompted, because 3am is now their 3am. The same conversation held as a quality initiative had run for a year with no effect.

### 3. Define the goal one level up and hold both subsystems to it

*When two subsystems each have a defensible local goal and the whole has none.*

**Why it works:** Suboptimization is only detectable against a stated system goal. Without one, every subsystem's behavior is defensible and disputes resolve by seniority. Naming the higher-level goal creates the standard that arbitrates.

**Strategy:** State the system-level outcome in one measurable sentence, then give both subsystems a shared line item against it. Joint accountability means both win together or neither does — a shared goal that only one party is graded on is not shared.

**Tech example:** Product and Engineering deadlock on debt every planning cycle. Define the system goal as "sustained delivery rate over four quarters," measured as features shipped per quarter with the trend line visible. Both teams are reviewed on the same trend. Product now has a reason to fund refactoring, because a declining trend is their problem too. See [Architecture Debt](architecture-debt.md).

### 4. Move the boundary so the subsystem contains its own consequence

*When the split itself is the problem.*

**Why it works:** Boundaries decide which costs are internal and which are external. A subsystem drawn around a full outcome has no one to export to; the tradeoff gets made inside one team's head instead of across a ticket queue.

**Strategy:** Redraw teams around outcomes rather than technology layers, so the coordination that used to happen between teams happens within one. Use this when the same coordination cost recurs on every project, not for a one-off dispute.

**Tech example:** Frontend and Backend teams split by layer produce API designs that serve neither, and every feature costs two roadmaps and a negotiation. Reorganize into feature teams owning a vertical slice end to end. API design becomes an internal decision made in an afternoon. The tradeoff you take on: less depth in each layer and some duplicated infrastructure work, which is why this lever is worth it only when the coordination tax is structural rather than occasional.

### 5. Rotate people across the boundary

*A supporting move, not a fix on its own.*

**Why it works:** Subsystems optimize against their model of the other side, and the model is usually a caricature built from tickets. People who have worked on both sides carry an accurate model back, which improves the quality of local decisions even when the metrics stay put.

**Strategy:** Run genuine multi-week embeds with real work assigned, not tours. Rotate the people who make the calls.

**Tech example:** A platform engineer spends six weeks on a product team and watches their own deprecation notices land mid-sprint with two weeks' warning. The next deprecation ships with a six-month window and a migration script. No policy changed; the person writing the policy had different information. Pair this with lever 1 — on its own the effect fades as the rotated person's memory does.

## What Would Change This Diagnosis

- **The behavior hurts the actor's own numbers too.** Then this is a capability or information gap, not suboptimization, and explaining will actually work. Check what they can see before assuming what they want.
- **There's one team and one goal, and the problem persists anyway.** With no subsystem boundary there's nothing to suboptimize across. Look at the loop the team is stuck in — read [Feedback Loops](feedback-loops.md).
- **Both subsystems already share the metric and still can't both hit it.** They're contending for something genuinely scarce, and no realignment creates more of it. Read [System Limits](limits.md).
- **The subsystem responded correctly but the effect showed up two quarters later against someone else's number.** That's an information delay masquerading as misalignment. Read [Delays](delays.md).
- **The conflict is stable and mild, but one departure would collapse the whole arrangement.** Goal alignment isn't your exposure; concentration is. Read [Resilience](resilience.md).

## Cross-References to Problems

- [Retention Problem](retention.md) — individual growth incentives pull people toward visible new work while unglamorous critical work concentrates on whoever won't refuse it, and those are the people who leave
- [Velocity Decline](velocity-decline.md) — cost-optimizing one department while delivery is owned by another exports the slowdown to a number nobody is currently accountable for
- [Architecture Debt](architecture-debt.md) — shared code degrades because every team is measured on its own delivery and no one is measured on the file
- [Cross-Team Communication](cross-team-communication.md) — silos are the rational output of per-team scoreboards, so communication programs fail while the scoreboards stand

---

## Summary

Hierarchy exists because complex systems can't route every decision through one place, and suboptimization is the standing cost of that arrangement: subsystems pursue local goals accurately enough to damage the whole. The behavior you're frustrated by is almost always the correct response to a real scoreboard, which is why arguing with the actor fails and changing the measure works. Find the subsystem whose local optimum is furthest from the global one, add the exported cost to what it's graded on, and say it in the review that counts.
