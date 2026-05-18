---
name: blog-write
description: >
  Write a new blog post optimized for Google rankings AND AI citation (ChatGPT,
  Perplexity, Google AI Overviews). Built for restaurant content: answer-first
  formatting, citation capsules, Q&A headings, Key Takeaways box, schema-ready
  structure. Invoke with a topic, keyword, or approved content brief from 04-BLOG/.
---

# Blog Write - Restaurant Content (AI-Optimized)

Writes complete blog articles with dual optimization: Google rankings + LLM citability.

## Project Context

This is a restaurant content marketing system. All posts must:
- Reflect the approved brand voice from `01-BRAND/voice.md`
- Target the cluster and intent assigned in `02-TOPICAL-MAP/topical-map.csv`
- Be saved to `04-BLOG/[cluster]/[post-slug]/draft.md`
- Include a completed `metadata.json` alongside the draft

## AI Citation Standards (Non-Negotiable)

Every post written in this project must meet these minimums before being shown to the user:

| Standard | Requirement |
|----------|-------------|
| Passage length | 120-180 words per H2 section (self-contained, extractable) |
| Answer-first | Each H2 opens with a direct answer in the first 1-2 sentences |
| Q&A headings | 60-70% of H2s phrased as questions |
| Citation capsules | 40-60 word standalone statement per major section |
| TL;DR box | 40-60 word summary at top of post |
| Key Takeaways | Bullet list of 4-6 takeaways at the top or bottom |
| FAQ section | Minimum 3 questions at the end |
| Sourced statistics | All stats linked to tier 1-3 sources - no fabricated data |

## Workflow

### Step 1: Load Context

Before writing anything:
1. Read `01-BRAND/voice.md` - apply voice attributes throughout
2. Read `01-BRAND/audience-profiles.md` - write for the right segment
3. Check `02-TOPICAL-MAP/intent-log.md` - confirm this intent isn't already owned
4. If a content brief exists in `04-BLOG/[cluster]/[post-slug]/`, load it

### Step 2: Select Template

Match the topic to a content type:
- "How to...", steps, process -> how-to guide
- "Best X", "Top N" -> listicle
- "X vs Y", comparison -> comparison
- Broad topic, comprehensive -> pillar page
- "What is X", definitions -> FAQ/knowledge base
- Local + seasonal -> local guide

### Step 3: Research

Find 6-10 current statistics (2024-2026 preferred):
- Prioritize restaurant industry sources, food media, local publications
- Mark every stat with source name + URL
- Flag any stat that can't be verified as [NEEDS SOURCE]

### Step 4: Write

Apply the 6 pillars throughout:
1. **Answer-first** - lead every section with the answer, then explain
2. **Passage structure** - 120-180 word self-contained blocks
3. **Q&A headings** - phrase H2s as questions where natural
4. **Citation capsules** - embed one 40-60 word citable statement per section
5. **Entity clarity** - name the restaurant, location, dish by full name consistently
6. **Freshness signals** - include datePublished and dateModified in frontmatter

### Step 5: Required Elements Checklist

Before finishing the draft, confirm:
- [ ] TL;DR box (top of post, 40-60 words)
- [ ] Key Takeaways (4-6 bullets)
- [ ] Citation capsule in each H2 section
- [ ] FAQ section (3+ questions)
- [ ] Internal link opportunities noted (read topical map for same-cluster posts)
- [ ] Cover image placeholder or Pixabay/Unsplash URL
- [ ] Frontmatter complete: title, description, datePublished, tags, cluster, slug

### Step 6: Save

Save draft to `04-BLOG/[cluster]/[post-slug]/draft.md`.

Fill in `04-BLOG/[cluster]/[post-slug]/metadata.json`:
```json
{
  "slug": "",
  "title": "",
  "meta_description": "",
  "cluster": "",
  "tier": "",
  "intent_fingerprint": "",
  "target_keyword": "",
  "secondary_keywords": [],
  "audience_segment": "",
  "funnel_stage": "",
  "word_count_target": "",
  "word_count": 0,
  "internal_links_out": [],
  "internal_links_in": [],
  "gbp_derivatives": [],
  "status": "draft",
  "ai_citation_score": null,
  "cover_image_url": "",
  "canonical_url": "",
  "publish_date": null,
  "last_updated": null,
  "author": "",
  "live_url": null,
  "notes": ""
}
```

Show the draft to the user. Then say:
*"Draft saved. Run `/blog-geo` to score it for AI citation readiness before finalizing."*
