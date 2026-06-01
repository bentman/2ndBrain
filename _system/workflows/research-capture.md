# Research Capture

Use this when the user is learning, comparing options, testing something, or asking to document research.

## Route

- Project-specific -> `_user/data/projects/[project]/research.md`
- Reusable technical/conceptual -> `_user/data/knowledge/`
- Personal/life -> `_user/data/life/`
- Useful source/link collection -> `_user/data/knowledge/` unless the user has created a reference subfolder
- Unclear -> `_user/data/inbox/quick-notes.md`

## Process

1. Identify the topic and why it matters.
2. Search for an existing related file.
3. Capture the useful findings, not raw source material.
4. Record sources when available.
5. Note open questions and gotchas.
6. Link related projects or knowledge notes.
7. Stop when the note is findable and useful.

## Minimal Structure

```markdown
# [Topic]

## Context
[Why this was researched]

## Findings
- [Useful finding]
- [Useful finding]

## Gotchas
- [Non-obvious issue]

## Open Questions
- [Question]

## Sources
- [Source]

## Related
- [Link]
```

Use `_system/templates/technical-summary.md` only when the topic needs more structure.
