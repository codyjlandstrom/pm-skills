# Claude Skills

Custom skills for Claude Code, built and verified with independent agent evals.

Most published skills get written, eyeballed, and shipped. That's fine for personal tools, but it's not enough when the skill is shaping decisions you'll act on. The skills in this repo are developed like any other piece of software: write, run independent evals, iterate, verify. Eval results are checked in.

## Install

Both options install the same skill. **Plugin install (A)** is recommended — it gives you updates via `/plugin update` and namespaces the skill cleanly. **Manual install (B)** is the fallback if you don't use Claude Code's plugin system.

### A — Install via Claude Code plugin marketplace

```
/plugin marketplace add codyjlandstrom/claude-skills
/plugin install mom-test@claude-skills
```

That's it. The skill is now available — invoke it with phrases like "mom test these questions" or "apply the mom test."

To update later: `/plugin update mom-test@claude-skills`.

### B — Manual install (drop the .skill file in)

1. Download [`releases/mom-test.skill`](releases/mom-test.skill).
2. The file is a zip — extract it to `~/.claude/skills/`. You should end up with `~/.claude/skills/mom-test/SKILL.md`.
3. Restart Claude Code or start a new session.

## Skills in this repo

### [Mom Test](skills/mom-test/)

Applies Rob Fitzpatrick's *The Mom Test* framework to product discovery work. Four modes:

- **Question Review** — classifies draft interview questions as Safe / Sequencing-sensitive / Risky, with rewrites for the risky ones.
- **Question Generation** — given a hypothesis, produces 5–8 discovery questions that test it without revealing it. Includes a "Things You Should NOT Say" section for live-call discipline.
- **Conversation Analysis** — analyzes call transcripts for compliments, hypothetical traps, buried signals, and interviewer bias. Distinguishes offered commitments from realized ones.
- **Assumption Extraction** — sweeps a product idea for assumptions across 8 categories (customer, problem, existing behavior, market, willingness to pay, workflow, technical feasibility, GTM), ranks them by risk, and gives you a conversation-based test for each top-tier one.

**Eval receipts:**
- [Reference run](skills/mom-test/evals/eval-results.md) (run by the same session that wrote the skill — known biased baseline)
- [Independent run v1](skills/mom-test/evals/eval-results-independent.md) — 8 fresh sub-agents, no exposure to the criteria
- [Independent run v2](skills/mom-test/evals/eval-results-independent-v2.md) — same 8 prompts after a framework iteration. Resolves an over-flagging bug in Mode 1 and codifies offered-vs-realized commitment grading in Mode 3.

8/8 pass on both independent runs. Differences between v1 and v2 are documented and reproducible.

## Repo layout

```
.claude-plugin/
├── plugin.json            # plugin manifest (single skill)
└── marketplace.json       # marketplace manifest — this repo serves itself

skills/mom-test/
├── SKILL.md               # main skill instructions
├── README.md              # skill-level docs
├── references/
│   └── principles.md      # framework reference (loaded by SKILL.md)
└── evals/
    ├── evals.json         # 8 test cases covering all four modes
    └── eval-results*.md   # results from each run

releases/
└── mom-test.skill         # packaged distribution artifact (for manual install)

HANDOFF.md                 # how the independent eval run is orchestrated
```

## Building a skill from this repo

If you want to fork and adapt the eval methodology for your own skills:

1. Copy `skills/mom-test/` as a starting structure.
2. Write your `SKILL.md` and any `references/`.
3. Add test cases to `evals/evals.json` covering the modes/use cases.
4. Run independent evals via `HANDOFF.md` (dispatches sub-agents in parallel, scores against expected output).
5. Iterate based on the eval gaps.
6. Add the new skill to `.claude-plugin/marketplace.json` so it ships with the next install.

## License

MIT
