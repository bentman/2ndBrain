# User Layer

This folder is the private user layer for 2ndBrain.

The 2ndBrain repository ignores everything here except this README and the empty folder skeleton. Real context and notes stay out of it.

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

The Markdown files are created by the agent on "set up my 2ndBrain", from the starters in `_system/templates/user/`. `someday.md` is created when first needed.

## Rules

- Work and life never share content. Each domain has its own inbox, index, log, journal, and reviews.
- To back up, make this folder its own private Git repository (`git init` here, plus a private remote if wanted). The outer repository ignores it. See Backup in `AGENTS.md`.
- Keep user facts out of `AGENTS.md` and `_system/`.
- Never force-add ignored `_user` content to the 2ndBrain repository. The commit guard (`_system/hooks/pre-commit`) blocks it.
