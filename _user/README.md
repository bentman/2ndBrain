# User Layer

This folder is the local user layer for 2ndBrain.

Tracked files here should stay public-safe. Real user context and data are private by default and ignored by Git.

## Local Files

Create these local files as needed:

- `facts.md` - compact facts an agent may need
- `preferences.md` - communication and workflow preferences
- `profile.md` - optional background context
- `boundaries.md` - privacy, safety, and handling rules

These files are intentionally ignored by Git.

## Data Folders

User data belongs under `data/`:

```text
_user/data/
├── inbox/
├── journal/
├── knowledge/
├── life/
└── projects/
```

Only the broad folder skeletons are tracked. Notes, project files, journal entries, and other user data stay local unless the user explicitly changes the Git rules.

## Maintenance Rules

- Keep user facts out of `AGENTS.md`.
- Keep portable process in `_system/`.
- Store private context and data under `_user/`.
- Do not force-add ignored `_user` content unless the user explicitly asks.
