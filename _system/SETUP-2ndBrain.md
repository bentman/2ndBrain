# Setup 2ndBrain

Summary: Step-by-step setup for a new or partly set-up 2ndBrain. `AGENTS.md` sends the agent here on "set up my 2ndBrain".

Follow the steps in order. Setup always asks; never fill answers with assumptions. If a command is blocked, follow "When A Command Is Blocked" in `AGENTS.md`.

## 1. Check What Exists

List which of these already exist:

- `_user/facts.md`, `_user/preferences.md`, `_user/boundaries.md`, `_user/inbox.md`
- `inbox.md`, `index.md`, `log.md` in `_user/work/` and `_user/life/`
- `_user/.git` (backup repository)
- The commit guard: `git config core.hooksPath` in the repository root prints `_system/hooks`

Show the list to the user. For each existing settings file, ask once whether to keep it or replace it. Never overwrite a file unless the user says to.

## 2. Ask The Questions, One At A Time

Start with one line: "I'll ask up to 11 short questions, one at a time. Answer, or reply `default`, `skip`, or `rest default`."

Then ask each question in its own message and wait for the answer before asking the next. Show the short explanation and the default with each question.

- `default` uses the default shown. `skip` leaves the field empty.
- `rest default` uses the defaults for every remaining question; go to step 3.
- Skip questions whose file is being kept.

| # | Question | Why it is asked | Default | Goes to |
|---|---|---|---|---|
| 1 | Your name, location or time zone, and role? | Dates, reminders, and context in answers | empty | `facts.md` About |
| 2 | Tools and platforms that affect how help should be given? | Commands and examples match your setup | empty | `facts.md` Tools |
| 3 | Current focus: one general line for work, one for life? No confidential detail. | Helps filing and suggestions | empty | `facts.md` Current Focus |
| 4 | How should replies sound: tone, length, format? | Sets the agent's style | direct, concise, simple Markdown | `preferences.md` Communication |
| 5 | What should the agent ask before doing? | Guards against unwanted changes | creating folders, restructuring, deleting | `preferences.md` Workflow |
| 6 | Which day for the weekly review? | When the agent reminds you to review | Monday | `preferences.md` Workflow |
| 7 | Work: how to handle employer-confidential material (never store, store only in `_user/work/`, or summarize without names), and what must never be stored? | Keeps work notes within your employer's rules | store only in `_user/work/`; never store credentials, secrets, customer personal data | `boundaries.md` Work |
| 8 | Life: what must never be stored, and how to handle details about other people? | Limits what personal detail is kept | never store credentials, account numbers, government IDs; keep only what is needed about others | `boundaries.md` Life |
| 9 | How should reminders from journal entries be raised? | When the agent brings up open reminders | during the weekly review | `boundaries.md` Reminders |
| 10 | Set up a private backup repository for your notes now? | Versions your notes; this repository never stores them | no | Step 5 |
| 11 | Only if 10 is yes. May work notes be backed up? When to commit, and when to push? | Work notes may need to stay on this machine | work notes not backed up; commit after reviews and large changes; push when asked | `preferences.md` Backup, `boundaries.md` Work |

## 3. Write The Files

1. Copy `_system/templates/user/*.md` to `_user/` and fill them from the answers.
   - Leave skipped fields empty. Never leave `[option | option]` placeholders.
   - Remove template guidance lines, such as "One general line each. No confidential detail."
2. Create these files if missing, with these first lines:

   | File | First line |
   |---|---|
   | `_user/inbox.md` | `# Inbox (space unknown)` |
   | `_user/work/inbox.md` | `# Work Inbox` |
   | `_user/life/inbox.md` | `# Life Inbox` |
   | `_user/work/index.md` | `# Work Index` |
   | `_user/life/index.md` | `# Life Index` |
   | `_user/work/log.md` | `# Work Log` |
   | `_user/life/log.md` | `# Life Log` |

3. Give each `index.md` the headings `## Projects`, `## Areas`, `## Knowledge`, `## Archive`.
4. Append `- [YYYY-MM-DD] setup | <what was created>` to each space `log.md`.
5. Do not create `someday.md`; it is created when first needed.

See `_system/example/` for what filled-in files look like.

## 4. Enable The Commit Guard

From the repository root, run:

```
git config core.hooksPath _system/hooks
```

This changes a Git setting so Git uses the tracked hook in `_system/hooks/`. Do not copy or create files in `.git/hooks/`.

## 5. Set Up Backup

Only if the answer to question 10 was yes.

1. Create `_user/.gitignore` containing `/README.md` and `.gitkeep`. If work notes are not backed up (question 11), also add `/work/`, and record that in `_user/boundaries.md`.
2. Do not run `git init` yourself. Tell the user to run it in `_user/`:

   ```
   git init -b main
   ```

   Why: the backup repository must be owned by the user's own account. Agents often run commands as a separate sandbox account, and Git refuses to work in a repository owned by a different account.
3. Tell the user they can add a private remote later. See **Backup** in `AGENTS.md`.

## 6. Verify And Report

From the repository root, run:

- `git config core.hooksPath` - should print `_system/hooks`
- `git status --short` - should show nothing under `_user/`

Then tell the user:

- What was created, and what was kept
- Any step that failed or was blocked, with the exact command and the folder to run it in
