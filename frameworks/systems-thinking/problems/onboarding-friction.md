---
title: "Onboarding Friction"
category: "Team & Culture"
related_concepts:
  - "System Limits"
  - "Delays"
  - "Feedback Loops"
  - "Stocks & Flows"
  - "Resilience"
stocks:
  - "working context in a new hire's head (systems, rationale, who to ask)"
  - "available senior attention, measured in uninterrupted hours per week"
  - "supply of starter tasks with a bounded blast radius"
  - "new hire confidence and willingness to ask questions"
flows:
  - "inflow: mentoring hours actually delivered (pairing, answers, review feedback)"
  - "inflow: self-service discovery from code, docs, and traces"
  - "outflow: senior attention consumed by delivery pressure and incidents"
  - "outflow: context decay while a new hire waits on a blocked question"
  - "outflow: early attrition of hires who never reached independence"
feedback_loops:
  - description: "slow ramp → new hire ships less → seniors absorb the delivery load → less senior attention available for mentoring → the next hire ramps slower"
    type: "reinforcing"
  - description: "long review latency → fewer learning cycles per week → less independent judgment → more hand-holding required per task → longer review queues"
    type: "reinforcing"
  - description: "new hire feels slow → asks fewer questions to avoid looking lost → gets less correction → stays wrong longer → feels slower"
    type: "reinforcing"
  - description: "visible ramp pain → onboarding investment (docs, buddy program, checklists) → faster ramp"
    type: "balancing"
delays:
  - "learning delay: the review latency itself — a three-day feedback cycle produces roughly one-tenth the learning of a three-hour cycle over the same month"
  - "information delay: 2-3 months before a broken onboarding shows up as flat throughput or a resignation"
  - "action delay: documentation written today pays off for hires who start two quarters from now"
limiting_factors:
  - "available senior attention per week, divided by concurrent new hires"
  - "median time-to-first-review on a new hire's pull request"
  - "supply of real work small enough to be safe and meaningful enough to teach"
---

# Onboarding Friction

## Problem Statement

New engineers take three months or more to contribute independently, and some of them leave before they get there. The org's standing explanation is that the documentation is out of date, and the standing response is to write more of it.

## System Diagnosis: What Systems Thinking Reveals

**Onboarding is throttled by available senior attention, and documentation volume is not the constraint.** Meadows' point about limiting factors is that a system responds only to the input that is currently binding. Every other input can be increased for free and nothing happens. A team with four senior engineers who each have two spare hours a week has eight hours of mentoring capacity, total. Doubling the wiki does not create a ninth hour. This is why documentation sprints feel productive and change nothing measurable: the org increased the abundant input and left the scarce one untouched. The tell is that after the sprint, new hires still ask the same questions — because the questions that actually block people are "why is it built this way" and "who owns this," and those live in someone's head by definition.

**The learning loop runs at the speed of the feedback cycle, which makes review latency an onboarding intervention.** A new hire learns by making a judgment call, seeing it corrected, and updating. That is one cycle. An engineer who waits three days for review gets roughly one cycle per week and spends the wait on low-confidence work they may have to throw away. An engineer who gets substantive review within three hours gets several cycles a day. Over one month those two people receive wildly different amounts of correction, and the difference shows up as a ramp-time gap that everyone attributes to talent. The delay in the loop, rather than the content of the feedback, is doing most of the damage.

**The reinforcing loop is that slow ramp eats the capacity that would end the slow ramp.** A hire who cannot work independently generates load: questions, reviews, rework, hand-holding. That load lands on exactly the senior engineers whose attention is the binding constraint. Those seniors then absorb the delivery work the new hire cannot do yet, which consumes the hours that would have gone to mentoring, which slows the next hire further. Each additional concurrent hire makes the constraint tighter, so the org's instinct under ramp pressure — hire more, onboard in a bigger cohort — accelerates the loop it was meant to relieve.

**There is a third loop, and it is social.** A new hire who feels slow starts rationing questions to avoid looking incompetent. Rationing questions means less correction, which means staying wrong longer, which confirms the feeling. This loop is invisible from the outside and usually surfaces only in an exit conversation at month seven.

**The balancing loop exists but points at the wrong lever.** Visible ramp pain does produce investment — checklists, buddy programs, onboarding docs. That loop works when it targets attention and cycle time. It produces nothing when it targets document count, and because it feels like action, it delays the real intervention by a quarter or more.

## Guided Discovery Questions

Answer these first. They separate an attention-constrained system from a task-supply problem, a codebase problem, and a hiring problem — which look identical from a distance and have nothing in common as fixes.

1. **For your last four or five hires in order, how many calendar days from start date to a merged PR that nobody had to walk them through?** Write the numbers down in sequence. A rising series means the reinforcing loop is running and each hire is arriving into a thinner attention budget. A flat series that is simply high means the constraint is structural rather than compounding.

2. **How many hours of genuinely unbooked senior time exist in a week, and how many people are currently drawing on them?** Count from calendars, not intentions. If the ratio is under roughly four protected hours per concurrent new hire, the limiting factor is confirmed and no content-based fix will move the number.

3. **What is the median time from a new hire opening a PR to the first substantive comment on it?** Not the first approval, the first real engagement. Under four hours means the learning loop is fast and the problem lies elsewhere. Over a day means you have found a lever that costs no headcount.

4. **When a new hire is blocked on a question, what is the actual median wait before they get an answer, and where do they ask?** A public channel with a two-hour response time is a healthy system. A DM to one overloaded person with a next-day reply is a bus factor of one masquerading as an onboarding process.

5. **Take the last twenty questions a new hire asked. How many were answerable from existing documentation?** If most were answerable, you have a navigation and search problem, and more documents make it worse. If most were "why was this decided" or "who owns this," documentation cannot fix them at any volume — that is tacit rationale, and it transfers only through conversation or decision records written at the time.

6. **What did each of your last three hires actually ship in week two, and who picked those tasks?** If the honest answer is "reading and setup," the constraint is task supply: there is no standing inventory of work small enough to be safe and real enough to teach. That is a different fix from attention.

7. **Break ramp time down by team and by mentor. Is the spread wide?** One slow team surrounded by fast ones is a local management issue, not a system property. Uniform slowness across teams points at the codebase or the deployment path instead.

8. **Of your last four hires, is one slow or are all four?** One out of four is a selection or role-fit question and belongs in a manager conversation this week. Four out of four is the system, and no amount of individual coaching will touch it.

## Diagnosis Checkpoint

Does your situation match this pattern?

- [ ] Time-to-first-independent-PR has increased across your last several hires
- [ ] Protected senior mentoring time is under four hours per week per concurrent new hire
- [ ] Median first-response time on a new hire's PR exceeds one working day
- [ ] Most blocking questions are about rationale and ownership rather than mechanics
- [ ] Mentoring and pairing are the first commitments dropped when a deadline approaches
- [ ] The organization's response so far has been documentation, checklists, or a longer onboarding curriculum

**Four or more:** this is the attention-constrained ramp with a slow learning loop. The recommendation below applies directly.

**Fewer than three, and ramp times are flat rather than rising:** you have a fixed structural cost, not a spiral. Look at the codebase and the local development loop — read [Architecture Debt](architecture-debt.md) instead.

**Fewer than three, and only one recent hire is slow:** this is a role-fit or performance conversation, and running a structural intervention to avoid having it will cost you two quarters and still leave the conversation to have.

## Where I'd Start

**I would put a hard service level on new-hire code review — first substantive response within four working hours — and pay for it by capping concurrent onboarding at the mentors who actually exist.**

The system logic: review latency is the cycle time of the learning loop, and cycle time multiplies. Cutting first-response time from two days to four hours takes a new hire from about one correction per week to several per day, which compounds over the first month into a fundamentally different engineer. Every other lever available to you adds material to the system. This one changes the rate at which the system converts material into competence, which is why it beats the alternatives at a fraction of the cost.

The cap is what makes the service level real. Four hours is a promise about senior attention, and senior attention is the binding constraint. If you have four mentors with two protected hours each, you can support two concurrent hires well or five badly, and the second choice is how teams end up with a five-month ramp. Cap it, and let reqs sit unfilled rather than admitting people into a system that cannot absorb them.

**Cost and time-to-signal:** the cost is real and it lands on your senior engineers' focus — interrupt-driven review is expensive, and their own feature delivery will drop this quarter. The cap costs you calendar time on open reqs. You will see the leading signal in two to three weeks: watch the new hire's PR size and revision count, both of which move fast when the loop tightens. Time-to-first-independent-PR is the lagging measure and takes a full hiring cycle to read, so pre-commit to the leading indicator or you will abandon this before it reports.

**The branch:** if question 3 shows first-response time is already under four hours and ramp is still slow, the constraint is task supply. Start instead by building a standing inventory of ten to fifteen bounded starter tasks — real work, small blast radius, a known-good implementation someone can compare against — and keep it stocked as a permanent obligation rather than a scramble the week someone starts.

**What I would not start with:** a documentation sprint. Writing docs is the most legible response, it consumes exactly the senior hours that are already scarce, and it acts on an input that is not binding. See [System Limits](limits.md) for why increasing a non-binding input produces nothing. Documentation earns its place later, written incrementally at the moment a question is asked, by the person who asked it.

## Systems Concepts at Play

- [System Limits](limits.md) — senior attention is the binding constraint, and every intervention that adds documentation instead of attention is optimizing a non-binding input
- [Delays](delays.md) — review latency is the cycle time of the learning loop, so shortening it multiplies the correction a new hire receives per week
- [Feedback Loops](feedback-loops.md) — slow ramp consumes the mentoring capacity that would speed the ramp, and question-rationing quietly reinforces it
- [Stocks & Flows](stocks-and-flows.md) — headcount is the visible stock; the governing stocks are working context in the hire's head and unbooked senior hours
- [Resilience](resilience.md) — an onboarding path that depends on one person answering every question fails completely the week that person takes vacation

## Intervention Strategies

### 1. Cap concurrent onboarding at real mentor capacity

**Why it works:** Acts directly on the limiting factor. Onboarding throughput equals mentor hours divided by hours-required-per-hire; adding hires to a fixed numerator lowers per-hire quality and raises total ramp time across the cohort.

**How:** Count protected senior hours per week from calendars. Divide by the four-to-six hours a ramping engineer genuinely consumes. That integer is your cap. Stagger start dates to respect it, and treat exceeding it as an explicit decision to slow the next two quarters.

**Tech example:** A platform team with six open reqs capped onboarding at two concurrent hires. Filling the reqs took an extra quarter. Time-to-first-independent-PR fell from eleven weeks to five, and the second pair ramped faster than the first because the first pair became mentors instead of a support burden.

### 2. Compress the learning cycle

**Why it works:** Shortens the delay inside the feedback loop. The same feedback delivered in three hours instead of three days produces several times the learning per month, and it prevents the new hire from building a day of work on a wrong assumption.

**How:** Put a four-hour first-response target on new-hire PRs and assign a named person per day rather than a rotating queue. Add a standing thirty-minute daily block where a mentor is reachable without scheduling. Push new hires toward small PRs, which are what makes fast review sustainable.

**Tech example:** An API team routed new-hire PRs to a dedicated review channel with a four-hour target. Median first response dropped from nineteen hours to two. Average PR size fell by half within three weeks because the hire stopped batching work to justify the wait, and the cohort reached independent shipping about a month earlier than the previous one.

### 3. Maintain a standing inventory of bounded starter work

**Why it works:** Builds a stock that is otherwise assembled in a panic on someone's first Monday. A task with a small blast radius and a known-good reference implementation lets a new hire generate learning cycles without consuming senior attention for every step.

**How:** Keep ten to fifteen tickets tagged and genuinely ready — scoped, with acceptance criteria, touching real production code, reversible if wrong. Refill it as a permanent team obligation. Never let a hire spend week one on environment setup and reading.

**Tech example:** An infrastructure team kept a "first fifteen" backlog of small, real changes across every service they owned. New hires merged something to production on day two. The measured effect was on confidence and question volume — hires who shipped in the first week asked substantially more questions in weeks two through six, which is the behavior you want.

### 4. Capture rationale at the moment it is asked

**Why it works:** Converts tacit knowledge into a durable stock at the one moment the cost is nearly zero — someone already has to answer the question. This is documentation aimed at the binding constraint, because it reduces future draw on senior attention rather than adding volume for its own sake.

**How:** Make the new hire, rather than the expert, write the answer down. Answer in a public channel, then have the asker turn it into a short decision record or a comment in the code. Keep it adjacent to the code, since a wiki nobody can find is a stock that decays to zero.

**Tech example:** A payments team required every new hire to open a documentation PR for any question that took more than ten minutes to answer. After two hires, the onboarding guide had been rewritten by the people who needed it. Repeat questions to the two senior engineers dropped noticeably, which returned hours to the constraint.

### 5. Instrument the ramp and give it an owner

**Why it works:** Strengthens the balancing loop by making the deviation visible early. The loop currently runs on someone noticing a problem months late; a measured number lets it respond in weeks.

**How:** Track days-to-first-merged-PR, days-to-first-independent-PR, and median new-hire review latency. Review them per cohort. Give one person accountability for the number, the way you would for uptime.

**Tech example:** A 60-person org started reporting time-to-first-independent-PR by team each month. Two teams were at five weeks and one at fourteen. The gap turned out to be a single undocumented deployment path, which was fixed in a week — a problem that had been invisible for a year because nobody owned the metric that would have exposed it.

## What Would Change This Diagnosis

- **Ramp times are flat across many hires rather than rising.** No compounding loop is running. You have a fixed structural cost, usually in the codebase or the local development loop — read [Architecture Debt](architecture-debt.md).
- **Experienced engineers are also slow on unfamiliar parts of the system.** The obstacle is the code, not the onboarding process. New hires are simply the most visible victims of it. Read [Velocity Decline](velocity-decline.md).
- **New hires ramp fine and then leave at eight to twelve months.** Onboarding is working; something downstream is not. Read [Retention Problem](retention.md).
- **Ramp is blocked by waiting on other teams for access, environments, or decisions.** That is an information-delay and coordination problem wearing an onboarding costume. Read [Cross-Team Communication](cross-team-communication.md).
- **One hire out of four is slow while the others are fine.** The system is functioning. This is a selection, role-fit, or management conversation, and structural interventions are an expensive way to postpone it.

## Tech Examples

### Scenario 1: The documentation sprint that changed nothing

**Symptom:** A 30-person engineering org measured average time-to-first-independent-PR at fourteen weeks and rising. Leadership ran a two-week documentation sprint: every team wrote setup guides, architecture overviews, and service READMEs.

**Diagnosis:** The next two hires ramped in thirteen and fifteen weeks. Reviewing their questions showed why — the blocking ones were "why does the ledger service retry this way" and "who decides whether this counts as a breaking change." No document held those answers, and the sprint had consumed roughly 200 senior hours, which came directly out of the mentoring budget for the quarter the new hires arrived.

**Intervention:** The team stopped writing documents and set a four-hour first-response target on new-hire PRs, staffed by a named daily reviewer, with concurrent onboarding capped at three. Any question that took more than ten minutes to answer became a documentation PR written by the person who asked it.

**Result:** The following cohort reached independent shipping in six weeks. Documentation improved anyway, written incrementally by the people who needed it, at roughly a tenth of the senior-hour cost.

### Scenario 2: The cohort that consumed its own mentors

**Symptom:** A team of eight grew by five hires in six weeks after a funding round. Three months later, throughput was below where it had been before the hiring, and one new hire had already resigned.

**Diagnosis:** The three senior engineers had a combined six protected hours per week and five people drawing on them. Each hire got about an hour of real mentoring per week, which is well under the threshold for independence. Because the hires could not take meaningful work, the seniors absorbed the delivery backlog, which erased the mentoring hours entirely — the reinforcing loop, running at full speed and visible in the calendar data.

**Intervention:** Onboarding was restructured into a staggered queue of two at a time. The remaining three hires spent the interim on a bounded starter backlog with asynchronous review. Senior mentoring blocks were moved onto calendars and treated like on-call shifts.

**Result:** Total time to get all five productive was about the same as the original plan predicted, but throughput stopped declining within a month, no further hires left, and the first pair to ramp became mentors for the second — the loop running in the useful direction for the first time.

## Related Problems

- [Retention Problem](retention.md) — the upstream half of this loop; every departure costs more when the ramp is slow, and a slow ramp produces its own departures
- [Velocity Decline](velocity-decline.md) — a team whose seniors are fully consumed by onboarding shows up as declining throughput a quarter later
- [Architecture Debt](architecture-debt.md) — when ramp times are uniformly high rather than rising, the codebase is usually the actual obstacle
- [Cross-Team Communication](cross-team-communication.md) — access, environment, and decision waits imported from other teams inflate ramp time without appearing in any onboarding process
