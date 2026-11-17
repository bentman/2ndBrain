# User Layer

This folder is the private user layer for 2ndBrain.

Everything here is ignored by Git except this README and the empty folder skeleton. Real context and notes stay local.

## Layout

```text
_user/
├── facts.md          compact facts an agent may need
├── preferences.md    communication and workflow preferences
├── boundaries.md     privacy and handling rules
├── inbox.md          holding place for items with no domain yet
├── work/
│   ├── inbox.md  someday.md  index.md  log.md
│   └── projects/  areas/  knowledge/  archive/  journal/
└── life/
    ├── inbox.md  someday.md  index.md  log.md
    └── projects/  areas/  knowledge/  archive/  journal/
```

The Markdown files are created by the agent on "set up my 2ndBrain", from the starters in `_system/templates/user/`.

## Rules

- Work and life never share content. Each domain has its own inbox, index, log, journal, and reviews.
- To back up, make this folder its own private Git repository (`git init` here). The outer repository ignores it.
- Keep user facts out of `AGENTS.md` and `_system/`.
- Do not force-add ignored `_user` content unless the user explicitly asks.
