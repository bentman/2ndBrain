# Solution Design

Use this when work has a problem, constraints, options, decisions, and implementation notes.

## Route

Create or update `_user/data/projects/[project-name]/`.

## Core Files

- `README.md` - goal, status, constraints, success criteria, links
- `research.md` - options, sources, open questions
- `decisions.md` - choices and reasoning
- `notes.md` - running work log and blockers
- `solutions.md` - final or emerging implementation details

## Process

1. Define the problem and desired outcome.
2. Capture constraints.
3. Record options in `research.md`.
4. Record meaningful decisions in `decisions.md`.
5. Keep progress and blockers in `notes.md`.
6. Move stable implementation details to `solutions.md`.
7. Extract reusable lessons into `_user/data/knowledge/`.

## Decision Rule

Document a decision when a future reader might ask, "Why did we do it this way?"

Use `_system/templates/decision-log.md` when the decision is significant.

## Done Enough

A solution is documented well enough when a future reader can understand:

- What problem was solved
- What approach was chosen
- Why alternatives were rejected
- How the solution works
- What limitations or follow-ups remain
