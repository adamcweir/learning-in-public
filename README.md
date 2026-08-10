# README

- These are skills, tools, and frameworks for thinking, self-inquiry, self-inspection, and work that I have compiled through reading, watching, listening, working, and learning widely
- I do not own any of these. I did not come up with any of these. In some cases, I have added my own interpretation and examples.
- I cite where and who they come from in every instance. For more information on any of them, refer to those sources.

---

## House Style: Be a Thought Partner

Everything in this repo — every framework, guide, tool, and note — is written to be used *with* someone working through a real situation. That means the material behaves like a good thinking partner would, not like a search result and not like a Socratic tutor who refuses to commit.

This applies to every document in this repo, and to any agent reading or extending it.

### The four rules

**1. Extract before you advise.**
Ask about the specifics first. What's actually happening, over what timeframe, what's already been tried, what changed right before it started. Most bad advice comes from answering the question as asked instead of the question underneath it. Guided discovery questions come *before* recommendations in every document, and they exist to surface information, not to withhold an answer.

**2. Then commit.**
Once the situation is clear enough, say what you actually think. Name a default. Say where you'd start and why. "It depends" is only acceptable when followed immediately by *what* it depends on and what you'd do in each case. A framework that only asks questions has offloaded the hard part back onto the person who came for help.

**3. Show the reasoning, not just the conclusion.**
Give the causal model behind the recommendation — the loop, the delay, the constraint. Someone who understands *why* an intervention works can adapt it when their situation differs. Someone who only has the conclusion is stuck the moment reality diverges.

**4. Say what would change your mind.**
Name the conditions under which the recommendation is wrong, and what evidence would falsify the diagnosis. This is what makes it a partnership instead of a pronouncement — the person can push back on the model, not just on the answer.

### What this looks like in practice

Not this:

> You have a reinforcing feedback loop. To fix it, break the loop.

Not this either:

> What do you think is happening? What might reinforce that? What would happen if you changed it?

This:

> Before I can point at a lever: how long has velocity been dropping, and did it start before or after the last two people left? If departures came first, this is probably the knowledge-loss spiral, and the highest-leverage move is forcing explicit handoff before the next departure rather than hiring faster — hiring adds people to a system that can't onboard them. If the decline predates the departures, that's a different diagnosis and I'd look at the debt loop instead.

Ask, then commit, then show your work, then say what would change it.

### Document conventions

- **Guided discovery questions come first.** Their job is to get the specifics on the table.
- **A diagnosis checkpoint follows.** Confirm the framework actually fits before prescribing from it.
- **Then a recommendation.** Every guide names a default starting point — the "if you only do one thing" lever — with the reasoning attached.
- **Then the full set of levers**, each with *why it works* (the system logic), *how to do it*, and a concrete example.
- **Then what would change the diagnosis.** Conditions under which the guide is pointing you wrong.
- **YAML frontmatter for structure, not hashtags.** Agents traverse YAML; they can't follow hashtags. Machine-readable metadata at the top, human-readable content below.
- **Bidirectional links.** If A references B, B references A.

### Frameworks in this repo

- [Systems Thinking](Frameworks/Systems%20Thinking/Systems%20Thinking.md) — problem-first reference guide for applying Donella Meadows' systems thinking to tech work. See its [METHODOLOGY.md](Frameworks/Systems%20Thinking/METHODOLOGY.md) for the reusable structure behind it.
- [Shape Up](Frameworks/Shape%20Up.md)
