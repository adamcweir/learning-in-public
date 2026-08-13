---
title: "Architecture Debt"
category: "Infrastructure & Debt"
related_concepts:
  - "Feedback Loops"
  - "Stocks & Flows"
  - "Delays"
  - "System Limits"
  - "System Traps"
  - "Hierarchy & Suboptimization"
  - "Resilience"
stocks:
  - "accumulated coupling and complexity in the codebase"
  - "workarounds, special cases, and dead code paths still executing"
  - "tests nobody trusts and therefore nobody uses as a safety net"
  - "subsystems with exactly one person willing to change them"
flows:
  - "inflow: shortcuts taken per sprint under schedule pressure"
  - "inflow: structural complexity added by each new feature"
  - "outflow: refactoring completed"
  - "outflow: deletion, decommissioning, and migration completion"
feedback_loops:
  - description: "schedule pressure → quick fix chosen over the clean change → coupling grows → the next change takes longer → the schedule slips → more schedule pressure"
    type: "reinforcing"
  - description: "a module becomes hard to understand → fewer engineers will open it → the ones who do make conservative bolt-on changes rather than restructuring → the module becomes harder to understand"
    type: "reinforcing"
  - description: "migration started → old path kept alive for safety → both paths must now be maintained → less capacity for migration → migration stalls → both paths persist"
    type: "reinforcing"
  - description: "debt causes a visible incident → attention and a cleanup budget appear → some debt is paid down → incidents stop → the budget disappears"
    type: "balancing"
delays:
  - "information delay: 3-12 months between a shortcut and the change it makes expensive"
  - "information delay: the engineer who takes the shortcut is usually not the one who pays for it"
  - "action delay: 1-2 quarters between refactoring work and measurable cycle-time improvement"
  - "perception delay: teams adapt to rising change cost, so the new normal feels normal"
limiting_factors:
  - "test and observability coverage on the modules that most need changing"
  - "the number of engineers who understand the hot subsystems"
  - "capacity that survives contact with a deadline"
  - "confidence in deploy and rollback, which sets how large a refactor anyone dares"
---

# Architecture Debt

## Problem Statement

Changes that should take a day take a week, and every one of them carries a risk of breaking something unrelated. The team can name the problem precisely and has been unable to do anything about it for several quarters.

## System Diagnosis: What Systems Thinking Reveals

**The quick-fix loop is the whole system, and it is reinforcing.** A deadline arrives. The clean change would touch four modules, so someone adds a conditional instead. That conditional couples two things that were separate, which means the next change in the area has to reason about both. The next change takes longer. The schedule slips. Schedule pressure rises. The next engineer, under more pressure than the last, takes a slightly worse shortcut. Every turn of this loop raises the pressure that drives the next turn, which is why teams describe debt as arriving suddenly after years of it accumulating quietly.

**Debt is a stock, and the stock level and the accumulation rate are separate problems with separate fixes.** The stock is how much coupling exists right now. The rate is how much you add per sprint. Teams overwhelmingly attack the stock — debt backlogs, cleanup sprints, rewrite proposals — because the stock is what hurts. The rate is what determines the trajectory. A team that pays down 100 units and adds 120 per quarter is losing while doing visible cleanup work, and will conclude that refactoring does not work. A team that cuts its rate to near zero improves every quarter without a single dedicated cleanup sprint, because features keep touching the code and clean changes leave it slightly better. Fix the rate first. The stock becomes tractable afterward, and part of it pays itself down.

**Debt is concentrated, so uniform paydown is mostly waste.** Take a year of commits and rank files by change frequency. In most codebases the top 5% of files absorb 40-60% of all changes. Complexity in a file nobody touches costs nothing — it is ugly and it is free. Complexity in a file touched twice a week taxes every sprint. The product of change frequency and complexity is where the cost lives, and it is a short list. Cleaning by lint score, by module, or by whoever volunteers spreads effort evenly across a distribution that is nothing like even.

**"We'll refactor after the deadline" never happens, and the reason is structural rather than cultural.** The loop's arrow runs through schedule pressure. Deferred cleanup is only ever scheduled into a window where pressure has abated — and pressure never abates, because the previous quarter's shortcuts made this quarter's work more expensive, and because any capacity that appears is immediately claimed by the roadmap. The promise is sincere every time and cannot be kept, which means each promise also spends a little of the team's belief that cleanup is possible. This is Meadows' "shifting the burden" trap: the quick fix is the symptomatic response, it works immediately, and each use erodes the capability to make the fundamental one.

**The limiting factor on paydown is the safety net.** Teams that cannot refactor usually cannot refactor because they cannot tell whether they broke something. Where tests are absent or untrusted, every restructuring is a gamble against production, so engineers rationally choose the additive change. Test and observability coverage on the hot files is the constraint that gates every other intervention in this document.

## Guided Discovery Questions

Answer these first. They separate a debt loop from three other things that produce identical complaints.

1. **Rank a year of commits by file. What fraction of changes landed in the top 5% of files?** Above 40% means debt is concentrated and a targeted list will work. Under 20% means change is spread evenly, which points at coupling between services or teams rather than within the code.

2. **Is the cost of change rising, or is it high and flat?** Rising means the loop is running and you must fix the rate. High and flat means a one-time stock you can size, schedule, and finish — a genuinely different and much easier problem.

3. **How many shortcuts landed last sprint, and can anyone name them?** If nobody can name them, the inflow is unmeasured, which means it is unmanaged. You cannot cap a rate you do not count.

4. **What happened to the last three "we'll clean this up after the launch" commitments?** Three promises and zero completions tells you the arrow runs through schedule pressure. Stop making the promise and change the mechanism.

5. **When something breaks in production, which files were involved?** Overlap between the incident list and the high-churn list confirms the diagnosis and gives you your paydown order for free.

6. **Pick the worst module and deliberately break something in it. Does anything fail before production?** This measures the limiting factor directly. A silent pass means your first intervention is the safety net, whatever else you had planned.

7. **How many engineers will voluntarily open the worst file?** One means the second reinforcing loop is running and the module is getting worse with every conservative change made to it.

8. **Who takes the shortcut, who pays for it, and how long between?** A gap of months, or a shortcut taken by one team and paid by another, means the feedback is too slow and too displaced to correct behavior on its own. Discipline campaigns fail against that structure.

## Diagnosis Checkpoint

Does your situation match this pattern?

- [ ] The same class of change takes visibly longer than it did a year ago
- [ ] Changes routinely break things in areas that appear unrelated
- [ ] Engineers can name specific modules they avoid touching
- [ ] Cleanup has been promised after a deadline at least twice and not delivered
- [ ] A small set of files absorbs a large share of all commits
- [ ] Refactoring is discussed as a project needing approval rather than as part of ordinary work

**Four or more:** the quick-fix loop is running and the recommendation below applies directly.

**Fewer than three, and the cost of change is high but stable:** you have a stock without a loop. Size it, schedule it, finish it. Read [Stocks & Flows](stocks-and-flows.md) and skip the loop-breaking work entirely.

**Changes are cheap inside your code but slow to get reviewed, approved, or released:** the constraint is a queue, not the architecture. Go to [Velocity Decline](velocity-decline.md) and start with its cycle-time decomposition.

## Where I'd Start

**I would cap the inflow at the hot spots: compute change frequency times complexity, take the top 5% of files, and declare them shortcut-free — changes there land clean, and that cost goes into the feature estimate instead of into a future promise.** I would do nothing about the existing stock for the first quarter.

The system logic: this cuts the "schedule pressure → quick fix" arrow at exactly the point where the loop's gain is highest, because the hot files are where the next change is going to land anyway. It also converts ordinary feature work into paydown — engineers are already in those files every week, and a clean change leaves them slightly better. You get outflow without booking any refactoring capacity, which is the only kind of outflow that survives a deadline.

**Time-to-signal:** the hot-spot list takes an afternoon with `git log` and any complexity tool. Cycle time on changes touching those files moves within six to eight weeks. Change failure rate follows within a quarter. Overall cost-of-change trends take two quarters, because the stock outside the hot spots is still there and still charging you.

**The cost I'm accepting:** features that touch hot spots get 20-30% more expensive, visibly, in planning, where someone will push back every time. That is the point — the cost was always being paid, and this moves it from an invisible tax on future work to a line item on current work. I am also accepting that the ugliest parts of the codebase stay ugly for a quarter, and I will be asked about them.

**The branch:**

- **If question 6 came back silent** — a deliberate break produced no failing test — build the safety net on the hot files first. Characterization tests and enough observability to detect a regression, three to four weeks of work. Nothing else in this document is executable until that exists.
- **If question 1 came back under 20%** — change is spread evenly, with no hot spots — then the coupling is at the service or team boundary rather than inside any file. Go to [Cross-Team Communication](cross-team-communication.md); a file-level list will find nothing to grab.

**What I would not start with:** a tech debt backlog, a dedicated cleanup sprint, or a rewrite. A backlog is a list of stock items with no rate control, so it grows faster than it drains. A cleanup sprint produces one visible burst and then returns the system to its prior inflow. A rewrite restarts the same loop on a new codebase with less knowledge and an active deadline, and it is the most reliable way to double the stock.

## Systems Concepts at Play

- [Feedback Loops](feedback-loops.md) — the quick-fix loop is the canonical reinforcing spiral in software, and the balancing loop that opposes it is event-driven and decays as soon as incidents stop
- [Stocks & Flows](stocks-and-flows.md) — the central distinction of this problem: the stock is what hurts, the rate is what determines whether it gets better
- [Delays](delays.md) — months between a shortcut and its cost, and displacement onto a different engineer, is why individual discipline cannot correct this
- [System Limits](limits.md) — test coverage and deploy confidence on the hot files gate every paydown intervention regardless of budget
- [System Traps](system-traps.md) — "refactor after the deadline" is shifting the burden to the symptomatic fix, and each use weakens the capability to make the real one
- [Hierarchy & Suboptimization](hierarchy.md) — every team is measured on shipping its own features, and nobody is measured on the shared cost of the coupling they add
- [Resilience](resilience.md) — high coupling removes the buffers that let a system absorb a bad change, which is why incident severity rises before velocity visibly falls

## Intervention Strategies

### 1. Cap the inflow before touching the stock

**Why it works:** Cuts the loop's strongest arrow. Stopping accumulation flattens the trajectory, which is the change that actually shows up in cycle time, and it costs a fraction of paying the stock down.

**How:** Make hot-spot files shortcut-free by rule. Everywhere else, allow shortcuts but require a one-line note in the PR saying what was deferred and what it will cost. Count those notes per sprint and treat that count as the metric — a rate you can see is a rate you can bound.

**Tech example:** A payments team allowed shortcuts anywhere except eleven files that absorbed half of all commits. Nothing was cleaned up for a quarter. Median cycle time on payment changes still dropped 28%, because the ordinary feature work now left those files marginally better each week.

### 2. Pay down by hot spot, never uniformly

**Why it works:** Cost is the product of complexity and change frequency. Complexity in untouched code costs nothing, so effort spent there returns nothing. Ranking by the product concentrates the entire budget on the tax you are actually paying.

**How:** `git log` for change counts over twelve months, any complexity metric for the second axis, multiply, take the top twenty files. Intersect with the last year's incident list. Work that list in order and stop when the ordering stops separating.

**Tech example:** A team ran a two-week debt sprint against a lint-score-ranked list of 90 files and saw no measurable change. Re-ranking by churn times complexity produced eleven files, five of which were untouched by the sprint. Two weeks on those eleven cut change failure rate by a third.

### 3. Put refactoring inside feature work rather than after it

**Why it works:** The arrow runs through schedule pressure, and pressure never abates. Work scheduled for after the pressure ends is scheduled for a moment that does not arrive. Work embedded in the estimate is protected by the same forces that protect the feature.

**How:** Stop producing separate cleanup tickets for hot-spot code. When a story touches a hot file, the estimate includes leaving that file better, and that is what gets committed to. Retire the phrase "we'll clean it up after" — the team has evidence about what that phrase predicts.

**Tech example:** An infra team had promised a scheduler cleanup for three consecutive quarters. They cancelled the project, added roughly 25% to any estimate touching the scheduler, and made restructuring part of the definition of done for those stories. The scheduler was substantially rewritten over five months without a single cleanup ticket.

### 4. Build the safety net before attempting the paydown

**Why it works:** Test and observability coverage on the hot files is the limiting factor. Where a refactor is a bet against production, engineers correctly choose the additive change, and adding capacity does nothing to change that calculation.

**How:** Write characterization tests that pin current behavior on the top hot-spot files — including the behavior that looks wrong, since something depends on it. Verify by deliberately breaking things and confirming the tests fail. Add enough metrics to detect a regression within an hour of deploy.

**Tech example:** A team spent three weeks writing characterization tests over a 4,000-line pricing module with no coverage. They shipped no features that month. Over the following two quarters that module absorbed four significant restructurings with zero production incidents, none of which anyone would have attempted before.

### 5. Delete instead of refactoring wherever you can

**Why it works:** Deletion is an outflow with no risk of adding complexity back. Half-finished migrations are a reinforcing loop of their own: both code paths must be maintained, which consumes the capacity needed to finish the migration.

**How:** Instrument the suspicious code paths and measure actual usage for a month. Delete what is unused. Finish or abandon every in-flight migration — pick one explicitly, and treat "both paths alive" as an active incident rather than a steady state.

**Tech example:** An API team found that 31% of their endpoints had served no traffic in six months. Deleting them removed four dependency upgrades from the roadmap and let them finish an auth migration that had been half-done for two years.

## What Would Change This Diagnosis

- **Cost of change is high but flat over several years.** No loop is running. This is a stock to size and schedule, and the rate-control machinery here is unnecessary overhead. Read [Stocks & Flows](stocks-and-flows.md).
- **Change frequency is spread evenly with no hot spots.** The coupling lives between services or teams, not inside files. Read [Cross-Team Communication](cross-team-communication.md).
- **Engineers make changes quickly but the changes wait for review or release.** The constraint is a queue downstream of the code. Go to [Velocity Decline](velocity-decline.md) and decompose cycle time first.
- **The slowdown began within a quarter of specific senior departures and sits in their subsystems.** The code did not change; the people who understood it left. Read [Retention Problem](retention.md).
- **Only engineers hired in the last year find the code hard, and the tenured ones do not.** That is a ramp and context problem wearing debt's clothing. Read [Onboarding Friction](onboarding-friction.md).

## Tech Examples

### Scenario 1: The debt sprint that changed nothing

**Symptom:** A 15-engineer team ran a two-week debt sprint after a year of complaints. They closed 90 tickets against a list ranked by static analysis score. Six weeks later, cycle time and change failure rate were both unchanged, and leadership concluded that refactoring does not pay.

**Diagnosis:** The lint-ranked list was ranked by ugliness, and ugliness is free in code nobody touches. Ranking the same codebase by twelve-month change count times complexity produced eleven files — five of which the sprint never touched — that absorbed 52% of all commits. The team had spent two weeks improving code the system was not charging them for.

**Intervention:** Rebuilt the list on churn times complexity, intersected it with the year's incident postmortems, and worked the top eleven files. Declared those files shortcut-free going forward so the improvement would hold.

**Result:** Change failure rate fell by roughly a third in one quarter and cycle time on changes touching those files fell 28%. The list was recomputed quarterly and shrank each time, because capping the inflow stopped new files from entering it.

### Scenario 2: The refactor that was always next quarter

**Symptom:** A platform team had committed to restructuring their job scheduler in three consecutive quarterly plans. Each quarter the work was descoped in week two under launch pressure. By the third quarter, an estimated 40% of on-call pages traced to the scheduler and two engineers had stopped volunteering for that rotation.

**Diagnosis:** The loop's arrow ran through schedule pressure, and every plan scheduled the cleanup into a hypothetical low-pressure window. That window never opened, because the deferred cleanup was itself making each subsequent quarter more expensive — the shortcuts taken to hit each launch raised the cost of the next one. Three sincere promises had also spent the team's belief that cleanup was achievable, which made the fourth easier to descope than the third.

**Intervention:** Cancelled the refactoring project outright and stopped putting it in plans. Instead, every story touching the scheduler carried roughly 25% additional estimate, and leaving the touched code structurally better became part of the definition of done. Three weeks of characterization tests went in first so the restructuring was safe to attempt incrementally.

**Result:** The scheduler was substantially rewritten over five months with no cleanup ticket ever filed and no project ever approved. Scheduler-related pages fell to under 10% of the total. The team applied the same pattern to two other subsystems in the following year.

## Related Problems

- [Velocity Decline](velocity-decline.md) — debt is one of four systems that produce a velocity drop, and the decomposition there tells you whether this file is your problem
- [Retention Problem](retention.md) — losing the people who understand a module raises its effective debt without a line of code changing
- [Onboarding Friction](onboarding-friction.md) — high coupling is what makes a new engineer's first three months expensive
- [Cross-Team Communication](cross-team-communication.md) — coupling that crosses team boundaries behaves like debt and cannot be fixed inside one codebase
