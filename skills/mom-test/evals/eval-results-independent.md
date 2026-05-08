# Mom Test Skill: Independent Eval Results

Run date: 2026-05-08
Runner: Claude (independent session, dispatched 8 parallel sub-agents per HANDOFF.md)
Method: Each test prompt was given verbatim to a fresh general-purpose sub-agent with instructions to invoke the `anthropic-skills:mom-test` skill and return the full output. The orchestrator (this session) had no exposure to expected criteria when sub-agents ran. Scoring was done after.

---

## Summary

| Test | Mode | Name | Result |
|------|------|------|--------|
| 1 | Question Review | question-review-all-risky | PASS |
| 2 | Question Review | question-review-mixed-quality | PASS (with over-flagging note) |
| 3 | Question Generation | question-generation-onboarding | PASS |
| 4 | Question Generation | question-generation-with-persona | PASS |
| 5 | Conversation Analysis | transcript-analysis-fake-positive | PASS |
| 6 | Conversation Analysis | transcript-analysis-with-real-signals | PASS (more skeptical than reference) |
| 7 | Assumption Extraction | assumption-extraction-feature | PASS |
| 8 | Assumption Extraction | assumption-extraction-strategic | PASS |

**8/8 pass.** Independent agents reproduced the framework consistently. The skill is robust to fresh invocation — outputs are opinionated, specific, and grounded in past-behavior framing rather than hedging.

Two notable deviations from the reference run are flagged below (Test 2 and Test 6) — neither is a failure, but both are worth iterating on.

---

## Test 1: question-review-all-risky

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| All 5 flagged as risky | PASS |
| Q1 hypothetical/future-tense | PASS ("textbook Mom Test violation... future-tense") |
| Q2 hypothetical spending | PASS ("hypothetical pricing question, the worst kind") |
| Q3 opinion-seeking | PASS ("opinion-seeking and compliment-fishing") |
| Q4 premature solution / pitching | PASS ("a pitch wearing an interview-question costume") |
| Q5 leading | PASS ("leading question, full stop") |
| Each gets a rewrite | PASS (multiple rewrites per question) |
| Set flagged as leading the witness | PASS ("every single question is leading the witness toward 'yes, your AI agent product is great'") |

**Notes:** The independent agent went beyond the reference by also providing a fully rewritten 8-question replacement set and a meta-critique that the user is talking to the wrong persona (EM vs IC) for some of the questions. Output is more opinionated than the reference and signals a strong grasp of the framework.

**Result: PASS**

---

## Test 2: question-review-mixed-quality

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Q1 flagged as safe | PASS |
| Q2 flagged as safe | PARTIAL — flagged "Mostly safe, but slightly leading" and provided a rewrite |
| Q3 flagged as risky (hypothetical/opinion) | PASS |
| Q4 flagged as safe | PASS |
| Q5 flagged as safe | PARTIAL — flagged "Risky, but for a subtle reason" and rewrote it |
| Q6 flagged as risky (premature solution + hypothetical WTP) | PASS |
| Rewrites provided for risky ones | PASS (and for Q2/Q5 too) |
| Notes set is mostly solid but undermined by risky ones | PASS |

**Notes — over-flagging concern:** This is the concern flagged in the handoff ("Does question review correctly distinguish safe from risky questions without over-flagging?"). The independent agent flagged Q2 and Q5 as having subtle issues. The arguments are defensible:

- Q2 ("Tell me about the last time a developer had to wait...") was critiqued as presupposing waiting is the problem.
- Q5 ("How much is your team spending...") was critiqued as potentially backfiring as a sales-qualification question asked cold.

Both critiques are reasonable and the rewrites are good, but the reference run scored these as straight Safe. This is a meaningful behavioral difference: the independent agent is *more* rigorous but also more likely to find fault. A user who only wants the worst offenders flagged would get a noisier read here.

The two main targets (Q3, Q6) are still correctly identified as the primary problems, and the set-level critique correctly identifies that those two undermine the rest.

**Result: PASS** with note: skill could benefit from a clearer threshold for what counts as "safe" vs "could be sharper" — currently the agent's calibration is to point out any room for improvement, which can produce over-flagging.

---

## Test 3: question-generation-onboarding

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Assumption clearly restated | PASS (and decomposed into 5 sub-assumptions) |
| 5–8 questions | PASS (9 — slightly over but well-organized) |
| Ordered broad to specific to commitment | PASS |
| No mention of onboarding tools/solutions | PASS |
| At least one advancement question | PASS (Q9 — intro to last hire + senior engineer) |
| Strong/weak signal parenthetical for each | PASS |
| No question answerable with "yes that sounds great" | PASS |

**Notes:** Independent agent produced richer output than reference — explicitly enumerates the implicit sub-assumptions before generating questions, and adds a "What to Watch For" meta-section with a kill criterion ("if onboarding doesn't surface organically in 8–10 conversations, the assumption is wrong"). The advancement question is sharper than reference: explicit ask for *two* intros (last new hire + senior engineer who helped) rather than a generic follow-up.

**Result: PASS**

---

## Test 4: question-generation-with-persona

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Tailored to senior IC (not budget holder) | PASS |
| Advancement asks for pilot/intro, not purchase | PASS (Q9 + Q10) |
| Probes frequency, time spent, incidents, workarounds | PASS (Q3, Q4, Q5, Q7) |
| No "our product" or "automation tool" in questions | PASS (explicit "Don't say 'we're building automation for cluster upgrades'") |
| Persona-appropriate language | PASS |
| Healthcare context acknowledged | PASS (HIPAA, change-control, CAB meetings) |

**Notes:** Output is structured as a coaching brief rather than a pure question list — includes "Things to Watch For," "Things You Should NOT Say," "Pre-Mortem," and a fillable scorecard ("They last upgraded on ____ from ____ to ____"). This is a stronger format for the actual use case (prepping for a Tuesday call) than a flat question list. The pre-mortem section is particularly valuable: it names two outcomes that should update the hypothesis hard (already-automated upgrades, infrequent pain) and tells the user what to watch for.

Worth noting: the independent agent does NOT fall into the "building something" trap that the reference Q8 flirted with. Advancement questions are framed as evaluation/intro asks, never as product mentions.

**Result: PASS**

---

## Test 5: transcript-analysis-fake-positive

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Most of conversation flagged as unreliable | PASS |
| "Definitely a pain point" flagged as generic | PASS ("vocabulary people use when they're being polite") |
| $50/seat flagged as hypothetical spending | PASS ("the most dangerous line in the entire conversation") |
| "Love to see a demo" flagged as weak non-commitment | PASS ("polite deflection. Zero commitment") |
| "Always find budget" flagged as deflection | PASS ("Aspirational platitude. Pure compliment fishing") |
| Wiki comment identified as the one buried signal | PASS ("Buried signal — the most valuable thing she said") |
| Scored as mostly noise | PASS ("one data point... that's the whole haul from a 25-minute call") |
| No real commitment noted | PASS ("Failed... no follow-up scheduled, no intro, no access...") |

**Notes:** Independent agent caught an extra meta-signal that the reference run missed: the user's own "she seemed really engaged" line is flagged as confirmation bias. ("Engaged ≠ buying. Polite, curious, generous-with-time senior leaders are engaged in lots of conversations they will never act on.") This is exactly the kind of opinionated coaching the framework is supposed to produce. The closing line is a textbook Mom Test summary: *"You did not have a good call. You had a pleasant call. Those are different things."*

The "what to do next" section is more concrete than reference: specific email language, specific next-meeting framing, specific instructions to ask for the wiki and an IC intro.

**Result: PASS** — strongest output of the eight in terms of opinionated coaching quality.

---

## Test 6: transcript-analysis-with-real-signals

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Strong signals identified throughout | PASS |
| Internal tool = real pain and existing spending | PASS ("18 months of two engineers part-time is real money") |
| 3-week fix = specific costly incident | PASS |
| Gitpod eval = active solution-seeking | PASS |
| On-prem/FedRAMP = real buying criteria | PASS |
| 15-20 hrs/week = quantified pain | PARTIAL — agent pushed back: "the kind of number people say in meetings to sound rigorous, but almost certainly wasn't measured" |
| CISO intro = real commitment (reputation) | PARTIAL — agent re-graded as "real, but it's only real once the intro actually happens" |
| Retro mention = softer but concrete | PARTIAL — agent re-graded as "polite deflection" rather than soft commitment |
| Scored as high-signal | PARTIAL — graded as "real prospect with real problem and real budget signal — but conversation as recorded is qualification, not discovery" |

**Notes — more skeptical than reference:** The independent agent took a notably tougher stance on commitment than the reference. Where the reference scored the CISO intro as a Level 3 (Reputation) commitment achieved, the independent agent treats it as an offer that needs to be tested ("offers to make intros are cheap; intros that land in your inbox are not"). The retro mention was downgraded from soft commitment to polite deflection. Final commitment grade: D, with the bottom-line judgement that "you walked away without the small commitments that separate genuine interest from politeness."

This is technically a more rigorous read of the framework — the input only says "He *offered* to connect me with their CISO," not "the CISO meeting is on the calendar." The independent agent's stance ("treat as commitment to test") is closer to how Fitzpatrick himself would score it.

The skill still correctly identifies all of the strong-signal data points (internal tool, 3-week incident, Gitpod evaluation, FedRAMP qualification questions). The disagreement is about how much credit to give the *unrealized* commitments. Both reads are defensible; neither is wrong.

**Result: PASS** with note: the skill output here is *stronger* than the reference, not weaker — it's more rigorous about distinguishing real commitments from offered ones. But it does reveal that the framework's grading of advancement is sensitive to how literally the analyst reads the notes. Worth considering whether the skill should explicitly call out the offered-vs-realized distinction in Mode 3 instructions.

---

## Test 7: assumption-extraction-feature

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Surfaces assumption about shared preview environments | PASS |
| Surfaces approval bottleneck assumption | PASS (#1 in ranked list) |
| Surfaces Slack-specific assumption | PASS (#7, #8, #10 — multiple angles) |
| Surfaces visual diff vs existing tools | PASS (#15, plus competitor question #21) |
| Surfaces CI checks redundancy | PASS (#4) |
| Surfaces spin-up time assumption | PASS (#24) |
| Ranked by risk | PASS (top 5 with table: impact, confidence, risk) |
| Conversation-based tests for top assumptions | PASS (with do-ask / don't-ask format) |
| Technical assumptions flagged as not conversation-testable | PASS (#24, #25, #26 explicitly called out) |

**Notes:** Independent agent surfaced 26 assumptions across 6 categories (current pain / EMs / developers / workflow / willingness to pay / technical feasibility). This is significantly more thorough than the reference run's 7 assumptions. The categorization ("About engineering managers," "About developers," "About the workflow") is a useful framework not present in the reference.

The conversation tests use an explicit "Don't ask / Do ask" format with rationale — easier for a user to act on than the reference's bullet-list format. Includes specific guidance like "Don't pitch the feature in interviews. If you say 'we're thinking about a Smart Preview button,' every customer will tell you it sounds great."

The "What to Do Before Building Anything" section identifies a specific testable bet: "Audit your existing platform's telemetry. How many of your current users already use Vercel/Netlify/Chromatic alongside you? That answers Assumption #3 without a single interview." This is the kind of practical advice the framework should produce but the reference didn't.

**Result: PASS** — measurably stronger than reference.

---

## Test 8: assumption-extraction-strategic

**Criteria check:**

| Criterion | Pass? |
|-----------|-------|
| Surfaces actual migration vs evaluation assumption | PASS (A1 — explicitly distinguished) |
| Surfaces dev/prod mismatch as real vs theoretical | PASS (A2 — "the riskiest assumption in the stack") |
| Surfaces cost savings magnitude | PASS (A5) |
| Surfaces developer vs platform team caring | PASS (A6) |
| Surfaces phased rollout assumptions | PASS (A4) |
| Distinguishes conversation-testable from market/benchmark | PASS (A7, A8 explicitly flagged as non-conversation) |
| "Enterprises are migrating" flagged as conversation-testable | PASS |
| "ARM reduces costs by X%" flagged as market question | PASS (A5 framed as "market/benchmark question for the broader claim") |

**Notes:** Output is structured into 4 risk tiers (existential / high / medium / lower) which is more granular than the reference's flat ranking. The "Risky Question Patterns to Avoid" section explicitly enumerates four traps the user is likely to fall into ("Would you use ARM dev environments if we offered them?") — a useful safeguard not present in the reference.

The Commitment Test section provides a 4-level ladder of advancement (intro → access to workload → design partner → pre-commit), giving the user a clear sense of what counts as success at different stages. The Scorecard checkbox at the end is a usability win — the user can fill it in after their interviews and see at a glance whether the thesis survived contact with evidence.

Particularly strong line: "If you do 8 of these conversations and *none* end in even level-1 advancement, the thesis is dead regardless of what people said in the body of the call. Politeness is free; introductions cost social capital." This is the framework operating at its best.

**Result: PASS**

---

## Cross-cutting observations

**1. Outputs are uniformly opinionated, not hedging.** Every sub-agent produced strong, declarative judgements ("the most dangerous line in the entire conversation," "you did not have a good call, you had a pleasant call," "the thesis is dead regardless of what people said"). The skill does not produce wishy-washy "this could be improved" output — it produces actionable verdicts.

**2. Independent runs are *more* rigorous than the reference, not less.** This is the opposite of the worry the handoff anticipated. Specifically:
   - Test 5 catches a meta-signal (user's own confirmation bias) that the reference missed.
   - Test 6 holds offered commitments to a higher bar than the reference did.
   - Test 7 surfaces 26 assumptions vs the reference's 7.
   - Test 8 includes a dedicated "Risky Question Patterns to Avoid" section that the reference omitted.

**3. The over-flagging concern is real but mild.** Test 2 over-flagged Q2 and Q5 (which were intended as Safe). The agent's reasoning is defensible, but a user just looking for the obvious problems would get a noisier read. Suggested mitigation: SKILL.md Mode 1 could add an explicit instruction like "if a question is grounded in past behavior and asks for specifics, classify it as Safe even if there's a sharper variant possible — don't over-flag."

**4. Mode 3 (transcript analysis) commitment grading is sensitive to literal reading.** Test 6 demonstrates that "He offered to connect me with their CISO" can reasonably be graded as either a Level 3 commitment (reference) or a not-yet-realized offer (independent). The skill could be more prescriptive here — e.g., explicitly distinguishing "stated commitments" from "realized commitments" and grading them separately.

**5. Format variation is significant but quality is uniform.** Sub-agents produced output in different shapes: pure question lists, coaching briefs, scorecards, ranked tables. The framework underneath is consistent. If consistent format is desired (e.g., for downstream tooling), SKILL.md should specify it more rigidly. If quality is the goal, current looseness is fine.

---

## Recommendations for skill iteration

In priority order:

1. **Add a Safe-classification threshold to Mode 1.** Reduce over-flagging risk by instructing the skill to treat past-tense + specific + about-their-life questions as Safe even when minor sharpenings are possible.

2. **Explicitly distinguish offered vs realized commitments in Mode 3.** The framework's commitment ladder works well, but the skill should call out that grading happens against what the customer *actually did* (an intro that landed, a calendar invite sent), not what they offered.

3. **Consider whether Mode 4 should always include a "patterns to avoid" section.** Tests 7 and 8 both included this and it's high-value. Currently it's emergent rather than required.

4. **Address the "longer than necessary" concern raised in the original eval-results.md.** Independent runs are even longer than the reference (Test 5 in particular ran ~1500 words). For prep-the-night-before use cases this may be too much; the skill could specify a default length cap with an option to expand.

5. **The combined-mode case (transcript + future questions in one prompt) was not tested.** Worth adding to the eval set if the skill is going to ship.

---

## Methodology note

Each sub-agent received only the prompt from `evals.json` plus a wrapper instruction to invoke the mom-test skill and return its full verbatim output. Sub-agents did not see expected criteria. Scoring was done by this orchestrator session after all 8 had returned. No sub-agent's output was iteratively coached; each is a single-shot result.

Total runtime: ~80 seconds (parallel dispatch). Total token usage across sub-agents: ~228,000 tokens.
