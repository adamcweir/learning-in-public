# Systems Thinking Reference Guide — Phase 2 Roadmap

**Phase 1 status: complete.** 7 concept deep-dives, 5 problem deep-dives, the Problem Gateway, and [METHODOLOGY.md](METHODOLOGY.md).

Everything below follows the extension process in METHODOLOGY.md Part 6. Nothing gets linked from the Gateway until the file exists.

---

## Problems to add

Ordered by how often they come up, which is the only ordering that matters for a problem-first guide.

**Scope Creep** — Feature requests expand without boundaries; timelines slip; quality drops.
Likely structure: reinforcing loop where accepted requests lower the perceived cost of the next request. Stock is the committed-scope backlog; the missing balancing loop is an explicit no. Related: Feedback Loops, Stocks & Flows, Hierarchy & Suboptimization.

**Burnout & Stress** — Exhaustion, disengagement, health impacts.
Likely structure: reinforcing loop through mistakes and rework. Key delay: recovery time scales nonlinearly with depletion, so the same intervention applied late costs far more. Strongly coupled to [Retention Problem](problems/retention.md) — write it after, and cross-link both directions. Related: Feedback Loops, Delays, Resilience, System Limits.

**Feature Bloat** — Product accumulates features; users overwhelmed; maintenance burden grows.
Likely structure: a stock with almost no outflow, because deleting features has a visible cost and an invisible benefit. Related: Stocks & Flows, System Traps (drift to low performance in the UX), Resilience.

**Hiring Bottleneck** — Can't hire fast enough to keep up with attrition.
Likely structure: a pure limits problem, and the useful move is finding which stage actually binds. Note the overlap with [Retention Problem](problems/retention.md) — the guide should say plainly that hiring faster is the wrong lever when knowledge loss is the driver, and link across. Related: System Limits, Delays, Stocks & Flows.

**Incident Load** — On-call volume rising; team spends more time firefighting than building.
Likely structure: reinforcing loop where incident load consumes the engineering time that would prevent incidents. Closely parallel to the debt loop in [Architecture Debt](problems/architecture-debt.md). Related: Feedback Loops, Resilience, System Traps.

---

## Concepts to add

Only add a concept when at least two problem files need it. Concepts without problems are theory, and theory is what this guide exists to avoid.

**Nonlinearity** — Why proportional thinking fails, and why doubling the input rarely doubles the output. Would strengthen the burnout and limits material considerably.

**System Boundaries** — What's in and out of scope for a diagnosis, and how drawing the boundary too tightly guarantees you find the wrong cause. Relevant to nearly every problem file; worth writing once the problem set is larger.

**Leverage Points** — Meadows' ranked list of places to intervene, from parameters (weakest) through goals and paradigms (strongest). This is arguably the most valuable chapter in the book and the hardest to make concrete. Write it only when there are enough problem files to draw real examples from — otherwise it becomes an abstract listicle.

---

## Structural work

- **Diagnostic entry point.** A single "I don't know which problem I have" flow that asks three or four questions and routes to the right file. High value for both practitioners and agents; only worth building at 10+ problem files.
- **Loop diagrams.** Explicitly out of scope in Phase 1. Revisit if the text descriptions of loops start being the confusing part.
- **Apply the methodology to a second framework.** The real test of [METHODOLOGY.md](METHODOLOGY.md) is whether it works on a domain other than systems thinking. Until that happens, it's a style guide with one user.

---

## Process for adding anything

1. Create the file from the template in [METHODOLOGY.md](METHODOLOGY.md)
2. Fill YAML `related_concepts` / `related_problems`
3. Update every file named in that YAML so the link is bidirectional in both frontmatter and body
4. Add the entry to the Problem Gateway in [Systems Thinking.md](Systems%20Thinking.md), moving it out of the Planned list
5. Verify every relative link resolves before committing
