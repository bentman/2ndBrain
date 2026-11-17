# Method

2ndBrain borrows a small number of ideas from established knowledge-management methods. This page explains what was taken and why. `AGENTS.md` holds the actual rules.

## What Is Used

| Idea | Source | How it shows up here |
|---|---|---|
| Organize by actionability | [PARA](https://fortelabs.com/blog/para/) - Tiago Forte | `projects/`, `areas/`, `knowledge/` (PARA's Resources), `archive/` in each domain |
| Capture, Organize, Distill, Express | [Building a Second Brain](https://www.buildingasecondbrain.com/) - Tiago Forte | The core loop in `AGENTS.md` |
| Distill in layers, only when reused | [Progressive Summarization](https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/) - Tiago Forte | One-line `Summary:` at the top of each note |
| Inbox, next actions, someday list, weekly review | [Getting Things Done](https://gettingthingsdone.com/what-is-gtd/) - David Allen | `inbox.md` and `someday.md` in each domain, the next-action line in project READMEs, `workflows/review.md` |
| Small linked notes, one idea each | [Zettelkasten](https://zettelkasten.de/introduction/) - Niklas Luhmann; [Evergreen notes](https://notes.andymatuschak.org/Evergreen_notes) - Andy Matuschak | The note rules for `knowledge/` |
| Agent-maintained index and log; ingest, query, lint | [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) - Andrej Karpathy | `index.md` and `log.md` per domain, the operations in `AGENTS.md` |
| Shallow, predictable folders | [Johnny.Decimal](https://johnnydecimal.com/) | The two-level depth limit |

## What Is Left Out

Left out on purpose, to keep the system easy to manage:

- Note IDs and numeric folder codes
- A raw source store and search tooling
- Task management beyond one next action per project
- Scripts, plugins, or any required app

Add one only when a real, repeated need shows up.

## Work and Life

The two domains have the same structure and never share content. This keeps employer-confidential material in one place that can be excluded, relocated, or deleted as a unit, and keeps personal material out of work contexts. Each domain has its own inbox, so the two do not mix even before filing.

## Files In `_system/`

- `workflows/capture.md` - inbox and filing
- `workflows/projects.md` - start, run, and close a project
- `workflows/knowledge.md` - write and maintain reusable notes
- `workflows/review.md` - weekly review and lint
- `templates/` - small copyable structures
- `templates/user/` - starters for the private `_user/*.md` files
- `example/` - a small filled-in domain showing the target shape
- `agent/2ndBrain.agent.md` - portable agent definition

Keep `_system/` user-neutral. User facts, preferences, and notes belong in `_user/`.
