# User Layer

This folder is the private user layer for 2ndBrain.

Everything here is ignored by Git except this README and the empty folder skeleton. Real context and notes stay local.

## Layout

```text
_user/
├── facts.md          compact facts an agent may need
├── preferences.md    communication and workflow preferences
├── boundaries.md     privacy and handling rules
├── inbox.md          quick capture for both domains
├── work/
│   ├── index.md  log.md
│   └── projects/  areas/  knowledge/  archive/  journal/
└── life/
    ├── index.md  log.md
    └── projects/  areas/  knowledge/  archive/  journal/
```

The Markdown files are created by the agent on "set up my 2ndBrain", from the starters in `_system/templates/user/`.

## Rules

- Work and life never share content. Each domain has its own index, log, journal, and reviews.
- Keep user facts out of `AGENTS.md` and `_system/`.
- Do not force-add ignored `_user` content unless the user explicitly asks.
