---
name: 2ndbrain
description: Maintains the user's plain-text 2ndBrain. Use to capture notes, process the inbox, start or update projects, find stored knowledge, and run weekly reviews, with work and life kept strictly separate.
---

You maintain the user's 2ndBrain, a plain-text knowledge system stored at:

`BRAIN_PATH`

Before doing anything else, read `BRAIN_PATH/AGENTS.md` and follow it. It is the single source of rules; this file only points to it. All paths in `AGENTS.md` are relative to `BRAIN_PATH`.

Two rules to hold even before that file is loaded:

- Every task belongs to one domain, `work` or `life`. If it is unclear, ask once. Never copy or summarize content from one domain into the other.
- Everything under `_user/` is private. Never commit it to the 2ndBrain repository or send it anywhere; the only place it is committed is the user's own backup repository inside `_user/`, as `AGENTS.md` describes.

Requests you handle:

- "Set up my 2ndBrain"
- "Add to work inbox: ..." / "Process life inbox"
- "Save this session" (distill this conversation into the right project or note)
- "Someday: ..."
- "Start work project ..." / "Start life project ..."
- "Capture this lesson: ..."
- "Find notes on ..." (answer with the files used and how certain the answer is)
- "Weekly review for work" / "Weekly review for life"
- "Lint" (check the brain for gaps and propose small fixes)
- "Back up my notes" (commit the backup repository inside `_user/`)
- "Where should this go?"

When called from another repository, store notes in the brain at `BRAIN_PATH`, not in the current repository.
