---
name: mom-test
description: >
  Apply Rob Fitzpatrick's "The Mom Test" framework to product discovery work.
  This skill is invoked explicitly when the user asks to use "the mom test skill"
  or phrases like "apply the mom test", "mom test this", or "use mom-test".
  It helps with: reviewing interview questions for bias, generating good customer
  discovery questions from hypotheses, analyzing conversation transcripts for
  weak signals and deflections, and extracting risky assumptions from product
  ideas. Use this skill any time the user wants to pressure-test their customer
  discovery approach, even if they phrase it casually (e.g., "are these good
  interview questions?" after invoking the skill earlier in the conversation).
---

# The Mom Test Skill

This skill applies The Mom Test framework to product discovery tasks. Before
doing anything else, read `references/principles.md` to load the full framework.

## Core Philosophy

The Mom Test is built on one insight: people will lie to you, not out of malice
but out of politeness. Your mom will tell you your app idea is great because she
loves you, not because it is great. The only way to get reliable signal from
customer conversations is to talk about *their life and behavior*, not your idea.

Three rules govern every question you write or evaluate:

1. Talk about their life, not your idea
2. Ask about specifics in the past, not hypotheticals about the future
3. Talk less, listen more

## Modes of Operation

When the user invokes this skill, determine which mode fits their request. If
ambiguous, ask.

### Mode 1: Question Review

The user has draft interview or discovery questions and wants them evaluated.

For each question:
- Classify it as **safe** (past behavior, specifics, their life) or **risky**
  (hypothetical, opinion-seeking, pitching-disguised-as-asking, future-tense
  promises, compliment-fishing)
- For risky questions, explain *why* it's risky using framework language
- Provide a rewritten version that preserves the intent but follows the rules
- Flag if the overall question set is leading the witness toward a predetermined
  answer

Format the output as a sequential review of each question. Don't just list
problems in the abstract; rewrite every risky question so the user walks away
with a usable set.

### Mode 2: Question Generation

The user provides a hypothesis, assumption, feature idea, or problem space and
wants discovery questions generated.

Process:
1. Restate the underlying assumption being tested (confirm with user if unclear)
2. Generate 5-8 questions that test the assumption without revealing it
3. For each question, include a parenthetical note on what signal a strong or
   weak answer would look like
4. Order questions from broad/warm-up to specific/commitment
5. Include at least one "advancement" question that pushes for a concrete next
   step (intro to another person, willingness to pay, letter of intent, etc.)

The questions should feel like a natural conversation, not an interrogation. If
the user provides context about who they're talking to, tailor the language and
framing accordingly.

### Mode 3: Conversation / Transcript Analysis

The user provides notes, a transcript, or a summary of a customer conversation
and wants it analyzed.

Analyze for:
- **Compliment deflections**: Where did the customer say nice things that
  contain no actionable information? Flag these and note what follow-up question
  would have extracted real signal.
- **Hypothetical traps**: Where did the conversation slip into "would you" or
  "do you think" territory? Note what actually happened vs. what was explored.
- **Missing specifics**: Where did the customer make a general claim ("we spend
  a lot on that") without being pressed for numbers, frequency, or examples?
- **Buried signals**: What offhand comments or complaints might indicate real
  pain that wasn't followed up on?
- **Commitment check**: Did the conversation end with any form of advancement
  (intro, payment, follow-up meeting, access to data), or just a compliment?

Provide a summary scorecard at the end: what was learned that's trustworthy, what
sounded good but is unreliable, and what to dig into next time.

### Mode 4: Assumption Extraction

The user provides a product idea, feature spec, PRD, or strategic initiative and
wants the riskiest assumptions surfaced.

Process:
1. List every implicit assumption (about the customer, the problem, the market,
   the willingness to pay, the workflow, the switching cost, etc.)
2. Rank them by risk: how bad is it if this assumption is wrong, and how
   confident are we that it's right?
3. For the top 3-5 riskiest assumptions, provide a concrete conversation-based
   test: who to talk to, what to ask, and what answer would validate or
   invalidate the assumption
4. Flag any assumptions that *can't* be tested through conversation (e.g., pure
   technical feasibility) and suggest alternative validation methods

## General Guidelines

Across all modes:

- Never let the user accidentally pitch their idea inside a discovery question.
  If a question contains the solution ("What if we built X?"), flag it
  immediately.
- Treat "would you use this?" and "would you pay for this?" as red flags, always.
  Past behavior and current spending are the only reliable predictors.
- Emotional language from customers ("I hate our current tool") is interesting
  but not sufficient. Always push toward: what have they actually *done* about
  the problem? Have they tried alternatives? Have they spent money? Have they
  built workarounds?
- When generating or reviewing questions, bias toward questions that are hard to
  answer with a polite lie. "How do you currently handle X?" is much harder to
  lie about than "Would a tool that does X be useful?"
- Advancement and commitment are the real currency. A conversation without a
  concrete next step is a conversation where you learned nothing about real
  demand.
