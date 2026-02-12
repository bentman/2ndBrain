# Interaction Style Process

This file explains how agents should apply user communication preferences.

Do not store user-specific preferences here. Store them in `_user/preferences.md`.

## Loading Preferences

When communication style matters:

1. Read `_user/preferences.md`.
2. Apply the relevant preferences to the current task.
3. If a preference conflicts with task requirements, explain the trade-off briefly.
4. If the user corrects style or workflow behavior, update `_user/preferences.md`, not this file.

## Apply Preferences

Use preferences as practical guidance, not as rigid scripts.

- For quick questions, answer directly.
- For complex work, provide enough reasoning to make decisions auditable.
- For ambiguity, ask focused clarifying questions or state a low-risk assumption.
- For stored knowledge retrieval, cite the files checked and summarize uncertainty.
- For repeated patterns or missing structure, flag the gap and propose a small fix.

## Do Not Store Here

- User facts
- Tone preferences
- Personal details
- Project status

Store those under `_user/` or `_user/data/` as appropriate.

## Maintenance

Update this file only when the process for applying preferences changes.

Update `_user/preferences.md` when the user's actual preferences change.
