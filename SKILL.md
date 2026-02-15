---
name: x-article-writer
description: |
  Write high-performing long-form X (Twitter) articles through a structured 5-phase
  pipeline: deep research, architecture, multi-draft generation, expert evaluation
  panel, and synthesis. Use when: (1) User wants to write an X article or long-form
  post, (2) User wants to write a policy analysis, opinion piece, or data-driven
  argument for social media, (3) User asks for help with a "thread" or "post" for
  X/Twitter, (4) User wants to maximize engagement on a piece of writing for X.
  Covers the full pipeline from research to final draft with iterative refinement.
author: Claude Code Community
version: 1.0.0
date: 2026-02-14
---

# X Article Writer

## Problem
Writing long-form content for X that balances analytical rigor with viral potential.
Most policy/analysis content either reads like a research note (low engagement) or a
hot take (low credibility). This skill produces content that is both shareable and
defensible through systematic research, multi-draft generation, and expert evaluation.

## Context / Trigger Conditions
- User wants to write a long-form article for X (Premium feature)
- User wants to write a policy analysis, market commentary, or data-driven argument
- User mentions X, Twitter, threads, or social media content
- User wants to "go viral" or maximize reach with analytical content
- User says "write me an article" in the context of social media publishing

## Solution

### Prerequisites
The user should fill in the PROMPT_TEMPLATE.md with:
1. Their identity and positioning goals
2. Their thesis (what they're arguing)
3. Their initial thinking (key arguments, data they know about)
4. Any pre-existing research (optional)
5. Tone and audience preferences

### The Pipeline

**Phase 1: Deep Research** (3 parallel agents)
- Agent 1A: Discourse & sentiment mapping
- Agent 1B: Data & historical precedent
- Agent 1C: Platform & viral strategy

**Phase 2: Architecture**
- 5-10 title options
- Structural skeleton with word counts
- Key data points to feature
- Tone calibration

**Phase 3: Multi-Draft Generation** (4 parallel agents)
- Draft A: The Analyst (data-first)
- Draft B: The Contrarian (punchy, provocative)
- Draft C: The Bridge Builder (empathetic, constructive)
- Draft D: The Storyteller (narrative-driven)

**Phase 4: Expert Evaluation Panel**
- 5 evaluators score all drafts 1-10
- Line-level feedback
- Synthesis recommendation

**Phase 5: Synthesis & Iteration**
- Hybrid construction from best elements
- 2-3 rounds of panel review until publication clearance
- Final deliverables: article, launch tweet, posting strategy

### Article Quality Standards
- Every claim gets an inline [n] citation with source URL
- No em dashes (strongest AI-writing signal)
- Steel-man opposing arguments before dismantling
- Bold subheadings for every section
- Sweet spot: 1,000-1,500 words
- Opening and closing must work as standalone tweets
- No filler phrases

### Posting Strategy
- Launch tweet under 280 chars
- Self-reply TLDR immediately after posting
- 4-5 follow-up tweets spaced over 48 hours
- 3-4 prepared rebuttals for likely pushback
- Tagging strategy: 2-3 people max in launch tweet

## Verification
The pipeline is working when:
- Research agents return structured, sourced data (not vague summaries)
- Multiple drafts have genuinely different voices
- The evaluation panel identifies issues the author didn't see
- Each iteration measurably improves scores
- All panel scores are 7+ before publication clearance

## Notes
- Total token usage is high (multiple agents, multiple iterations). Worth it for important pieces.
- The user should review and provide feedback between phases.
- Always save intermediate versions. Users often want to go back to earlier phrasing.
- For shorter content (single tweets, LinkedIn posts), skip Phases 3-4 and write directly.
- See PROMPT_TEMPLATE.md for the full user-facing template.
