# Purpose

You are an agent writing agent instructions and artifacts from documents in this vault, usable by other agents. Read the human write-up, then break it down following this document.

This is a repository of frameworks, tools, and people that can be leveraged as agent skills — to help with an individual's problem-solving, or as a thought partner.

Two entry points a user comes in through:

- **They want a thought partner.** Offer the personas available, sourced from `people/`.
- **They come with a problem or situation.** Ask enough to place it, then propose the framework or tool that fits.

Every framework, person, and tool has a human-written source page. It stays exactly as written — never edited, only linked to and expanded from. Everything derived from it (concepts, problems, skills, deep-dives) is agent-written. See **Marking Authorship** below for how the two are told apart.

Where a human page's rituals, concepts, or advice call for their own page, break them out — one page per ritual/concept/problem, in the right subfolder, following the templates below.

This document assumes nothing about which agent, model, or tool is reading it. Everything here is plain markdown, read directly — no tool-specific config, no assumption of a particular skill-packaging format. Any agent pointed at this file and a source page can follow it end to end.

---

# Process

Every breakdown or addition follows this sequence. Step 5 is not a later cleanup pass — it happens in the same sitting as everything else, every time.

1. **Decide if it needs a folder.** See When to Break a Page Down.
2. **Build the folder.** Source page renamed and untouched, one file per sub-item. See Folder Shape.
3. **Mark authorship** on every derived page. See Marking Authorship.
4. **Write each page** with the right frontmatter and section order, in the house style. See Frontmatter by Sub-Item Type, Section Order, and Writing Stance.
5. **Update the theme index.** Tag the new or changed landing page with `topics:`, and add it to the relevant theme page(s) in `topics/Topics.md`. See Cross-Cutting Themes.
6. **Check the completion checklist** before calling it done.

---

# When to Break a Page Down

Not every page earns a folder. Expand a source page when at least one of these is true:

- It names 3+ distinct concepts, rituals, or techniques that would each need their own diagnosis/discovery-question treatment to be useful in a real conversation.
- Someone would plausibly ask about one piece of it without needing the whole thing.
- It's long enough that a single page would bury the part someone actually came for.

If none of these are true, leave it as a single page. A one-page tool or a person's link-dump doesn't need a folder — see `tools/socratic-questioning.md` or `people/michael-pollan.md`, which are fine as they are.

**Example:** `frameworks/shape-up.md`'s "Key Rituals and Artifacts" already names five distinct rituals (Shaping, Pitch, Betting, Building, Cool-down), each with its own steps and its own "when would someone ask about just this one" case. That clears the bar — it should become `frameworks/shape-up/` with the source page plus one page per ritual.

---

# Structure

Help agents know when and how to use it. Users will come with their problems or situation that they want to spar with the agent about.

Every topic's landing page (the file a user or agent lands on first — e.g. `Systems Thinking - Agent-written.md`) needs two things, in some form. The exact heading text can vary by topic — Systems Thinking calls its index "Problem Gateway" rather than "Agents/Skills Available," and that's fine — but both of these have to be present somewhere on the page:

## When to use it

State the trigger conditions plainly: what a user says, asks, or describes that means this topic applies. Prefer concrete phrasing over category names — "throughput dropping despite stable headcount" over "a velocity problem." If a topic covers more than one situation, this doubles as the index into those situations (Systems Thinking's "Problem Gateway" does both jobs at once).

## Agents/Skills Available

Specific to each concept, person, or framework: a list of the derived pages under this topic, each as a one-line bolded link plus what it's for. This is the payoff of the breakdown — it's how an agent (or the user) finds the right sub-page instead of reading the whole topic.

---

# Folder Shape

For anything past the expansion threshold:

```
{category}/{topic}/
  {Topic} - source.md      <- the original human-written page, untouched, renamed with " - source"
  {sub-item}.md             <- one per ritual/concept/problem/technique, agent-written
  {sub-item}.md
  ...
```

`{category}` is whichever top-level folder the topic already lives in (`frameworks/`, `people/`, `tools/`). When a topic has more than one *kind* of sub-item, use subfolders — the pattern already proven in `frameworks/systems-thinking/` is `concepts/` for foundational principles and `problems/` for situations. `frameworks/shape-up/` would likely want `rituals/`.

**Never link to a file that doesn't exist yet.** List planned-but-unwritten sub-items in a "Planned" section without links — see the Problem Gateway's "Planned" list for the pattern.

---

# Marking Authorship

Every derived page carries a `written_by` field in frontmatter: `human` or `agent`.

This replaces the ad-hoc "- Agent-written" filename suffix used in the first systems-thinking pass — a filename suffix isn't machine-readable and doesn't scale past one file per topic. Going forward:

- **Human-written source pages** get renamed with " - source" appended once a topic is broken out (e.g. `Shape Up.md` → `shape-up - source.md`). Leave the content untouched. Add `written_by: "human"` in frontmatter only if frontmatter already exists on the page — don't add frontmatter to a source page solely for this.
- **Agent-written pages** always get `written_by: "agent"` in frontmatter, alongside whatever else their type requires below.

---

# What a "Skill" Is Here

A skill is a markdown page in the topic's folder — the same file type as a concept or problem page, not a separately packaged, tool-specific skill format (e.g. Claude Code's `SKILL.md`, a Cursor rule, or similar). Shape:

```yaml
---
skill_name: "Name"
written_by: "agent"
trigger:
  - "What a user says or asks that means this applies"
  - "What a situation looks like that means this applies"
related_concepts: []
---
```

```markdown
## When to Use
(the trigger conditions above, written as prose)

## How to Act
(stance, discovery questions to ask, what to commit to — following the house style)
```

**Why this shape and not a packaged skill format:** the vault is read as context by an agent already in conversation, whatever that agent's tooling is — that's exactly how `frameworks/systems-thinking/` works today, with no install step and no dependency on any one provider's plugin system. If a specific skill earns reuse outside this vault, promote it to whatever packaged-skill format your agent tooling supports, as a deliberate, separate step later. That's not the default for every framework, person, or tool that gets broken down.

---

# Frontmatter by Sub-Item Type

**Problem / situation page:**

```yaml
---
title: "Problem Title"
written_by: "agent"
category: "..."
related_concepts: []
stocks: []
flows: []
feedback_loops:
  - description: "..."
    type: "reinforcing | balancing"
delays: []
limiting_factors: []
---
```

**Concept page:**

```yaml
---
concept_name: "Name"
written_by: "agent"
concept_types: ["Reinforcing | Balancing | Structural"]
related_problems: []
intervention_categories: []
---
```

**Skill page:** see above.

**People and Tools pages that don't fit the stocks/flows/delays vocabulary** — most won't; that vocabulary belongs to systems thinking specifically, not to the vault as a whole. Use just:

```yaml
---
title: "..."
written_by: "agent"
related_people: []
related_tools: []
related_frameworks: []
---
```

Don't force stocks/flows language onto a page that isn't a systems-thinking framework.

---

# Section Order

For systems-thinking-shaped content, follow what's already proven in `frameworks/systems-thinking/problems/retention.md` and `frameworks/systems-thinking/concepts/feedback-loops.md`: Problem Statement → Diagnosis → Guided Discovery Questions → Diagnosis Checkpoint → Where I'd Start → Intervention Strategies → What Would Change This Diagnosis → Examples → Related Problems.

For everything else (most People and Tools pages), the minimum bar is **When to Use**, then either **How to Act** (skill page) or **What It Is** (concept-shaped page). Don't invent new section names per page — reuse these unless a page genuinely needs something the others don't cover.

---

# Writing Stance

Don't restate it here — follow the [house style](../README.md#house-style-be-a-thought-partner): extract before you advise, then commit, show the reasoning, say what would change your mind. Every derived page follows it, regardless of topic.

---

# Light Research

When a source page references something without explaining it — a named technique, a person's framework, a book — a short outbound link plus a one-sentence gloss is enough. Don't write a parallel essay on someone else's idea. Cite per the repo norm: name the source, link it, and keep your interpretation clearly separate from the source's own claims.

---

# Cross-Cutting Themes (`topics/`)

This is Process step 5. Do it in the same sitting as the rest of the breakdown, not as a follow-up — a page that's structurally complete but untagged is not done.

Not to be confused with a "topic" as used everywhere above (a single framework, tool, or person getting broken down) — `topics/` is a separate, cross-cutting index that groups material by *theme* (Product Management, Operational Efficiency, and so on) regardless of which of `frameworks/`, `tools/`, or `people/` it lives in. See [topics/Topics.md](../topics/Topics.md) for the current set of themes and the worked example.

When you break down or add a framework, tool, or person:

- Add a `topics: []` field to its landing page's frontmatter (or its own frontmatter, if it's a single unbroken page with frontmatter already), listing every theme in `topics/Topics.md` it belongs to.
- Add it to each of those theme pages, under the right category, as a one-line bolded link plus what it's for — same as any other index entry.
- Don't add a `topics` field to a human-written source page solely for this, same rule as **Marking Authorship**. Its theme assignment lives in the theme page only, one-directionally, until it has an agent-written landing page of its own.
- If nothing existing fits, either add a new theme page and list it in `topics/Topics.md`, or — if it's genuinely thin (one item, no real cluster yet) — note it under that page's "Coverage Gaps" instead of creating a page with nothing in it.

---

# Completion Checklist

A breakdown is done when:

- [ ] The source page is untouched and renamed with " - source"
- [ ] Every derived page has `written_by: "agent"` and the frontmatter shape for its type
- [ ] Every `related_*` link is bidirectional — if A references B, B references A
- [ ] Every link resolves to a file that exists
- [ ] The topic's landing page has both a **When to use it** and an **Agents/Skills Available** section (in whatever heading form fits the topic)
- [ ] The repo [README](../README.md)'s topic index is updated, if this is a new top-level framework, person, or tool
- [ ] It's tagged under at least one theme in [topics/Topics.md](../topics/Topics.md), and that theme page links back
- [ ] At least one worked example exists per skill or problem page

---

# Worked Example

Don't duplicate content here — read `frameworks/systems-thinking/` for the canonical example of this process applied to a framework, and match its length, tone, and link discipline when adding new pages.
