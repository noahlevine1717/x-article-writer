# X ARTICLE WRITER — YOUR BRIEF

Fill in the sections below, then paste this entire document into Claude Code. The pipeline will handle research, drafting, evaluation, and synthesis automatically.

---

## 1. ABOUT YOU

- **Name / X Handle**: [e.g., @yourhandle]
- **Approximate follower count**: [e.g., 2,400 — this affects tone calibration]
- **Professional role / background**: [e.g., "Fintech PM at a Series B startup" — establishes your credibility angle]
- **Positioning goal**: What do you want to be known for after publishing this piece?
- **Disclosure** (if any): Financial interests, affiliations, or conflicts to disclose at the end of the article. Leave blank if none.

## 2. THE ASSIGNMENT

What are you arguing? Describe your thesis in 2-3 sentences.

> [Write your thesis here. Be specific about what you believe and why you think the conventional wisdom is wrong.]

**Example** (delete before submitting):
> "Remote-first companies will outperform hybrid ones over the next decade, not because
> remote work is inherently better, but because it forces written communication culture,
> which compounds into better decision-making. The 'return to office' movement is
> optimizing for short-term manager comfort at the cost of long-term organizational IQ."

## 3. YOUR INITIAL THINKING

List your early instincts, key arguments, data points you already know about, and angles you want to explore. Be specific. These are starting points — the research phase will go beyond them, stress-test your priors, and may surface better arguments.

- [Argument or angle 1]
- [Argument or angle 2]
- [Data point you've seen or suspect exists]
- [Historical parallel you think is relevant]
- [Angle you're curious about but haven't researched]

**Example** (delete before submitting):
- GitLab's all-remote handbook has 2,000+ pages of written process; their IPO valuation was 11x revenue vs. ~6x for comparable hybrid SaaS companies
- I've seen data that async-first teams ship more features per engineer per quarter, but I don't remember the source — needs verification
- Historical parallel: the shift from oral to written legal contracts in 17th-century England led to more reliable enforcement — similar dynamic?
- Angle I haven't explored: does remote-first create selection bias by attracting more self-directed workers, and is that the real cause of outperformance?

**Important**: Mark anything you're unsure about. The research agents will verify claims and find counter-evidence. It's better to include a hunch that gets disproven than to leave it out.

## 4. RESEARCH CONTEXT (Optional)

Paste any data points, sources, or research you've already verified. Include URLs where possible. This prevents the research agents from re-discovering what you already know and lets them focus on finding new material.

```
- [Data point]: [Source URL]
- [Data point]: [Source URL]
```

## 5. TONE & POSITIONING

**Tone spectrum** — check one:
- [ ] Adversarial ("the other side is wrong and here's proof")
- [ ] Educational ("here's what the data actually shows")
- [ ] Bridge-building ("I understand both sides, but the evidence points one way")
- [ ] Contrarian ("everyone is missing this angle")

**Tone reference**: Name 1-2 writers or accounts whose voice you admire for this kind of content.
> [e.g., "Matt Levine's deadpan delivery of absurdity," "Byrne Hobart's analytical density," "Packy McCormick's accessible optimism"]

**Target audience**: Who must share this for it to succeed? Name specific communities or account types.
> [e.g., "policy staffers and finance Twitter," "crypto Twitter and fintech founders," "mainstream tech audience"]

**Red lines**: Anything you do NOT want to say, imply, or be associated with?
> [e.g., "Don't attack [specific person]," "Don't imply [X]," "Avoid sounding like a [Y] shill"]

---

# PIPELINE INSTRUCTIONS (for Claude — do not edit below this line)

> **You're done.** Everything below is instructions for Claude's pipeline. You don't need to read or modify any of it. Just paste this entire document (including everything below) into Claude Code and the pipeline runs automatically. You'll be asked for feedback between phases.

## PHASE 1: DEEP RESEARCH

Launch 3 research agents in parallel. Save all outputs to `/research/` directory.

### Agent 1A — Discourse & Sentiment (`/research/sentiment_analysis.md`)

Map the full debate landscape around the topic defined in Section 2.

Search for and document positions from both sides. For each argument found:
- The claim being made
- Who is making it (specific people, organizations, publications)
- Engagement level (how much traction is it getting)
- Argument strength (1-10, how hard is it to counter)

Output format:
```
## Side A Arguments (ranked by frequency/engagement)
1. [Claim] — [Who] — [Engagement level] — [Strength 1-10]

## Side B Arguments (ranked by frequency/engagement)
1. [Claim] — [Who] — [Engagement level] — [Strength 1-10]

## Gaps in the Discourse (arguments neither side is making well)
## Rhetorical/Emotional Patterns (what framing gets engagement)
## Surprising Findings
```

### Agent 1B — Data & Historical Precedent (`/research/data_points.md`)

Find hard, sourced data for every claim in Section 3. Go beyond the user's initial thinking — find data they haven't considered, historical parallels they haven't drawn, and counter-evidence that must be addressed.

Output format:
```
### [Topic]
- Claim: [What we could argue]
- Data: [Specific number/fact]
- Source: [URL]
- Strength: [1-10, how bulletproof]
- Counter-argument: [What the other side would say]
- Rebuttal: [How to handle it]
```

### Agent 1C — Platform & Viral Strategy (`/research/platform_strategy.md`)

Research what makes similar content perform well on X:
- Analyze top-performing X articles/threads in this topic space
- Note: length, structure, tone, hook style, title patterns
- Optimal posting times for the target audience (from Section 5)
- Tone benchmarks for accounts at the user's follower range

---

## PHASE 2: ARTICLE ARCHITECTURE

Using all research, generate and save to `/architecture/article_plan.md`:

1. **5-10 title options** ranging from aggressive to measured
2. **Structural skeleton** with section-by-section purpose and target word count
3. **Key data points** that must be featured (the strongest ammunition from research)
4. **Tone calibration notes** based on the user's selections in Section 5

---

## PHASE 3: MULTI-DRAFT GENERATION

Write 4 complete drafts in parallel. Each agent receives: all research files, the architecture plan, and specific instructions for their archetype.

| Draft | File | Archetype | Voice |
|-------|------|-----------|-------|
| A | `/drafts/draft_A.md` | The Analyst | Data-first, precise, every claim sourced, research-note quality |
| B | `/drafts/draft_B.md` | The Contrarian | Punchy, provocative, strong hook, rhetorical force |
| C | `/drafts/draft_C.md` | The Bridge Builder | Empathetic to all sides, firm on facts, constructive |
| D | `/drafts/draft_D.md` | The Storyteller | Narrative-driven, historical framing, scene-setting |

Target: 1,000-2,000 words each.

### Quality Standards for All Drafts

- Every factual claim gets an inline [n] citation
- All notes collected at bottom under ### Notes with source name, date, URL
- No em dashes (strongest signal of AI-generated text — use commas, colons, periods, parentheses)
- No filler phrases: "It's worth noting," "Let's dive in," "Here's the thing," "Interestingly"
- Bold ## subheadings for every section
- Steel-man the opposing argument before dismantling it
- Opening must work as a standalone hook
- Closing must work as a standalone tweet

---

## PHASE 4: EXPERT EVALUATION PANEL

Evaluate all 4 drafts through 5 expert lenses. Save to `/evaluations/panel_review.md`.

| Evaluator | Focus | Key Question |
|-----------|-------|-------------|
| Viral/Marketing Strategist | Hook, shareability, screenshot moments | "Would I stop scrolling and share this?" |
| Domain Expert | Factual accuracy, logical coherence, counter-arguments | "Could an opponent poke holes in this?" |
| Platform Native | Authenticity, engagement prediction, tone | "Does this feel like a real person?" |
| Professional Editor | Length, pacing, prose quality, redundancy | "Is every sentence earning its place?" |
| Brand Strategist | Author positioning, blowback risk, long-term value | "How does this reflect on the author?" |

Score each draft 1-10 per evaluator. Provide:
- Scorecard table
- Line-level feedback per evaluator per draft
- Synthesis recommendation: which draft as base + what to steal from each other

---

## PHASE 5: SYNTHESIS & ITERATION

### Step 1: Hybrid Construction
- Use the highest-scoring draft as the base
- Pull the best elements from other drafts (best hook, strongest data, best rhetorical moves)
- Construct a hybrid maximizing across all 5 evaluation dimensions

### Step 2: Iteration
- Run evaluation panel on the hybrid
- Implement fixes
- Run panel again
- Repeat until all scores are 7+ with no critical blockers (typically 2-3 rounds)

### Step 3: Final Deliverables (save to `/final/`)

**`/final/article.md`** — The article, ready to paste into X's article editor

**`/final/launch_tweet.md`** — Under 280 characters. Must work as a standalone hook.

**`/final/posting_strategy.md`** — Including:
- Recommended posting day/time
- 5-10 accounts to tag or quote-tweet for amplification
- Self-reply TLDR (post immediately after article)
- 4-5 follow-up tweets spaced over 48 hours, each a standalone insight
- 3-4 prepared rebuttals for likely pushback
