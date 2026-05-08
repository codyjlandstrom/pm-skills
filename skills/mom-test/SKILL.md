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

For each question, classify it into one of three tiers:

- **Safe**: Past behavior, specifics, about their life. No changes needed.
- **Sequencing-sensitive**: The question follows the rules structurally, but it
  reveals your focus area or hypothesis. Safe if asked later in the conversation
  (after trust is built and broader context is established), but risky if asked
  too early. Flag these with a note on where in the conversation they belong.
- **Risky**: Hypothetical, opinion-seeking, pitching-disguised-as-asking,
  future-tense promises, or compliment-fishing. Explain *why* it's risky using
  framework language, and provide a rewritten version that preserves the intent
  but follows the rules.

Flag if the overall question set is leading the witness toward a predetermined
answer.

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

After the questions, include a short "Things You Should NOT Say" section. List
3-5 specific phrases, framings, or question patterns that would accidentally
reveal the hypothesis, pitch the solution, or otherwise contaminate the
conversation. This helps the user stay disciplined during the live call when
they're tempted to ad-lib.

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
- **Interviewer bias**: Flag any editorializing in the notes that reflects the
  interviewer's feelings rather than observable facts. Phrases like "she seemed
  really engaged," "he was excited about the idea," or "it was a really positive
  call" are the interviewer's interpretation, not data. These are dangerous
  because they inflate perceived signal and obscure what was actually said.
- **Commitment check**: Did the conversation end with any form of advancement
  (intro, payment, follow-up meeting, access to data), or just a compliment?
  Critically distinguish between **offered** commitments ("he said he'd intro me
  to the CISO") and **realized** commitments ("he emailed the CISO and CC'd me
  that afternoon"). An offered commitment is a weak signal until it actually
  happens. Many offered intros, follow-ups, and meetings never materialize.
  Score offered commitments one level lower on the commitment ladder than
  realized ones.

Provide a summary scorecard at the end: what was learned that's trustworthy, what
sounded good but is unreliable, and what to dig into next time.

### Mode 4: Assumption Extraction

The user provides a product idea, feature spec, PRD, or strategic initiative and
wants the riskiest assumptions surfaced.

Process:
1. Sweep for assumptions across these categories systematically:
   - **Customer**: Who has this problem? Are they who we think they are?
   - **Problem**: Is the problem real, frequent, and painful enough to solve?
   - **Existing behavior**: What are they doing today, and is it bad enough to
     change?
   - **Market**: Is the timing right? Is the market large enough?
   - **Willingness to pay**: Will they spend money on this, and how much?
   - **Workflow/adoption**: Will this fit into how they work, or does it require
     behavior change?
   - **Technical feasibility**: Can we actually build this?
   - **Go-to-market**: Can we reach these customers, and through what channel?
2. Rank them by risk: how bad is it if this assumption is wrong, and how
   confident are we that it's right?
3. For the top 3-5 riskiest assumptions, provide a concrete conversation-based
   test: who to talk to, what to ask, and what answer would validate or
   invalidate the assumption
4. Flag any assumptions that *can't* be tested through conversation (e.g., pure
   technical feasibility, market sizing) and suggest alternative validation
   methods

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
