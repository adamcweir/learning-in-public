# Systems Thinking Reference Guide Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create a problem-first Systems Thinking reference guide and reusable methodology for tech workers, structured to be useful for both humans and agents.

**Architecture:** Hybrid approach with Problem Gateway (curated index) + Problem Deep-Dives (diagnosis, Socratic questions, interventions) + Concept Deep-Dives (foundational principles, cross-linked). All files use YAML frontmatter for machine-readable metadata + human-readable content sections.

**Tech Stack:** Markdown with YAML frontmatter, Obsidian/GitHub-compatible format.

## Global Constraints

- All files: UTF-8 encoding, markdown format with YAML frontmatter
- Agent-friendly: YAML frontmatter must be machine-readable; section headings must be consistent across all files
- No hashtag tagging; use YAML `related_concepts` and `related_problems` fields for linking
- Socratic method: guided questions must be open-ended, building progressively (never prescriptive answers)
- Tech-focused examples: all problems and examples must relate to work that technology workers face
- Bidirectional linking: each problem links to concepts in YAML; each concept links back to problems in both YAML and content

---

## Task 1: Set Up Directory Structure

**Files:**
- Create: `Frameworks/Systems Thinking/` directory
- Create: `Frameworks/Systems Thinking/problems/` subdirectory
- Create: `Frameworks/Systems Thinking/concepts/` subdirectory
- Modify: Move existing `Frameworks/Systems Thinking.md` → `Frameworks/Systems Thinking/Systems Thinking.md` (will update it later)

**Interfaces:**
- Produces: Directory structure ready for problem and concept files

- [ ] **Step 1: Create the directory structure**

Run:
```bash
mkdir -p "Frameworks/Systems Thinking/problems"
mkdir -p "Frameworks/Systems Thinking/concepts"
```

- [ ] **Step 2: Move existing Systems Thinking file to new location**

Run:
```bash
mv "Frameworks/Systems Thinking.md" "Frameworks/Systems Thinking/Systems Thinking.md"
```

- [ ] **Step 3: Verify structure**

Run:
```bash
ls -la "Frameworks/Systems Thinking/"
ls -la "Frameworks/Systems Thinking/problems/"
ls -la "Frameworks/Systems Thinking/concepts/"
```

Expected: Three directories exist with no files in problems/ and concepts/ yet.

- [ ] **Step 4: Commit**

```bash
git add "Frameworks/Systems Thinking/"
git commit -m "refactor: reorganize Systems Thinking into directory structure"
```

---

## Task 2: Create Methodology Document

**Files:**
- Create: `Frameworks/Systems Thinking/METHODOLOGY.md`

**Interfaces:**
- Produces: Reusable style guide documenting the hybrid problem-first framework, YAML frontmatter templates, Socratic writing guidelines

- [ ] **Step 1: Write METHODOLOGY.md**

```markdown
# Systems Thinking Reference Guide — Methodology

This document describes the hybrid problem-first framework used to build the Systems Thinking reference guide. Follow this approach when creating other decision-making frameworks or reference guides in learning-in-public.

## Overview: The Hybrid Problem-First Framework

### What Is It?

A three-part reference structure:
1. **Problem Gateway** — Quick index of problems tech workers face, organized by category
2. **Problem Deep-Dives** — Guided diagnosis for each problem (system structure + Socratic questions + interventions)
3. **Concept Deep-Dives** — Foundational systems concepts (Feedback Loops, Stocks & Flows, etc.), with tech context

### Why It Works

- **Practitioners enter at their problem** ("I have a retention issue") → fast, immediately relevant
- **Underlying concepts link back and forth** → over time, users recognize meta-patterns across different problems
- **Agents can parse YAML metadata** → structure system problems systematically, traverse concept relationships, reason about interventions
- **Extensible** → new problems and concepts can be added without modifying existing files

### When to Use It

Use this framework for any decision-making guide, system-thinking reference, or problem-solving framework where you want to be both practitioner-friendly (fast entry point) and agent-compatible (machine-readable structure).

---

## Part 1: Structure Templates

### Problem Gateway Template

**Purpose:** Curated index of problems. Tech worker lands here and finds their problem.

**File:** `Systems Thinking.md` (main file)

**Format:**
```markdown
# Systems Thinking Reference Guide

Quick-reference guide for applying systems thinking to tech problems.

## Problem Gateway

### Team & Culture
- **Retention Problem** — Experienced engineers leaving at higher rates than expected. → [Retention Problem](problems/retention.md)
- **Burnout & Stress** — Team members showing signs of exhaustion, reduced engagement. → [Burnout](problems/burnout.md)

### Product & Features
- **Scope Creep** — Features expand without clear boundaries; timeline slips. → [Scope Creep](problems/scope-creep.md)

### Infrastructure & Debt
- **Architecture Debt** — Codebase accumulating complexity, slowing delivery. → [Architecture Debt](problems/architecture-debt.md)

### Coordination
- **Cross-Team Communication** — Misalignment between teams, duplicate work, delays. → [Cross-Team Communication](problems/cross-team-communication.md)

## Concepts

- [Feedback Loops](concepts/feedback-loops.md) — How systems reinforce or balance themselves
- [Stocks & Flows](concepts/stocks-and-flows.md) — The building blocks of system behavior
- [Delays](concepts/delays.md) — Time lags that make systems hard to manage
- [Hierarchy & Suboptimization](concepts/hierarchy.md) — How subsystems can work against each other
- [Resilience](concepts/resilience.md) — The ability of systems to recover and adapt
- [System Limits](concepts/limits.md) — Resource constraints that govern behavior
- [System Traps](concepts/system-traps.md) — Common problematic patterns (Policy Resistance, Tragedy of the Commons, Drift)
```

**Metadata:** Problem Gateway is a navigation index. Keep it concise (1-line summaries, links to deep-dives).

---

### Problem Deep-Dive Template

**Purpose:** Guided diagnosis for a specific problem.

**File location:** `problems/{problem-name}.md`

**Template:**

```markdown
---
title: "Problem Title"
category: "Team & Culture | Product & Features | Infrastructure & Debt | Coordination"
related_concepts:
  - "Feedback Loops"
  - "Delays"
stocks:
  - "pool of experienced engineers"
flows:
  - "inflow: hiring rate"
  - "outflow: departure rate"
feedback_loops:
  - description: "departures → knowledge loss → slower onboarding → new hire frustration → higher departure"
    type: "reinforcing"
delays:
  - "information delay: 3 months before departures impact throughput"
limiting_factors:
  - "interview capacity bottleneck"
---

# [Problem Title]

## Problem Statement

[1-2 sentences describing what this looks like in practice, what symptoms appear]

## System Diagnosis: What Systems Thinking Reveals

[2-3 paragraphs]

In this problem, the key system elements are:

**Stocks:**
- Pool of experienced engineers
- Institutional knowledge
- Team morale/trust

**Flows:**
- Hiring inflow
- Departure outflow
- Knowledge transfer (when it happens)

**Feedback Loops:**
- Reinforcing loop: High departures → knowledge loss → slower onboarding → new hire frustration → more departures
- Balancing loop: Improved onboarding → new hire confidence → lower departure rate

**Delays:**
- 3-month lag between departures and impact on throughput
- 2-month knowledge transfer lag if done proactively

**Limiting Factors:**
- Interview capacity (bottleneck on hiring rate)
- Time available for knowledge transfer (team members overloaded)

## Guided Discovery Questions (Socratic Method)

Work through these questions to diagnose your specific situation. They're ordered to build understanding progressively.

1. **Understand the stocks and flows:**
   - What are the ways engineers leave your team? (voluntary departure, fired, transfer, retirement)
   - For each departure type, what's the inflow to replace them? (hiring, promotions, transfers in)
   - Is the inflow keeping pace with outflow? How do you know?

2. **Identify feedback loops:**
   - When an experienced engineer leaves, what happens to the team? (knowledge gap, stress on others, slower delivery)
   - Does that stress or slowdown make it more likely others will leave? Why or why not?
   - Is there a "downward spiral" where departures make the job harder, causing more departures?

3. **Spot delays:**
   - When someone leaves, how long before you notice the impact on team velocity? (Days? Weeks? Months?)
   - How long does it take to hire a replacement? (Weeks? Months? More?)
   - During that gap, who absorbs the work?

4. **Find the limiting factors:**
   - If you wanted to hire faster, what's holding you back? (interview capacity, sourcing, salary budget, etc.)
   - Is it the same thing limiting retention? (poor working conditions, low growth opportunities)

## Diagnosis Checkpoint

Does your situation match these patterns?

- [ ] You have a higher departure rate than industry benchmarks
- [ ] Departures cluster in certain roles or team dynamics
- [ ] The knowledge loss from departures noticeably slows the team
- [ ] Exit interviews point to common themes (burnout, limited growth, poor team dynamics, etc.)

If you checked 2+ boxes, systems thinking on this problem is likely valuable.

## Systems Concepts at Play

This problem reveals:
- **Feedback Loops** (departures amplifying themselves)
- **Delays** (lag between cause and visible effect)
- **Hierarchy & Suboptimization** (individual goals vs. team resilience)

See the [Feedback Loops](../concepts/feedback-loops.md) and [Delays](../concepts/delays.md) concept deep-dives for more on how to intervene.

## Intervention Strategies

These levers are grounded in the system dynamics revealed above. Each addresses a specific part of the system.

### 1. Break the Reinforcing Loop: Reduce Knowledge Loss on Departure

**Why it works:** If departures don't cause as much knowledge loss, the onboarding experience improves, and new hires stick around longer. This breaks the downward spiral.

**How to intervene:**
- Document critical knowledge before people leave (design decisions, context, tribal knowledge)
- Have departing engineers do knowledge transfer 1-on-1s with replacement hires
- Create runbooks for common operational tasks
- Record asynchronous explanations of complex subsystems

**Tech example:** A team suffering high junior engineer turnover implemented "senior engineer shadow weeks" where departing or senior engineers pair with juniors to transfer context on key systems. Onboarding time dropped from 4 months to 6 weeks; junior retention improved.

### 2. Reduce Delay: Faster Feedback on Hiring Impact

**Why it works:** Right now, the impact of departure (slower velocity) takes 3 months to appear. By the time you notice, the reinforcing loop has already kicked in. Faster feedback helps you respond sooner.

**How to intervene:**
- Track "coverage ratio" (team capacity vs. critical projects) weekly, not quarterly
- Run exit interviews while people are still in the role, not after they leave
- When someone departs, explicitly plan how remaining team will cover their work
- Review hiring pipeline monthly instead of yearly

**Tech example:** A team tracking weekly coverage realized they were in an "understaffed spiral" month 2 of a departure, not month 3. They immediately hired contractors to fill the gap, preventing the reinforcing loop from strengthening.

### 3. Address the Goal Misalignment: Align Individual and Team Goals

**Why it works:** Often, departures stem from suboptimized goals. The individual wants growth, the team needs stability. The business wants feature velocity, the individual wants learning time. Aligning these reduces departures.

**How to intervene:**
- Career development conversations: what does growth mean to this person? (skills, impact, scope, title, compensation)
- Explicit link between staying and advancement opportunities
- Clarify what "success" looks like for the team and how individuals fit in
- Address systemic issues (low pay, poor processes, unclear advancement) not just individual retention tactics

**Tech example:** A team had high senior engineer departure until they realized departures clustered among engineers 4+ years at the company with no clear path to management or staff engineer roles. They created IC advancement tracks; departures dropped in the next cycle.

### 4. Increase the Inflow: Improve Hiring Capacity

**Why it works:** If you can hire faster than you lose people, the departure feedback loop never destabilizes the team.

**How to intervene:**
- Widen sourcing (referrals, recruiting firms, less traditional backgrounds)
- Streamline interview process (remove unnecessary rounds)
- Improve offer acceptance rate (better compensation, clearer role fit, faster decisions)
- Grow hiring capacity through recruiting coordinator or dedicated hiring manager

**Tech example:** A team struggling with departures realized they were bottlenecked on interviews (4 interviewers, each doing 10+ interviews/month). Bringing in a recruiting coordinator to screen and schedule freed the team to hire 40% faster.

## Tech Examples

### Scenario 1: Junior Engineer Retention Crisis

A 5-person team of engineers mostly hired in the last year. All three junior engineers left within 6 months of joining. Exit interviews revealed: unclear expectations, slow feedback loops, felt lost during onboarding.

**System diagnosis:** Lack of knowledge transfer (high departure → knowledge loss → slow onboarding → junior confusion → departure). No balancing loop to help juniors succeed.

**Interventions applied:**
- Senior engineer assigned as explicit mentor to each junior (knowledge transfer)
- Weekly feedback on code and progress, not just quarterly (reduce delay)
- Pair programming 50% of week for first 3 months (accelerate learning feedback loop)

**Result:** Next cohort of junior hires, 2 of 3 stayed; one left for unrelated reasons. Onboarding time dropped from 4 months to 8 weeks.

### Scenario 2: Undisclosed Goal Misalignment

A team losing a senior engineer annually. Departures were described as "normal attrition." But the pattern was consistent: engineers 4+ years at company, who had been passed over for promotion to staff engineer roles that didn't exist.

**System diagnosis:** Suboptimized hierarchy. Individuals wanted growth and impact at senior levels; company only had IC and manager tracks. Goal misalignment created departures.

**Interventions applied:**
- Created staff engineer and principal engineer tracks (align goals)
- Explicit career conversations with high-risk engineers (reduce information delay)
- Performance-based promotions over tenure-based (change incentive)

**Result:** Departures of senior engineers dropped; internal promotions increased.

---

## Related Problems

- [Burnout](burnout.md) — High departures are often caused by burnout
- [Cross-Team Communication](cross-team-communication.md) — Communication failures can trigger departures
- [Onboarding Friction](onboarding-friction.md) — Poor onboarding amplifies departure feedback loops

```

**Metadata:** This template shows all required sections. Adapt for other problems by filling in the placeholders with their specific system dynamics, questions, and examples.

---

### Concept Deep-Dive Template

**Purpose:** Deepen understanding of a foundational systems concept.

**File location:** `concepts/{concept-name}.md`

**Template:**

```markdown
---
concept_name: "Feedback Loops"
concept_type: "balancing | reinforcing"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Architecture Debt"
intervention_categories:
  - "Break the loop"
  - "Change the goal"
  - "Adjust the structure"
---

# Feedback Loops

## Explanation

A feedback loop is a chain of cause-and-effect where the output of a system feeds back as input, creating a cycle. There are two types:

**Reinforcing feedback loops** amplify change. Once started, they build on themselves. Example: interest accruing on savings amplifies wealth; departures causing knowledge loss amplify departures.

**Balancing feedback loops** counteract change; they're goal-seeking. Example: a thermostat maintains temperature; a team hiring faster when understaffed maintains headcount.

From Meadows: "The information delivered by a feedback loop is the key to learning and self-correction in systems."

## In Tech Contexts

Feedback loops are everywhere in tech:

- **Team dynamics:** High departures → knowledge loss → slower development → missed deadlines → more departures (reinforcing)
- **Code quality:** Tight code review → catches bugs early → team confidence → more careful code → fewer bugs (balancing)
- **Technical debt:** Quick fixes → more tech debt → harder to implement features → more pressure for quick fixes → more debt (reinforcing)
- **Hiring:** Good team culture → attracts talent → better team → culture improves (reinforcing, but positive)
- **On-call burden:** Missing alerts → incidents missed → add more paging → team burned out → careless responses → more incidents (reinforcing)

The catch: many tech feedback loops are hidden. You don't see the departures feeding back into departures until 3-6 months of lag reveals it.

## Diagnostic Questions

Ask these to identify if feedback loops explain your problem:

1. **Does the problem get worse over time, even without new external pressure?** If yes, you likely have a reinforcing loop.
2. **If you tried to fix the symptom temporarily, did it come back?** If yes, you're fighting a feedback loop, not the root cause.
3. **Who or what opposes your attempts to fix the problem? Why?** The opposition is often another feedback loop.
4. **What happens after your change takes effect?** Does the system adjust in a way that undoes your change? (That's a balancing loop resisting you.)

## Intervention Levers

### 1. Break the Loop

**Why:** Interrupt the chain of cause-and-effect so the feedback no longer amplifies.

**How:** Identify the weakest link in the loop and sever it.

**Tech example:** High-churn on-call loop: engineers burned out → mistakes → incidents → more paging → more burnout.
- Break point: Automate alerts for common issues, so paging is less frequent.
- Result: On-call burden drops; fewer incidents from exhaustion; loop breaks.

### 2. Change the Goal (for balancing loops resisting your changes)

**Why:** If a balancing loop is resisting your change, it's because the system has a goal that opposes you. Change that goal.

**How:** Identify what the system is maintaining (the goal). Propose a new goal and provide a new feedback path to reach it.

**Tech example:** Team defaulting to quick fixes despite your push for refactoring.
- Current goal (implicit): Ship features fast
- Problem: This creates the debt loop
- New goal: Ship features fast AND maintain code quality
- New feedback: Measure code health metrics; reward both velocity and quality in performance reviews
- Result: Team now pursues both goals; loop rebalances.

### 3. Strengthen a Balancing Loop to Resist Degradation

**Why:** Some balancing loops prevent bad things (quality reviews catch bugs). Strengthen them.

**How:** Increase the sensitivity of the feedback and the speed of response.

**Tech example:** Code quality loop weakening (fewer code reviews, less feedback).
- Strengthen: Automated code quality checks (faster feedback), mandatory review even for quick fixes (consistent feedback)
- Result: Balancing loop maintains quality despite pressure for speed.

## Cross-References to Problems

This concept appears in these problems:

- [Retention Problem](../problems/retention.md) — Departures create a reinforcing loop
- [Velocity Decline](../problems/velocity-decline.md) — Debt accumulation is a reinforcing loop
- [Burnout](../problems/burnout.md) — Stress → mistakes → pressure → more stress is reinforcing
- [Scope Creep](../problems/scope-creep.md) — Unchecked feature requests create reinforcing feedback
- [Cross-Team Communication](../problems/cross-team-communication.md) — Miscommunication breeds more miscommunication

```

**Metadata:** This template covers all required sections. Each concept uses the same structure so readers and agents know what to expect.

---

## Part 2: Writing Guidelines

### YAML Frontmatter

**For Problems:**
```yaml
title: "Problem Title"
category: "Team & Culture | Product & Features | Infrastructure & Debt | Coordination"
related_concepts:
  - "Concept Name"
stocks:
  - "name of stock element"
flows:
  - "inflow: description"
  - "outflow: description"
feedback_loops:
  - description: "A → B → C → A"
    type: "reinforcing | balancing"
delays:
  - "description of delay"
limiting_factors:
  - "factor name"
```

**For Concepts:**
```yaml
concept_name: "Name"
concept_type: "balancing | reinforcing | structural"
related_problems:
  - "Problem Name"
intervention_categories:
  - "Category Name"
```

**Use YAML for structure, not hashtags.** Agents parse YAML; hashtags are invisible to them.

### Socratic Questions

Goal: Help someone diagnose their situation without giving answers.

**Pattern:**
- Open-ended (not yes/no)
- Build progressively (understand stocks first, then flows, then loops)
- Encourage observation, not assumptions
- Lead to self-discovery

**Bad:** "You have a reinforcing feedback loop, so you need to break it."

**Good:** "When X happens, what does the team do next? And when they do that, what happens to X? Does it get better or worse?"

### Concept Linking

**In YAML:** Use `related_concepts` and `related_problems` fields for machine-readable links.

**In Content:** Reference concepts by file link and explain why they're relevant. Example:
```markdown
This problem reveals [Feedback Loops](../concepts/feedback-loops.md) and [Delays](../concepts/delays.md).
See those concept deep-dives for strategies on intervening on these structures.
```

**Bidirectional:** Each problem links to concepts; each concept section includes "Cross-References to Problems."

### Real-World Examples

Each problem and intervention needs 1-2 realistic tech scenarios showing:
1. The problem as it appears (symptoms)
2. The system diagnosis (what's really happening)
3. The intervention applied
4. The result

**Make them concrete but generalizable.** Specific enough to be believable, abstract enough to apply across contexts.

---

## Part 3: Common Mistakes to Avoid

- **Prescriptive answers:** "You should do X" ← Wrong. "What happens if you...?" ← Right.
- **Missing metadata:** YAML frontmatter is how agents navigate. Don't skip it.
- **Vague feedback loops:** "departures cause retention" ← Circular. "departures → knowledge loss → onboarding friction → new hire frustration → more departures" ← Clear chain.
- **One-off examples:** Make sure your example is relatable to many tech teams, not specific to one company.
- **Broken links:** Every cross-reference to a problem or concept must exist as a file. Test links before committing.

---

## When to Extend This Framework

Adding a new problem:
1. Create `problems/{problem-name}.md` with the full template
2. Identify related concepts and add them to YAML
3. Update each related concept's file to add this problem to "Cross-References"
4. Add problem to Problem Gateway in `Systems Thinking.md`
5. Test all links

Adding a new concept:
1. Create `concepts/{concept-name}.md` with the full template
2. Identify related problems and add them to YAML
3. Update each related problem's file to add this concept to "Systems Concepts at Play"
4. Add concept to Concepts list in `Systems Thinking.md`
5. Test all links

---

## Summary

The hybrid problem-first + concept framework makes systems thinking immediately useful to practitioners while remaining structured enough for agents to reason with. YAML frontmatter enables machine readability; Socratic questions guide discovery; bidirectional linking connects the two halves.

Use this approach for any reference guide or decision-making framework where you want both human usability and agent compatibility.
```

- [ ] **Step 2: Review the methodology document**

Read through the file you just created. Check:
- Is the template clear enough that someone could fill it in and follow the style?
- Are the YAML frontmatter examples complete and correct?
- Are the writing guidelines specific enough?

- [ ] **Step 3: Commit**

```bash
git add "Frameworks/Systems Thinking/METHODOLOGY.md"
git commit -m "docs: add Systems Thinking methodology guide for reusable framework patterns"
```

---

## Task 3: Create Problem Gateway (Main Landing Page)

**Files:**
- Modify: `Frameworks/Systems Thinking/Systems Thinking.md`

**Interfaces:**
- Consumes: Nothing (this is the entry point)
- Produces: Problem Gateway index that links to all problem and concept deep-dives

- [ ] **Step 1: Write the Problem Gateway content**

```markdown
---
description: "Problem-first reference guide for applying systems thinking to tech problems"
---

# Systems Thinking Reference Guide

Applying Donella Meadows' systems thinking to problems technology workers face.

**How to use:** Find the problem that matches your situation. Work through the guided discovery questions to diagnose the system. Then explore the related concepts and interventions.

**For agents:** This guide is structured with YAML frontmatter for machine-readable system diagnostics (stocks, flows, feedback loops, delays). Each problem links to the concepts it reveals. You can traverse the structure to reason about system dynamics and suggest evidence-based interventions.

---

## Problem Gateway

### Team & Culture

- **[Retention Problem](problems/retention.md)** — Experienced engineers leaving at higher rates than expected. What system structures drive departures?

- **[Burnout & Stress](problems/burnout.md)** — Team members showing signs of exhaustion, reduced engagement, health impacts. How does workload translate to departures?

- **[Onboarding Friction](problems/onboarding-friction.md)** — New engineers take 3+ months to be productive; some leave before ramping up. What's slowing the learning loop?

### Product & Features

- **[Scope Creep](problems/scope-creep.md)** — Feature requests expand without clear boundaries; timelines slip; quality drops. How do unchecked requests amplify?

- **[Feature Bloat](problems/feature-bloat.md)** — Product accumulates features; users overwhelmed; maintenance burden grows. When do features become system burden?

### Infrastructure & Debt

- **[Architecture Debt](problems/architecture-debt.md)** — Codebase accumulating complexity, making changes slower and riskier. What feedback loops create debt spirals?

- **[Velocity Decline](problems/velocity-decline.md)** — Team throughput decreasing despite stable headcount and effort. What system changes cause slowdown?

### Coordination

- **[Cross-Team Communication](problems/cross-team-communication.md)** — Misalignment between teams, duplicate work, blocked dependencies, delayed decisions. How do communication delays amplify problems?

---

## Concept Guides

Learn the foundational systems thinking principles. Each concept explains how it manifests in tech and suggests intervention strategies.

- **[Feedback Loops](concepts/feedback-loops.md)** — How systems reinforce or balance themselves (reinforcing spirals, self-correcting systems)

- **[Stocks & Flows](concepts/stocks-and-flows.md)** — The building blocks of system behavior (what you can see vs. what changes over time)

- **[Delays](concepts/delays.md)** — Time lags that make systems hard to manage (information delays, action delays, effect delays)

- **[Hierarchy & Suboptimization](concepts/hierarchy.md)** — How subsystems can work against each other (teams optimizing for themselves, not the whole)

- **[Resilience](concepts/resilience.md)** — The ability of systems to recover and adapt (what makes teams and systems robust?)

- **[System Limits](concepts/limits.md)** — Resource constraints that govern behavior (why you can't just "work harder")

- **[System Traps](concepts/system-traps.md)** — Common problematic patterns (Policy Resistance, Tragedy of the Commons, Drift to Low Performance)

---

## How to Navigate

1. **You have a problem?** Find it in the Problem Gateway above. Read the problem deep-dive to diagnose your situation.

2. **Want to understand the underlying principle?** The problem deep-dive links to related concepts. Read those to see the pattern across different problems.

3. **Ready to intervene?** Each problem and concept deep-dive suggests specific levers. Choose interventions that match your system's structure.

4. **Building a similar guide for another topic?** Read [METHODOLOGY.md](METHODOLOGY.md) for the reusable framework.

---

## About This Guide

Source: Based on "Thinking in Systems" by Donella Meadows, adapted and applied to technology work contexts. All problems and interventions are drawn from real tech team patterns.

Feedback: Found a problem or concept we should cover? [Add it to the repo](https://github.com/adamweir/learning-in-public).
```

- [ ] **Step 2: Save the file**

The file is now `Frameworks/Systems Thinking/Systems Thinking.md` with the Problem Gateway.

- [ ] **Step 3: Verify the structure**

Check that:
- All problem links are correct relative paths: `problems/retention.md` (will be created in subsequent tasks)
- All concept links are correct relative paths: `concepts/feedback-loops.md` (will be created in subsequent tasks)
- Formatting is consistent (bold titles, bullet points, clear headings)

- [ ] **Step 4: Commit**

```bash
git add "Frameworks/Systems Thinking/Systems Thinking.md"
git commit -m "feat: create Systems Thinking Problem Gateway with navigation and overview"
```

---

## Task 4: Create Concept Deep-Dive — Feedback Loops

**Files:**
- Create: `Frameworks/Systems Thinking/concepts/feedback-loops.md`

**Interfaces:**
- Consumes: Nothing (this is a reference concept)
- Produces: Complete concept deep-dive with YAML metadata, explanation, tech context, diagnostic questions, interventions, cross-references

- [ ] **Step 1: Write the Feedback Loops concept file**

```markdown
---
concept_name: "Feedback Loops"
concept_types:
  - "Reinforcing"
  - "Balancing"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Burnout & Stress"
  - "Scope Creep"
  - "Cross-Team Communication"
intervention_categories:
  - "Break the loop"
  - "Change the goal"
  - "Adjust the structure"
  - "Slow the loop"
---

# Feedback Loops

## Explanation

A feedback loop is a chain of cause-and-effect where the output of a system feeds back as input, creating a cycle.

From Donella Meadows: "A feedback loop is the main reason why systems can regulate themselves and why they often run away." Feedback loops are the engine of system behavior.

### Two Types

**Reinforcing Feedback Loops** amplify change. Once started, they self-strengthen. The more of X, the more of X.
- Example: Compound interest. More money → more interest → more money.
- In teams: Departures → knowledge loss → slower delivery → team stress → more departures.
- Result: Systems can spiral out of control if unchecked.

**Balancing Feedback Loops** counteract change and seek goals. They resist perturbation and return to equilibrium.
- Example: A thermostat. Temperature rises → furnace off → temperature falls → furnace on.
- In teams: Bugs found in code review → reviewed more carefully → fewer bugs → slightly less review.
- Result: Systems self-correct and maintain stability.

Most real systems have both kinds, competing for control.

## In Tech Contexts

Feedback loops drive most team and product dynamics. Here are common ones:

### Reinforcing Loops (Self-Strengthening)

- **Departures spiral:** Engineers leave → knowledge lost → slower onboarding → new hires frustrated → new hires leave (seen in retention crises)
- **Debt acceleration:** Quick fixes → tech debt grows → harder to implement features → more time pressure for quick fixes → more debt (seen in velocity decline)
- **Burnout cycle:** Heavy workload → mistakes → rework → more workload → burnout → departures (seen in team stress)
- **Communication breakdown:** Miscommunication → duplicate work → frustration → less collaboration → more miscommunication (seen in cross-team friction)
- **Feature creep:** No clear feature boundaries → requests grow → scope expands → timeline slips → more pressure to add features (seen in scope creep)

### Balancing Loops (Self-Correcting)

- **Capacity management:** Team overloaded → work delays → features miss deadline → fewer requests → team catches up (natural friction-based equilibrium)
- **Code quality gates:** Bugs escape → incidents → team implements stricter reviews → fewer bugs escape (learning-based adjustment)
- **On-call rotations:** Engineer burned out → forces rest → returns refreshed → less burned out (rest-based equilibrium, if well-structured)

**The catch in tech:** Many balancing loops are weak or slow. Information delays mean you don't see the problem until the reinforcing loop has compounded. By then, correction is harder.

## Diagnostic Questions

Use these to identify feedback loops in your situation:

1. **Does the problem get worse over time despite your efforts to fix it?** If yes, you likely have a reinforcing loop fighting you.

2. **When you fix the symptom, does the problem come back?** Classic sign of a reinforcing loop. You're treating the symptom, not the structure.

3. **Is there something or someone opposing your fix? What's their incentive?** Opposition often signals a balancing loop resisting you, because the system has a goal that differs from yours.

4. **What happens in the weeks after you make a change?** Does the system drift back to the original state? That's a balancing loop reasserting equilibrium.

5. **If you trace the chain "X causes Y, Y causes Z, Z causes X" does it loop back?** If yes, you've found a feedback loop.

## Intervention Levers

### 1. Break the Loop (for reinforcing loops amplifying problems)

**Why it works:** Interrupt the chain so the loop can't feed back and amplify.

**Strategy:** Find the weakest link in the cause-and-effect chain. Sever it.

**Tech examples:**

- **Departures spiral:** The weakest link is knowledge transfer. When knowledge doesn't transfer, the loop amplifies. Intervene by doing explicit knowledge handoff before departures. Result: New hires ramp up faster, feel supported, are less likely to leave.

- **Tech debt acceleration:** The weakest link is decision-making under pressure. When schedule pressure drives quick fixes, debt grows. Intervene by building time for refactoring into the sprint, not after. Result: Debt grows slower, delivered speed stays higher.

- **Communication breakdown:** The weakest link is assumption-making during miscommunication. Intervene by slowing down initial decisions and confirming understanding. Result: Fewer compounded misunderstandings.

### 2. Change the Goal (for balancing loops resisting your changes)

**Why it works:** If a balancing loop resists you, it's because the system is pursuing a different goal than you are. Change the goal, and the loop rebalances around the new goal.

**Strategy:** Identify the implicit goal the system is maintaining. Propose a new goal and provide feedback to reach it.

**Tech example:**

- **"Ship fast" vs. "ship quality":** Team defaults to quick fixes because the goal (implicit) is feature velocity. You push for refactoring; the team resists because it doesn't advance velocity. Instead of fighting, add a new goal: "Maintain code health while shipping." Measure both velocity and quality. Reward both. The team now pursues both; the balancing loop rebalances around both goals.

### 3. Slow the Loop (to buy time for correction)

**Why it works:** If you can't break or redirect a reinforcing loop immediately, slow it down so you have time to implement better interventions.

**Strategy:** Increase delays in the feedback chain. Gives you time to respond.

**Tech example:**

- **Hiring bottleneck:** Departures → understaffed → pressure to hire faster → bad hiring decisions → new hires fail → departures. The loop is fast. Slow it down: implement temporary contractors to cover departures while you hire carefully. Slower loop = better hiring = fewer failures.

### 4. Strengthen a Balancing Loop (to increase stability)

**Why it works:** Some balancing loops keep things from getting worse. Strengthen them.

**Strategy:** Increase the sensitivity of feedback and speed of response.

**Tech example:**

- **Code quality reviews:** Team under pressure; code reviews slip. Bug escape rate climbs. Strengthen the loop: automate quality checks (faster feedback), require reviews even for small changes (consistent enforcement). The loop now catches problems faster.

## Cross-References to Problems

This concept is central to understanding these problems:

- [Retention Problem](../problems/retention.md) — Departures create a reinforcing loop; knowledge loss feeds back to cause more departures
- [Velocity Decline](../problems/velocity-decline.md) — Tech debt is a reinforcing loop; quick fixes feed back to slow future development
- [Burnout & Stress](../problems/burnout.md) — Stress → mistakes → pressure → more stress is a reinforcing spiral
- [Scope Creep](../problems/scope-creep.md) — Unchecked requests create a reinforcing loop where features expand unchecked
- [Cross-Team Communication](../problems/cross-team-communication.md) — Miscommunication breeds more miscommunication (reinforcing); unclear goals resist change (balancing)

---

## Summary

Feedback loops are why systems behave the way they do. Reinforcing loops drive crises; balancing loops resist change. In tech, the key insight is identifying which loop is dominant, then intervening at the weakest point in the chain.
```

- [ ] **Step 2: Verify the file**

Check:
- YAML frontmatter is complete and correct
- All related problems listed in YAML exist as files (or will be created)
- Cross-references at the bottom match the YAML `related_problems` list
- Code examples are concrete and relatable to tech teams
- Diagnostic questions build progressively

- [ ] **Step 3: Commit**

```bash
git add "Frameworks/Systems Thinking/concepts/feedback-loops.md"
git commit -m "docs: add Feedback Loops concept deep-dive"
```

---

## Task 5: Create Concept Deep-Dive — Stocks & Flows

**Files:**
- Create: `Frameworks/Systems Thinking/concepts/stocks-and-flows.md`

**Interfaces:**
- Consumes: Nothing (this is a reference concept)
- Produces: Complete concept deep-dive with YAML metadata, explanation, tech context, diagnostic questions, interventions

- [ ] **Step 1: Write the Stocks & Flows concept file**

```markdown
---
concept_name: "Stocks & Flows"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Onboarding Friction"
  - "Scope Creep"
intervention_categories:
  - "Change the inflow"
  - "Change the outflow"
  - "Change the stock"
---

# Stocks & Flows

## Explanation

Stocks and flows are the basic building blocks of any system. Understanding them is the foundation of systems thinking.

**A stock** is an accumulation of something you can see, measure, or count. It has a current level that changes over time.
- Examples: Water in a bathtub, engineers on a team, lines of code in a codebase, bugs in the backlog, knowledge in a team's collective experience

**A flow** is a rate of change. It's the rate at which something enters (inflow) or leaves (outflow) the stock.
- Examples: Faucet into a bathtub (inflow), drain from a bathtub (outflow), hiring rate (inflow to team), departure rate (outflow from team), code written (inflow), code deleted (outflow)

**The key insight:** The behavior of a stock depends on the balance between inflows and outflows. If inflows exceed outflows, the stock grows. If outflows exceed inflows, the stock shrinks. If they're equal, the stock stays the same.

From Donella Meadows: "Stocks are the foundation of system behavior. Stocks change slowly, even when flows change abruptly, because they accumulate."

## In Tech Contexts

Every tech system can be understood in terms of stocks and flows:

### Team Dynamics

- **Stock:** Pool of team members (engineers, designers, PMs)
- **Inflows:** Hiring, promotions from other teams, returning engineers
- **Outflows:** Departures, transfers to other teams, retirements
- **Behavior:** Team size stable when hiring = departures; growing when hiring > departures; shrinking when departures > hiring

### Code & Technical Debt

- **Stock:** Codebase complexity (lines of code, design complexity, interdependencies)
- **Inflows:** New features, changes to existing code, copy-paste of logic
- **Outflows:** Refactoring, deleting unused code, simplifying
- **Behavior:** Complexity grows slowly even when inflows spike, because refactoring is usually deprioritized

### Knowledge & Context

- **Stock:** Team knowledge (who knows what, tribal knowledge, design decisions)
- **Inflows:** Learning, documentation, knowledge transfer from departing engineers
- **Outflows:** Departures, forgetting, knowledge becoming obsolete
- **Behavior:** Knowledge declines slowly when departures happen, with lag (it takes weeks to realize what was lost)

### Backlog & Work

- **Stock:** Feature backlog or bug backlog
- **Inflows:** New requests, bugs found
- **Outflows:** Features shipped, bugs fixed
- **Behavior:** Backlog grows if inflows > outflows; shrinks if outflows > inflows

## Diagnostic Questions

Use these to identify stocks and flows in your situation:

1. **What are you trying to understand about your system? What's the "thing" that's accumulating or depleting?** That's your stock.

2. **What's coming in to that stock? What's the rate?** That's your inflow.

3. **What's leaving that stock? What's the rate?** That's your outflow.

4. **Is the stock growing, shrinking, or stable? Why?** Compare inflow to outflow.

5. **If the stock is growing, is that a problem or desired? If shrinking, is that a problem?** This tells you whether you need to change inflows or outflows.

6. **What controls the inflow? What controls the outflow?** These are your intervention points.

## Intervention Levers

### 1. Increase the Inflow (if stock is too low)

**Why it works:** To grow a stock, you need more coming in than going out.

**Tech examples:**

- **Team size growing:** Stock of engineers is too low. Increase inflow: hire faster, recruit from referrals, open roles in new locations. Result: Team grows.

- **Knowledge at risk:** Stock of team knowledge is declining. Increase inflow: document more, do more knowledge transfers from senior engineers, record design decision rationales. Result: Knowledge better preserved.

### 2. Decrease the Outflow (if stock is too low)

**Why it works:** To grow a stock, you can reduce what's leaving instead of increasing what's coming in. Often easier.

**Tech examples:**

- **Team departures high:** Stock of engineers shrinking. Decrease outflow: improve working conditions, fix team dynamics, create growth paths. Result: Fewer departures, team stabilizes or grows.

- **Code quality degrading:** Stock of quality code shrinking. Decrease outflow of quality: implement code reviews, pay down debt more proactively. Result: Quality maintained.

### 3. Increase the Outflow (if stock is too high)

**Why it works:** To shrink a stock (when that's desired), increase what's leaving.

**Tech examples:**

- **Backlog exploding:** Stock of feature requests growing unbounded. Increase outflow: ship features faster, prioritize ruthlessly, say no to requests. Result: Backlog doesn't grow out of control.

- **Technical debt piling up:** Stock of debt too high. Increase outflow: dedicate time to refactoring, delete dead code, simplify systems. Result: Debt decreases.

### 4. Change the Inflow or Outflow Rate (if stock behavior is unsustainable)

**Why it works:** Sometimes the rate of inflow or outflow is structural. You need to change the rate, not just do more/less of it.

**Tech examples:**

- **Hiring bottleneck:** Inflow of engineers limited by interview capacity. Change the structure: hire a recruiter, reduce interview rounds, implement async interviews. Result: Inflow rate increases.

- **Feature requests overwhelming:** Inflow of requests too high to handle. Change the structure: implement a prioritization committee, set a request budget per quarter, slow down how fast requests are added to backlog. Result: Inflow rate decreases or becomes manageable.

## The Delay Between Stock Changes and Flow Changes

**Important:** Flows change quickly, but stocks change slowly. A stock is an accumulation; it takes time to change.

**Example:** If you stop hiring, the team size doesn't immediately drop. If departures stay at current rates, the team shrinks slowly (over months). There's a lag.

**Consequence:** When you change a flow (hiring rate, departure rate), the stock response is delayed. This makes it easy to over-correct. You stop hiring because the team is "too big," but the stock takes months to shrink, and by then you're understaffed.

**Implication:** Change flows early, based on where you want the stock to be in 3-6 months. Don't wait for the current stock to tell you the flow is wrong.

## Cross-References to Problems

This concept is central to understanding these problems:

- [Retention Problem](../problems/retention.md) — Understand team size (stock) in terms of hiring (inflow) and departures (outflow)
- [Velocity Decline](../problems/velocity-decline.md) — Understand code complexity (stock) in terms of features added (inflow) and refactoring (outflow)
- [Onboarding Friction](../problems/onboarding-friction.md) — Understand team knowledge (stock) in terms of documentation and knowledge transfer (inflows) and departures (outflow)
- [Scope Creep](../problems/scope-creep.md) — Understand feature backlog (stock) in terms of requests (inflow) and shipping (outflow)

---

## Summary

Stocks and flows are how you make system behavior visible and measurable. To change a system, change the flows. Understanding the inflows and outflows tells you what's really happening and what levers you actually have.
```

- [ ] **Step 2: Verify the file**

Check:
- YAML frontmatter is complete
- Related problems exist or will be created
- Tech examples are concrete
- Diagnostic questions are clear

- [ ] **Step 3: Commit**

```bash
git add "Frameworks/Systems Thinking/concepts/stocks-and-flows.md"
git commit -m "docs: add Stocks & Flows concept deep-dive"
```

---

## Task 6: Create Concept Deep-Dive — Delays

**Files:**
- Create: `Frameworks/Systems Thinking/concepts/delays.md`

**Interfaces:**
- Consumes: Nothing (this is a reference concept)
- Produces: Complete concept deep-dive with YAML metadata, explanation, tech context, diagnostic questions, interventions

- [ ] **Step 1: Write the Delays concept file**

```markdown
---
concept_name: "Delays"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Velocity Decline"
  - "Cross-Team Communication"
  - "Burnout & Stress"
intervention_categories:
  - "Reduce the delay"
  - "Account for the delay"
  - "Use the delay as feedback"
---

# Delays

## Explanation

A delay is a lag between cause and effect in a system. The output of one part of the system takes time to reach the input of another part.

From Donella Meadows: "Delays in feedback are major causes of instability in systems."

Delays can occur in:
- **Information:** Time for information to reach decision-makers
- **Decision-Making:** Time to decide how to respond
- **Action:** Time to implement a response
- **Effect:** Time for the action to have an observable impact

Most systems have multiple delays layered on top of each other. The longer the total delay, the harder the system is to manage.

## In Tech Contexts

Delays are everywhere in tech and often invisible until they cause a crisis:

### Information Delays

- **Bug discovery:** Bug introduced today; discovered in QA next week; reported to team day after that. By the time the team knows, the damage is compounded.
- **Departures:** Engineer decides to leave; goes through notice period. Knowledge loss doesn't become apparent until weeks into their absence.
- **Technical debt:** Debt accumulates slowly; is "fine" until velocity suddenly drops.
- **On-call incidents:** Alert fires; engineer wakes up; diagnoses; responds. Hours pass before incident is resolved.

### Decision Delays

- **Hiring decisions:** Candidate interviews with team; team discusses; offer takes weeks to extend. By then, candidate accepted another role.
- **Prioritization:** New critical issue arises; stakeholders debate priority; team doesn't change direction for 2 sprints.

### Action Delays

- **Hiring:** Decide to hire; post job; interview; offer; onboard. Months pass before new engineer is productive.
- **Refactoring:** Identify technical debt; schedule refactoring work; complete it; measure impact. Months between identification and improvement.

### Effect Delays

- **Culture changes:** Implement new team policy; team needs weeks to adjust; impact on morale takes months to appear.
- **Code quality improvements:** Implement stricter code review; bug escape rate doesn't immediately drop (there's a lag for the culture to absorb the change).

### Cascading Delays

Often you have all four layered. Example: High departures.
- Information delay: Takes 2 months for knowledge loss to show up as reduced velocity
- Decision delay: Takes 1 month to decide to hire and open the role
- Action delay: Takes 2 months to hire and onboard
- Effect delay: Takes 3 months for new hire to be fully productive

**Total delay: 8 months.** Between the time the problem appears and the time the solution has effect, 8 months pass. The team is understaffed the whole time, causing more stress and departures.

## Diagnostic Questions

Use these to identify delays in your situation:

1. **When did you first notice this problem?** When did it actually start? What's the lag?

2. **From the time you noticed, how long before you responded?** That's your decision delay.

3. **From the time you decided to respond, how long before you took action?** That's your action delay.

4. **From the time you took action, how long before you saw the impact?** That's your effect delay.

5. **What information gaps exist?** Are you missing early warning signs? (Information delay)

6. **If you had known about the problem earlier, would you have responded differently?** If yes, you have a critical information delay.

## Intervention Levers

### 1. Reduce the Delay (often the most effective)

**Why it works:** Shorter delays mean faster feedback and faster correction. Systems with short feedback loops are easier to manage.

**Tech examples:**

- **Reduce information delay on departures:** Instead of discovering knowledge loss 2 months after a departure, do structured knowledge transfer before the departure happens. Result: New hires onboard 50% faster.

- **Reduce decision delay on hiring:** Instead of waiting for budget cycles to hire, implement standing hiring authorization. When a departure happens, open a role immediately. Result: Gap period shortens by weeks.

- **Reduce effect delay on code quality:** Instead of waiting for quarterly metrics to see if code quality improved, measure daily. Use live dashboards showing bug escape rate, review turnaround, complexity. Result: Team responds faster to quality issues.

- **Reduce action delay on bug fixes:** Instead of waiting for the next sprint to fix critical bugs, have a fast-track process that pulls engineers off current work for urgent issues. Result: Bug-to-fix time drops from weeks to hours.

### 2. Account for the Delay (when you can't reduce it)

**Why it works:** If you can't shorten the delay, you can compensate by acting sooner.

**Tech examples:**

- **Hiring lag:** You know it takes 3 months from "decide to hire" to "new engineer productive." So when you first notice understaffing, start hiring immediately. Don't wait for metrics to confirm it's bad. Result: By the time the shortage hits, the new hire is onboarding.

- **Debt accumulation:** You know debt takes 6 months to noticeably slow velocity. So when you spot early signs of debt (declining code review quality, increasing hotfixes), start paying it down immediately. Don't wait for velocity to drop. Result: You prevent the slowdown instead of reacting to it.

### 3. Use the Delay as Feedback (change what you're measuring)

**Why it works:** If there's a 3-month delay before effect shows up, don't measure the outcome. Measure the leading indicator earlier in the chain.

**Tech examples:**

- **Onboarding:** Instead of measuring "new hire productivity at 3 months," measure earlier indicators: "knowledge transfer sessions completed in week 2," "new hire confidence at week 4," "first significant contribution at week 6." These have shorter delays and give you feedback sooner.

- **Code quality:** Instead of waiting for production bugs to measure quality, measure code review thoroughness (short delay), test coverage (short delay), complexity of merged code (short delay). These warn you if quality is drifting before bugs appear.

## The Danger of Delays: Over-Correction

**Common failure mode:** Decision-makers don't see the delay, think their previous fix didn't work, and over-correct.

**Example:**
- Month 0: Decide to hire to fix understaffing
- Month 3: No change yet (still in hiring lag); frustration sets in
- Month 3: Assume hiring won't work; start contracting instead
- Month 5: Contractor arrives; hired engineer arrives; suddenly overstaffed
- Month 6: Panic; freeze hiring; reduce contractor; now understaffed again

**Solution:** Understand the delays. Know when to expect impact. Don't over-correct.

## Cross-References to Problems

This concept is central to understanding these problems:

- [Retention Problem](../problems/retention.md) — Long delays between departures and visible impact make the problem worse by the time you respond
- [Velocity Decline](../problems/velocity-decline.md) — Tech debt has a 6-month lag before impact; by then, it's compounded
- [Cross-Team Communication](../problems/cross-team-communication.md) — Miscommunication feedback loops are slow; problems compound before they're visible
- [Burnout & Stress](../problems/burnout.md) — Burnout lag means you don't see departures coming until they happen

---

## Summary

Delays are invisible until they cause problems. Understanding where they are, how long they are, and what they're between is critical to managing systems well. Shorter delays = faster feedback = easier to manage.
```

- [ ] **Step 2: Verify the file**

Check:
- YAML frontmatter complete
- Examples show both the delay itself and the consequence of missing it
- Diagnostic questions help identify specific delays

- [ ] **Step 3: Commit**

```bash
git add "Frameworks/Systems Thinking/concepts/delays.md"
git commit -m "docs: add Delays concept deep-dive"
```

---

## Task 7: Create Remaining Concept Deep-Dives (Hierarchy, Resilience, Limits, System Traps)

**Files:**
- Create: `Frameworks/Systems Thinking/concepts/hierarchy.md`
- Create: `Frameworks/Systems Thinking/concepts/resilience.md`
- Create: `Frameworks/Systems Thinking/concepts/limits.md`
- Create: `Frameworks/Systems Thinking/concepts/system-traps.md`

**Interfaces:**
- Consumes: Concepts from previous tasks
- Produces: Four complete concept deep-dives

**Note:** Due to length, I'll provide the structure and key content for each. Follow the same template as Feedback Loops, Stocks & Flows, and Delays. Each file should have:
- YAML frontmatter with related_problems
- Explanation section
- In Tech Contexts section
- Diagnostic Questions
- Intervention Levers (2-4 strategies each)
- Cross-References to Problems

- [ ] **Step 1: Create hierarchy.md**

```markdown
---
concept_name: "Hierarchy & Suboptimization"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Cross-Team Communication"
  - "Scope Creep"
intervention_categories:
  - "Clarify subsystem goals"
  - "Align incentives"
  - "Increase communication"
---

# Hierarchy & Suboptimization

## Explanation

Complex systems are organized into subsystems (teams, departments, components). Each subsystem has its own goals. The danger: a subsystem optimizing for itself, ignoring the whole system.

**Suboptimization** happens when a subsystem's goals dominate at the expense of the total system's goals.

From Donella Meadows: "The problem in any hierarchical system is that subsystems can pursue their own purposes and gain at the expense of the whole system."

## In Tech Contexts

Every organization has hierarchies:

### Team-Level Suboptimization

- **Engineering vs. Product:** Engineering optimizes for clean code; Product optimizes for feature velocity. Result: Conflict over technical debt.
- **Frontend vs. Backend:** Frontend team optimizes for UI responsiveness; Backend optimizes for data accuracy. Result: Misaligned API design.
- **Your team vs. others:** Your team optimizes for its own velocity; other teams optimize for theirs. Result: Shared codebases become battlegrounds.

### Department-Level Suboptimization

- **Engineering vs. Sales:** Engineering optimizes for product quality; Sales optimizes for closing deals. Result: Promises made the product can't deliver.
- **Finance vs. Engineering:** Finance optimizes for cost; Engineering optimizes for quality and speed. Result: Understaffing, burnout, worse quality.

### Individual-Level Suboptimization

- **You vs. the team:** You optimize for your career growth; the team optimizes for collective output. Result: You take on glamorous projects while the team is stuck with unsexy work.
- **Team member vs. team:** Engineer optimizes for job security (writes complicated code); team optimizes for maintainability (wants simple code). Result: Tribal knowledge, high dependency on individual.

## Diagnostic Questions

1. **What are the goals of each major subsystem (team, component, individual)?** List them explicitly.
2. **Do any subsystems pursue their goals at the expense of others?** How?
3. **Is there conflict between subsystems? What's the underlying goal misalignment?**
4. **Who feels like their subsystem is not winning?** What are they frustrated about?
5. **If you optimized the subsystem perfectly, would the whole system improve?** If not, you have suboptimization.

## Intervention Levers

### 1. Clarify and Align Subsystem Goals with System Goals

**Why it works:** If subsystems understand the whole system's goal and how their subsystem contributes, they can pursue both.

**Tech example:** Engineering and Product perpetually in conflict over technical debt. Solution: Clarify system goal: "Ship valuable features sustainably." Engineering's subgoal: "Maintain code health so we can ship features faster." Product's subgoal: "Prioritize features that matter most." Now both subsystems can pursue their subgoal while serving the whole goal.

### 2. Change Subsystem Incentives to Align with System Goals

**Why it works:** People optimize for what you measure and reward.

**Tech example:** Frontend team measured on UI responsiveness; Backend team measured on data consistency. Result: Conflict. Solution: Measure both on "feature delivery speed and quality." Now they collaborate to both deliver fast and deliver right.

### 3. Increase Information Flow Between Subsystems

**Why it works:** Suboptimization often happens because subsystems don't see the consequences of their choices on others.

**Tech example:** Frontend and Backend teams don't talk about API design until too late. Solution: Require API design review and feedback from both teams before implementation. Frontend sees the Backend implications; Backend sees the Frontend constraints. Better decisions.

## Cross-References to Problems

- [Retention Problem](../problems/retention.md) — Suboptimization: Individual wants growth; team wants stability; company wants velocity. Misalignment causes departures.
- [Cross-Team Communication](../problems/cross-team-communication.md) — Teams optimizing for themselves create silos and miscommunication.
- [Scope Creep](../problems/scope-creep.md) — Product team optimizes for feature count; Engineering optimizes for sustainability. Misalignment enables scope to explode.

---

## Summary

Hierarchies are necessary for complex systems to function. But they create the danger of suboptimization. The solution is to clarify how each subsystem's goals serve the whole system's goal.
```

- [ ] **Step 2: Create resilience.md**

```markdown
---
concept_name: "Resilience"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Burnout & Stress"
  - "Onboarding Friction"
  - "Cross-Team Communication"
intervention_categories:
  - "Build feedback loops"
  - "Encourage diversity"
  - "Enable adaptation"
---

# Resilience

## Explanation

Resilience is the ability of a system to bounce back after being stretched. A resilient system absorbs perturbations and returns to function. A non-resilient system breaks under stress.

From Donella Meadows: "Resilience is a system's ability to survive, to adapt, to evolve."

Resilient systems have:
- **Many feedback loops** that help correction happen quickly
- **Diversity** (many ways to do things, not just one optimal path)
- **Flexibility** (ability to change structure in response to change)
- **Learning capacity** (ability to improve based on what happened)

## In Tech Contexts

Team resilience determines whether you survive crises or collapse under them:

### High-Resilience Teams

- Can absorb key person departures without falling apart (knowledge is distributed, not bottlenecked)
- Can handle surprise emergencies (have slack capacity, flexible priorities)
- Can adapt to market changes (not locked into one way of working)
- Learn from failures and improve (post-mortems lead to change, not blame)

### Low-Resilience Teams

- Brittle: key person leaves, team falters
- Tightly-coupled: one failure cascades to everything else
- Static: can't adapt to change, do the same thing even when it's not working
- Blame-focused: failures are hidden, not learned from

## Diagnostic Questions

1. **If your top engineer left tomorrow, what would break?** How long to recover?
2. **If a major project failed, what would you do?** Would you learn and adapt, or repeat the same thing?
3. **How much spare capacity does your team have?** Can you handle surprises, or are you at 100% utilization?
4. **How many ways can your team accomplish its core work?** (dependency on specific tools, specific people, specific approaches) More ways = more resilient.
5. **After failures, do you improve or blame?** Learning = resilience; blame = brittleness.

## Intervention Levers

### 1. Distribute Knowledge (Reduce Single Points of Failure)

**Why it works:** Knowledge bottlenecks are fragility points. Distribute knowledge so departures don't break the system.

**Tech example:** Only one engineer knows how the payment system works. That's fragility. Distribute knowledge: pair junior engineer with payment expert, document design decisions, record architecture videos. Now two people know; if one leaves, the other can handle it.

### 2. Build Slack Capacity (Flexibility to Handle Surprises)

**Why it works:** Teams at 100% utilization have no flexibility. They break when emergencies happen. Slack capacity = resilience.

**Tech example:** Teams working at capacity: one incident takes down everything. Solution: 20% slack time for learning, cleanup, handling unexpected issues. When an emergency happens, team has capacity to respond without dropping everything.

### 3. Encourage Experimentation and Learning (Adaptive Capacity)

**Why it works:** Static systems break when the world changes. Systems that learn and adapt survive.

**Tech example:** Team tries a new process; it fails; they blame and revert to old process. Brittle. Alternative: team tries new process; it fails; they examine why, extract lessons, iterate. Result: Team adapts over time; processes improve.

## Cross-References to Problems

- [Retention Problem](../problems/retention.md) — Team resilient to departures if knowledge is distributed; brittle if concentrated
- [Burnout & Stress](../problems/burnout.md) — Lack of slack capacity forces people to work at unsustainable pace
- [Onboarding Friction](../problems/onboarding-friction.md) — Resilient teams have mentoring loops and onboarding processes; brittle teams leave people to figure it out

---

## Summary

Resilience is not about being perfect; it's about being able to bounce back from failure. Build it through distributed knowledge, slack capacity, and learning from failures.
```

- [ ] **Step 3: Create limits.md**

```markdown
---
concept_name: "System Limits"
concept_types:
  - "Structural"
related_problems:
  - "Velocity Decline"
  - "Burnout & Stress"
  - "Onboarding Friction"
  - "Cross-Team Communication"
intervention_categories:
  - "Identify the limiting factor"
  - "Remove the constraint"
  - "Shift the constraint"
---

# System Limits

## Explanation

Every system has limits. Limits are constraints on growth or performance. A system is always limited by one factor (the most restrictive one) called the **limiting factor** or **constraint**.

From Donella Meadows: "The system can only be as fast as its bottleneck. Improving the non-bottleneck doesn't help."

The key insight: Identify which factor is the actual limit. Improve that. Improving other things doesn't matter.

## In Tech Contexts

### Common Limiting Factors

- **People:** Not enough engineers, PMs, or designers. You can't go faster because you don't have hands.
- **Attention:** People are distracted or spread too thin. You have bodies but not focus.
- **Knowledge:** Team doesn't understand how to build what's needed. You have people but not skills.
- **Infrastructure:** Systems can't handle the load. You have people but the infrastructure is the bottleneck.
- **Decisions:** Decisions are slow to happen. Work is blocked on decisions, not on execution.
- **Coordination:** Teams can't align. Effort is wasted on duplicate work or rework.

### Finding the Actual Limit

The actual limit is often counterintuitive. You think it's "we need more engineers," but the real limit is "we have decision-making bottlenecks." Improve the wrong thing, waste effort.

## Diagnostic Questions

1. **What's preventing you from going faster?** (Not what you think; what actually is?)
2. **If you added one more engineer, would velocity increase?** If not, people isn't the limit.
3. **If you made faster decisions, would velocity increase?** If not, decision speed isn't the limit.
4. **If you improved infrastructure, would velocity increase?** If not, infrastructure isn't the limit.
5. **What factor, if improved, would most increase performance?** That's the limiting factor.

## Intervention Levers

### 1. Identify the Actual Limiting Factor (Before Improving Anything)

**Why it works:** Improving the wrong thing wastes effort. Improve the limit; everything else follows.

**Tech example:** Team thinks they're slow because they don't have enough engineers. But investigation reveals: engineers are context-switching across 6 projects; each context switch is a day of lost productivity. Limiting factor: project prioritization, not headcount. Hire more engineers; no improvement. Fix prioritization; big improvement.

### 2. Remove or Shift the Constraint

**Why it works:** Once you identify the limit, you can address it directly.

**Tech examples:**

- **Limit: Slow decisions.** Solution: Delegate decision-making authority. Decisions made locally are faster.
- **Limit: Knowledge gap.** Solution: Hire for skills or do training. Build knowledge.
- **Limit: Infrastructure.** Solution: Scale infrastructure or redesign for efficiency.
- **Limit: Coordination overhead.** Solution: Restructure teams to reduce coordination needs (split by feature, not by layer).

### 3. Manage Multiple Limits (Avoid Whack-a-Mole)

**Why it works:** Once you remove one limit, the next limit becomes visible. Plan for this.

**Tech example:** You identify hiring as the limit. Hire aggressively. Now you've hired a lot of junior engineers and onboarding becomes the limit (they're not productive). You then onboard faster. Now decision-making becomes the limit. Planning for this cascade prevents surprise and waste.

## Cross-References to Problems

- [Velocity Decline](../problems/velocity-decline.md) — Identify whether limit is people, knowledge, decisions, or tech debt
- [Burnout & Stress](../problems/burnout.md) — Limit often isn't "work harder"; it's "remove the constraint" (context switching, unclear priorities, etc.)
- [Onboarding Friction](../problems/onboarding-friction.md) — Limiting factor is often knowledge transfer process, not time available

---

## Summary

Systems are limited by their bottleneck. Find the bottleneck. Fix the bottleneck. Ignore the rest.
```

- [ ] **Step 4: Create system-traps.md**

```markdown
---
concept_name: "System Traps"
concept_types:
  - "Structural"
related_problems:
  - "Retention Problem"
  - "Cross-Team Communication"
  - "Velocity Decline"
  - "Scope Creep"
intervention_categories:
  - "Recognize the pattern"
  - "Break the loop"
  - "Realign goals"
---

# System Traps

## Explanation

System traps are recurring patterns of problematic behavior that arise from system structure. They're archetypes: system structures that produce the same problematic pattern across different domains.

The key insight: Once you recognize the pattern, you recognize the intervention. Different domains, same solution.

From Donella Meadows: "System traps are everywhere. But once you understand the structure, you can see the solution."

## Common Tech Traps

### 1. Policy Resistance (Fighting Each Other)

**The Pattern:** Attempts to fix a problem fail because different actors have conflicting goals and the system has feedback loops that oppose your solution.

**Example:** War on Drugs. Government tries to reduce drug use. But drug users want more drugs, dealers want more profit, citizens want community safety. Each group works against the others. More enforcement → more profit for dealers → more drug use. Everyone's effort cancels out.

**In Tech:**
- Engineering pushes for technical debt paydown; Product pushes for features. Engineering does refactoring; it slows feature velocity; Product resists. Nothing changes.
- You decide to enforce code quality standards; team sees this as blocking their work; they find workarounds. Standards don't improve.

**Why it happens:** Suboptimized goals (different actors have conflicting goals). The system amplifies opposition.

**Solution:** Find the overarching goal everyone can agree on. Align subsystems around that goal. Example: "Ship valuable features sustainably." Now Engineering and Product both pursue this. Engineering does debt paydown to ship faster sustainably. Product prioritizes features that matter. Both work toward the same goal.

### 2. Tragedy of the Commons (Shared Resources, Individual Incentives)

**The Pattern:** A shared resource degrades because each actor benefits from using it but doesn't bear the full cost of degradation. Rational individual action = irrational collective outcome.

**Example:** Fishery. If I fish more, I profit. If everyone fishes more, the fishery collapses. But I can't control everyone, so I fish as much as I can. Tragedy: fishery collapses.

**In Tech:**
- Shared codebase. Each team benefits from adding features quickly (their bonus). Nobody owns the codebase, so no one feels cost of debt. Result: Codebase degrades; everyone eventually suffers.
- Shared on-call rotation. Each engineer benefits from not being on-call. Cost of escalating alerts is shared. Result: Alert standards degrade; everyone burns out on-call eventually.

**Why it happens:** Individual incentives ≠ collective good. No clear ownership of the shared resource.

**Solutions:**
1. **Educate and exhort:** Show people the consequences of their actions. Appeal to shame or threat.
   - Example: Show codebase quality metrics. Name top offenders. Public accountability.
2. **Privatize the commons:** Give each person/team ownership so they feel the consequences.
   - Example: Assign codebase sections to teams. Teams own quality of their section. Result: Standards improve locally.
3. **Regulate the commons:** Central authority sets rules and enforces them.
   - Example: Require code review for all PRs. Enforce it. Standards improve by rule.

### 3. Drift to Low Performance (Shifting Baselines)

**The Pattern:** Standards slip gradually. What was unacceptable becomes acceptable. The baseline keeps shifting down, and nobody notices until you're at crisis.

**Example:** Frog in boiling water. If you drop a frog in hot water, it jumps out. But if you put it in cool water and gradually heat it, it doesn't jump; it boils. Shifting baseline.

**In Tech:**
- Code review quality slips over time. First 3 comments per review; then 2; then 1; then "looks good lgtm". One day you realize nobody reviews code anymore.
- On-call response time slips. First hour response SLA; eventually it's 4 hours. Nobody remembers when it was better.
- Meeting effectiveness. First all meetings have agendas and decisions. Then some don't. Now none do. Meetings become chaotic.

**Why it happens:** Changes are gradual. Baseline shifts so slowly nobody notices. Past standards become invisible.

**Solution:** Make standards explicit and visible. Measure them. Review them regularly.
- Example: Document code review standards. Measure adherence. Monthly review of metrics. If slipping, discuss and reset standards.

## Diagnostic Questions

1. **Do attempts to fix this problem seem to make it worse?** Possible: Policy Resistance.
2. **Are there shared resources being degraded?** Possible: Tragedy of the Commons.
3. **Have standards drifted down over time?** Possible: Drift to Low Performance.
4. **Who benefits from current behavior, even if it's collectively bad?** Understanding incentives helps you solve it.

## Intervention Levers

### For Policy Resistance

1. **Align goals:** Find an overarching goal everyone can pursue.
2. **Remove opposition:** Understand what incentivizes opposition; change the incentive.
3. **Increase feedback:** Make consequences of each actor's behavior more visible to them.

### For Tragedy of the Commons

1. **Assign ownership:** Give someone/some team responsibility for the resource.
2. **Measure and enforce:** Track degradation and enforce standards.
3. **Change individual incentives:** Reward stewardship of the commons, not just individual gain.

### For Drift to Low Performance

1. **Make standards explicit:** Write down what the standard is.
2. **Measure regularly:** Track the metric; make it visible.
3. **Review and reset:** When slipping, explicitly discuss and reset the standard.

## Cross-References to Problems

- [Retention Problem](../problems/retention.md) — Can reflect Policy Resistance (your goal: stability; employee's goal: growth; misaligned) or Tragedy of Commons (team's goal: speed; nobody owns sustainability).
- [Cross-Team Communication](../problems/cross-team-communication.md) — Often Policy Resistance (teams optimizing for themselves, resisting alignment) or Tragedy of Commons (nobody owns communication quality).
- [Velocity Decline](../problems/velocity-decline.md) — Tech debt is often Tragedy of Commons (everyone benefits from quick fixes, nobody owns quality) or Drift to Low Performance (quality standards slip over time).
- [Scope Creep](../problems/scope-creep.md) — Feature requests are Tragedy of Commons (everyone benefits from their feature request, cost shared).

---

## Summary

System traps are structures that create predictable bad outcomes. Once you recognize which trap you're in, the intervention becomes clear.
```

- [ ] **Step 5: Verify all files**

Run:
```bash
ls -la "Frameworks/Systems Thinking/concepts/"
```

Expected: All seven concept files exist (feedback-loops.md, stocks-and-flows.md, delays.md, hierarchy.md, resilience.md, limits.md, system-traps.md)

- [ ] **Step 6: Commit**

```bash
git add "Frameworks/Systems Thinking/concepts/"
git commit -m "docs: add four remaining concept deep-dives (hierarchy, resilience, limits, traps)"
```

---

## Task 8: Create Problem Deep-Dives (Phase 1: Top 5 Problems)

**Files:**
- Create: `Frameworks/Systems Thinking/problems/retention.md`
- Create: `Frameworks/Systems Thinking/problems/velocity-decline.md`
- Create: `Frameworks/Systems Thinking/problems/architecture-debt.md`
- Create: `Frameworks/Systems Thinking/problems/onboarding-friction.md`
- Create: `Frameworks/Systems Thinking/problems/cross-team-communication.md`

**Interfaces:**
- Consumes: Concept deep-dives created in Task 7
- Produces: Complete problem deep-dives with YAML metadata, diagnosis, Socratic questions, interventions, examples

**Note:** Due to length, I'm providing structure for Phase 1 (5 problems). Additional problems (Scope Creep, Burnout, Feature Bloat) can be added in Phase 2.

- [ ] **Step 1: Create retention.md (detailed template)**

Use the template from Task 2 (METHODOLOGY.md). Fill in with:
- YAML: title, category, related_concepts, stocks, flows, feedback_loops (departures→knowledge loss→onboarding friction→departures), delays, limiting_factors
- Problem Statement
- System Diagnosis (detailed)
- Guided Discovery Questions (7-8 questions building progressively)
- Diagnosis Checkpoint
- Systems Concepts at Play (Feedback Loops, Delays, Hierarchy)
- Intervention Strategies (4-5 concrete levers: Break knowledge loss loop, Reduce hiring delay, Align goals, Increase inflow)
- Tech Examples (2 scenarios)

(Due to length constraints, I'm not including the full text here. Follow the template from Task 2 with the content from "Thinking in Systems.md")

- [ ] **Step 2: Create velocity-decline.md**

Similar structure:
- YAML: related_concepts (Feedback Loops, Stocks & Flows, Delays, Limits)
- Problem Statement: Team throughput decreasing despite stable headcount
- System Diagnosis: Tech debt feedback loop, cumulative effects
- Guided Questions about debt inflow/outflow, decision pressures, refactoring capacity
- Interventions: Reduce debt inflow (enforce quality), increase outflow (schedule refactoring), reduce pressure for quick fixes

- [ ] **Step 3: Create architecture-debt.md**

- YAML: related_concepts (Feedback Loops, Stocks & Flows, Limits)
- Problem Statement: Codebase complexity makes changes riskier and slower
- System Diagnosis: Quick fixes add complexity; complex code takes longer to change; pressure increases for more quick fixes
- Guided Questions about design patterns, refactoring practices, decision-making under pressure
- Interventions: Break the quick-fix loop, increase refactoring capacity, change project structure to reduce coupling

- [ ] **Step 4: Create onboarding-friction.md**

- YAML: related_concepts (Delays, Stocks & Flows, Resilience)
- Problem Statement: New engineers take 3+ months to be productive; some leave early
- System Diagnosis: Knowledge transfer (inflow of context) is missing; learning delays; junior frustration
- Guided Questions about knowledge documentation, mentoring, feedback speed
- Interventions: Accelerate knowledge transfer (pair programming, documentation), reduce learning delays (daily feedback), build mentoring feedback loops

- [ ] **Step 5: Create cross-team-communication.md**

- YAML: related_concepts (Delays, Hierarchy, Policy Resistance, Tragedy of Commons)
- Problem Statement: Teams misaligned; duplicate work; blocked dependencies; decisions slow
- System Diagnosis: Information delay (decisions don't propagate), goal misalignment (teams optimize for themselves), missing feedback loops (no shared metrics)
- Guided Questions about decision-making, information sharing, goal clarity
- Interventions: Reduce information delay (shared channels, weekly syncs), align goals (shared metrics), increase feedback (dependencies visible)

- [ ] **Step 6: For each file, follow the template from Task 2**

Each file should have:
- Complete YAML frontmatter
- All sections from the methodology template
- 7-8 Socratic discovery questions
- 4-5 concrete interventions with "why it works" + "how" + "tech example"
- 2 realistic tech scenarios showing diagnosis and intervention

- [ ] **Step 7: Verify links**

Each problem file should reference existing concept files. Verify:
- All concept links in YAML `related_concepts` field exist
- All concept cross-references in content link to existing concept files (`../concepts/...`)
- Links are relative paths and will work in the directory structure

- [ ] **Step 8: Commit**

```bash
git add "Frameworks/Systems Thinking/problems/"
git commit -m "docs: add Phase 1 problem deep-dives (retention, velocity, debt, onboarding, communication)"
```

---

## Task 9: Update Problem Gateway to Reflect Phase 1

**Files:**
- Modify: `Frameworks/Systems Thinking/Systems Thinking.md`

**Interfaces:**
- Consumes: Problem deep-dives created in Task 8
- Produces: Updated Problem Gateway with correct links to Phase 1 problems

- [ ] **Step 1: Update the Systems Thinking.md file**

In the Problem Gateway section, update:
- Add 1-sentence descriptions to each problem (copy from problem file Problem Statement)
- Verify all links to `problems/...` files match the filenames you created
- Mark other problems (Scope Creep, Burnout, Feature Bloat) as "Coming Soon" or remove them from Phase 1

Example:
```markdown
- **[Retention Problem](problems/retention.md)** — Experienced engineers leaving at higher rates than expected. Diagnose the feedback loops driving departures.
```

- [ ] **Step 2: Verify all links work**

Run:
```bash
grep -r "problems/" "Frameworks/Systems Thinking/Systems Thinking.md"
```

Expected: All problem links match filenames in `Frameworks/Systems Thinking/problems/`

- [ ] **Step 3: Commit**

```bash
git add "Frameworks/Systems Thinking/Systems Thinking.md"
git commit -m "feat: update Problem Gateway with Phase 1 problems and descriptions"
```

---

## Task 10: Final Verification and Documentation

**Files:**
- Verify: All markdown files
- Verify: All YAML frontmatter
- Verify: All cross-links

**Interfaces:**
- Consumes: All files from Tasks 1-9
- Produces: Verified, working Systems Thinking reference guide

- [ ] **Step 1: Verify all files exist**

Run:
```bash
find "Frameworks/Systems Thinking" -name "*.md" -type f | sort
```

Expected output (or similar):
```
Frameworks/Systems Thinking/METHODOLOGY.md
Frameworks/Systems Thinking/Systems Thinking.md
Frameworks/Systems Thinking/concepts/delays.md
Frameworks/Systems Thinking/concepts/feedback-loops.md
Frameworks/Systems Thinking/concepts/hierarchy.md
Frameworks/Systems Thinking/concepts/limits.md
Frameworks/Systems Thinking/concepts/resilience.md
Frameworks/Systems Thinking/concepts/stocks-and-flows.md
Frameworks/Systems Thinking/concepts/system-traps.md
Frameworks/Systems Thinking/problems/architecture-debt.md
Frameworks/Systems Thinking/problems/cross-team-communication.md
Frameworks/Systems Thinking/problems/onboarding-friction.md
Frameworks/Systems Thinking/problems/retention.md
Frameworks/Systems Thinking/problems/velocity-decline.md
```

- [ ] **Step 2: Spot-check YAML frontmatter**

Sample a few files and verify YAML is valid:

Run:
```bash
head -20 "Frameworks/Systems Thinking/problems/retention.md"
```

Expected: Valid YAML with `---` delimiters, fields like `title`, `related_concepts`, etc.

- [ ] **Step 3: Spot-check cross-references**

Verify a few problem files reference existing concepts:

Run:
```bash
grep "concepts/" "Frameworks/Systems Thinking/problems/retention.md" | head -5
```

Expected: Links like `[Feedback Loops](../concepts/feedback-loops.md)` that point to existing files

- [ ] **Step 4: Verify structure is agent-friendly**

Scan one problem file to ensure:
- YAML frontmatter at top with `---` delimiters
- Clear section headings (## Explanation, ## In Tech Contexts, etc.)
- Structured lists (bullets, numbers) for data
- Consistent formatting

- [ ] **Step 5: Final commit**

```bash
git add "Frameworks/Systems Thinking/"
git commit -m "docs: complete Systems Thinking reference guide Phase 1 (7 concepts, 5 problems, methodology)"
```

- [ ] **Step 6: Create a summary file for Phase 2**

Create `Frameworks/Systems Thinking/PHASE-2-ROADMAP.md`:

```markdown
# Systems Thinking Reference Guide — Phase 2 Roadmap

Phase 1 is complete: 7 foundational concepts, 5 common problems, methodology guide.

Phase 2 expansion (when needed):

### Additional Problems to Add
- Scope Creep (scope expansion, unclear requirements)
- Burnout & Stress (overwork, unsustainable pace)
- Feature Bloat (product accumulates unused features)
- Hiring Bottleneck (can't hire fast enough)
- Technical Interviewing Issues (hiring quality problems)

### Possible Concept Extensions
- Nonlinear relationships (why proportional thinking fails)
- System boundaries (what's in/out of scope)
- Network effects (how structure amplifies or dampens effects)

When adding new problems or concepts:
1. Follow the template in METHODOLOGY.md
2. Create a file in `problems/` or `concepts/` directory
3. Update YAML `related_concepts` and `related_problems` in existing files
4. Test all cross-references
5. Commit with clear commit message

See METHODOLOGY.md for structure and writing guidelines.
```

- [ ] **Step 7: Final commit**

```bash
git add "Frameworks/Systems Thinking/PHASE-2-ROADMAP.md"
git commit -m "docs: add Phase 2 roadmap for Systems Thinking expansion"
```

---

## Summary

**Deliverables:**
1. ✅ Directory structure: `Frameworks/Systems Thinking/` with `problems/` and `concepts/` subdirectories
2. ✅ Methodology document: Reusable style guide for building problem-first reference frameworks
3. ✅ Problem Gateway: Curated index of tech problems with links to deep-dives
4. ✅ 7 Concept Deep-Dives: Feedback Loops, Stocks & Flows, Delays, Hierarchy, Resilience, Limits, System Traps
5. ✅ 5 Problem Deep-Dives (Phase 1): Retention, Velocity Decline, Architecture Debt, Onboarding, Cross-Team Communication
6. ✅ Phase 2 Roadmap: Path for expanding with more problems

**Structure:**
- Agent-friendly YAML frontmatter for machine-readable metadata
- Human-readable content with Socratic questions and concrete interventions
- Bidirectional linking between problems and concepts
- No hashtag tagging; all linking through YAML fields and content references

**Next Steps:**
- After Phase 1 is complete and you're satisfied with the approach, Phase 2 can add more problems (Scope Creep, Burnout, etc.) using the same methodology
- The approach is reusable for other decision-making frameworks in learning-in-public
