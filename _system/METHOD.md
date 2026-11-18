# Method

2ndBrain borrows a few ideas from established knowledge-management methods. This page lists what was taken. `AGENTS.md` holds the rules.

## What Is Used

| Idea | From | Where you see it |
|---|---|---|
| File things by how actionable they are | [PARA](https://fortelabs.com/blog/para/), Tiago Forte | `projects/`, `areas/`, `knowledge/`, `archive/` |
| Capture, Organize, Distill, Express | [Building a Second Brain](https://www.buildingasecondbrain.com/), Tiago Forte | The core loop |
| Summarize a note when you reuse it | [Progressive Summarization](https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/), Tiago Forte | The `Summary:` line on each note |
| Inbox, next actions, someday list, weekly review | [Getting Things Done](https://gettingthingsdone.com/what-is-gtd/), David Allen | `inbox.md`, `someday.md`, project next actions, the weekly review |
| Small linked notes, one idea each | [Zettelkasten](https://zettelkasten.de/introduction/), Niklas Luhmann; [Evergreen notes](https://notes.andymatuschak.org/Evergreen_notes), Andy Matuschak | The rules for `knowledge/` notes |
| An index and a log the agent maintains | [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f), Andrej Karpathy | `index.md`, `log.md`, and the ingest, query, and lint operations |
| Shallow, predictable folders | [Johnny.Decimal](https://johnnydecimal.com/) | The two-level folder limit |

`knowledge/` is what PARA calls Resources.

## What Is Left Out

- Note IDs and numbered folders
- A store of raw source files, and search tooling
- Task management beyond one next action per project
- Scripts (other than the commit guard), plugins, and required apps

Add one only when a real, repeated need shows up.

## Work And Life

The two spaces have the same structure and never share content. Each has its own inbox.

The separation is a rule the agent follows. It is not a technical barrier.

## Files In `_system/`

| Path | Purpose |
|---|---|
| `SETUP-2ndBrain.md` | Step-by-step setup the agent follows on "set up my 2ndBrain" |
| `workflows/capture.md` | Inbox and filing |
| `workflows/projects.md` | Start, run, and close a project |
| `workflows/knowledge.md` | Write and maintain reusable notes |
| `workflows/review.md` | Weekly review and lint |
| `templates/` | Small structures to copy |
| `templates/user/` | Starters for the private settings files |
| `example/` | A small filled-in example |
| `agent/2ndBrain.agent.md` | Portable agent definition |
| `hooks/pre-commit` | Commit guard that keeps private notes out of this repository |

Keep `_system/` free of personal content. Facts, preferences, and notes belong in `_user/`.
