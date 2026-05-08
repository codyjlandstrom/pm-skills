# Mom Test

A Claude skill that applies Rob Fitzpatrick's "The Mom Test" framework to product discovery work.

## What it does

This skill helps product people pressure-test their customer discovery approach. It operates in four modes:

1. **Question Review** - Evaluate draft interview questions for bias, hypotheticals, leading language, and compliment-fishing. Every risky question gets a rewrite.
2. **Question Generation** - Given a hypothesis or assumption, generate interview questions that test it without revealing what you want to hear.
3. **Conversation Analysis** - Analyze customer call transcripts or notes for deflections, missing specifics, buried signals, and whether real commitment was obtained.
4. **Assumption Extraction** - Surface the riskiest assumptions in a product idea, feature spec, or strategic initiative, and suggest how to test each through conversation.

## Installation

Download the latest `mom-test.skill` from [releases] and install it in Claude.

## Usage

This skill uses explicit invocation. Trigger it with phrases like:

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

## Development

### Structure

```
mom-test/
├── SKILL.md                    # Main skill instructions
├── references/
│   └── principles.md           # Detailed framework reference
├── evals/
│   └── evals.json              # Test cases (excluded from .skill package)
├── README.md
└── .gitignore
```

### Building

Package the skill using the skill-creator tooling:

```bash
PYTHONPATH=/path/to/skill-creator python -m scripts.package_skill /path/to/mom-test
```

### Testing

The `evals/` directory contains test prompts covering all four modes. These are excluded from the packaged `.skill` file but live in the repo for development.

## License

MIT
