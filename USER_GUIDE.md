# 2ndBrain User Guide

2ndBrain keeps useful context out of chat history and in plain files that you and an AI agent can both read.

## Core Idea

Put information where your future self would look for it. If the right place is unclear, put it in the inbox and sort it later.

## Work And Life

Everything you store lives in one of two domains, `work` or `life`. They have the same structure and never share content. Say which one you mean ("add to my work inbox", "weekly review for life"); the agent asks if it cannot tell.

## Structure

```text
_user/
├── facts.md  preferences.md  boundaries.md
├── inbox.md          only for items with no domain yet
├── work/
└── life/
```

Inside each domain:

- `projects/` - things with a goal and an end
- `areas/` - ongoing responsibilities
- `knowledge/` - reusable notes and lessons
- `archive/` - finished or inactive work
- `journal/` - weekly summaries
- `inbox.md` - quick capture, sorted later
- `someday.md` - ideas you are not acting on yet
- `index.md` - a catalog the agent keeps current
- `log.md` - a running record of what changed

Your notes under `_user/` are private and ignored by this repository. Only `_user/README.md` and the empty folder skeleton are public. See Backup below for keeping versions of your notes.

## Common Requests

```text
Set up my 2ndBrain
Add to work inbox: [note]
Process life inbox
Save this session
Someday: [idea]
Start work project: [name]
Capture this lesson: [lesson]
Find notes on [topic]
Weekly review for life
Lint
Back up my notes
Where should this go?
```

## The Weekly Habit

Once a week, per domain, ask for a weekly review. The agent empties the inbox with you, checks every project has a next action, archives finished work, skims the someday list, flags gaps, writes the week's journal entry, and commits the backup. It should take minutes. If a week goes by without one, the agent mentions it once.

## Backup

Your notes are not stored in this repository's history. To keep versions of them, let the agent turn `_user/` into its own private Git repository during setup, or run `git init` there yourself. Add a private remote if you want a copy off this machine.

The agent then commits after each weekly review, after any large change, and when you say "back up my notes". It pushes only as your `preferences.md` says, and only after checking the remote is private.

The backup holds both work and life. If work notes must not leave this machine, tell the agent to keep `work/` out of the backup before you add any.

To restore on a new machine, clone 2ndBrain, then inside `_user/` run `git init`, `git remote add origin <your private repo>`, `git fetch origin`, and `git checkout -B main origin/main`.

## Keep It Simple

If a pattern emerges, tell the agent to adjust the structure or instructions. If something feels like overhead, remove it. `_system/METHOD.md` explains where the ideas come from.
