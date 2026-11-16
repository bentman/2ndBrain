# 2ndBrain

A plain-text personal knowledge system maintained with an AI agent. Markdown only: no app, no scripts, no build.

## Repository Layout

- `AGENTS.md` - the agent's operating rules (single source of truth)
- `USER_GUIDE.md` - how to use it day to day
- `_system/` - method, workflows, templates, and the portable agent definition
- `_user/` - your private context and notes, split into `work/` and `life/` (ignored by Git)

## Setup

1. Clone the repository.
2. Open it with an AI agent that reads `AGENTS.md` (Claude Code, GitHub Copilot, Codex, Cursor, and others do so automatically).
3. Say: `Set up my 2ndBrain`.

The agent creates your private files under `_user/`. Nothing else is needed.

## Use The Agent From Anywhere

`_system/agent/2ndBrain.agent.md` is a portable agent definition. Installed at user level, it lets you reach your brain from any other project.

1. Copy the file to the location for your platform:
   - GitHub Copilot / VS Code: `~/.copilot/agents/2ndBrain.agent.md`
   - Claude Code: `~/.claude/agents/2ndbrain.md`
2. In the copy, replace `BRAIN_PATH` with the absolute path to this repository.

The file only points to `AGENTS.md`, so the rules never need to be kept in sync. Platforms without an agent-file format can be given the same instruction directly: "Read `AGENTS.md` in my 2ndBrain folder and follow it."

## Notes

- Your notes are not version controlled by this repository. Back up `_user/` however you back up other private files.
- The system is meant to be changed. Edit the files, or tell the agent to adjust them.

## Credits

This is a small Markdown-and-agent implementation that borrows from several established methods. It is not an official or complete version of any of them. See `_system/METHOD.md` for what was taken from each.

- [Building a Second Brain](https://www.buildingasecondbrain.com/) and [PARA](https://fortelabs.com/blog/para/) - Tiago Forte
- [Progressive Summarization](https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/) - Tiago Forte
- [Getting Things Done](https://gettingthingsdone.com/what-is-gtd/) - David Allen
- [Zettelkasten](https://zettelkasten.de/introduction/) - Niklas Luhmann
- [Evergreen notes](https://notes.andymatuschak.org/Evergreen_notes) - Andy Matuschak
- [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) - Andrej Karpathy
- [Johnny.Decimal](https://johnnydecimal.com/)
- [AGENTS.md](https://agents.md/) - open format for agent instructions
