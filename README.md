# X Article Writer — Claude Code Skill

A Claude Code skill that produces publication-ready long-form X (Twitter) articles through a structured 5-phase pipeline: deep research, architecture, multi-draft generation, expert evaluation panel, and synthesis.

You provide your topic, perspective, and key arguments. The skill handles everything else.

## What It Does

1. **Deep Research** (3 parallel agents) — Maps the debate landscape, finds hard data with sources, and analyzes what makes similar content perform on X
2. **Architecture** — Generates title options, structural skeleton, and tone calibration based on research
3. **Multi-Draft Generation** (4 parallel agents) — Produces 4 complete drafts with different voices: Analyst, Contrarian, Bridge Builder, and Storyteller
4. **Expert Evaluation Panel** — Scores all drafts across 5 dimensions (virality, accuracy, authenticity, prose quality, brand positioning) with line-level feedback
5. **Synthesis & Iteration** — Combines the best elements into a final article, iterates with the panel until publication-ready

## Example Output

Here's what the skill produces for a sample topic ("Why ZIRP Nostalgia is Wrong"):

**Article** (excerpt):
> The zero-interest-rate era didn't create innovation. It subsidized it. And there's a
> difference most of tech Twitter refuses to see. Between 2010 and 2021, venture dollars
> deployed grew 4.2x [1], but the share of VC-backed companies reaching profitability
> within 5 years actually declined [2]...

**Launch Tweet:**
> Everyone misses ZIRP. Almost nobody can explain what it actually produced. I ran the numbers.

**Posting Strategy** (excerpt):
> - Post: Tuesday 9:15 AM ET
> - Tag: @conaborern @compound248 (active in ZIRP discourse this week)
> - Self-reply TLDR: "ZIRP 4.2x'd VC spend but decreased the profitability rate..."

## Full Output

- A polished article ready to paste into X's article editor (1,000-1,500 words, fully cited with 15-25 footnotes)
- A launch tweet (under 280 chars)
- A posting strategy with timing, accounts to tag, follow-up tweets, and prepared rebuttals

## Quick Start

**Step 1.** Install the skill (one-time setup):

```bash
mkdir -p ~/.claude/skills/x-article-writer
cp SKILL.md ~/.claude/skills/x-article-writer/SKILL.md
```

**Step 2.** Open `PROMPT_TEMPLATE.md` and fill in Sections 1-5 with your topic, thesis, and preferences. (~10 minutes)

**Step 3.** Paste the filled-in template into Claude Code. The pipeline runs automatically.

**Step 4.** Review output at each phase. The skill pauses for your feedback between phases.

> **Don't use Claude Code?** You can paste the filled-in `PROMPT_TEMPLATE.md` directly into any Claude conversation. The template contains the full pipeline instructions.

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Claude Code skill definition (copy to `~/.claude/skills/`) |
| `PROMPT_TEMPLATE.md` | Fill-in template with your topic and details |
| `PRD.md` | Full pipeline specification and quality standards |

## Requirements

- Claude Code with access to web search (for research phase)
- X Premium (for publishing long-form articles)

## Troubleshooting

| Problem | Cause | Fix |
|---------|-------|-----|
| Research phase returns vague summaries | Web search may be disabled or rate-limited | Confirm Claude Code has web search access. If limited, paste key sources into Section 4 of the template. |
| Pipeline stalls or produces a single draft | Context window may be full | Break the run into phases: run Phases 1-2 first, save the research files, then start a new conversation for Phases 3-5 with the saved research. |
| Article sounds generic or AI-written | Section 3 (Your Initial Thinking) was too sparse | Add more specific arguments, personal anecdotes, and strong opinions. The drafts can only be as distinctive as your input. |
| Evaluation scores plateau, never improving | Topic may be too broad | Narrow your thesis. "AI regulation" is too broad; "Why the EU AI Act's compute thresholds will backfire" is specific enough. |

## How It Was Built

This skill was developed through a real production run writing a long-form policy analysis article for X. The article went through 3 research agents, 4 draft agents, 3 evaluation rounds, and 3 major revisions. The pipeline, evaluation criteria, and quality standards were refined through that process and generalized into this skill.

## License

MIT
