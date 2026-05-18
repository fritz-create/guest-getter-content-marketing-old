---
name: blog-rewrite
description: >
  Rewrite and optimize an existing blog post for Google rankings and AI citations
  (GEO/AEO). Replaces fabricated statistics with sourced data, applies answer-first
  formatting, injects citation capsules, adds FAQ section, and updates freshness
  signals. Use for existing restaurant blog posts that predate this system or
  scored below 70 on the AI citation audit.
argument-hint: "[path to existing post or post slug]"
---

# Blog Rewrite - Optimize Existing Posts for AI Search

Rewrites existing restaurant blog posts to meet the AI citation standard used across this system.

## When to Use

- Post scored below 70 on `/blog-geo`
- Client has existing blog posts that predate this system
- Post was written without AI citation standards
- Post has fabricated or unsourced statistics

## Project Standard

After rewriting, the post must score **≥ 70/100** on `/blog-geo` before being saved as `final.md`.

## Workflow

### Step 1: Audit First (Read-Only)

Load the post. Run a silent audit before touching anything:

**Statistics check:**
- Identify all statistics and claims with numbers
- Mark each as: [SOURCED - has URL] or [UNSOURCED - no link] or [FABRICATED - verify returns nothing]
- Count: sourced / unsourced / fabricated
- Do not begin rewriting until this count is confirmed

**AI signal check:**
- Measure sentence length variance (target SD > 6 - low variance = AI signal)
- Scan for known AI phrases: "dive into", "in today's landscape", "game-changer", "seamlessly", "leverage", "delve", "crucial", "elevate", "robust", "tapestry", "navigate the landscape", "cutting-edge", "harness the power of", "multifaceted", "embark"
- Estimate: what % reads as AI-generated?

**Structure check:**
- Does it have a TL;DR box? Citation capsules? FAQ section? Q&A headings?
- Are H2 sections 120–180 words?
- Does it have answer-first formatting?

Report the audit summary before rewriting.

### Step 2: Rewrite

Apply in this order:

1. **Fix statistics first** - replace every unsourced or fabricated stat with a verified, linked source. If no source can be found, remove the claim or reframe as a general observation.

2. **Apply answer-first format** - each H2 section must open with the direct answer in the first 1–2 sentences.

3. **Adjust passage lengths** - expand or trim sections to hit the 120–180 word target for each H2 block.

4. **Reframe H2s as questions** - convert 60–70% of H2 headings to questions where natural for the restaurant topic.

5. **Inject citation capsules** - add a 40–60 word standalone citable statement to each major section.

6. **Add TL;DR box** - 40–60 word summary at the top if missing.

7. **Add/expand FAQ section** - minimum 3 questions at the end. Phrase as natural restaurant queries.

8. **Remove AI phrases** - replace all flagged phrases with specific, concrete language.

9. **Update freshness signals** - add or update `dateModified` in frontmatter to today's date.

10. **Voice check** - read `01-BRAND/voice.md` and verify the rewrite matches the brand tone. Adjust any sections that drift.

### Step 3: Save and Score

Save the rewrite to `04-BLOG/[cluster]/[post-slug]/draft.md` (overwrite existing).

Then automatically run the AI citation audit (same logic as `/blog-geo`) and report the new score.

If score ≥ 70: *"Rewrite complete. New AI Citation Score: [X]/100. Ready to finalize."*
If score < 70: *"Rewrite complete but score is [X]/100 - still below threshold. Remaining issues: [list]."*
