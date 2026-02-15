# X Article Writer — Claude Code Skill

A Claude Code skill that produces publication-ready long-form X (Twitter) articles through a structured 5-phase pipeline: deep research, architecture, multi-draft generation, expert evaluation panel, and synthesis.

You provide your topic, perspective, and key arguments. The skill handles everything else.

## What It Does

1. **Deep Research** (3 parallel agents) — Maps the debate landscape, finds hard data with sources, and analyzes what makes similar content perform on X
2. **Architecture** — Generates title options, structural skeleton, and tone calibration based on research
3. **Multi-Draft Generation** (4 parallel agents) — Produces 4 complete drafts with different voices: Analyst, Contrarian, Bridge Builder, and Storyteller
4. **Expert Evaluation Panel** — Scores all drafts across 5 dimensions (virality, accuracy, authenticity, prose quality, brand positioning) with line-level feedback
5. **Synthesis & Iteration** — Combines the best elements into a final article, iterates with the panel until publication-ready

## Output

- A polished article ready to paste into X's article editor (1,000-1,500 words, fully cited)
- A launch tweet (under 280 chars)
- A posting strategy with timing, accounts to tag, follow-up tweets, and prepared rebuttals

## Quick Start

### Option 1: Use as a Claude Code Skill

Copy `SKILL.md` to your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/x-article-writer
cp SKILL.md ~/.claude/skills/x-article-writer/SKILL.md
```

Then copy `PROMPT_TEMPLATE.md`, fill in your details, and paste it into Claude Code.

### Option 2: Use Standalone

Copy the contents of `PROMPT_TEMPLATE.md`, fill in your details, and paste directly into any Claude conversation. The template contains the full pipeline instructions.

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Claude Code skill definition (copy to `~/.claude/skills/`) |
| `PROMPT_TEMPLATE.md` | Fill-in template with your topic and details |
| `PRD.md` | Full product requirements document with pipeline details |

## Requirements

- Claude Code with access to web search (for research phase)
- X Premium (for publishing long-form articles)

## How It Was Built

This skill was developed through a real production run writing a long-form policy analysis article for X. The article went through 3 research agents, 4 draft agents, 3 evaluation rounds, and 3 major revisions. The pipeline, evaluation criteria, and quality standards were refined through that process and generalized into this skill.

## License

MIT
