# Session Notes

Shared handoff file for Codex, Claude, and any other LLM working in this folder.

## Purpose

Use this file for cross-session context that helps agents stay aligned. It should not replace the existing workflow tracker. Keep workflow phase status and approvals in `00-START-HERE/SESSION-STATE.md`.

## Read Order for All LLMs

At the start of every session:

1. Read `session-notes.md`.
2. Read `CLAUDE.md` and `AGENT.md`.
3. Read `00-START-HERE/SESSION-STATE.md`.
4. Read any source files named in the active handoff below.
5. Confirm the newest user request before changing files.

## Source of Truth

- Workflow status and approval gates: `00-START-HERE/SESSION-STATE.md`
- Full phase workflow and content rules: `AGENT.md`
- Claude startup behavior: `CLAUDE.md`
- Original client input: `00-START-HERE/CLIENT-INTAKE.md`
- Cross-LLM coordination, recent handoff notes, blockers, and file touchpoints: `session-notes.md`

## Coordination Rules

- Before any session end, clear, compact, or handoff, append a token-efficient entry to the Session Log.
- Every Session Log entry must include the LLM used, trigger, work done, files touched, and next step or blocker.
- Update Active Handoff when the next agent needs to know current state, blockers, or recently touched files.
- Do not overwrite another agent's notes unless correcting a clear factual error.
- Preserve approval gates from `SESSION-STATE.md`.
- Mark uncertain items with `[NEEDS CONFIRMATION]`.
- Do not store secrets, API keys, passwords, cookies, or private credentials here.
- Use exact relative file paths when mentioning files.
- Keep entries brief. No transcripts, raw command output, long reasoning, or repeated context already stored elsewhere.

## Session Log Format

Use this compact format:

```md
### YYYY-MM-DD - LLM - Trigger
- Did: One-line summary of completed work.
- Files: `path`, `path`
- Next: Immediate next action, or `none`.
- Blockers: Only unresolved blockers, or `none`.
```

Triggers: `session-end`, `clear`, `compact`, `handoff`, or `update`.

## Active Handoff

**Last updated:** 2026-04-27  
**Updated by:** Codex  
**Client:** Malt & Barley Public House  
**Website:** https://maltandbarley.ca/  
**Current phase:** Phase 5 - Calendar  

**Next workflow action:** Review or finalize the SEO/GEO casual dining draft, assign dates for the 2 GBP drafts tied to the published local pubs post and 3 GBP drafts tied to casual dining, and continue Phase 5 calendar scheduling cleanup.

**Open confirmations:**

- Confirm planned dates for the two GBP drafts tied to "How People Find Local Pubs in Kitchener".
- Review or finalize "When a Pub Is the Right Choice for Casual Dining"; canonical URL and cover image are needed before final schema and publish SEO check.
- Schedule the patio-related post ahead of May if it remains a priority.

**Recently touched files:**

- `session-notes.md`
- `00-START-HERE/SESSION-STATE.md`
- `CLAUDE.md`
- `AGENT.md`
- `02-TOPICAL-MAP/topical-map.csv`
- `02-TOPICAL-MAP/intent-log.md`
- `03-CALENDAR/backlog.csv`
- `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/draft.md`
- `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/kw-research.md`
- `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/metadata.json`
- `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/seo-audit.md`
- `06-REPURPOSING/when-a-pub-is-the-right-choice-for-casual-dining/derivative-plan.md`
- `06-REPURPOSING/when-a-pub-is-the-right-choice-for-casual-dining/gbp-drafts.md`
- `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/draft.md`
- `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/metadata.json`
- `05-GBP/GBP-POST-LOG.csv`
- `06-REPURPOSING/how-people-find-local-pubs-kitchener/derivative-plan.md`
- `06-REPURPOSING/how-people-find-local-pubs-kitchener/gbp-drafts.md`

## Session Log

### 2026-04-27 - Codex - session-end
- Did: Reviewed the casual dining draft against SEO best practices and identified publish blockers.
- Files: `session-notes.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/draft.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/metadata.json`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/seo-audit.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/kw-research.md`
- Next: Confirm canonical/live URL, cover image, author, publish date, and GBP dates before final schema and publish SEO check.
- Blockers: Canonical URL, cover image, author, publish date, live URL, Semrush data, and GBP dates still need confirmation.

### 2026-04-27 - Codex - session-end
- Did: Read startup handoff files and SESSION-STATE.md, then summarized current workflow state for the user.
- Files: `session-notes.md`, `AGENT.md`, `CLAUDE.md`, `00-START-HERE/SESSION-STATE.md`
- Next: Confirm GBP dates, review or finalize the casual dining draft, and clean up Phase 5 calendar scheduling.
- Blockers: Casual dining canonical/live URL, cover image, GBP dates, and Semrush data still need confirmation.

### 2026-04-27 - Codex - session-end
- Did: Read startup handoff files and summarized current workflow state for the user.
- Files: `session-notes.md`, `CLAUDE.md`, `AGENT.md`, `00-START-HERE/SESSION-STATE.md`
- Next: Continue Phase 5 calendar cleanup and content production confirmations.
- Blockers: Local pubs publish date/live URL and GBP dates still need confirmation.

### 2026-04-27 - Codex - session-end
- Did: Marked the local pubs post as published from user-provided live URL and created the next casual dining blog draft.
- Files: `00-START-HERE/SESSION-STATE.md`, `02-TOPICAL-MAP/topical-map.csv`, `02-TOPICAL-MAP/intent-log.md`, `03-CALENDAR/backlog.csv`, `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/metadata.json`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/draft.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/kw-research.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/metadata.json`, `05-GBP/GBP-POST-LOG.csv`, `06-REPURPOSING/how-people-find-local-pubs-kitchener/derivative-plan.md`, `session-notes.md`
- Next: Review/finalize the casual dining draft and assign dates for the 2 GBP drafts from the published local pubs post.
- Blockers: GBP dates still need confirmation; Semrush data for casual dining was not provided.

### 2026-04-27 - Codex - session-end
- Did: Applied local Claude SEO blog command standards to the casual dining draft, added AI citation elements, and created three GBP extraction drafts plus a derivative plan.
- Files: `00-START-HERE/SESSION-STATE.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/draft.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/metadata.json`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/seo-audit.md`, `05-GBP/GBP-POST-LOG.csv`, `06-REPURPOSING/when-a-pub-is-the-right-choice-for-casual-dining/derivative-plan.md`, `06-REPURPOSING/when-a-pub-is-the-right-choice-for-casual-dining/gbp-drafts.md`, `session-notes.md`
- Next: Confirm canonical/live URL, cover image, and GBP dates before final schema and publish check.
- Blockers: Casual dining canonical URL, cover image, GBP dates, and Semrush data still need confirmation.

### 2026-04-27 - Codex - session-end
- Did: Normalized casual dining source links to the non-www Malt & Barley domain.
- Files: `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/draft.md`, `session-notes.md`
- Next: Use `https://maltandbarley.ca/` as the canonical domain moving forward.
- Blockers: none.

### 2026-04-27 - Codex

- Created this shared coordination file at the user's request.
- Linked it from `CLAUDE.md` and `AGENT.md` so future LLM sessions read it during startup.
- Left workflow phase status unchanged in `00-START-HERE/SESSION-STATE.md`.

### 2026-04-27 - Codex - update

- Did: Added mandatory compact, clear, handoff, and session-end logging protocol.
- Files: `session-notes.md`, `CLAUDE.md`, `AGENT.md`
- Next: Phase 5 calendar work in `03-CALENDAR/backlog.csv`.
- Blockers: Superseded by later 2026-04-27 correction below.

### 2026-04-27 - Codex - update

- Did: Earlier correction marked "How People Find Local Pubs in Kitchener" as planned. Superseded by later correction below: it is written/draft.
- Files: `00-START-HERE/SESSION-STATE.md`, `02-TOPICAL-MAP/topical-map.csv`, `02-TOPICAL-MAP/intent-log.md`, `03-CALENDAR/backlog.csv`, `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/metadata.json`, `05-GBP/GBP-POST-LOG.csv`, `session-notes.md`
- Next: Superseded by later correction below.
- Blockers: Superseded by later correction below.

### 2026-04-27 - Codex - update

- Did: Locked blog plus GBP package format, saved the written local pubs draft and GBP drafts, and corrected status inversion: local pubs is written/draft while casual dining is in progress.
- Files: `07-ASSETS/templates/blog-draft-template.md`, `07-ASSETS/templates/gbp-post-template.md`, `07-ASSETS/templates/blog-gbp-package-template.md`, `07-ASSETS/templates/derivative-plan-template.md`, `07-ASSETS/templates/blog-metadata-template.json`, `06-REPURPOSING/REPURPOSING-RULES.md`, `05-GBP/GBP-FOLDER-README.md`, `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/draft.md`, `04-BLOG/local-pub-discovery/how-people-find-local-pubs-kitchener/metadata.json`, `06-REPURPOSING/how-people-find-local-pubs-kitchener/derivative-plan.md`, `06-REPURPOSING/how-people-find-local-pubs-kitchener/gbp-drafts.md`, `04-BLOG/occasion-pub-experience/when-a-pub-is-the-right-choice-for-casual-dining/metadata.json`, `02-TOPICAL-MAP/topical-map.csv`, `02-TOPICAL-MAP/intent-log.md`, `03-CALENDAR/backlog.csv`, `05-GBP/GBP-POST-LOG.csv`, `00-START-HERE/SESSION-STATE.md`, `session-notes.md`
- Next: Confirm whether the local pubs draft is final and continue the casual dining post.
- Blockers: Local pubs publish date/live URL and GBP dates still need confirmation.
