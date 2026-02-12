# 2ndBrain User Guide

2ndBrain is a simple plain-text system for keeping useful context out of chat history and in files.

It stores:
- User context and preferences
- Projects and decisions
- Reusable knowledge
- Personal research
- Journal notes and reminders
- Quick inbox captures

## Core Idea

Put information where your future self would naturally look for it.

If the right place is unclear, put it in the inbox and sort it later.

## Structure

```text
2ndBrain/
├── AGENTS.md
├── README.md
├── USER_GUIDE.md
├── _system/
└── _user/
    ├── facts.md
    ├── preferences.md
    ├── profile.md
    ├── boundaries.md
    └── data/
        ├── inbox/
        ├── journal/
        ├── knowledge/
        ├── personal/
        └── projects/
```

## How To Use It

Tell an AI agent:

```text
Read AGENTS.md and help me maintain this 2ndBrain.
```

Common requests:

```text
Add to inbox: [note]
Process inbox
Capture this lesson: [lesson]
Start project: [name]
Find notes on [topic]
Generate weekly summary
Where should this go?
```

## Where Things Go

- `_user/facts.md` - compact user facts
- `_user/preferences.md` - communication and workflow preferences
- `_user/boundaries.md` - privacy and handling rules
- `_user/data/inbox/` - unsorted quick notes
- `_user/data/journal/` - time-based notes and reminders
- `_user/data/knowledge/` - reusable concepts, lessons, references, gotchas
- `_user/data/personal/` - personal research and decisions
- `_user/data/projects/` - active and archived project work

## Keep It Simple

The system is intentionally easy to change. If a pattern emerges, tell the agent to adjust the structure or instructions. If something feels like overhead, simplify it.
