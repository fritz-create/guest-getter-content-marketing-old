# Session Notes

Shared cross-LLM notes for this workspace.

This file keeps Claude, Codex, ChatGPT, and other LLMs aligned across sessions. It does not replace `00-START-HERE/SESSION-STATE.md`. Use `SESSION-STATE.md` for formal phase status and approvals. Use this file for practical handoff context, decisions, constraints, and next actions.

## How to Use This File

Read this file at the start of every session after reading `AGENT.md`, `CLAUDE.md`, and `00-START-HERE/SESSION-STATE.md`.

Update this file when any of the following happens:
- A phase starts, pauses, gets approved, or is skipped.
- The user makes a strategic decision or correction that future LLMs must honor.
- A file or template is changed.
- A blocker appears.
- A content direction, brand rule, or workflow rule is clarified.
- Work stops before the next obvious action is complete.

Keep notes concise and factual. Do not duplicate full documents here. Link to the source file or name the relevant file instead.

## Current Workspace Status

- Workspace type: Master content marketing template for restaurant brands.
- Active client: None.
- Intake status: `00-START-HERE/CLIENT-INTAKE.md` is blank.
- Session status: `00-START-HERE/SESSION-STATE.md` has no active phase.
- Git status: This folder is not currently a Git repository.

## Shared Rules

- Read `AGENT.md` before doing phase work.
- Do not advance any phase without user approval.
- Do not create client content before brand documents are approved.
- Do not guess missing facts. Mark unknowns with `[UNCONFIRMED]` or `[NEEDS CONFIRMATION]`.
- Avoid em dashes in generated files and user-facing content. Use hyphens instead.
- Preserve the folder structure unless the user approves a workflow change.

## Latest Handoff

### 2026-04-27

- Created this shared `session-notes.md` file so multiple LLMs can stay aligned across sessions.
- Recommended using `SESSION-STATE.md` for formal phase tracking and this file for cross-agent handoff notes.
- Current folder appears to be the reusable master template, not a live client copy.
- Improved template consistency:
  - Added `04-BLOG/cluster-index.md` because the blog folder README referenced it.
  - Added `.gitignore` for local OS/editor files and `.claude/settings.local.json`.
  - Updated `02-TOPICAL-MAP/topical-map.csv` and `03-CALENDAR/backlog.csv` to include `tier`, `primary_kw`, and `intent_fingerprint` fields.
  - Updated `07-ASSETS/templates/blog-metadata-template.json` and `.claude/commands/blog-write.md` so metadata fields match.
  - Updated `00-START-HERE/existing-data/IMPORT-INSTRUCTIONS.md` to map imported tier data.
  - Normalized Unicode arrows, dashes, comparison symbols, and pass/fail symbols to ASCII across text-based template files.
  - Added root `README.md` as a neutral entry point for humans and non-Claude LLMs.
