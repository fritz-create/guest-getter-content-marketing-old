---
name: blog-schema
description: >
  Generate complete JSON-LD schema markup for a restaurant blog post. Produces
  BlogPosting, Organization, Person, BreadcrumbList, FAQPage, and ImageObject
  schema using the @graph pattern. Critical for AI discoverability - AI crawlers
  use structured data to identify authoritative sources. Run before publishing
  any finalized post.
argument-hint: "[path to final.md or post slug]"
---

# Blog Schema - JSON-LD for Restaurant Posts

Generates complete structured data for restaurant blog posts. Schema is the primary signal AI crawlers use to understand entity relationships and content authority.

## Project Context

Every finalized post in this system needs schema before it can be considered publish-ready. The schema file is saved alongside the post content.

Save output to: `04-BLOG/[cluster]/[post-slug]/schema.json`

## Required Schema Types

Every restaurant blog post gets all of these:

1. **BlogPosting** - the article itself
2. **Organization** - the restaurant as publisher (pulled from `01-BRAND/location-signals.md`)
3. **Person** - the author (pulled from brand docs or use restaurant name as author)
4. **BreadcrumbList** - navigation path for AI context
5. **FAQPage** - if the post has an FAQ section (strong AI citation signal)
6. **ImageObject** - cover image with dimensions and caption

## Workflow

### Step 1: Load Data Sources

Read:
- `04-BLOG/[cluster]/[post-slug]/final.md` - extract title, description, dates, FAQ pairs, images, word count, tags, slug
- `01-BRAND/location-signals.md` - restaurant name, address, website URL, logo
- `04-BLOG/[cluster]/[post-slug]/metadata.json` - publish date, live URL, cluster

### Step 2: Generate @graph Schema

Output a single `<script type="application/ld+json">` block using the @graph pattern:

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "BlogPosting",
      "@id": "{siteUrl}/blog/{slug}#article",
      "headline": "[title - max 110 chars]",
      "description": "[meta description - 150–160 chars]",
      "datePublished": "YYYY-MM-DD",
      "dateModified": "YYYY-MM-DD",
      "wordCount": [number],
      "author": { "@id": "{siteUrl}#author" },
      "publisher": { "@id": "{siteUrl}#organization" },
      "image": { "@id": "{siteUrl}/blog/{slug}#primaryimage" },
      "mainEntityOfPage": { "@type": "WebPage", "@id": "{siteUrl}/blog/{slug}" },
      "keywords": ["tag1", "tag2"],
      "articleSection": "[cluster name]",
      "inLanguage": "en-US"
    },
    {
      "@type": "Organization",
      "@id": "{siteUrl}#organization",
      "name": "[restaurant name]",
      "url": "[website URL]",
      "logo": { "@type": "ImageObject", "url": "[logo URL]" },
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "[street]",
        "addressLocality": "[city]",
        "addressRegion": "[state]",
        "postalCode": "[zip]"
      }
    },
    {
      "@type": "Person",
      "@id": "{siteUrl}#author",
      "name": "[author name or restaurant name]",
      "url": "{siteUrl}/about"
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        { "@type": "ListItem", "position": 1, "name": "Home", "item": "{siteUrl}" },
        { "@type": "ListItem", "position": 2, "name": "Blog", "item": "{siteUrl}/blog" },
        { "@type": "ListItem", "position": 3, "name": "[cluster]", "item": "{siteUrl}/blog/[cluster]" },
        { "@type": "ListItem", "position": 4, "name": "[title]", "item": "{siteUrl}/blog/{slug}" }
      ]
    },
    {
      "@type": "ImageObject",
      "@id": "{siteUrl}/blog/{slug}#primaryimage",
      "url": "[cover image URL]",
      "width": 1200,
      "height": 630,
      "caption": "[alt text or image description]"
    }
  ]
}
```

### Step 3: Add FAQPage (If FAQ Section Exists)

If the post has a FAQ section, add a FAQPage node to the @graph:

```json
{
  "@type": "FAQPage",
  "@id": "{siteUrl}/blog/{slug}#faq",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[question text]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[answer text - full sentence, self-contained]"
      }
    }
  ]
}
```

Extract every Q&A pair from the FAQ section. Each answer must be a complete, self-contained response (AI crawlers extract these verbatim).

### Step 4: Validate

Check before saving:
- [ ] No placeholder text remaining (`{siteUrl}`, `[restaurant name]`, etc. - flag any that couldn't be filled)
- [ ] `datePublished` is set (use draft date if not yet published)
- [ ] `headline` is under 110 characters
- [ ] `description` is 150–160 characters
- [ ] FAQPage answers are self-contained (each answer makes sense standalone)
- [ ] All `@id` references are consistent within the @graph

### Step 5: Save

Save to `04-BLOG/[cluster]/[post-slug]/schema.json`.

Report: *"Schema generated with [N] types: BlogPosting, Organization, Person, BreadcrumbList, [FAQPage if present], ImageObject. Saved to schema.json. Paste the `<script>` block into the `<head>` of the published page."*

Flag any fields that required `[NEEDS CONFIRMATION]` - these must be filled before publishing.
