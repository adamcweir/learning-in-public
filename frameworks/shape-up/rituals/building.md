---
skill_name: "Building"
written_by: "agent"
trigger:
  - "A pitch has been bet on and the team needs to actually execute it"
  - "A project is running long and someone's asking whether to extend the deadline"
  - "Progress tracking feels like it needs a burndown chart or a sprint board"
related_concepts:
  - "Betting"
  - "Cool-down"
  - "The Technical Implementer"
---

# Building

## When to Use

Use this for the execution phase of a bet — once a pitch has won at the betting table, this is how the team spends the cycle actually building it. It's also the thing to reach for when someone's asking how to track progress: Shape Up's answer is the 9-box breakdown, not a burndown chart.

## How to Act

**Ask first:**
- What are the "9 boxes" for this project — the distinct phases or scopes the pitch breaks into for shared tracking?
- Is the six-week clock already running, or does the team still need to translate the pitch into that breakdown first?

**Where I'd start:** Fix the cycle length going in — six weeks is the default because it's long enough to build something real and short enough to see the end from the start — and translate the pitch into 9 boxes of implementation immediately, using the [9-box template](../artifacts/nine-box-template.md), so progress has something more granular than "in progress" to report against. Track completion at the box level, not story points or velocity; the fixed variable here is time, not scope, so the useful signal is which boxes remain, not how many points are burned. If a box turns out to hide more than expected, that's exactly what [The Technical Implementer](../skills/the-technical-implementer.md) should have flagged as a rabbit hole during shaping — a bad surprise here is a signal to name rabbit holes more aggressively next time, not just a scheduling problem.

If the cycle ends and the project isn't done, it ends by default. That's a feature, not a failure — it prevents projects from quietly running forever. Continuing requires going back to [Betting](betting.md) for another cycle, not extending in place.

**What would change this:** If a project is consistently blowing past six weeks, that's evidence the shaping was wrong-sized for the appetite — the fix is tighter shaping next time, not a longer default cycle.

## Related

- [Betting](betting.md) — what triggers a build cycle
- [Cool-down](cool-down.md) — what follows it
- [The Technical Implementer](../skills/the-technical-implementer.md) — the lens that should have caught a box's hidden complexity before this ritual started
- [9-Box Template](../artifacts/nine-box-template.md)
- [Shape Up - source](../Shape%20Up%20-%20source.md)
