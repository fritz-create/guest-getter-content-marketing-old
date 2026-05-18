# Existing Data Import

## For the User

Drop existing content data files here before Phase 4A begins. The agent reads everything in this folder before proposing any pillars or topics.

Accepted formats:
- Excel files (.xlsx) - see mapping below
- CSV exports from Google Sheets
- A list of existing blog post URLs (one per line in any .txt or .md file)
- A keyword list (any .csv)

---

## Excel / Spreadsheet Mapping

If the client provides a spreadsheet (like a topical map or keyword research file), map the columns to this system as follows:

| Their Column | Maps To | Our File |
|---|---|---|
| Content Pillar / Pillar name | `pillar` | content-pillars.csv |
| Customer question / Intent | `customer_question` | content-pillars.csv |
| What it covers / In scope | `covers` | content-pillars.csv |
| What it does not cover / Out of scope | `does_not_cover` | content-pillars.csv |
| Topic / Sub-topic / Theme | `topic` | topical-map.csv |
| Blog title / Working title | `working_title_1` | topical-map.csv |
| Main KW / Primary keyword | `primary_kw` | topical-map.csv |
| Volume | `volume` → use as TAM | kw-opportunities.csv |
| KD / KD% | `kd_pct` | kw-opportunities.csv |
| Intent (C/I/PAA/L) | `intent` | kw-opportunities.csv |
| CPC | `cpc` | kw-opportunities.csv |
| TAM | `tam` | kw-opportunities.csv |
| SOM | `som` | kw-opportunities.csv |
| Status (Published/In Progress) | `status` | topical-map.csv |
| Content URL | `live_url` | topical-map.csv |

---

## For the Agent

When Phase 4A begins, check this folder before proposing anything.

### Step 1 - Identify what exists

Read every file. For each item:
- Is it a pillar definition, a topic, a keyword list, or a blog URL list?
- Does it have boundary definitions (covers / does not cover)?
- Does it have keyword data (volume, KD%, intent)?
- Are any posts already published (live URLs present)?

### Step 2 - Audit Report

Present before building anything:

```
EXISTING DATA AUDIT
-------------------
Pillars found: [list]
Topics found per pillar: [summary]
Working titles / blog titles found: [count]
Keywords with volume data: [count]
Published URLs: [list]
Potential intent overlaps: [list]
Gaps already visible: [list]
```

Ask: "Does this mapping look right before I build the pillars?"

### Step 3 - Integrate, don't replace

- Use existing pillars as the foundation - rename only if the boundary is unclear
- Map existing topics and titles into topical-map.csv - do not recreate
- Assign intent fingerprints to existing published posts in intent-log.md
- Flag cannibalization risks before Phase 4B begins
- Propose only genuine gaps as new additions

### Step 4 - Existing blog posts

If live URLs are present, fetch each one. Read title, headings, and topic. For each:
- Map to a pillar and topic
- Write an intent fingerprint and add to intent-log.md as published
- Flag any two posts competing for the same intent (cannibalization)
- Note posts that are thin, outdated, or mistargeted

Present findings before Phase 4A gate. Decisions on existing posts affect pillar boundaries.

### Rule

Never discard existing data to start fresh. Build on what exists.
