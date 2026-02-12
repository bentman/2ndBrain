# Project Kickoff

Use this when work needs a dedicated project folder.

## When To Create A Project

Create `_user/data/projects/[project-name]/` when the work has any of these:

- A clear goal
- Multiple sessions
- Decisions to track
- Research to compare
- Implementation notes worth preserving
- A final solution or lesson to extract

## Naming

Use short lowercase names with hyphens:

```text
_user/data/projects/[short-specific-name]/
```

## Minimal Files

```text
_user/data/projects/[project-name]/
├── README.md
├── research.md
├── decisions.md
├── notes.md
└── solutions.md
```

Create all five for substantial projects. For small experiments, start with `README.md` and `notes.md`, then add files only as needed.

## README Minimum

```markdown
# [Project Name]

**Status:** Planning | Active | On Hold | Complete
**Started:** YYYY-MM-DD

## Purpose
[Why this project exists]

## Goals
- [Goal]

## Constraints
- [Constraint]

## Success Criteria
[How we know it worked]

## Key Files
- `research.md`
- `decisions.md`
- `notes.md`
- `solutions.md`
```

## Kickoff Questions

Ask only what is needed:

- What problem are we solving?
- What constraints matter?
- What does success look like?
- What is already known?
- What is the next action?

## Maintenance

- Keep project state in the project folder.
- Extract reusable lessons to `_user/data/knowledge/`.
- Mark completed or inactive work in the project README, or move it into a user-created archive folder if that pattern becomes useful.
