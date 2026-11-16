# Plan: 2ndBrain v2 — proven concepts, work/life split, portable agent

## Context

The repo is a small Markdown + agent "second brain" credited only to Tiago Forte's book. It works, but:

- **No real work/life boundary.** `_user/data/life/` is one folder beside `projects/`, `knowledge/`, `journal/`; "work" is implied, never named.
- **Missing proven pieces.** No Areas or Archive (PARA), no index or log for the agent to navigate by, no review habit, no note-quality rules.
- **Duplication in `_system/`.** `ROUTING.md` repeats `AGENTS.md`; `solution-design.md` repeats `project-kickoff.md`; `research-capture.md` and `knowledge-transfer.md` overlap; three templates overlap.
- **No agent definition.** Only `AGENTS.md`, which works when the repo is open, not from elsewhere.

Goal: fold in a handful of reputable concepts, make work and life two clearly separate domains, and ship one portable agent definition — while staying Markdown-only, with no scripts and fewer files than today.

No private user data exists yet (only `.gitkeep` files), so restructuring needs no migration.

## Decisions already made

- **Separation:** two parallel domains, `_user/work/` and `_user/life/`, identical structure, one shared inbox.
- **Agent:** you selected only "user-level install notes". I read that as: ship **one portable agent file** in the repo plus instructions to copy it to `~/.copilot/agents/` and `~/.claude/agents/`, and no repo-level `.github/agents` or `.claude/agents` wrappers. `AGENTS.md` stays as the rulebook the agent file points to. Say so if you meant something else.

## Concepts adopted (and what is deliberately left out)

| Source | What we take | What we skip |
|---|---|---|
| **PARA** — Tiago Forte | Organize by actionability: `projects/`, `areas/`, `knowledge/` (= Resources), `archive/` in each domain | — |
| **CODE** — Tiago Forte | Core loop becomes Capture → Organize → Distill → Express | — |
| **Progressive summarization** — Forte | One-line `Summary:` at the top of each note; distill when a note is reused, not upfront | Multi-layer highlighting |
| **GTD** — David Allen | Single inbox, "next action" line in every project README, weekly review | Contexts, full task management |
| **Zettelkasten / Evergreen notes** — Luhmann, Ahrens, Andy Matuschak | Knowledge notes: one idea per note, title states the idea, linked to related notes, updated rather than duplicated | Note IDs, mandatory linking quotas |
| **LLM Wiki** — Andrej Karpathy | Per-domain `index.md` (one line per note, agent reads it first) and append-only `log.md`; three operations: ingest, query, lint | `raw/` source store, search tooling |
| **Johnny.Decimal** | Depth rule only: nothing deeper than two folders below a domain | Numeric IDs |

Each row gets a credited link in the README (links verified at write time).

## Target layout

```text
2ndBrain/
├── AGENTS.md                  rules (single source of truth, ~120 lines)
├── README.md                  what it is, setup, agent install, credits
├── USER_GUIDE.md              how to use it day to day
├── _system/
│   ├── METHOD.md              the concepts above, in one page
│   ├── agent/2ndBrain.agent.md   portable agent definition
│   ├── workflows/
│   │   ├── capture.md         inbox + ingest
│   │   ├── projects.md        kickoff, decisions, close-out to archive
│   │   ├── knowledge.md       writing and maintaining notes
│   │   └── review.md          weekly review + lint
│   └── templates/
│       ├── note.md  project-readme.md  decision-log.md  weekly-review.md
│       └── user/ facts.md preferences.md boundaries.md   (starters)
└── _user/                     private, gitignored except skeleton
    ├── README.md
    ├── facts.md  preferences.md  boundaries.md
    ├── inbox.md
    ├── work/  index.md log.md projects/ areas/ knowledge/ archive/ journal/
    └── life/  index.md log.md projects/ areas/ knowledge/ archive/ journal/
```

The `_user/data/` level is removed (one less folder to think about).

## Changes

### 1. `AGENTS.md` — rewrite, same length
- Keep: purpose, load order, editing rules, query rules, default behavior.
- **Domains section (new):** every task has one active domain, `work` or `life`. Infer it from the request; ask once if unclear. Rules:
  - Read and write only inside the active domain, plus `_user/*.md` and `inbox.md`.
  - Never copy or summarize content from one domain into the other. A cross-domain reference is a bare link, no details.
  - Weekly reviews, indexes and logs are per domain.
  - Check `_user/boundaries.md` before storing anything work-derived.
- **Core loop:** replace Classify/Check/Update/Link/Stop with Capture → Organize → Distill → Express, keeping "search before creating" and "stop when findable".
- **Routing:** PARA table per domain (absorbs `_system/ROUTING.md`).
- **Operations:** ingest (file it, update `index.md`, append to `log.md`), query (read `index.md` first, cite files, say certain/partial/missing), lint (the existing Gap Handling list plus orphan notes, stale index lines, cross-domain leaks).
- **Setup:** on "set up my 2ndBrain", create the private files from `_system/templates/user/` and empty `index.md`/`log.md` per domain. This replaces any setup script.
- Fold in the four useful lines of `_system/interaction-style.md`.

### 2. `_system/` — consolidate (12 files → 12, but no overlap)
- Delete `ROUTING.md`, `interaction-style.md`, `README.md` (its file list moves to `METHOD.md`).
- Merge `project-kickoff.md` + `solution-design.md` → `workflows/projects.md`; add "next action" line and close-out step (extract lessons to `knowledge/`, move folder to `archive/`).
- Merge `research-capture.md` + `knowledge-transfer.md` → `workflows/knowledge.md` with the note rules.
- New `workflows/capture.md` and `workflows/review.md` (review is a short checklist: empty inbox, update project next actions, archive finished work, lint, write the week's journal entry).
- Merge `lesson-learned.md` + `technical-summary.md` → `templates/note.md`; keep `decision-log.md`; add `project-readme.md`, `weekly-review.md`, and `templates/user/*`.
- New `METHOD.md`: one page explaining the table above.

### 3. `_user/` skeleton and `.gitignore`
- Replace `_user/data/**` skeleton with `.gitkeep` files under `_user/work/*` and `_user/life/*`.
- Rewrite the `_user` ignore block for the new paths: ignore everything under `_user/` except `README.md` and the `.gitkeep` files.
- Remove the stale "Work-specific" comment at the end of `.gitignore`.
- Update `_user/README.md` for the new layout.

### 4. Agent definition — `_system/agent/2ndBrain.agent.md`
- Frontmatter limited to the fields both formats accept: `name: 2ndbrain`, `description: ...`. No `tools` (both platforms then inherit all tools), no `model`.
- Body (~20 lines): brain location placeholder `BRAIN_PATH`, "read `BRAIN_PATH/AGENTS.md` and follow it", the domain rule restated in two lines, and the command list (capture, process inbox, start project, find, weekly review, lint).
- No rules duplicated from `AGENTS.md`.

### 5. `README.md` and `USER_GUIDE.md`
- README: layout, three-step setup (clone, open with an agent, say "set up my 2ndBrain"), agent install notes, expanded credits.
- Agent install notes: copy the file to `~/.copilot/agents/2ndBrain.agent.md` (Copilot / VS Code) and `~/.claude/agents/2ndbrain.md` (Claude Code), replace `BRAIN_PATH`. Note that Codex, Cursor and others pick up `AGENTS.md` automatically when the repo is open.
- USER_GUIDE: new structure, work/life rule in plain words, common requests, weekly review.

## Out of scope
- Scripts, binaries, search tooling, Obsidian plugins.
- Syncing or backing up private `_user` content (optional later: point `_user/work` at a separate private location).

## Verification
1. `git status` / `git ls-files` — only public-safe files tracked; create a dummy `_user/work/knowledge/test.md` and `_user/facts.md` and confirm `git check-ignore -v` ignores both, then delete them.
2. `grep -r "_user/data\|ROUTING.md\|interaction-style" .` returns nothing outside `plans/`.
3. Every relative link in tracked Markdown resolves to an existing file; every external credit link loads.
4. Line counts: `AGENTS.md` ≤ ~130, each workflow ≤ ~50.
5. Dry run in a fresh session: "set up my 2ndBrain", "add to inbox: X", "process inbox", "start work project Y", "weekly review for life" — confirm files land in the right domain and that a work note is not surfaced in a life query. Remove the test data afterwards.
6. Copy the agent file to `~/.claude/agents/2ndbrain.md` only with your go-ahead, and confirm it loads.
