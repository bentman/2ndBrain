# Your Private Notes

This folder holds your notes and settings.

The 2ndBrain repository ignores everything here except this README and the empty folders. This README is public, so keep personal details out of it.

## Layout

```text
_user/
├── facts.md          basic context about you
├── preferences.md    how the agent should communicate and work
├── boundaries.md     what may be stored, and where
├── inbox.md          items with no space chosen yet
├── work/
│   ├── inbox.md  someday.md  index.md  log.md
│   └── projects/  areas/  knowledge/  archive/  journal/
└── life/
    ├── inbox.md  someday.md  index.md  log.md
    └── projects/  areas/  knowledge/  archive/  journal/
```

The agent creates these files when you say "set up my 2ndBrain". `someday.md` appears the first time you need it.

## Rules

- Work and life never share content.
- To back up your notes, this folder becomes its own private Git repository. `USER_GUIDE.md` shows how.
- Never add these files to the 2ndBrain repository. The commit guard refuses it once switched on.
