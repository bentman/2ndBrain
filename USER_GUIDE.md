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
├── inbox.md
├── work/
└── life/
```

Inside each domain:

- `projects/` - things with a goal and an end
- `areas/` - ongoing responsibilities
- `knowledge/` - reusable notes and lessons
- `archive/` - finished or inactive work
- `journal/` - weekly summaries
- `index.md` - a catalog the agent keeps current
- `log.md` - a running record of what changed

All of `_user/` is private and ignored by Git.

## Common Requests

```text
Set up my 2ndBrain
Add to inbox: [note]
Process inbox
Start work project: [name]
Capture this lesson: [lesson]
Find notes on [topic]
Weekly review for life
Lint
Where should this go?
```

## The Weekly Habit

Once a week, per domain, ask for a weekly review. The agent empties the inbox with you, checks every project has a next action, archives finished work, flags gaps, and writes the week's journal entry. It should take minutes.

## Keep It Simple

If a pattern emerges, tell the agent to adjust the structure or instructions. If something feels like overhead, remove it. `_system/METHOD.md` explains where the ideas come from.
