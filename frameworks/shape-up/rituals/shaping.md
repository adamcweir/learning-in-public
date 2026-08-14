---
skill_name: "Shaping"
written_by: "agent"
trigger:
  - "A raw idea, feature request, or problem exists but no one has defined what 'done' looks like"
  - "Someone wants to skip straight to a spec or a set of wireframes before the problem is pinned down"
  - "A PRD keeps growing because the underlying problem was never made concrete"
related_concepts:
  - "Pitch"
  - "Betting"
  - "The Designer"
  - "The Strategist"
  - "The Technical Implementer"
  - "Shape a Pitch"
---

# Shaping

## When to Use

Use this when a project is still raw — an idea, a complaint, a request — and nothing has been committed to yet. It's the step before a pitch exists, so reach for it whenever someone's about to write a spec, brief, or set of wireframes without first fixing the boundaries of the problem.

It's also the fix for a specific failure mode: work that starts vague and never ends, because nobody defined what "shaped enough to build" means before building started.

## How to Act

**Ask first:**
- What's the raw idea or problem, in one sentence, without a proposed solution attached?
- How much time is this worth? An afternoon of thought, or a full six-week cycle?
- Who needs to be in the room — [someone technical](../skills/the-technical-implementer.md), [someone with design sense](../skills/the-designer.md), and [someone thinking strategically about tradeoffs](../skills/the-strategist.md)?

**Where I'd start:** Set the boundaries before sketching anything. Fix the appetite (how much time this is worth) and the problem definition first — solutions drift to fill whatever time you didn't bound in advance. Only after that, rough out the solution at a level *above* wireframes: concrete enough that a technical person could build it, abstract enough that you haven't pre-decided details that hide real complexity. This ordering is the whole point of shaping — skip it and you get either a vague brief that never converges, or a wireframe that fakes confidence about a solution nobody's pressure-tested.

The four steps, in order:
1. **Set boundaries.** Fix the appetite and the problem definition.
2. **Rough out the elements.** Sketch a solution at higher abstraction than wireframes — explore breadth before detail.
3. **Address risks and rabbit holes.** Look for holes, unanswered questions, or spots that could trip up the team; cut or specify until they're resolved.
4. **Write the pitch.** Package the result — see [Pitch](pitch.md).

**What would change this:** If the "idea" is actually already well-understood and low-risk (a known bug, a small well-scoped fix), full shaping is overkill — just write the pitch directly, or skip the ritual entirely. Shaping earns its cost when the problem or solution space is genuinely uncertain.

## Related

- [Pitch](pitch.md) — the artifact this ritual produces
- [Betting](betting.md) — where a finished pitch goes next
- [The Designer](../skills/the-designer.md), [The Strategist](../skills/the-strategist.md), [The Technical Implementer](../skills/the-technical-implementer.md) — the three lenses this ritual needs in the room
- [Shape a Pitch](../skills/shape-a-pitch.md) — running this ritual as a simulated three-person session when there's no actual room
- [Shape Up - source](../Shape%20Up%20-%20source.md)
