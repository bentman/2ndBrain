# 2ndBrain User Guide

2ndBrain keeps useful context out of chat history and in plain files that you and an AI agent can both read.

## The Core Idea

Put information where your future self would look for it.

If you are not sure where something belongs, put it in the inbox. Sort it later.

## Work And Life

Everything you store lives in one of two spaces: `work` or `life`.

- They have the same structure.
- They never share content.
- Say which one you mean, for example "add to my work inbox". If the agent cannot tell, it asks.

## Where Things Live

All of your notes are under `_user/`:

```text
_user/
├── facts.md  preferences.md  boundaries.md     your settings
├── inbox.md                                    items with no space chosen yet
├── work/
└── life/
```

Inside `work/` and `life/`:

| Name | What goes there |
|---|---|
| `projects/` | Things with a goal and an end |
| `areas/` | Ongoing responsibilities |
| `knowledge/` | Reusable notes and lessons |
| `archive/` | Finished or inactive work |
| `journal/` | Weekly summaries |
| `inbox.md` | Quick notes, sorted later |
| `someday.md` | Ideas you are not acting on yet |
| `index.md` | A catalog the agent keeps current |
| `log.md` | A running record of what changed |

Your notes are private. This repository ignores them. Only `_user/README.md` and the empty folders are public.

## What To Say

| Say this | What happens |
|---|---|
| `Set up my 2ndBrain` | Creates your private files and settings |
| `Add to work inbox: [note]` | Saves a quick note to sort later |
| `Process life inbox` | Goes through the inbox with you and files each item |
| `Save this session` | Writes the decisions and progress from this chat into the right project |
| `Someday: [idea]` | Adds an idea to the someday list |
| `Start work project: [name]` | Creates a project folder with a next action |
| `Capture this lesson: [lesson]` | Writes a reusable knowledge note |
| `Find notes on [topic]` | Answers from your notes and names the files used |
| `Weekly review for life` | Runs the weekly review for that space |
| `Lint` | Checks for gaps and proposes small fixes |
| `Back up my notes` | Commits your notes to the backup |
| `Where should this go?` | Tells you where something belongs |

Use `work` or `life` in any request to choose the space.

## A Week In Use

The files in `_system/example/work/` show one week of a made-up project. This is how they came to be:

| You say | What changes |
|---|---|
| `Start work project: team wiki migration` | A project folder appears under `projects/`, with a README and a next action. The project is added to `index.md`. |
| `Add to work inbox: ask platform team about page history` | One line is added to `inbox.md`. Nothing else happens yet. |
| `Someday: template for onboarding pages` | One line is added to `someday.md`. |
| `Save this session` (after a chat about a failed trial) | Progress goes into the project's `notes.md`. The decision goes into `decisions.md`. The lesson becomes a note in `knowledge/`. |
| `Find notes on redirects` | The agent answers from the knowledge note and names the file. |
| `Weekly review for work` | The inbox is emptied, the next action is updated, and the week's entry is written under `journal/`. |

Each change is also recorded as one line in `log.md`.

## The Weekly Review

Once a week, ask for a review of each space. It should take minutes.

The agent:

1. Empties the inbox with you.
2. Checks that every project has a next action.
3. Archives finished work.
4. Skims the someday list.
5. Flags gaps.
6. Writes the week's journal entry.
7. Commits the backup.

If a week passes without a review, the agent mentions it once.

## Settings

Three files in `_user/` control how the system behaves:

| File | What it controls |
|---|---|
| `preferences.md` | Tone, answer length, your review day, and when the backup is committed and pushed |
| `boundaries.md` | What may be stored, what never is, and whether work notes are backed up |
| `facts.md` | Basic context about you |

Edit them directly, or tell the agent what to change. When you correct the agent, it updates `preferences.md` so the correction sticks.

## The Commit Guard

The commit guard is a small Git hook. It refuses any commit that contains private notes.

It is switched on once per copy of the repository. Setup does this for you. To do it by hand, run this in the 2ndBrain folder:

```bash
git config core.hooksPath _system/hooks
```

The guard does not run when Git merges. Never pull or merge your private backup into the 2ndBrain folder.

Never run `git clean` in the 2ndBrain folder. It deletes notes that are not yet backed up.

## Backup

Your notes are not saved in this repository's history. To keep versions of them, `_user/` becomes its own private Git repository, separate from this one.

### Set It Up

Let the agent do it during setup, or run this yourself:

```bash
cd _user
git init -b main
```

For a copy off this machine, add a private remote. The agent checks that the remote is private before every push.

### What The Agent Does

- Commits after each weekly review and after any large change.
- Commits when you say "back up my notes".
- Pushes only as `preferences.md` says.

### Work Notes

One backup holds both spaces. If work notes must stay on this machine, tell the agent before you add any. It then leaves `work/` out of the backup.

### A Second Machine

Clone 2ndBrain, then restore your notes inside `_user/`:

```bash
cd _user
git init -b main
git remote add origin <your private repository URL>
git fetch origin
git checkout -B main origin/main
```

Then switch on the commit guard (see The Commit Guard above).

Two habits when you use more than one machine:

- Before you start, update your notes: `git -C _user pull`
- Never run `git pull` with your private repository's address in the 2ndBrain folder itself. That would mix your private notes into the public repository.

## When Something Goes Wrong

| What you see | What to do |
|---|---|
| A commit fails with "Commit blocked" | A private file was about to go into the public repository. The message lists it. Run `git restore --staged <path>` for each file listed. |
| `git pull` in the 2ndBrain folder says "divergent branches" | You pulled the private repository into the public one. Do not merge or rebase. Your notes belong inside `_user/`; follow A Second Machine above. |
| A note is in the wrong space | Tell the agent which note and where it belongs. It moves the file and updates both indexes. |
| Notes are missing on another machine | Run `git -C _user pull`. Work notes kept out of the backup exist only on the machine where they were written. |
| The agent keeps asking "work or life?" | Name the space in your request, for example "add to my life inbox". |
| The agent does not follow the system | Tell it: "Read `AGENTS.md` and follow it." |

## Keep It Simple

If a pattern emerges, tell the agent to adjust the structure or the instructions. If something feels like overhead, remove it.

`_system/METHOD.md` explains where the ideas come from.
