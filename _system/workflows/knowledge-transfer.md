# Knowledge Transfer

Use this when the user needs to explain something clearly or reuse an explanation later.

## Route

- Repeated explanation -> `_user/data/knowledge/`; create topic subfolders only when useful
- Project-specific explanation -> relevant `_user/data/projects/[project]/` file
- One-off response -> answer directly; do not create a file unless asked

## Process

1. Search for an existing explanation.
2. Decide whether this needs permanent capture.
3. Write for the intended audience.
4. Include examples and gotchas.
5. Link related knowledge or project files.

## Minimal Structure

```markdown
# [Concept]

## What It Is
[Plain explanation]

## Why It Matters
[Problem it solves]

## How It Works
[Practical explanation]

## Example
[Realistic example]

## Gotchas
- [Common pitfall]

## Related
- [Link]
```

## Rule

Capture reusable explanations. Do not clutter `_user/data/knowledge/` with one-off answers.
