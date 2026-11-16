# Projects

Use this when work has a goal, an end, and more than one session.

## Start

Create `[domain]/projects/[short-lowercase-name]/` with:

- `README.md` - purpose, status, next action, goals, constraints (use `_system/templates/project-readme.md`)
- `notes.md` - running log and open questions

Add these only when needed:

- `research.md` - options, findings, sources
- `decisions.md` - choices and reasoning
- `solutions.md` - stable implementation details

Ask only what is needed: What problem are we solving? What does success look like? What is the next action?

Then add the project to the domain `index.md` and `log.md`.

## Run

- Keep all project state in the project folder.
- Keep **Next action** in the README current. A project without one is stalled.
- Record a decision when a future reader might ask "why did we do it this way?" Use `_system/templates/decision-log.md` for significant ones.
- Move details from `notes.md` to `solutions.md` once they are stable.

## Close

1. Set the README status to Complete or Dropped, with the date and outcome.
2. Extract reusable lessons into `knowledge/` notes.
3. Move the whole folder to `[domain]/archive/`.
4. Update `index.md` and append to `log.md`.

## Areas vs Projects

A project ends; an area does not. Ongoing responsibilities go in `areas/` as a single file each (for example `areas/health.md`). When an area produces work with a goal and an end, start a project and link the two.
