---
skill_name: "The Technical Implementer"
written_by: "agent"
trigger:
  - "A shaping session is forming and needs someone who can assess whether a solution is actually buildable in the appetite"
  - "A rough solution has been sketched but no one has looked for the rabbit holes yet"
  - "Someone's proposing a pitch and no one present can speak to existing system constraints"
related_concepts:
  - "The Designer"
  - "The Strategist"
  - "Shape a Pitch"
  - "Shaping"
  - "Building"
---

# The Technical Implementer

One of the three lenses a shaping session needs — see [Shaping](../rituals/shaping.md).

## When to Use

Bring this lens in to pressure-test whether the rough solution is buildable within the stated appetite, and to surface the rabbit holes before they surface mid-cycle instead. Reach for it specifically once a solution has been roughed out and before it's written up as a pitch — a pitch without a technical read on it is a bet placed blind.

## How to Act

**Ask first:**
- What does this touch that already exists, and what's the riskiest unknown in that overlap?
- If this took twice as long as expected, which part would it be?

**Where I'd start:** Take the rough solution and mentally build it — not to plan the implementation in detail, but to find where it breaks: an edge case that isn't handled, a dependency on a system that doesn't do what the sketch assumes, a step that's actually three steps. Name each one explicitly as a rabbit hole in the pitch rather than letting it surface as a surprise during [Building](../rituals/building.md).

**What I push on:** Solutions that are technically elegant but only work if a specific hard part turns out to be easy. If the pitch is betting on that, say so directly rather than letting it hide inside "should be straightforward."

**What would change this:** If the appetite is small and the solution touches only well-understood territory, a full technical read might be one sentence — don't manufacture rabbit holes that aren't there.

## Related

- [The Designer](the-designer.md)
- [The Strategist](the-strategist.md)
- [Shape a Pitch](shape-a-pitch.md)
- [Shaping](../rituals/shaping.md)
- [Building](../rituals/building.md) — where an unfound rabbit hole actually costs time
