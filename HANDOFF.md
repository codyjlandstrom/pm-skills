# Mom Test Skill: Independent Eval Handoff

## Context

We built a custom Claude skill called "mom-test" that applies Rob Fitzpatrick's "The Mom Test" framework to product discovery work. The skill is installed and active. The repo with source and test cases lives at `~/sites/claude-skills/`.

The skill operates in four modes:
1. **Question Review** - Evaluate interview questions for bias and anti-patterns
2. **Question Generation** - Generate discovery questions from a hypothesis
3. **Conversation Analysis** - Analyze customer call notes for signal vs noise
4. **Assumption Extraction** - Surface and rank risky assumptions in a product idea

## What to do

Run independent eval tests against the mom-test skill. The test cases are in `~/sites/claude-skills/skills/mom-test/evals/evals.json`. There are 8 tests covering all four modes.

For each test case:
1. Spawn a sub-agent with the prompt from the `prompt` field in evals.json
2. Capture the sub-agent's full response
3. Evaluate the response against the `expected_output` criteria
4. Score as PASS/FAIL with notes on any gaps

The skill files are at:
- `~/sites/claude-skills/skills/mom-test/SKILL.md` (main skill)
- `~/sites/claude-skills/skills/mom-test/references/principles.md` (framework reference)

Previous eval results (run by the same session that wrote the skill, so potentially biased) are at `~/sites/claude-skills/skills/mom-test/evals/eval-results.md`. All 8 passed, but the goal of this independent run is to see if a fresh agent produces comparably rigorous output.

## What to look for

Beyond pass/fail, pay attention to:
- Does the skill produce output that's *opinionated* and specific, or does it hedge and generalize?
- Does question review correctly distinguish safe from risky questions without over-flagging?
- Does question generation avoid leaking the hypothesis being tested?
- Does conversation analysis correctly identify the one real signal in test 5 (the wiki comment) while flagging everything else as noise?
- Are the assumption extractions genuinely ranked by risk, or just listed?

## After testing

Write results to `~/sites/claude-skills/skills/mom-test/evals/eval-results-independent.md` and commit to the repo on main. Flag any tests that fail or produce notably weaker output than expected.
