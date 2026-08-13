---
description: "Problem-first reference guide for applying systems thinking to tech problems"
source: "Thinking in Systems — Donella Meadows"
---

# Systems Thinking Reference Guide

Applying Donella Meadows' systems thinking to problems technology workers face.

**How to use:** Find the problem that matches your situation. Work through the guided discovery questions to get the specifics on the table, check the diagnosis fits, then read the recommended starting lever before the full menu of interventions.

**How this guide behaves:** It asks before it advises, then it commits. Each guide names a default starting point and says what would change that recommendation. See the [house style](../../README.md#house-style-be-a-thought-partner).

**For agents:** Every file carries YAML frontmatter with machine-readable system structure — `stocks`, `flows`, `feedback_loops` (typed reinforcing/balancing), `delays`, `limiting_factors`. Problems and concepts link bidirectionally via `related_concepts` / `related_problems`, so the guide is traversable as a graph. Section headings are consistent across files; `## Where I'd Start` holds the recommendation and `## What Would Change This Diagnosis` holds the falsification conditions.

---

## Problem Gateway

### Team & Culture

- **[Retention Problem](retention.md)** — Experienced engineers leaving faster than you can replace them. Is this a compensation problem or a knowledge-loss spiral?

- **[Onboarding Friction](onboarding-friction.md)** — New engineers take 3+ months to be productive, and some leave before they get there. What's throttling the learning loop?

### Infrastructure & Debt

- **[Velocity Decline](velocity-decline.md)** — Throughput dropping despite stable headcount and effort. What changed in the system that didn't change in the team?

- **[Architecture Debt](architecture-debt.md)** — Every change is slower and riskier than the last. Which loop is manufacturing the complexity?

### Coordination

- **[Cross-Team Communication](cross-team-communication.md)** — Misalignment, duplicate work, blocked dependencies, decisions that take weeks. Is this an information delay or a goal conflict?

### Planned

Not yet written. Following the process in [METHODOLOGY.md](../../docs/METHODOLOGY.md).

- Scope Creep — feature requests expand without boundaries; timelines slip
- Burnout & Stress — exhaustion, disengagement, health impacts
- Feature Bloat — product accumulates features; users overwhelmed; maintenance grows
- Hiring Bottleneck — can't hire fast enough to keep up with attrition

---

## Concept Guides

The foundational principles. Each explains how the concept shows up in tech and which levers it gives you.

- **[Feedback Loops](feedback-loops.md)** — How systems reinforce or balance themselves. The engine behind most spirals.

- **[Stocks & Flows](stocks-and-flows.md)** — The building blocks. What's accumulating, what's draining, and at what rate.

- **[Delays](delays.md)** — Time lags that make systems hard to steer and easy to overcorrect.

- **[Hierarchy & Suboptimization](hierarchy.md)** — How subsystems win at the expense of the whole.

- **[Resilience](resilience.md)** — Why systems that look efficient break badly.

- **[System Limits](limits.md)** — The single binding constraint, and why everything else you optimize does nothing.

- **[System Traps](system-traps.md)** — Recurring pathological patterns: Policy Resistance, Tragedy of the Commons, Drift to Low Performance, Seeking the Wrong Goal.

---

## How to Navigate

1. **You have a problem.** Find it in the Problem Gateway. The problem deep-dive walks you from symptom to diagnosis to a recommended first move.

2. **You want the underlying principle.** Each problem links to the concepts it reveals. Read those to see the same structure show up in problems that look unrelated.

3. **You want to diagnose something not listed.** Start with [Stocks & Flows](stocks-and-flows.md) to find what's accumulating, then [Feedback Loops](feedback-loops.md) to find what's driving it, then [Delays](delays.md) to understand why your fixes aren't showing up yet.

4. **You're building a similar guide for another topic.** Read [METHODOLOGY.md](../../docs/METHODOLOGY.md) for the reusable structure. What's queued for this guide is listed above, under Planned.

---

## About This Guide

**Source:** Donella Meadows, *Thinking in Systems* — [full text](https://blas.com/wp-content/uploads/2019/07/Thinking-in-Systems.pdf). Notes in [[Thinking in Systems]]. The concepts are hers; the tech applications, examples, and interventions are the interpretation layer.

**Related:** [[ecosystems]], [[socratic-questioning]], [[opportunity-solution-trees]]
