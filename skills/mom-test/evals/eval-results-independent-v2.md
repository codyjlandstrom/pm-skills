# Mom Test Skill: Independent Eval Results v2 (Post-Update)

Run date: 2026-05-08
Runner: Claude (independent session, dispatched 8 parallel sub-agents per HANDOFF.md)
Skill version: SKILL.md and principles.md updated 2026-05-08 with five framework changes:
1. Mode 1: three-tier classification (Safe / Sequencing-sensitive / Risky)
2. Mode 2: required "Things You Should NOT Say" section
3. Mode 3: explicit "Interviewer bias" detection
4. Mode 3: offered vs. realized commitment distinction (codified in principles.md §5)
5. Mode 4: systematic 8-category assumption sweep

Pre-flight check: confirmed installed skill at `~/Library/Application Support/Claude/.../skills/mom-test/` was a stale snapshot and synced repo files before dispatching sub-agents. Verified all 5 changes were present before running.

---

## Summary

| Test | Mode | Name | v1 Result | v2 Result | Delta |
|------|------|------|-----------|-----------|-------|
| 1 | Question Review | question-review-all-risky | PASS | PASS | unchanged |
| 2 | Question Review | question-review-mixed-quality | PASS (over-flag) | **PASS (over-flag fixed)** | improved |
| 3 | Question Generation | question-generation-onboarding | PASS | PASS | unchanged |
| 4 | Question Generation | question-generation-with-persona | PASS | PASS | unchanged |
| 5 | Conversation Analysis | transcript-analysis-fake-positive | PASS | PASS | unchanged (now grounded in framework) |
| 6 | Conversation Analysis | transcript-analysis-with-real-signals | PASS (more skeptical) | **PASS (now framework-grounded)** | improved |
| 7 | Assumption Extraction | assumption-extraction-feature | PASS | PASS | unchanged |
| 8 | Assumption Extraction | assumption-extraction-strategic | PASS | PASS | improved (explicit framework refs) |

**8/8 pass. Two of the three v1 issues are fully resolved; the third (Things You Should NOT Say label adoption) is partial.**

---

## Test 2: question-review-mixed-quality — OVER-FLAGGING FIXED

This was the primary motivation for the v1 → v2 changes. v1 flagged Q2 and Q5 as Risky outright, when the eval criteria expected them to be Safe.

**v2 verdicts:**

| Q | v1 verdict | v2 verdict | Expected |
|---|------------|------------|----------|
| Q1 | Safe | Safe ("Keep as-is") | Safe |
| Q2 | "Mostly safe, but slightly leading" → rewrote it | "Safe, but presupposes the problem exists. Soften." | Safe |
| Q3 | Risky | "Risky. This is the biggest red flag in the set. Cut it." | Risky |
| Q4 | Safe | "Safe, but shallow as written. Deepen it." | Safe |
| Q5 | "Risky, but for a subtle reason" → rewrote it | "Safe in spirit but will likely get stonewalled as asked." | Safe |
| Q6 | Risky | "Risky. Cut it. This is a pitch wearing a question mark." | Risky |

**The over-flagging is fixed.** Q2 and Q5 are now classified as Safe rather than Risky — the agent makes a clear distinction between "Risky (Cut it)" and "Safe (with optional sharpening)." Q3 and Q6 remain the two clear Risky calls, matching the expected output.

**Note on label adoption:** The agent did not literally use the "Sequencing-sensitive" tier label from the new SKILL.md. Instead, it produced a softer two-tier output: "Risky / Safe (with caveats)." The framework's *intent* — distinguish genuine red flags from improvable-but-acceptable questions — is honored, even if the label itself is not. This is acceptable but worth noting: if the label adoption matters for downstream consumers, SKILL.md may need to enforce it more explicitly (e.g., "use the literal label 'Sequencing-sensitive' for this category").

**Result: PASS — primary v1 issue resolved.**

---

## Test 6: transcript-analysis-with-real-signals — OFFERED vs REALIZED EXPLICIT

v1 marked this PASS but with a note that the agent's commitment grading was more skeptical than the reference run, and that the framework was sensitive to literal vs. charitable reading.

**v2 explicitly invokes the new principles.md language.** Direct quote from the v2 output:

> "He offered to connect me with their CISO. **Genuinely positive — but it's an offer, not an introduction. Offers evaporate. Until that calendar invite exists, treat it as zero.**"

This is essentially quoting the new principles.md addition: *"An offered commitment ('I'll intro you to our CISO') is not the same as a realized commitment... score offered commitments one level lower than realized ones on the ladder above."*

**Net advancement: still scored at near-zero**, with the same firm stance v1 took, but now anchored in framework language rather than the agent's independent judgement. This is the desired outcome: the skill produces consistent rigor across runs because the framework now codifies what previously had to be inferred.

The signal-detection portion is unchanged — internal tool, 3-week fix, Gitpod evaluation, on-prem/FedRAMP, 15-20 hour figure (still appropriately skeptical) all correctly identified.

**Bonus catch:** The agent now produces a literal advancement-check table:

| Form of advancement | Happened? |
|---|---|
| Concrete next meeting on calendar | No |
| Demo scheduled | No |
| Intro to CISO confirmed (calendar invite) | **No (offered only)** |
| ... | ... |

This is a more rigorous format than v1 produced. The "offered only" annotation is exactly the new framework distinction in action.

**Result: PASS — v1 inconsistency resolved by codifying the offered vs realized distinction.**

---

## Test 5: transcript-analysis-fake-positive — INTERVIEWER BIAS NOW CODIFIED

v1 caught the user's "she seemed really engaged" line as confirmation bias on its own. v2 catches the same thing, but now the framework explicitly prompts for it. Quote from v2:

> "**'25 minutes, really engaged the whole time'**
> Verdict: Your own projection, not data.
> Engagement is not demand. People are engaged in conversations about their problems all the time without ever buying anything. Be very careful about reading energy as intent."

This was already happening in v1 emergently. v2 reinforces it with explicit framework language. No regression. No new gaps.

**Result: PASS — no behavior change but now framework-grounded.**

---

## Test 8: assumption-extraction-strategic — EXPLICITLY INVOKES NEW FRAMEWORK

v2 includes a direct callback to the new interviewer-bias instruction:

> "**Watch especially for interviewer bias creeping into your notes:** 'they seemed really excited about ARM' is not data. 'They've migrated 30% of prod to Graviton in the last 6 months and lost 2 engineer-weeks to a glibc-on-arm64 bug last sprint' is data."

And a "Specific risks in your current framing" section that ends with:

> "The most dangerous question you can ask in this round is 'would ARM support be valuable to you?' Every customer will say yes. **Ban that question and its variants from every conversation in this discovery cycle.**"

This is the spirit of "Things You Should NOT Say" applied to Mode 4. Even though it's an assumption-extraction prompt, the agent generated discovery questions and called out the risky patterns to avoid. Cross-mode framework consistency.

**Result: PASS — strongest demonstration that framework changes propagated.**

---

## Tests 1, 3, 4, 7 — UNCHANGED

These four tests were strong PASSes in v1 and remain strong PASSes in v2. No regressions introduced by the framework changes.

| Test | v1 | v2 |
|------|----|----|
| 1 | All 5 risky correctly identified, with rewrites and replacement set | Same |
| 3 | 8–9 questions, broad-to-specific, advancement question, sub-assumption decomposition | Same — 10 questions with 2 advancement asks |
| 4 | Senior IC tailored, healthcare context, no product-mention | Same — explicit pre-mortem and "what would falsify" section |
| 7 | 26 assumptions across 6 categories, top 5 with conversation tests | Same — 27 assumptions across 7 categories |

---

## Issues Resolved (vs v1 recommendations)

1. ✅ **Add Safe-classification threshold to Mode 1** — Implemented as three-tier (Safe / Sequencing-sensitive / Risky). Effect achieved; Test 2 over-flagging fixed even though the literal label "Sequencing-sensitive" was not adopted by the agent.

2. ✅ **Distinguish offered vs realized commitments in Mode 3** — Implemented in principles.md §5. Test 6 now produces consistent commitment grading anchored in framework language.

3. ✅ **Mode 4 systematic category sweep** — Implemented as 8-category checklist. Tests 7 and 8 both produce categorized output (though categories don't always literally match the 8 prescribed, the systematic sweep behavior is achieved).

4. ⚠️ **"Things You Should NOT Say" required in Mode 2** — Partially implemented. The instruction is in SKILL.md but agents don't always produce a section with that exact heading. They produce equivalent content under headings like "Things to Watch For," "Pre-Call Prep," or embed don't-ask guidance into the question parentheticals. Spirit is honored; literal section adoption is inconsistent.

5. ✅ **Interviewer bias detection in Mode 3** — Implemented. Tests 5 and 8 both explicitly invoke the framework. Behavior is consistent and well-grounded.

---

## Remaining Calibration Concerns

**1. Label adoption is loose.** The agents are interpreting the *intent* of the new framework rather than producing literal labeled sections. For Test 2, "Sequencing-sensitive" is not used as a label even though the underlying classification is correct. For Test 4, "Things You Should NOT Say" is not labeled even though the don't-do guidance is present.

If the goal is human-readable, opinionated output: this is fine. The framework is being applied.

If the goal is structured output that downstream tools (or other skills) can parse: the SKILL.md needs more prescriptive language. Something like *"Use the literal heading 'Things You Should NOT Say' as a section title in your output"* or *"Classify each question with one of these three exact labels: Safe, Sequencing-sensitive, Risky"* would force the format.

**2. Mode 4 8-category sweep is interpreted, not applied verbatim.** Test 7 used 7 categories ("About the developer's current pain," "About engineering managers as approvers," etc.) that overlap with but don't directly map to the 8 framework categories (Customer / Problem / Existing behavior / Market / WTP / Workflow / Technical / GTM). The agent is doing thoughtful categorization but not adopting the prescribed taxonomy. Same trade-off as #1.

---

## Recommendation for v3 (if iteration continues)

If the next round of changes targets format consistency:

- Add explicit "use this exact heading" / "use this exact label" instructions for Mode 1 tier classification, Mode 2 "Things You Should NOT Say" section, and Mode 4 category sweep.
- Consider adding a short "Output format example" at the end of each Mode in SKILL.md showing the expected structure.

If the next round targets behavior, no changes are urgent — the framework is producing the desired rigor. The remaining inconsistency is presentational.

---

## Methodology

Each sub-agent was given the prompt from `evals.json` verbatim, plus a wrapper instructing it to invoke `anthropic-skills:mom-test` and return the full output. Sub-agents had no exposure to expected criteria or to v1 results. Scoring was done by this orchestrator session after all 8 returned.

Total runtime: ~80 seconds (parallel dispatch). Total token usage across sub-agents: ~237,000 tokens.

Pre-flight: confirmed installed skill files at the runtime location matched the updated repo files before dispatching.
