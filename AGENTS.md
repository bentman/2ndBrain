# 2ndBrain Agent Instructions

## What This Is

2ndBrain is a plain-text knowledge system. Your job is to help maintain it so information is easy to capture, find, and reuse.

`AGENTS.md` holds durable operating rules only. Do not store status, user facts, project details, research findings, or reminders here.

Two layers:
- `_system/` - reusable method, workflows, and templates
- `_user/` - one user's private context and notes, split into `work/` and `life/`

The repository is public-safe. Everything under `_user/` is ignored by Git except `README.md` and `.gitkeep` skeletons. Never force-add ignored `_user` content unless the user explicitly asks.

## Load Order

1. Read this file.
2. Read `_user/boundaries.md` before storing sensitive, personal, or work-derived information.
3. Read `_user/facts.md` and `_user/preferences.md` only when user context or tone matters.
4. Read the active domain's `index.md`, then only the files the task needs.
5. Read `_system/` files only when this file is not enough.

If the private `_user` files do not exist yet, run **Setup** below.

## Domains: Work and Life

Everything the user stores belongs to exactly one domain: `_user/work/` or `_user/life/`.

- Every task has one active domain. Infer it from the request; if it is unclear, ask once.
- Read and write only inside the active domain, plus `_user/*.md` and `_user/inbox.md`.
- Never copy, move, or summarize content from one domain into the other. If a note must point across, use a bare link with no details.
- Indexes, logs, journals, and reviews are per domain. Never combine them.
- Search both domains only when the user explicitly asks, and label each result with its domain.
- Shared user context (`facts.md`, `preferences.md`, `boundaries.md`) stays in `_user/` and holds no work-confidential detail.

## Where Things Go

Inside each domain, file by how actionable the content is:

| Folder | Holds |
|---|---|
| `projects/[name]/` | Work with a goal and an end. Always has a next action. |
| `areas/` | Ongoing responsibilities with no end date (health, finances, a team, a system). |
| `knowledge/` | Reusable notes: concepts, lessons, references, gotchas. |
| `archive/` | Finished or inactive projects and areas, moved here whole. |
| `journal/[year]/[year]-W[week].md` | Weekly summaries and time-based context. |
| `index.md` | Catalog: one line per project, area, and knowledge note. |
| `log.md` | Append-only record of what was added, reviewed, or cleaned up. |

`_user/inbox.md` is the single capture point for both domains.

Keep it shallow: no folder deeper than two levels below a domain. If content fits more than one place, choose the most actionable home and link. Do not duplicate.

## Core Loop

1. **Capture** - Get it written down. If the destination is unclear, use `_user/inbox.md`.
2. **Organize** - Pick the domain, then the folder. Search for an existing file before creating one.
3. **Distill** - Keep what is useful: decisions, facts, dates, sources, open questions. Start each note with a one-line `Summary:`.
4. **Express** - Use it: answer, draft, decide. File reusable results back as notes.

Stop when the content is findable and useful. Do not add structure beyond what the task needs.

## Operations

**Ingest** - when storing something:
1. File it per the table above.
2. Add or update its line in the domain `index.md`: `- [Title](path) - one-line summary`.
3. Append to the domain `log.md`: `- [YYYY-MM-DD] ingest | Title -> path`.

**Query** - when answering from stored context:
1. Read the active domain's `index.md` first, then the files it points to. Search the domain if the index is not enough.
2. Cite the files used. Say whether the answer is certain, partial, or missing.
3. Offer to file a reusable answer as a knowledge note.

**Lint** - during a weekly review or when asked, flag and propose the smallest fix for:
- Notes missing from `index.md`, or index lines pointing to missing files
- Notes with no links in or out
- Projects with no next action, or finished projects not yet archived
- Decisions or progress that exist only in chat
- Content in the wrong domain, or user facts outside `_user/`
- Duplicated notes, stale claims, broken links
- Anything Git would track under `_user/` beyond the skeleton

Log reviews and lint passes in `log.md` the same way as ingests.

## Notes

- One idea per knowledge note. The title states the idea.
- Link related notes with relative Markdown links.
- Update an existing note rather than writing a near-duplicate.
- Distill when a note is reused, not upfront.
- One-off answers do not need a file unless the user asks or the pattern repeats.

## Setup

On "set up my 2ndBrain", or when private files are missing and needed:

1. Copy `_system/templates/user/*.md` to `_user/` and ask the user only what is needed to fill them.
2. Create `_user/inbox.md`.
3. Create `index.md` and `log.md` in `_user/work/` and `_user/life/`.

No scripts are needed.

## Editing Rules

- Keep Markdown simple.
- Prefer updating existing files over creating new ones.
- Do not duplicate user facts, project state, or process rules across files.
- Use `_system/templates/` when structure helps and `_system/workflows/` when a task needs more detail.
- Update `_system/` and `AGENTS.md` only when the process itself changes.
- If the user corrects tone or workflow behavior, update `_user/preferences.md`.

## Default Behavior

Be concise, direct, and practical. Answer quick questions directly. Ask focused questions only when needed, or state a low-risk assumption. Preserve useful information in the smallest appropriate place.
