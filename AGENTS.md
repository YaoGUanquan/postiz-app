# OpenCode Session Rules

This file defines the required startup and memory-update workflow for OpenCode sessions in this repository.

## Mandatory Startup Checklist

At the beginning of every new session, read these files first:

1. `CLAUDE.md`
2. `docs/opencode/project-memory.md`
3. `docs/opencode/recovery-runbook.md`
4. `docs/opencode/session-log.md`

Then run and review:

- `git status`
- `git branch --show-current`
- `git log --oneline -5`

## Mandatory Session Update Rule

After each meaningful task batch (feature/fix/deploy/config change), append one entry to:

- `docs/opencode/session-log.md`

Use the format exactly:

```md
## YYYY-MM-DD HH:MM UTC

- Branch: <branch>
- Goal: <what this batch did>
- Changes:
  - <file/path and action>
  - <file/path and action>
- Commands Run:
  - `<command>`
  - `<command>`
- Validation:
  - <what passed/failed>
- Next Step:
  - <recommended next action>
```

## Memory File Responsibilities

- `docs/opencode/project-memory.md`
  - Keep architecture, conventions, important paths, and active customization notes current.
- `docs/opencode/recovery-runbook.md`
  - Keep resume/recovery commands accurate and minimal.
- `docs/opencode/session-log.md`
  - Chronological execution log for handoff and crash recovery.

## Secrets and Safety

- Never store secrets/tokens/passwords in memory docs.
- Keep sensitive values in runtime `.env` files outside git whenever possible.
