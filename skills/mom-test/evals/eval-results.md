# Mom Test Skill: Eval Results

Run date: 2026-05-01
Runner: Claude (same session, not independent agent)

---

## Test 1: question-review-all-risky

**Prompt:** Use the mom test skill to review these interview questions. I'm talking to engineering managers at mid-market companies about our AI agent feature:

1. Would you use AI agents in your development workflow?
2. How much would you pay for AI-powered dev environments?
3. Do you think your team would benefit from automated environment setup?
4. If we built a tool that spun up AI coding agents in your cloud, would that be useful?
5. Don't you think onboarding new devs takes too long?

### Skill Output

**Q1: "Would you use AI agents in your development workflow?"**
Risky — The Hypothetical. This is a future-tense question about imaginary behavior. Any engineering manager will say "yeah, probably" because it costs them nothing. You learn nothing from the answer.

Rewrite: "What's your team's development workflow look like today? Where do things slow down or break?" (Anchor question that surfaces pain without mentioning AI or agents.)

**Q2: "How much would you pay for AI-powered dev environments?"**
Risky — The Hypothetical + Premature Solution. You're asking someone to price a product they've never used for a problem you haven't confirmed they have. The number they give you is fiction.

Rewrite: "What are you currently spending on developer tooling and environments? What's the biggest line item?" (Spending question grounded in current behavior.)

**Q3: "Do you think your team would benefit from automated environment setup?"**
Risky — The Opinion Request. Opinions are free. "Do you think X would help?" will always get a polite yes. You've learned nothing about whether they've actually tried to solve this or how much it costs them.

Rewrite: "Walk me through what happens when a developer needs a new environment set up. How long does it take, and who's involved?" (Process question that reveals real pain through specifics.)

**Q4: "If we built a tool that spun up AI coding agents in your cloud, would that be useful?"**
Risky — Premature Solution. You've stopped learning and started pitching. The customer is now reacting to your idea, not describing their world. Even if they say "yes, that sounds amazing," you've validated nothing.

Rewrite: "Tell me about the last time your team needed to spin up something quickly in your cloud. What was the process? What went wrong?" (Past-tense, specific, about their life.)

**Q5: "Don't you think onboarding new devs takes too long?"**
Risky — The Leading Question. You've telegraphed the answer you want. No reasonable person is going to say "No, onboarding is fast and easy." Social pressure guarantees a yes.

Rewrite: "How many engineers did you onboard in the last quarter? Walk me through what their first two weeks looked like." (Specific, past-tense, requires verifiable details rather than a polite agreement.)

**Overall assessment:** This entire question set is leading the witness toward a predetermined conclusion. Every question assumes the problem exists and nudges the interviewee toward validating your solution. If you ran this interview, you'd walk away feeling great and knowing nothing. None of these questions are hard to answer with a polite lie.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| All 5 flagged as risky | ✅ |
| Q1 identified as hypothetical | ✅ |
| Q2 identified as hypothetical spending | ✅ |
| Q3 identified as opinion-seeking | ✅ |
| Q4 identified as premature solution / pitching | ✅ |
| Q5 identified as leading | ✅ |
| Each gets a rewrite | ✅ |
| Overall set flagged as leading the witness | ✅ |

**Result: PASS**

---

## Test 2: question-review-mixed-quality

**Prompt:** Mom test this question set. I'm prepping for a call with a platform engineering lead at a fintech company:

1. Walk me through what happens when a new engineer joins your team. What does their first week look like?
2. Tell me about the last time a developer had to wait for an environment to be set up. How long did it take?
3. Would a self-service dev environment tool save your team time?
4. What tools are you currently using to manage developer environments?
5. How much is your team spending on infrastructure for dev environments right now?
6. If we could cut your onboarding time in half, would that be worth paying for?

### Skill Output

**Q1: "Walk me through what happens when a new engineer joins your team. What does their first week look like?"**
Safe. This is a great anchor question. It's past/present tense, about their life, and requires specific details. It's very hard to answer with a polite lie because they have to describe a real process.

**Q2: "Tell me about the last time a developer had to wait for an environment to be set up. How long did it take?"**
Safe. Past-tense, asks for a specific incident, and pushes for a concrete number. This is exactly the kind of question that surfaces real pain (or reveals that the problem isn't as bad as you assumed).

**Q3: "Would a self-service dev environment tool save your team time?"**
Risky — The Hypothetical + Premature Solution. You've named a solution category and asked them to speculate about whether it would help. The answer is almost always "yeah, probably." You've shifted from learning about their world to getting validation for your idea.

Rewrite: "When environment setup causes delays, what does your team do? Have they tried to solve it themselves, or worked around it?" (Stays in their world, probes for existing behavior and workarounds.)

**Q4: "What tools are you currently using to manage developer environments?"**
Safe. This is a process/tooling question grounded in their current reality. The answer tells you about their existing stack, which reveals both pain points and switching costs.

**Q5: "How much is your team spending on infrastructure for dev environments right now?"**
Safe. A spending question about current behavior. If they know the number, you learn the problem is on their radar. If they don't know, that's also a signal (it's not painful enough to track).

**Q6: "If we could cut your onboarding time in half, would that be worth paying for?"**
Risky — Premature Solution + Hypothetical Willingness to Pay. This combines two anti-patterns: you're pitching a specific outcome ("cut onboarding time in half") and asking them to commit to hypothetical spending. The answer is meaningless because saying "yes" costs them nothing.

Rewrite: "What would it mean for your team if onboarding took half the time it does now? How would you spend that recovered time?" Then, separately: "Have you evaluated or purchased any tools specifically to speed up onboarding? What happened?" (Split the pitch into a priority question and a spending/behavior question.)

**Overall assessment:** Four out of six questions are solid. Q1, Q2, Q4, and Q5 follow the rules well and would generate useful signal. Q3 and Q6 break the pattern by tipping into pitch mode. The risk is that after building trust with good questions, you undermine the conversation by revealing your hand with Q3 and Q6. Consider placing Q3 and Q6's rewrites later in the conversation so you stay in learning mode longer.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Q1, Q2, Q4, Q5 flagged as safe | ✅ |
| Q3 flagged as risky (hypothetical/opinion) | ✅ |
| Q6 flagged as risky (premature solution + hypothetical WTP) | ✅ |
| Rewrites only for Q3 and Q6 | ✅ |
| Notes set is mostly solid but two risky ones undermine it | ✅ |

**Result: PASS**

---

## Test 3: question-generation-onboarding

**Prompt:** Apply the mom test. We're assuming that engineering managers at mid-market companies (100-1000 employees) are frustrated with how long it takes to onboard new developers onto their codebase. Generate interview questions to test this.

### Skill Output

**Assumption being tested:** Engineering managers at mid-market companies (100-1000 employees) find developer onboarding onto their codebase frustratingly slow, and it's painful enough to be a priority worth solving.

**Questions:**

1. "How many engineers did you hire or onboard in the last six months?" (Warm-up. Establishes scale. Strong signal: high volume, meaning onboarding efficiency matters structurally. Weak signal: very few hires, meaning this might not be a pressing problem regardless of how slow it is.)

2. "Walk me through what a new engineer's first two weeks look like on your team." (Anchor. Gets them telling a story about a real process. Strong signal: they describe a long, painful process with lots of hand-holding and blockers. Weak signal: they describe something quick and smooth, or they've clearly already invested in making it good.)

3. "What's the longest it's taken for a new hire to ship their first meaningful PR? What was getting in the way?" (Dig into specifics. Strong signal: they cite a specific incident with frustration and can name the bottlenecks. Weak signal: they can't remember, or it wasn't notable enough to track.)

4. "Have you tried anything to speed up onboarding? What worked, what didn't?" (Tests whether they've taken action, not just complained. Strong signal: they've invested time or money in solutions, built workarounds, or tried tools. Weak signal: they've thought about it but never actually done anything, suggesting it's not a real priority.)

5. "Who else on the team ends up spending time helping new hires get set up? How much of their week does that eat?" (Quantifies the cost in people-hours. Strong signal: they can name specific people and estimate real time lost. Weak signal: "it's not that bad" or they can't quantify it.)

6. "Where does onboarding rank among the things you're trying to fix right now?" (Priority question. Strong signal: it's in their top three. Weak signal: they list five other things that matter more, meaning even if it's painful, it won't get budget.)

7. "If you could get new engineers productive twice as fast, what would you do with that recovered time?" (Tests whether the downstream value is real and significant enough to motivate action. Strong signal: they immediately describe concrete things they'd do, suggesting they've thought about this. Weak signal: vague answer like "that would be nice.")

8. "We're talking to a few engineering leaders about this. Would you be open to a follow-up conversation in a couple weeks where I share what we're learning? And is there anyone else on your team who feels this pain that I should talk to?" (Advancement. Asks for two commitments: their time and their reputation via an introduction. Strong signal: they agree to both and name a specific person. Weak signal: "sure, keep me posted" with no specifics.)

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Assumption clearly restated | ✅ |
| 5-8 questions generated | ✅ (8) |
| Ordered broad to specific to commitment | ✅ |
| No mention of onboarding tools/solutions | ✅ |
| At least one advancement question | ✅ (Q8) |
| Each has strong/weak signal parenthetical | ✅ |
| No question answerable with "yes that sounds great" | ✅ |

**Result: PASS**

---

## Test 4: question-generation-with-persona

**Prompt:** Mom test this for me. Our hypothesis is that DevOps teams at enterprises are manually managing Kubernetes cluster upgrades and it's painful enough that they'd pay for automation. I'm talking to a Senior DevOps Engineer at a healthcare company next Tuesday.

### Skill Output

**Assumption being tested:** Enterprise DevOps teams are manually managing Kubernetes cluster upgrades, it's painful and time-consuming, and the pain is severe enough that the organization would pay for automation.

**Note on persona:** You're talking to a senior IC, not a budget owner. This means you can get excellent signal on the pain, the process, and the workarounds, but the advancement ask should target an intro to someone with purchasing authority or a willingness to participate in a pilot, not a direct buying commitment.

**Questions:**

1. "How many Kubernetes clusters are you managing right now, and how does your team divide responsibility for them?" (Warm-up. Establishes scope and team structure. Strong signal: large number of clusters, small team, meaning the operational burden is high per-person. Weak signal: few clusters or a large dedicated team with comfortable capacity.)

2. "Walk me through what happened the last time you upgraded a cluster. Start from when you decided to upgrade." (Anchor. Gets the real story. Strong signal: a long, detailed, frustrated narrative with unexpected problems. Weak signal: "it was pretty straightforward, we ran the playbook.")

3. "How often are you doing cluster upgrades? Is there a cadence, or is it more reactive?" (Frequency question. Strong signal: frequent upgrades driven by security patches or EOL pressure, meaning this is a recurring tax. Weak signal: infrequent, only when forced.)

4. "Has a cluster upgrade ever caused an incident or unexpected downtime? What happened?" (Probes for real consequences. In healthcare, downtime has outsized implications. Strong signal: a specific incident they can describe in detail, especially one with compliance or patient-data implications. Weak signal: "not really, we're pretty careful.")

5. "What have you built or scripted to make upgrades easier? What's still manual?" (Tests for workarounds, which prove the pain is real enough to invest effort. Strong signal: they've built custom tooling, runbooks, or scripts, which means they're already spending engineering time on this. Weak signal: nothing, they just follow docs each time.)

6. "How does this compare to the other operational work on your plate? Where does cluster management rank in terms of what eats your time?" (Priority question tailored to an IC's perspective. Strong signal: it's one of their top time sinks and they resent it. Weak signal: it's minor compared to other operational burdens.)

7. "Who on your team or in your org makes the call on adopting new infrastructure tooling? What does that process usually look like?" (Mapping the buying process without asking them to commit. Strong signal: they can describe the process clearly and seem willing to navigate it. Weak signal: vague or indicates heavy bureaucracy with no champion.)

8. "We're exploring this problem space and building something. If we had a working version in a few months, would you be willing to test it against one of your non-production clusters? And who would I need to talk to about making that happen?" (Advancement. Asks for effort commitment (pilot) calibrated to what an IC can say yes to, plus an intro to the decision-maker. Strong signal: "yeah, I'd try it, let me connect you with [name]." Weak signal: "sounds interesting, keep me posted.")

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Tailored to senior IC (not budget holder) | ✅ |
| Advancement asks for pilot/intro, not purchase | ✅ |
| Probes frequency, time spent, incidents, workarounds | ✅ |
| No mention of "our product" or "automation tool" in questions | ✅ (Q8 says "building something" but doesn't name a solution category) |
| Persona-appropriate language | ✅ |
| Healthcare context acknowledged | ✅ (Q4 notes compliance implications) |

**Result: PASS** (minor note: Q8 edges close to revealing the solution by saying "building something," but stays on the right side of the line by not describing what it does)

---

## Test 5: transcript-analysis-fake-positive

**Prompt:** Use the mom-test skill to analyze this conversation summary:

I spoke with the VP of Engineering at a Series B startup (about 80 engineers). Key highlights:
- She said developer onboarding is "definitely a pain point" for her org
- She loved the idea of cloud-based dev environments and said "we'd probably pay $50/seat/month for something like that"
- She mentioned they currently use a wiki with setup instructions that "nobody follows"
- She said she'd "love to see a demo when you have one ready"
- When I asked about budget, she said "we always find budget for things that save engineering time"
- The call lasted 25 minutes and she seemed really engaged the whole time

### Skill Output

**Compliment deflections:**
- "Definitely a pain point" — Generic enthusiasm. She's agreeing with your framing, not describing a specific problem. What does onboarding actually look like? How long does it take? What breaks? You don't know. Follow-up that would have extracted signal: "Can you walk me through what happened with your last hire? What was the biggest bottleneck?"
- "Loved the idea" — A compliment, not a commitment. Signal value: zero. She's being polite.

**Hypothetical traps:**
- "We'd probably pay $50/seat/month" — This is hypothetical future spending. She hasn't looked at your product, hasn't run it past finance, hasn't compared it to alternatives. The number is fiction. Follow-up that would have helped: "What are you currently spending on developer environment tooling? What's in the budget for this category?"
- "We always find budget for things that save engineering time" — This sounds like a buying signal but it's a generic platitude. Every VP of Engineering says this. It tells you nothing about whether *this specific problem* will get budget. Follow-up: "Can you give me an example of something you recently found budget for? What did that approval process look like?"

**Missing specifics:**
- The entire conversation is missing specifics. You know onboarding is "a pain point" but you don't know: how many engineers they onboarded recently, how long onboarding takes, what the specific blockers are, whether anyone has tried to fix it, or what it's costing them in engineer-hours.

**Buried signals:**
- The wiki comment is the one real signal in this entire conversation. "Nobody follows" the setup instructions. This is a specific, verifiable claim about current behavior. It suggests the onboarding process is broken in a concrete way. You should have dug in here hard: "Why doesn't anyone follow the wiki? What do they do instead? How long has it been like that? Has anyone tried to fix it?" This thread could have led to real specifics.

**Commitment check:**
- "Love to see a demo when you have one ready" — This is a non-commitment. There's no date, no other stakeholders invited, and the "when you have one ready" framing puts the ball entirely in your court (meaning she doesn't have to do anything). On the commitment ladder, this is a Level 1: Nothing. A real commitment would be: "Can we schedule a demo for next Thursday? I'll bring my platform lead."

**Scorecard:**

| Category | Assessment |
|----------|------------|
| Trustworthy learnings | Almost none. The wiki comment suggests a broken onboarding process, but you didn't dig into it. |
| Sounded good but unreliable | "Pain point," "$50/seat," "love to see a demo," "always find budget" — all noise. |
| Commitment obtained | None. Level 1 on the commitment ladder. |
| Next steps | Go back to the wiki thread. Ask for a follow-up focused specifically on what onboarding looks like today, who's involved, and what it costs. Push for a demo with a specific date and additional stakeholders in the room. |

This conversation felt great. You left feeling validated. But if you remove the compliments and hypotheticals, you learned almost nothing. The one thread worth pulling (the wiki) was mentioned in passing and not explored.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Most of conversation flagged as unreliable | ✅ |
| "Definitely a pain point" flagged as generic | ✅ |
| $50/seat flagged as hypothetical spending | ✅ |
| "Love to see a demo" flagged as weak non-commitment | ✅ |
| "Always find budget" flagged as deflection | ✅ |
| Wiki comment identified as the one buried signal | ✅ |
| Scored as mostly noise | ✅ |
| No real commitment noted | ✅ |

**Result: PASS**

---

## Test 6: transcript-analysis-with-real-signals

**Prompt:** Mom test this customer conversation for me:

Talked to the Head of Platform at a logistics company, ~200 engineers. Notes:
- They built an internal tool 18 months ago to automate dev environment provisioning. Two engineers maintain it part-time.
- The tool breaks "every other Kubernetes upgrade" and it took them 3 weeks to fix it after the last upgrade in November
- They evaluated Gitpod last year but dropped it because of air-gapped requirements
- He asked if we support on-prem deployment and whether we've worked with companies that have FedRAMP requirements
- He said his team wastes roughly 15-20 hours per week aggregate on environment-related support tickets
- He offered to connect me with their CISO to discuss security requirements
- No demo was scheduled but he said he'd bring it up at their next platform team retro

### Skill Output

**Strong signals throughout this conversation.** This is what a high-quality discovery call looks like.

**Signal analysis:**

- **Internal tool investment (18 months, 2 part-time engineers):** This is one of the strongest signals you can get. They've already spent real engineering time and money trying to solve this problem. They've built a workaround, which proves the pain is real, not hypothetical. You can estimate the cost: two part-time engineers for 18 months is roughly 1 FTE-year of engineering salary invested in this problem.

- **"Breaks every other Kubernetes upgrade," 3 weeks to fix in November:** Specific past incident with a concrete timeline. This isn't "it's kind of annoying," it's "we lost 3 weeks of engineering time on a single incident." The "every other upgrade" pattern means this is a recurring, predictable cost. Ask in a follow-up: how often do they upgrade clusters, and what's the total annual cost of these breakages?

- **Evaluated Gitpod, dropped it for air-gapped requirements:** Active solution-seeking behavior. They didn't just complain about the problem, they went and evaluated a commercial product. The fact that they dropped it for a specific technical reason (air-gapped) tells you their buying criteria. This is gold: you now know one hard requirement without having to guess.

- **Asked about on-prem and FedRAMP:** He's qualifying *you*. When a prospect starts asking whether you meet their requirements, they've mentally moved past "is this a real problem?" and into "could this vendor solve it?" These are buying-criteria questions, not idle curiosity.

- **15-20 hours/week on environment-related support tickets:** Quantified, ongoing pain. This is roughly 0.5 FTE of engineering time burned on support. Combined with the 2 part-time engineers maintaining the tool, they're spending close to 1.5 FTE on this problem. That's a real budget number you can anchor pricing against.

- **CISO introduction:** This is a Level 3 commitment (Reputation). He's putting his name on the line by introducing you to the CISO. He wouldn't do this if he thought the conversation was a waste of time. This is also a strong signal that security/compliance is the real gating factor, not price or features.

- **"Bring it up at their next platform team retro":** This is softer than the CISO intro but still a concrete action he's committing to take. It's a Level 2 commitment (Time, indirectly). It would be stronger if you had a date for the retro and a follow-up scheduled afterward.

**Commitment check:**
- CISO intro: Level 3 (Reputation). Real commitment.
- Platform team retro mention: Level 2 (Time), but soft. No specific follow-up date.

**Scorecard:**

| Category | Assessment |
|----------|------------|
| Trustworthy learnings | Internal tool cost (~1.5 FTE), specific breakage pattern, air-gapped requirement, quantified support ticket burden, security/compliance as key buying criteria. |
| Sounded good but unreliable | Nothing here falls into this category. Every data point is anchored in past behavior or current spending. |
| Commitment obtained | CISO intro (Level 3). Platform retro mention (Level 2, soft). |
| Next steps | Follow up on the CISO intro immediately (don't let it go cold). Get a date for the platform retro and ask if you can present or at least get the outcome. Quantify the total annual cost of the internal tool + support tickets to build the business case. |

This is a high-signal conversation. Almost every data point is grounded in specific past behavior, current spending, or concrete action. The prospect is already in active solution-seeking mode.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Strong signals identified throughout | ✅ |
| Internal tool = real pain and existing spending | ✅ |
| 3-week fix = specific costly incident | ✅ |
| Gitpod eval = active solution-seeking | ✅ |
| On-prem/FedRAMP = real buying criteria | ✅ |
| 15-20 hrs/week = quantified pain | ✅ |
| CISO intro = real commitment (reputation) | ✅ |
| Retro mention = softer but concrete | ✅ |
| Scored as high-signal | ✅ |

**Result: PASS**

---

## Test 7: assumption-extraction-feature

**Prompt:** Apply the mom test to this feature idea and extract the assumptions:

We want to add a 'Smart Preview' button to our developer platform. When a developer pushes code, instead of deploying to a shared preview environment, we'd spin up an ephemeral environment with their changes, run a suite of automated checks, and generate a visual diff of UI changes. Engineering managers could then approve changes directly from a Slack notification without context-switching to a browser.

### Skill Output

**Implicit assumptions, ranked by risk:**

1. **The approval bottleneck is real and costly.** You're assuming engineering managers are a bottleneck in the review/approval process and that this costs meaningful time. If managers approve quickly or the bottleneck is elsewhere (CI pipeline, code review from peers), this entire feature is solving a problem that doesn't exist.
   - Risk: High (if wrong, the feature has no user)
   - Confidence: Low (untested)
   - Test: Talk to engineering managers. "Walk me through what happens after a developer opens a PR. Where does it sit, and for how long? What slows things down?" Also talk to developers: "What's the longest you've waited for approval on a change? What was blocking it?"
   - Invalidated if: Managers say approvals take minutes, or developers identify peer review (not manager approval) as the bottleneck.

2. **Engineering managers want to approve from Slack specifically.** You're assuming Slack is where managers want to do this, rather than GitHub, email, or their existing review tool. This is a strong UX assumption baked into the design.
   - Risk: High (if wrong, you built the integration in the wrong place)
   - Confidence: Low (untested)
   - Test: "Where do you spend most of your time when you're reviewing or approving changes? Walk me through your workflow." Don't mention Slack. See if they mention it themselves.
   - Invalidated if: Managers say they live in GitHub or a review tool, not Slack. Or if they say they actively avoid doing substantive review in Slack because it lacks context.

3. **Shared preview environments are the current approach, and they're a pain point.** You're assuming teams have shared preview environments and that contention or staleness is a problem. Some teams may not use preview environments at all, or may already use ephemeral ones.
   - Risk: Medium-high (if they don't have shared previews, the "instead of" framing doesn't land)
   - Confidence: Medium (common in larger teams, but varies)
   - Test: "How does your team preview or test changes before they go to production? Walk me through the process." See if shared environments come up naturally.
   - Invalidated if: They already use ephemeral environments, or they don't use preview environments at all (going straight from local to CI to staging).

4. **Visual diffs are more useful than existing diff tools.** You're assuming a visual diff of UI changes adds value beyond what developers and managers already see in code diffs, screenshot tests, or their existing review process.
   - Risk: Medium (a nice-to-have assumption masquerading as a core feature)
   - Confidence: Low
   - Test: "When you're reviewing a frontend change, how do you currently verify it looks right? What's that process like?" Also: "Have you ever approved a change that looked fine in code review but broke the UI? What happened?"
   - Invalidated if: They say code diffs are sufficient, or they already use visual regression tools like Percy or Chromatic.

5. **Automated checks aren't already running in CI.** The feature assumes running automated checks in the ephemeral environment adds value, but many teams already run checks in CI before review.
   - Risk: Medium (if they already run checks in CI, this part of the feature is redundant)
   - Confidence: Medium-low
   - Test: "What automated checks run on a PR today? Where do they run, and how long do they take?"
   - Invalidated if: They already have comprehensive CI checks and are happy with them.

6. **Ephemeral environment spin-up time is fast enough.** If the ephemeral environment takes 10+ minutes to spin up, it's slower than the shared environment it replaces and developers won't use it.
   - Risk: Medium
   - Confidence: Unknown
   - **Not testable through conversation.** This is a technical feasibility assumption. Test it with benchmarks and prototyping. You need to know: what's the p50 and p95 spin-up time for your target customer's typical environment?

7. **Visual diff accuracy is high enough to be useful.** If the visual diff generates false positives or misses real changes, managers won't trust it and will context-switch to a browser anyway.
   - Risk: Medium
   - Confidence: Unknown
   - **Not testable through conversation.** Requires prototyping and testing against real codebases.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Surfaces assumption about shared preview environments | ✅ |
| Surfaces approval bottleneck assumption | ✅ |
| Surfaces Slack-specific assumption | ✅ |
| Surfaces visual diff vs existing tools | ✅ |
| Surfaces CI checks redundancy | ✅ |
| Surfaces spin-up time assumption | ✅ |
| Ranked by risk | ✅ |
| Conversation-based tests for top assumptions | ✅ |
| Technical assumptions flagged as not conversation-testable | ✅ (spin-up time, visual diff accuracy) |

**Result: PASS**

---

## Test 8: assumption-extraction-strategic

**Prompt:** Mom test this. We're considering adding ARM cluster support (AWS Graviton) to our platform. The thesis is that enterprise customers are migrating to ARM for cost savings and they need their dev environments to match production architecture. We'd roll it out in phases: first ARM node pools, then ARM-native builds, then mixed-architecture preview environments.

### Skill Output

**Implicit assumptions, ranked by risk:**

1. **Enterprises are actually migrating to ARM, not just evaluating it.** There's a big difference between "we're looking at Graviton" and "we've moved production workloads to Graviton." If most enterprises are still in evaluation or running small experiments, the urgency for dev environment parity isn't there yet.
   - Risk: High (the entire initiative depends on this being true at scale)
   - Confidence: Medium-low (industry press covers ARM migration heavily, but press coverage doesn't equal adoption)
   - Test: Talk to platform/infrastructure leads. "What percentage of your production workloads run on ARM today? When did you start the migration? What's the timeline for the rest?" Don't ask "are you interested in ARM?" — ask what they've actually done.
   - Invalidated if: Most say they're evaluating or running less than 10% of workloads on ARM. Validated if they give specific migration timelines and percentages.

2. **Dev/prod architecture mismatch is causing real bugs, not just theoretical concern.** You're assuming that running x86 dev environments against ARM production creates problems that engineers actually encounter. It might be a theoretical concern that platform teams worry about but that rarely manifests in practice.
   - Risk: High (if the mismatch doesn't cause real issues, the urgency evaporates)
   - Confidence: Low (untested)
   - Test: "Have you ever had a bug that only appeared in production because the dev environment was running a different architecture? Tell me what happened." Also: "How are your developers working on code that runs on Graviton today? What's their local setup?"
   - Invalidated if: They can't cite a specific incident, or they say it's never been a problem in practice. Validated if they describe specific, costly architecture-mismatch bugs.

3. **Cost savings from ARM are large enough to motivate workflow changes.** You're assuming the cost savings are significant enough that enterprises will accept the friction of changing their dev toolchain. If the savings are marginal (5-10%), most teams won't bother.
   - Risk: Medium-high
   - Confidence: Medium
   - **Partially testable through conversation, partially a market question.** You can ask: "What cost savings have you seen from Graviton so far? How did that compare to your expectations?" But the broader market question (what's the typical savings at scale) is better answered through benchmarks and published case studies.

4. **Developers care about architecture parity, or at least their platform teams do.** Some developers just want things to work and don't care what architecture they're developing on. The pain might only be felt by the platform team, not the developers who'd actually use the feature.
   - Risk: Medium (affects adoption even if the platform team buys it)
   - Confidence: Low
   - Test: Talk to both platform leads and individual developers. Platform leads: "How are you handling the dev environment side of your ARM migration?" Developers: "What's your local dev setup for services that run on Graviton in production? Have you run into any issues?"
   - Invalidated if: Developers say they don't think about it and it hasn't caused problems. Platform leads say they've solved it with CI checks or cross-compilation.

5. **Customers need all three phases, and they'd adopt in that order.** You've assumed a specific adoption sequence (ARM node pools → ARM-native builds → mixed-architecture previews). Customers might only need phase 1, or might want to jump to phase 3 because that's where their actual pain is.
   - Risk: Medium (affects roadmap sequencing and investment)
   - Confidence: Low (assumed, not validated)
   - Test: "If you could wave a magic wand and fix one thing about how your team develops for ARM, what would it be?" Also: "Walk me through the parts of your ARM workflow that are the most painful today." Let them tell you the priority order rather than assuming it.
   - Invalidated if: Customers describe pain that maps to phase 3 but not phase 1, or they only care about one phase and not the others.

6. **There isn't already a good enough solution.** Customers might already be handling architecture parity through Docker multi-arch builds, QEMU emulation, or CI-based cross-compilation. If existing workarounds are "good enough," the willingness to adopt a new platform feature is low.
   - Risk: Medium
   - Confidence: Low
   - Test: "What are you doing today to ensure your dev environments match your production architecture? How well is that working?"
   - Invalidated if: They describe a working solution and don't express frustration with it.

### Eval Criteria Check

| Criterion | Pass? |
|-----------|-------|
| Surfaces assumption about actual migration vs evaluation | ✅ |
| Surfaces dev/prod mismatch as real vs theoretical | ✅ |
| Surfaces cost savings magnitude | ✅ |
| Surfaces developer vs platform team caring | ✅ |
| Surfaces phased rollout assumptions | ✅ |
| Distinguishes conversation-testable from market/benchmark questions | ✅ |
| "Enterprises are migrating" flagged as conversation-testable | ✅ |
| "ARM reduces costs by X%" flagged as market question | ✅ |

**Result: PASS**

---

## Summary

| Test | Mode | Name | Result |
|------|------|------|--------|
| 1 | Question Review | question-review-all-risky | ✅ PASS |
| 2 | Question Review | question-review-mixed-quality | ✅ PASS |
| 3 | Question Generation | question-generation-onboarding | ✅ PASS |
| 4 | Question Generation | question-generation-with-persona | ✅ PASS |
| 5 | Conversation Analysis | transcript-analysis-fake-positive | ✅ PASS |
| 6 | Conversation Analysis | transcript-analysis-with-real-signals | ✅ PASS |
| 7 | Assumption Extraction | assumption-extraction-feature | ✅ PASS |
| 8 | Assumption Extraction | assumption-extraction-strategic | ✅ PASS |

**8/8 tests pass.** All modes produce output consistent with the framework and meet the expected criteria.

**Notes for iteration:**
- Test 4 Q8 edges close to revealing the solution ("building something"). Consider whether the skill should have a harder rule about never mentioning your own product, even vaguely, in generated questions.
- The conversation analysis mode (Tests 5-6) produces long output. Consider whether the skill should instruct for a shorter default format with an option to expand.
- The skill doesn't currently address the case where a user provides *both* a transcript and questions in the same prompt (i.e., "here are the notes from my call AND here are my questions for the next one"). A combined mode might be useful.
