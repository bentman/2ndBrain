# 2ndBrain

A second brain in plain text files, kept tidy by an AI agent.

You talk to the agent. It files your notes, tracks your projects, and finds things again later. Everything is Markdown that you can read and edit yourself.

## At A Glance

- **Two separate spaces.** Work and life are stored apart and never mixed.
- **Private by default.** Your notes never go into this public repository.
- **Nothing to install.** No app and no build. Just Markdown files and one small Git hook.
- **Works with common agents.** Claude Code, GitHub Copilot, Codex, Cursor, and others that read `AGENTS.md`.

What using it looks like:

```text
Add to work inbox: ask the platform team about page history
Process work inbox
Find notes on redirects
Weekly review for life
```

## What Is In The Repository

| Path | What it is |
|---|---|
| `AGENTS.md` | The rules the agent follows |
| `USER_GUIDE.md` | How to use it day to day |
| `_system/` | The method, workflows, templates, a worked example, the agent definition, and the commit guard |
| `_user/` | Your private notes, split into `work/` and `life/` |
| `LICENSE` | MIT license |

## Setup

1. Clone this repository.
2. Open the folder with an AI agent that reads `AGENTS.md`.
3. Say: `Set up my 2ndBrain`

The agent then does three things:

- Creates your private files under `_user/`.
- Turns on the commit guard (see below).
- Offers to set up a private backup for your notes.

## Settings

Three files in `_user/` control how the system behaves. Edit them yourself, or tell the agent what to change.

| File | What it controls |
|---|---|
| `preferences.md` | Tone, answer length, your review day, and when the backup is committed and pushed |
| `boundaries.md` | What may be stored, what never is, and whether work notes are backed up |
| `facts.md` | Basic context about you |

## Keeping Your Notes Private

Two things keep your notes out of this public repository:

- **Ignore rules.** Git ignores everything under `_user/` except its README and the empty folders.
- **Commit guard.** A small hook that refuses any commit containing private notes.

The guard is switched on once per copy of the repository. Setup does this for you. To do it by hand, run this in the repository folder:

```bash
git config core.hooksPath _system/hooks
```

Two limits to know about:

- The guard does not run when Git merges.
- Never pull or merge your private backup into this repository. The backup belongs inside `_user/`. The User Guide shows how.

## Use The Agent From Any Project

`_system/agent/2ndBrain.agent.md` lets you reach your brain while working in another folder.

1. Copy the file to **one** of these locations:

   | Platform | Copy it to |
   |---|---|
   | GitHub Copilot / VS Code | `~/.copilot/agents/2ndBrain.agent.md` |
   | Claude Code | `~/.claude/agents/2ndbrain.md` |

2. Open your copy and replace `BRAIN_PATH` with the full path to this repository.

Pick one location only. VS Code reads both and would list the agent twice.

For any other agent, give it this instruction: "Read `AGENTS.md` in my 2ndBrain folder and follow it."

## Credits

This is a small implementation that borrows ideas from several established methods. It is not an official version of any of them. `_system/METHOD.md` shows what was taken from each.

- [Building a Second Brain](https://www.buildingasecondbrain.com/) and [PARA](https://fortelabs.com/blog/para/) - Tiago Forte
- [Progressive Summarization](https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/) - Tiago Forte
- [Getting Things Done](https://gettingthingsdone.com/what-is-gtd/) - David Allen
- [Zettelkasten](https://zettelkasten.de/introduction/) - Niklas Luhmann
- [Evergreen notes](https://notes.andymatuschak.org/Evergreen_notes) - Andy Matuschak
- [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) - Andrej Karpathy
- [Johnny.Decimal](https://johnnydecimal.com/)
- [AGENTS.md](https://agents.md/) - open format for agent instructions

## License

[MIT](LICENSE)
