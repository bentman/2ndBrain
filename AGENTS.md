# 2ndBrain Agent Instructions

## What This Is

2ndBrain is a plain-text knowledge system. Your job is to help maintain it so information is easy to capture, find, and reuse.

`AGENTS.md` is only for durable operating rules. Do not store current status, user facts, project details, research findings, or reminders here.

The system is split into two portable layers:
- `_system/` - reusable process, templates, and agent guidance
- `_user/` - one user's facts, preferences, boundaries, and private local data

The repository is meant to be public-safe. `_user/*.md` and `_user/data/**` content are ignored by Git; only `.gitkeep` folder skeletons should be tracked.

In a fresh clone, private `_user` Markdown files may not exist. Create or update them locally only when needed.

## Load Order

1. Read this file.
2. Read `_user/facts.md` only when user context matters.
3. Read `_user/preferences.md` only when tone or workflow behavior matters.
4. Read `_user/boundaries.md` before storing sensitive, work-derived, or personal information.
5. Read `_user/data/` files only as needed for the task.
6. Read `_system/` files only when this file is not enough.

## Routing Rules

Put information where it will be looked for later:

- `_user/` - user facts, profile, preferences, boundaries, and data
- `_system/` - portable process rules, templates, and system maintenance docs
- `_user/data/knowledge/` - durable concepts, lessons, references, patterns, and gotchas
- `_user/data/projects/` - active project state, research, decisions, notes, and solutions
- `_user/data/projects/` - completed or inactive projects can stay here or move into a user-created archive folder
- `_user/data/personal/` - personal research and decisions
- `_user/data/journal/` - time-based summaries, reminders, and temporal context
- `_user/data/inbox/quick-notes.md` - unprocessed quick capture

If content fits more than one place, choose the smallest useful home and link to related files. Do not duplicate.

## Core Loop

For any task:

1. **Classify** - Decide what type of information this is.
2. **Check** - Search for an existing file before creating a new one.
3. **Update** - Add only useful context, decisions, facts, dates, sources, and open questions.
4. **Link** - Connect related projects, knowledge, journal entries, or user facts.
5. **Stop** - Do not add structure beyond what the task needs.

## Common Actions

### Quick Capture

Use `_user/data/inbox/quick-notes.md` when the destination is unclear or the user wants friction-free capture.

### Research

Project-specific research goes in `_user/data/projects/[project]/research.md`.

Reusable technical or conceptual research goes in `_user/data/knowledge/`.

Personal research goes in `_user/data/personal/`.

### Projects

Use a project folder when work has a goal, constraints, decisions, or multiple sessions.

Core files:
- `README.md` - purpose, status, goals, constraints, links
- `research.md` - investigation and sources
- `decisions.md` - choices and reasoning
- `notes.md` - running log and open questions
- `solutions.md` - final or emerging implementation details, when useful

### Knowledge Transfer

Reusable explanations go in `_user/data/knowledge/`. Create topic subfolders only when the user needs them.

One-off explanations do not need permanent files unless the user asks or the pattern repeats.

### Journal

Use `_user/data/journal/[year]/[year]-W[week].md` for weekly summaries and temporal context.

Follow reminder behavior in `_user/boundaries.md`.

## Gap Handling

Flag gaps when they reduce future usefulness:

- A repeated topic has no durable note in `_user/data/knowledge/`.
- A project has decisions or progress only in chat.
- A file references missing or stale content.
- User facts appear outside `_user/`.
- User data appears outside `_user/data/`.
- Process docs are longer or more complex than the actual workflow.
- Git would track private `_user` content.

When flagging a gap, name it and propose the smallest fix.

## Editing Rules

- Keep Markdown simple.
- Prefer updating existing files over creating new ones.
- Do not duplicate user facts outside `_user/`.
- Do not duplicate project state outside the project folder.
- Do not duplicate process rules across many files.
- Use templates from `_system/templates/` when structure helps.
- Update `_system/` only when the process changes.
- Update `AGENTS.md` only when durable routing or operating rules change.
- Never force-add ignored `_user` content unless the user explicitly asks.

## Query Rules

When answering from stored context:

1. Search `_user/data/knowledge/`.
2. Search active `_user/data/projects/`.
3. Search `_user/data/journal/`.
4. Search `_user/` only for user-specific context.

Say what you checked and whether the answer is certain, partial, or missing.

## Default Behavior

Be concise, direct, and practical. Ask focused questions only when needed. Preserve useful information in the smallest appropriate place.
