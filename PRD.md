# PRD: X Article Writer — Claude Code Skill

## Overview

A Claude Code skill that takes a user's topic, perspective, and key arguments and produces a publication-ready long-form X (Twitter) article through a structured 5-phase pipeline: deep research, architecture, multi-draft generation, expert evaluation panel, and synthesis.

The user provides a filled-in prompt template with their identity, topic, initial thinking, and any pre-existing research. The skill handles everything else.

---

## Problem

Writing high-quality long-form content for X that balances analytical rigor with viral potential is hard. Most attempts produce either:
- A research note (credible but low engagement)
- A hot take (engaging but low credibility)

This skill produces content that is both shareable and defensible by separating research, drafting, evaluation, and synthesis into discrete phases with parallel sub-agents.

---

## Target User

Anyone with Claude Code who wants to write a data-driven, long-form X article on a topic they have strong opinions and some initial thinking on. Typical use cases:
- Policy analysis or rebuttal
- Market commentary or contrarian take
- Industry analysis with a clear thesis
- Data-driven argument on a debated topic

---

## How It Works

### Step 1: User fills in the prompt template

The user copies `PROMPT_TEMPLATE.md`, fills in their details, and pastes it into Claude Code (or runs it as a prompt file). The template has 5 sections:

1. **Author Profile** — who they are, handle, follower count, positioning goals
2. **The Assignment** — what they want to argue, in 2-3 sentences
3. **Initial Thinking** — their early instincts, key arguments, data they know about (explicitly marked as "starting points, not prescriptive")
4. **Research Context** — any data points or sources they've already verified
5. **Tone & Positioning** — how they want to come across (adversarial vs. educational, specific tone references)

### Step 2: The 5-phase pipeline runs

The skill executes the full pipeline automatically, saving intermediate outputs to organized directories so the user can review at any stage.

---

## The 5-Phase Pipeline

### Phase 1: Deep Research (3 parallel agents)

Three research agents run simultaneously, each with a specific output format:

**Agent 1A — Discourse & Sentiment**
- Map the full debate landscape: who is saying what, on which side
- Identify the strongest arguments on each side
- Find gaps in the discourse (arguments nobody is making well)
- Note rhetorical/emotional patterns that drive engagement

Output format:
```
## Side A Arguments (ranked by frequency/engagement)
1. [Claim] — [Who] — [Engagement level] — [Strength 1-10]

## Side B Arguments (ranked by frequency/engagement)
1. [Claim] — [Who] — [Engagement level] — [Strength 1-10]

## Gaps in the Discourse
## Rhetorical/Emotional Patterns
```

**Agent 1B — Data & Historical Precedent**
- Find hard, sourced data for every claim the user wants to make
- Discover historical parallels the user may not have considered
- Stress-test the user's priors (find counter-evidence too)

Output format:
```
### [Topic]
- Claim: [What we're arguing]
- Data: [Specific number/fact]
- Source: [URL]
- Strength: [1-10]
- Counter-argument: [What the other side would say]
- Rebuttal: [How to handle it]
```

**Agent 1C — Platform & Viral Strategy**
- Research what makes similar content perform well on X
- Analyze top-performing articles/threads in the user's space
- Optimal posting times for the target audience
- Tone benchmarks for the user's follower range

All outputs saved to `/research/` directory.

### Phase 2: Article Architecture

Using the research, generate:
- 5-10 title options (ranging from aggressive to measured)
- Structural skeleton with section-by-section purpose and target word count
- Key data points that must be featured
- Tone calibration notes based on user's positioning goals

Saved to `/architecture/article_plan.md`.

### Phase 3: Multi-Draft Generation (4 parallel agents)

Four drafts, each with a meaningfully different approach:

| Draft | Archetype | Voice | Risk |
|-------|-----------|-------|------|
| A | The Analyst | Data-first, precise, research-note quality | Could be dry |
| B | The Contrarian | Punchy, provocative, bold opening claim | Could alienate moderates |
| C | The Bridge Builder | Empathetic to opponents, firm on facts | Could be too soft for virality |
| D | The Storyteller | Narrative-driven, historical framing | Could bury the lede |

Each agent receives the research files and architecture plan. Target: 1,000-2,000 words each.

Saved to `/drafts/draft_A.md` through `/drafts/draft_D.md`.

### Phase 4: Expert Evaluation Panel

All 4 drafts evaluated through 5 expert lenses, each scoring 1-10:

| Evaluator | Focus | Key Question |
|-----------|-------|-------------|
| Viral/Marketing Strategist | Hook, shareability, screenshot moments | "Would I stop scrolling and share this?" |
| Domain Expert | Factual accuracy, logical coherence, counter-arguments | "Could an opponent poke holes in this?" |
| Platform Native | Authenticity, engagement prediction, tone | "Does this feel like a real person or a press release?" |
| Professional Editor | Length, pacing, prose quality, redundancy | "Is every sentence earning its place?" |
| Brand Strategist | Author positioning, blowback risk, long-term value | "How does this reflect on the author in 6 months?" |

Produces:
- Scorecard table with all scores
- Line-level feedback per evaluator per draft
- Synthesis recommendation: which draft as base + what to steal from each other

Saved to `/evaluations/panel_review.md`.

### Phase 5: Synthesis & Iteration

**Step 1 — Hybrid Construction**
- Use the highest-scoring draft as the base
- Pull the best elements from other drafts (best hook, strongest data presentation, best rhetorical moves)
- Construct a hybrid that maximizes across all 5 evaluation dimensions

**Step 2 — Iteration Protocol**
- Apply evaluation panel feedback
- Run panel again on revised version
- Implement fixes
- Repeat until panel gives publication clearance (target: 2-3 rounds)

**Step 3 — Final Deliverables**

Saved to `/final/` directory:

| File | Contents |
|------|----------|
| `article.md` | The article, ready to paste into X's article editor |
| `launch_tweet.md` | Under 280 chars, works as standalone hook |
| `posting_strategy.md` | Timing, accounts to tag, follow-up tweets, prepared rebuttals |

---

## Prompt Template

The user-facing template (`PROMPT_TEMPLATE.md`) should be structured as:

```markdown
# X ARTICLE WRITER — YOUR BRIEF

## 1. ABOUT YOU
- **Name / Handle**:
- **Follower count**:
- **Professional role**:
- **Positioning goal**: What do you want to be known for after this piece?
- **Disclosure**: Any financial interests or affiliations to disclose?

## 2. THE ASSIGNMENT
What are you arguing? Describe in 2-3 sentences.

## 3. YOUR INITIAL THINKING
List your early instincts, key arguments, data points you know about,
and angles you want to explore. These are starting points — the research
phase will go beyond them.

- [Argument 1]
- [Argument 2]
- [Data point you've seen]
- [Historical parallel you suspect exists]
- [Angle you're curious about]

**Important**: These are directional. The research agents will stress-test
your priors, find new ammunition, and may surface better arguments than
what you've listed.

## 4. RESEARCH CONTEXT (Optional)
Paste any data points, sources, or research you've already verified.
This saves time and prevents the agents from re-discovering what you
already know.

## 5. TONE & POSITIONING
- **Tone spectrum**: Where do you fall?
  - [ ] Adversarial ("the other side is wrong and here's proof")
  - [ ] Educational ("here's what the data actually shows")
  - [ ] Bridge-building ("I understand both sides, but...")
  - [ ] Contrarian ("everyone is missing this angle")
- **Tone reference**: Name 1-2 writers whose voice you admire
  (e.g., "Matt Levine's deadpan delivery," "Byrne Hobart's density")
- **Audience**: Who must share this for it to succeed?
  (e.g., "policy staffers," "crypto Twitter," "fintech founders")
- **Red lines**: Anything you do NOT want to say or imply?
```

---

## Article Quality Standards

These are baked into every phase of the pipeline:

### Structure
- Title creates curiosity without revealing the conclusion
- Subtitle contains a concrete, surprising data point that works as a standalone hook
- Bold subheadings for every section (visual anchors for skimmers)
- Opening scene (100-150 words) sets the stage with narrative, not data
- Evidence section leads with the most devastating data point
- Closing works as a standalone tweet (2-3 sentences, rhythmic, no hedging)

### Tone
- Every factual claim gets an inline [n] citation
- Steel-man the opposing argument before dismantling it
- Acknowledge where opponents have a point (builds credibility)
- Precise language over hyperbole ("$2.9 trillion in excess reserves" > "banks are terrified")
- Let the argument speak for itself rather than telling readers what to conclude

### AI Detection Avoidance
- No em dashes (strongest signal of AI-generated text)
- Vary sentence length naturally
- No filler phrases: "It's worth noting," "Let's dive in," "Here's the thing," "Interestingly"
- Use the author's natural vocabulary, not generic analytical language

### Citations
- Inline [n] format for every factual claim
- All notes collected at the bottom under ### Notes
- Each note includes: source name, date, and URL where possible
- Target: 15-25 citations for a data-heavy piece
- Every footnote must have a real, verifiable URL or explicit explanation

### Length
- Sweet spot: 1,000-1,500 words for article body
- Footnotes are separate and don't count toward reading length
- Every sentence must earn its place

---

## Posting Strategy Standards

The launch materials include:

### Launch Tweet
- Under 280 characters
- Must work as a standalone hook even if no one clicks
- Best technique: compress the article's core tension into natural prose

### Follow-Up Tweets (spaced over 48 hours)
- 4-5 standalone tweets, each pulling a single insight from the article
- Spaced at roughly: +4hrs, +20hrs, +28hrs, +44hrs
- Each must work independently (someone seeing only this tweet should still engage)

### Tagging Strategy
- 2-3 people MAX in the launch tweet (selective = confident)
- Quote-tweet others over the next 24 hours as engagement builds
- Never @-mention people inside the article itself

### Prepared Rebuttals
- 3-4 rebuttals for the most likely pushback
- Each includes: who it's likely from, and a 2-3 sentence data-driven response

---

## Directory Structure

```
/research/
  sentiment_analysis.md
  data_points.md
  platform_strategy.md
/architecture/
  article_plan.md
/drafts/
  draft_A.md   (Analyst)
  draft_B.md   (Contrarian)
  draft_C.md   (Bridge Builder)
  draft_D.md   (Storyteller)
/evaluations/
  panel_review.md
/final/
  article.md
  launch_tweet.md
  posting_strategy.md
```

---

## Parallelization Strategy

**Maximize parallel agents:**
- Phase 1: All 3 research agents simultaneously
- Phase 3: All 4 draft agents simultaneously

**Do NOT parallelize:**
- Phase 1 → Phase 2 (architecture needs research)
- Phase 2 → Phase 3 (drafts need architecture)
- Phase 3 → Phase 4 (evaluation needs drafts)
- Phase 4 → Phase 5 (synthesis needs evaluation)

---

## Success Criteria

The pipeline is working when:
- Research agents return structured, sourced data (not vague summaries)
- Multiple drafts have genuinely different voices (not minor variations)
- The evaluation panel identifies issues the author didn't see
- Each iteration measurably improves scores
- The final version incorporates the best elements from multiple drafts
- All panel scores are 7+ with no critical blockers before publication clearance

---

## What This Skill Does NOT Do

- It does not post to X (the user copies the final article manually)
- It does not manage ongoing engagement (replies, quote-tweets after posting)
- It does not guarantee virality (it maximizes the probability)
- It does not replace the user's judgment (the user reviews and approves at each phase)
