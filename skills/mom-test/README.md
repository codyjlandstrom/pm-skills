# Mom Test

A Claude Code skill that applies Rob Fitzpatrick's *The Mom Test* framework to product discovery work.

## What it does

Pressure-tests your customer discovery in four modes:

1. **Question Review** - classifies draft interview questions as Safe, Sequencing-sensitive, or Risky. Every risky question gets a rewrite. Flags when the overall set is leading the witness.
2. **Question Generation** - given a hypothesis, produces 5–8 discovery questions that test it without revealing it. Each question comes with a strong/weak signal note. Includes a "Things You Should NOT Say" section for live-call discipline.
3. **Conversation Analysis** - analyzes transcripts or notes for compliment deflections, hypothetical traps, missing specifics, buried signals, and interviewer bias. Distinguishes offered commitments ("he said he'd intro me") from realized ones (the intro actually landed).
4. **Assumption Extraction** - sweeps a product idea for assumptions across 8 categories (customer, problem, existing behavior, market, willingness to pay, workflow, technical feasibility, GTM), ranks them by risk, and gives you a conversation-based test for each top-tier one.

## Install

See the [top-level README](../../README.md#install) for both install paths. TL;DR:

```
/plugin marketplace add codyjlandstrom/pm-skills
/plugin install mom-test@pm-skills
```

## Usage

The skill uses explicit invocation. Trigger it with phrases like:

- "use the mom test skill"
- "mom test this"
- "apply the mom test"

### Examples

**Review questions before a customer call:**
> Mom test these interview questions: [your questions]

**Generate questions from a hypothesis:**
> Apply the mom test. We're assuming that [your assumption]. Generate interview questions.

**Analyze a conversation:**
> Use the mom-test skill to analyze this customer call: [your notes]

**Extract assumptions from a feature idea:**
> Mom test this feature idea and extract the assumptions: [your spec]

## Evals

Receipts that this skill produces consistent, opinionated output:

- [Reference run](evals/eval-results.md) - run by the session that wrote the skill (known biased baseline).
- [Independent run v1](evals/eval-results-independent.md) - 8 fresh sub-agents with no exposure to the criteria. 8/8 pass. Surfaced a Mode 1 over-flagging bug and a Mode 3 commitment-grading inconsistency.
- [Independent run v2](evals/eval-results-independent-v2.md) - same 8 prompts after framework changes. Both v1 issues resolved; 8/8 still pass.

The 8 test cases live in [`evals/evals.json`](evals/evals.json). The methodology is documented in the repo-level [`HANDOFF.md`](../../HANDOFF.md).

## Structure

```
mom-test/
├── SKILL.md                # main skill instructions
├── references/
│   └── principles.md       # framework reference loaded by SKILL.md
├── evals/
│   ├── evals.json          # 8 test cases (excluded from the .skill package)
│   └── eval-results*.md    # results from each independent run
└── README.md
```

## License

MIT
