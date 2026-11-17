# Worked Example

A small, fictional `work` space showing what filled-in files look like. A `life` space has exactly the same shape.

Nothing here is real user data. Do not store notes in this folder; real notes go under `_user/`.

```text
example/
├── facts.md  preferences.md  boundaries.md     filled-in settings
└── work/
    ├── index.md
    ├── log.md
    ├── inbox.md
    ├── someday.md
    ├── projects/team-wiki-migration/
    │   ├── README.md
    │   ├── notes.md
    │   └── decisions.md
    ├── knowledge/
    │   └── redirects-must-ship-with-a-migration.md
    └── journal/2026/
        └── 2026-W04.md
```

Things to notice:

- Every note and project starts with a one-line **Summary**.
- The project README has a single **Next action**.
- The knowledge note states one idea in its title and links back to the project it came from.
- `index.md` has one line per item; `log.md` has one line per event.
- The journal entry links to the project and the note instead of repeating them.

`USER_GUIDE.md` (A Week In Use) shows which request produced each file.
