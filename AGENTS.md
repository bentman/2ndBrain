# 2ndBrain Agent Instructions

## What This Is

2ndBrain is a plain-text knowledge system. Your job is to help maintain it so information is easy to capture, find, and reuse.

`AGENTS.md` holds durable operating rules only. Do not store status, user facts, project details, research findings, or reminders here.

Two layers:
- `_system/` - reusable method, workflows, and templates
- `_user/` - one user's private context and notes, split into `work/` and `life/`

This repository is public. It ignores everything under `_user/` except `README.md` and `.gitkeep` skeletons. Private notes are versioned only in the backup repository described under **Backup**.

## Hard Rules

These override everything else in this file.

1. **One space per task.** Every task is `work` or `life`. If it is unclear, ask once.
2. **Never cross spaces.** Do not copy, move, or summarize content from one space into the other. The only exception is moving a misfiled item when the user asks; then update the index and log in both spaces.
3. **Never put private notes in this repository.** Write notes only under `_user/`. Never force-add them, never pull or merge the backup repository into this one, and never bypass the commit guard (`--no-verify`). The guard does not run on merges.
4. **Never push the backup to a public remote.** Check that the remote is private before every push.
5. **Read `_user/boundaries.md` first** when storing anything sensitive, personal, or work-derived.

## Load Order

1. Read this file.
2. Read `_user/facts.md` and `_user/preferences.md` only when user context or tone matters.
3. Read the active space's `index.md`, then only the files the task needs.
4. Glance at the active space's `log.md`. If the last `review` entry is more than a week old, say so once at the start of the session. If there is no `review` entry yet, say nothing.
5. Read `_system/` files only when this file is not enough.

If the private `_user` files do not exist yet, run **Setup** below.

## Spaces: Work and Life

Everything the user stores belongs to exactly one space: `_user/work/` or `_user/life/`. Spaces exist only under `_user/`; never create `work/` or `life/` anywhere else.

- Infer the active space from the request.
- Read and write only inside the active space, plus the shared `_user/*.md` files.
- If a note must point to the other space, use a bare link with no details.
- Inboxes, indexes, logs, journals, and reviews are per space. Never combine them.
- Search both spaces only when the user explicitly asks, and label each result with its space.
- Shared user context (`facts.md`, `preferences.md`, `boundaries.md`) stays in `_user/` and holds no work-confidential detail.

## Where Things Go

Inside each space, file by how actionable the content is:

| Folder | Holds |
|---|---|
| `projects/[name]/` | Work with a goal and an end. Always has a next action. |
| `areas/` | Ongoing responsibilities with no end date (health, finances, a team, a system). |
| `knowledge/` | Reusable notes: concepts, lessons, references, gotchas. |
| `archive/` | Finished or inactive projects and areas, moved here whole. |
| `journal/[year]/[year]-W[week].md` | Weekly summaries, reminders, and time-based context, by ISO week with two digits (`2026-W03`). Raise reminders as `_user/boundaries.md` says. |
| `inbox.md` | Unsorted quick capture for this space. |
| `someday.md` | Ideas not being acted on yet. One line each. |
| `index.md` | Catalog: one line per project, area, and knowledge note, under the headings Projects, Areas, Knowledge, Archive. |
| `log.md` | Append-only record of what was added, reviewed, or cleaned up. |

`_user/inbox.md` holds only items whose space is not yet known. Move them to a space inbox as soon as it is. Keep it empty, and keep confidential work detail out of it.

Keep it shallow: no folder deeper than two levels below a space. If content fits more than one place, choose the most actionable home and link. Do not duplicate.

## Core Loop

1. **Capture** - Get it written down. If the destination is unclear, use the space's `inbox.md`. If the space itself is unclear and asking would interrupt, use `_user/inbox.md`.
2. **Organize** - Pick the space, then the folder. Search for an existing file before creating one.
3. **Distill** - Keep what is useful: decisions, facts, dates, sources, open questions. Start each note with a one-line `Summary:`.
4. **Express** - Use it: answer, draft, decide. File reusable results back as notes.

Stop when the content is findable and useful. Do not add structure beyond what the task needs.

## Operations

**Ingest** - when storing something:
1. File it per the table above.
2. Add or update its line in the space `index.md`: `- [Title](path) - one-line summary`.
3. Append to the space `log.md`: `- [YYYY-MM-DD] ingest | Title -> path`.

**Query** - when answering from stored context:
1. Read the active space's `index.md` first, then the files it points to. Search the space if the index is not enough.
2. Cite the files used. Say whether the answer is certain, partial, or missing.
3. Offer to file a reusable answer as a knowledge note.

**Save session** - on "save this session", or when a conversation produced decisions or progress that exist only in chat:
1. Pick the space and the project or note it belongs to.
2. Distill, do not transcribe: decisions with reasons are appended to the project's `decisions.md`, progress and open questions to `notes.md`, reusable lessons to `knowledge/`.
3. Update the project's next action, then follow Ingest for anything new.

**Lint** - during a weekly review or when asked, flag and propose the smallest fix for:
- Notes missing from `index.md`, or index lines pointing to missing files
- Notes with no links in or out
- Projects with no next action, or finished projects not yet archived
- Items sitting in `_user/inbox.md`, or `someday.md` entries that are now active or dead
- Decisions or progress that exist only in chat
- Content in the wrong space, or user facts outside `_user/`
- Duplicated notes, stale claims, broken links
- Anything Git would track under `_user/` beyond the skeleton, or the commit guard not enabled (`git config core.hooksPath`, run in the repository root, should print `_system/hooks`)

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
2. Create `_user/inbox.md`, and `inbox.md`, `index.md`, and `log.md` in `_user/work/` and `_user/life/`. Create `someday.md` when first needed.
3. Enable the commit guard from the repository root: `git config core.hooksPath _system/hooks`.
4. Offer to set up Backup below.

See `_system/example/` for what filled-in files look like.

## Backup

Private notes are not part of this repository's history. Back them up as a separate private Git repository inside `_user/`:

- Set up once, with the user's agreement: `git init` in `_user/`. The outer repository ignores it. The user adds a private remote if they want an off-machine copy. Create `_user/.gitignore` containing `/README.md` and `.gitkeep`, so the two repositories never track the same file.
- If `_user/.git` exists, commit there after each weekly review, after any large change, and on "back up my notes", with a one-line message. Never commit private content to the outer repository.
- Push only when the user asks or the Backup setting in `_user/preferences.md` says to.
- Before every push, check that the remote is private (for GitHub: `gh repo view --json isPrivate`). If it is public or cannot be checked, do not push; tell the user.
- The backup repository's remote and branch live in `_user/.git`. Never write its URL into tracked files.
- One backup repository holds both spaces. During setup, ask whether work notes may be backed up. If not, add `/work/` to `_user/.gitignore` before any work note is committed, and record it in `_user/boundaries.md`.
- Never run `git clean` in the outer repository; it deletes uncommitted private notes.
- Restore on a new machine: clone this repository, then in `_user/` run `git init`, `git remote add origin <url>`, `git fetch origin`, `git checkout -B main origin/main`.

## Editing Rules

- Keep Markdown simple.
- Prefer updating existing files over creating new ones.
- Do not duplicate user facts, project state, or process rules across files.
- Use `_system/templates/` when structure helps and `_system/workflows/` when a task needs more detail.
- Update `_system/` and `AGENTS.md` only when the process itself changes.
- If the user corrects tone or workflow behavior, update `_user/preferences.md`.

## Default Behavior

Be concise, direct, and practical. Answer quick questions directly. Ask focused questions only when needed, or state a low-risk assumption. Preserve useful information in the smallest appropriate place.
