---
name: blog-geo
description: >
  AI Citation Readiness audit for blog posts. Scores 0–100 across 5 categories:
  passage-level citability, Q&A formatting, entity clarity, content structure,
  AI crawler accessibility. Generates citation capsules and platform-specific
  recommendations for ChatGPT, Perplexity, and Google AI Overviews.
  Run this before finalizing any blog post in this project.
argument-hint: "[path to draft.md or post slug]"
---

# Blog GEO - AI Citation Readiness Audit

Scores a restaurant blog post for AI citation readiness. Run after writing, before finalizing.

## Project Context

Every blog post in this system must hit a minimum AI Citation Readiness Score of **70/100** before advancing to `final.md`. Below 70 = revise before finalizing.

Score thresholds:
- **90–100**: Excellent - publish as-is
- **70–89**: Good - fix priority items, then finalize
- **50–69**: Needs Work - revise before finalizing (do not skip)
- **Below 50**: Poor - significant rewrite needed

## Scoring Categories (100 pts total)

| Category | Points | What it measures |
|----------|--------|-----------------|
| Passage-Level Citability | 27 | 120–180 word self-contained sections |
| Q&A Formatting | 20 | Question H2s, answer-first structure, FAQ |
| Entity Clarity | 20 | Consistent naming, unambiguous topic |
| Content Structure | 20 | TL;DR, tables, ordered lists, citation capsules |
| AI Crawler Accessibility | 13 | Static HTML, robots.txt, schema in HTML |

## Workflow

### Step 1: Read the Post

Load the draft from `04-BLOG/[cluster]/[post-slug]/draft.md`.
Extract: heading structure, paragraph word counts, FAQ presence, schema, TL;DR, tables, lists.

### Step 2: Score Each Category

**Passage-Level Citability (27 pts)**
Count sections where each H2 block is 120–180 words AND self-contained (makes sense extracted from context).
- 27 pts: 80%+ sections pass
- 20 pts: 60–79%
- 13 pts: 40–59%
- 7 pts: 20–39%
- 0 pts: <20%

**Q&A Formatting (20 pts)**
- 60–70% of H2s phrased as questions → 7 pts
- Each H2 opens with a direct answer → 7 pts
- Dedicated FAQ section (3+ Q&A pairs) → 6 pts

**Entity Clarity (20 pts)**
- One unambiguous primary topic → 5 pts
- Consistent entity naming throughout → 5 pts
- Clear topic statement in intro → 5 pts
- Title accurately reflects content → 5 pts

**Content Structure (20 pts)**
- TL;DR box (40–60 words, top of post) → 4 pts
- Comparison tables with proper structure → 4 pts
- Ordered lists for step-by-step content → 4 pts
- Definition formatting for key terms → 4 pts
- Citation capsules (40–60 word quotable statements) → 4 pts

**AI Crawler Accessibility (13 pts)**
- Static HTML content (not JS-rendered) → 4 pts
- robots.txt allows: GPTBot, ClaudeBot, PerplexityBot → 5 pts
- Schema in static HTML, not JS-injected → 4 pts

### Step 3: Platform-Specific Analysis

**ChatGPT** - Favors: well-cited content, listicles, authoritative sources, recency
**Perplexity** - Favors: freshness (2–3 day window matters most), community-validated content
**Google AI Overviews** - Favors: pages already ranking in top 10, high domain authority

For each platform: rate citability (High / Medium / Low) and give 2–3 specific improvements.

### Step 4: Generate Citation Capsules

For every H2 section that lacks a citation capsule, write one:
- 40–60 words, self-contained
- Structure: specific claim + data/evidence + source
- Label clearly: "Suggested citation capsule for: [H2 heading]"

### Step 5: Report

Output the AI Citation Readiness Report:

```
## AI Citation Readiness Report: [Post Title]

**Score: [X]/100 - [Rating]**

### Score Breakdown
| Category | Score | Max |
|----------|-------|-----|
| Passage-Level Citability | X | 27 |
| Q&A Formatting | X | 20 |
| Entity Clarity | X | 20 |
| Content Structure | X | 20 |
| AI Crawler Accessibility | X | 13 |
| Total | X | 100 |

### Per-Section Citability
[table of H2 sections with word count, self-contained Y/N, citable Y/N]

### Platform Ratings
- ChatGPT: [High/Medium/Low] - [1–2 specific fixes]
- Perplexity: [High/Medium/Low] - [1–2 specific fixes]  
- Google AIO: [High/Medium/Low] - [1–2 specific fixes]

### Suggested Citation Capsules
[one per section that lacks one]

### Priority Fixes (sorted by impact)
1. [Most impactful]
2. [Second]
3. [Third]
```

### Step 6: Update Metadata

Write the AI citation score to `04-BLOG/[cluster]/[post-slug]/metadata.json`:
```json
"ai_citation_score": [score]
```

### Step 7: Decision

- Score ≥ 70 → *"Score is [X]/100. Ready to finalize. Run `/blog-seo-check` before publishing."*
- Score < 70 → *"Score is [X]/100 - below the 70-point threshold. Apply the priority fixes above before finalizing."*
