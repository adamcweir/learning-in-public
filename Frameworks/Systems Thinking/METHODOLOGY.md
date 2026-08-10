# Systems Thinking Reference Guide — Methodology

This document describes the hybrid problem-first framework used to build the Systems Thinking reference guide. Follow this approach when creating other decision-making frameworks or reference guides in learning-in-public.

It assumes the [repo house style](../../README.md#house-style-be-a-thought-partner): extract before you advise, then commit, show the reasoning, and say what would change your mind. This document translates that stance into concrete file structure.

---

## Overview: The Hybrid Problem-First Framework

### What Is It?

A three-part reference structure:

1. **Problem Gateway** — Quick index of problems tech workers face, organized by category
2. **Problem Deep-Dives** — Guided diagnosis for each problem: system structure, discovery questions, a recommended starting lever, the full set of interventions
3. **Concept Deep-Dives** — Foundational systems concepts (Feedback Loops, Stocks & Flows, etc.) with tech context

### Why It Works

- **Practitioners enter at their problem** ("I have a retention issue") → fast, immediately relevant. Tech workers don't think in systems theory; they think in "retention is dropping" and "the codebase is slowing us down."
- **Underlying concepts link back and forth** → over time, users recognize meta-patterns across different problems
- **Agents can parse YAML metadata** → structure system problems systematically, traverse concept relationships, reason about interventions
- **Extensible** → new problems and concepts can be added without modifying existing files

### When to Use It

Use this framework for any decision-making guide, reference, or problem-solving framework where you want to be both practitioner-friendly (fast entry point) and agent-compatible (machine-readable structure).

### Cost / Benefit

It costs more upfront: YAML metadata on every file, bidirectional link maintenance, a recommendation on every guide (which requires actually having an opinion). The payoff is that the material stays usable as it grows, and both people and agents can navigate it without reading everything.

---

## Part 1: The Stance

This is the part that most affects whether the guide is useful. Get it wrong and you produce either a listicle or a therapy session.

### Extract before you advise

Every problem and concept file leads with **Guided Discovery Questions**. Their purpose is to get situation-specific facts on the table — timelines, sequence of events, what's already been tried, what changed. Not to make the reader guess the answer you're withholding.

Good discovery questions are:

- **Specific about observables.** "How many people left in the last two quarters, and what did each say in their exit conversation?" beats "What do you think is causing departures?"
- **Sequenced.** Establish the structure (what's accumulating?), then the rates (what's flowing in and out?), then the loops (what feeds back?), then the delays (how long until you'd see it?).
- **Aimed at what would distinguish two diagnoses.** The best question is the one whose answer rules something out.

### Then commit

After the discovery questions and the diagnosis checkpoint, every guide has a **Where I'd Start** section. This names one default lever and says why. Rules for writing it:

- Name **one** thing, not a menu. The full menu comes next, in Intervention Strategies.
- Give the system logic in a sentence: which loop it breaks, which flow it changes, which delay it shortens.
- Be honest about cost and time-to-signal. "This takes a quarter before you'd see movement" is part of the recommendation.
- If the right first move genuinely depends on a branch, write the branch explicitly: *"If X, start with A. If Y, start with B."* Two named paths is a recommendation. "It depends on your context" is not.

### Show the reasoning

Every intervention carries three things: **why it works** (in system terms — the loop, stock, flow, or delay it acts on), **how to implement it**, and **a concrete tech example**. Someone who has the causal model can adapt when their situation diverges from the example.

### Say what would change your mind

Every guide ends its diagnostic portion with **What Would Change This Diagnosis** — the observations that would mean the framework is pointing you wrong, and where to go instead. This is what keeps the guide a partner rather than an oracle. It also gives agents an explicit falsification condition instead of letting them pattern-match confidently onto the wrong problem.

---

## Part 2: Structure Templates

### Problem Gateway Template

**Purpose:** Curated index of problems. Tech worker lands here and finds their problem.

**File:** `Systems Thinking.md` (main file)

Keep entries to one line: bolded link, an em-dash, the symptom as it actually appears, and the diagnostic question it opens. Group by category (Team & Culture, Product & Features, Infrastructure & Debt, Coordination).

**Never link to a file that doesn't exist yet.** List planned problems in a separate "Planned" section without links.

---

### Problem Deep-Dive Template

**File location:** `problems/{problem-name}.md`

**Frontmatter:**

```yaml
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
  - description: "departures → knowledge loss → slower onboarding → new hire frustration → more departures"
    type: "reinforcing"
delays:
  - "information delay: 3 months before departures show up in throughput"
limiting_factors:
  - "interview capacity bottleneck"
---
```

**Section order (use these headings exactly — agents rely on them):**

| Section | Length | Contains |
|---|---|---|
| `## Problem Statement` | 1–2 sentences | The symptom as the reader would describe it |
| `## System Diagnosis: What Systems Thinking Reveals` | 2–4 paragraphs | Stocks, flows, loops, delays, limiting factor — named explicitly |
| `## Guided Discovery Questions` | 6–8 questions | Specific, sequenced, aimed at ruling things out |
| `## Diagnosis Checkpoint` | 4–6 checks | Yes/No/Partial list confirming the framework applies |
| `## Where I'd Start` | 2–4 paragraphs | One default lever, the system logic, cost, time-to-signal. Branch explicitly if needed |
| `## Systems Concepts at Play` | short | Links to concept files, one line each on why it's relevant |
| `## Intervention Strategies` | 4–5 levers | Each: why it works / how / tech example |
| `## What Would Change This Diagnosis` | 3–5 items | Observations that mean you're in a different problem, and where to go |
| `## Tech Examples` | 2 scenarios | Symptom → diagnosis → intervention → result |
| `## Related Problems` | short | Links to adjacent problem files |

---

### Concept Deep-Dive Template

**File location:** `concepts/{concept-name}.md`

**Frontmatter:**

```yaml
---
concept_name: "Name"
concept_types:
  - "Reinforcing | Balancing | Structural"
related_problems:
  - "Problem Name"
intervention_categories:
  - "Category Name"
---
```

**Section order:**

| Section | Contains |
|---|---|
| `## Explanation` | What it is in Meadows' terms, why it matters |
| `## In Tech Contexts` | How it shows up in software, teams, products, infrastructure |
| `## Diagnostic Questions` | 5–6 questions for "does this concept apply to me?" |
| `## Where I'd Start` | The default lever for this concept, with system logic |
| `## Intervention Levers` | 3–5 strategies, each with why it works / strategy / tech example |
| `## What Would Change This Diagnosis` | When this concept is the wrong lens, and which concept to read instead |
| `## Cross-References to Problems` | Links back to every problem listing this concept |
| `## Summary` | 2–3 sentences |

---

## Part 3: Writing Guidelines

### YAML frontmatter

Use YAML for structure, not hashtags. Agents parse YAML; hashtags are invisible to them.

Every problem file's `related_concepts` must appear as a real concept file, and that concept file must list the problem in `related_problems`. Links are bidirectional or they're broken.

### Discovery questions

**Bad (prescriptive):** "You have a reinforcing feedback loop, so you need to break it."

**Also bad (withholding):** "What do you think is happening? And what might that cause?"

**Good:** "How long has velocity been declining, and did the decline start before or after the last departures? That sequence tells us whether we're looking at a knowledge loop or a debt loop."

The question should have a stated purpose. Say what the answer would tell you.

### Recommendations

Write `Where I'd Start` in first person and commit to it. Include:

- the lever, named specifically
- the system logic — one sentence
- expected time-to-signal
- the cost or tradeoff you're accepting
- an explicit branch if the right answer genuinely forks

### Concept linking

**In YAML:** `related_concepts` and `related_problems`.

**In content:** link by relative path and explain relevance in the same sentence.

```markdown
This problem reveals [Feedback Loops](../concepts/feedback-loops.md) — departures compound because
knowledge loss makes the next departure more costly.
```

### Real-world examples

Each problem needs 1–2 realistic tech scenarios showing: the symptom, the diagnosis, the intervention, the result. Concrete enough to be believable, general enough to apply across teams. Avoid examples that only work at one company size or one org shape.

---

## Part 4: Common Mistakes to Avoid

- **Refusing to answer.** Questions that never resolve into a recommendation are a failure mode, not rigor. See the house style.
- **Answering before extracting.** A recommendation given before the discovery questions is a guess with confidence attached.
- **Vague feedback loops.** "Departures cause retention problems" is circular. "Departures → knowledge loss → onboarding friction → new-hire frustration → more departures" is a chain you can cut.
- **Missing metadata.** YAML frontmatter is how agents navigate. Don't skip it.
- **Broken links.** Every cross-reference must resolve to a file that exists. Test before committing.
- **One-off examples.** If the example only works at a 2,000-person company, it isn't an example.
- **Menu-only interventions.** Five equally-weighted options with no recommended default pushes the hard decision back to the reader.

---

## Part 5: Worked Examples

Rather than duplicate content here (which drifts), read the canonical examples in the repo:

- **Problem deep-dive:** [Retention Problem](problems/retention.md) — full length, all sections
- **Concept deep-dive:** [Feedback Loops](concepts/feedback-loops.md) — full length, all sections

Match their length, tone, and section structure when adding new files.

---

## Part 6: Extending This Framework

**Adding a problem:**

1. Create `problems/{problem-name}.md` from the template
2. Fill YAML `related_concepts`
3. Add the problem to each of those concepts' `related_problems` and Cross-References section
4. Add it to the Problem Gateway in `Systems Thinking.md`
5. Verify every link resolves

**Adding a concept:**

1. Create `concepts/{concept-name}.md` from the template
2. Fill YAML `related_problems`
3. Add the concept to each of those problems' `related_concepts` and Systems Concepts at Play section
4. Add it to the Concepts list in `Systems Thinking.md`
5. Verify every link resolves

---

## Summary

The hybrid problem-first + concept framework makes systems thinking immediately useful to practitioners while staying structured enough for agents to reason with. YAML frontmatter enables machine readability. Discovery questions surface the specifics. A named recommendation gives the reader somewhere to start. Falsification conditions keep it honest.

Use this approach for any reference guide or decision-making framework where you want both human usability and agent compatibility.
