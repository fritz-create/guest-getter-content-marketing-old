---
name: blog-seo-check
description: >
  Pre-publish SEO validation checklist for restaurant blog posts. Checks title
  tag length and keyword placement, meta description quality, heading hierarchy,
  internal/external links, canonical URL, Open Graph tags, Twitter Card, URL
  structure, image alt text, and AI citation elements. Produces a pass/fail
  checklist with specific fixes. Run after blog-geo passes - this is the final
  gate before publishing.
argument-hint: "[path to final.md or post slug]"
---

# Blog SEO Check - Pre-Publish Validation

Final pass before a restaurant blog post goes live. Catches SEO issues missed during writing.

## When to Run

After `/blog-geo` scores >= 70 AND the post has been finalized to `final.md`. This is the last step before telling the client to publish.

## Checklist (Pass/Fail)

### Title Tag
- [ ] 40-60 characters
- [ ] Primary keyword in first half of title
- [ ] Unique - no other post uses this title
- [ ] No keyword stuffing or clickbait

### Meta Description
- [ ] 150-160 characters
- [ ] Contains primary keyword naturally
- [ ] Describes what the reader will get
- [ ] Ends with a soft CTA or value statement

### Heading Structure
- [ ] Exactly one H1 (matches title or close variation)
- [ ] H2s are used for main sections (not H3 jumping to H2)
- [ ] No heading levels skipped (H1 -> H2 -> H3, not H1 -> H3)
- [ ] Primary keyword appears in at least one H2
- [ ] 60-70% of H2s phrased as questions (AI citation standard)

### Internal Links
- [ ] At least 2 internal links to other posts in the same cluster
- [ ] At least 1 internal link to the cluster hub post
- [ ] Anchor text is descriptive (not "click here" or "read more")
- [ ] No internal links to posts marked as drafts in topical-map.csv

### External Links
- [ ] All statistics linked to their source
- [ ] No broken or redirected external links
- [ ] External links to authoritative sources (not competitor restaurant sites)
- [ ] External links open in new tab (target="_blank")

### URL Structure
- [ ] Slug is lowercase, hyphenated
- [ ] Slug contains primary keyword
- [ ] Slug is under 60 characters
- [ ] No dates in slug (avoid: /2024/blog-post)

### Open Graph Tags
- [ ] og:title set (can match page title)
- [ ] og:description set (can match meta description)
- [ ] og:image set with correct URL
- [ ] og:image is 1200x630 pixels (OG standard)
- [ ] og:type = "article"

### Twitter Card
- [ ] twitter:card = "summary_large_image"
- [ ] twitter:title set
- [ ] twitter:description set
- [ ] twitter:image set

### Images
- [ ] Cover image present
- [ ] All images have descriptive alt text (not filename, not empty)
- [ ] Cover image includes restaurant name or dish name in alt text
- [ ] No images over 500KB (flag for compression)

### AI Citation Elements (Cross-check with blog-geo)
- [ ] TL;DR box present (40-60 words, top of post)
- [ ] Citation capsules present in each H2 section
- [ ] FAQ section present (3+ questions)
- [ ] datePublished and dateModified in frontmatter
- [ ] schema.json file exists alongside final.md

### Canonical
- [ ] Canonical URL set in frontmatter
- [ ] Canonical URL matches the intended live URL exactly

## Workflow

### Step 1: Load Files

Read:
- `04-BLOG/[cluster]/[post-slug]/final.md`
- `04-BLOG/[cluster]/[post-slug]/metadata.json`
- `04-BLOG/[cluster]/[post-slug]/schema.json` (check existence)
- `02-TOPICAL-MAP/topical-map.csv` (to validate internal link targets)

### Step 2: Run Every Check

Go through every item in the checklist. Mark PASS or FAIL with the specific value found.

Example:
```
Title tag: PASS 52 characters - "Best Ramen in Austin: 7 Spots Worth the Wait"
Meta description: FAIL 171 characters - trim by 11 characters
H1: PASS Present and unique
```

### Step 3: Report

```
## SEO Check: [Post Title]

### Results Summary
- Passed: [N]/[total]
- Failed: [N]/[total]
- Warnings: [N]/[total]

### Failures (fix before publishing)
[list each failed check with the specific fix]

### Warnings (fix if possible)
[list warnings]

### Publish Readiness
[READY TO PUBLISH] - all critical checks passed
[NOT READY] - [N] critical issues must be fixed first
```

Critical failures that block publishing:
- Missing or broken title tag
- Missing meta description
- Duplicate H1 or missing H1
- Broken internal links
- Missing og:image
- Missing schema.json
- No AI citation elements (TL;DR, FAQ)

Warnings (non-blocking but should fix):
- Meta description slightly long/short
- No Twitter card
- Images missing alt text (non-cover images)
- External links not opening in new tab
