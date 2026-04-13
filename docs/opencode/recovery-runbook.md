# Recovery Runbook (OpenCode)

## 1) Resume Context Fast

From repo root:

```bash
git status
git branch --show-current
git log --oneline -5
```

Then read:

- `docs/opencode/project-memory.md`
- `CLAUDE.md`

## 2) Re-open Current Custom Work

```bash
git checkout dev/openai-baseurl
git status
```

Inspect customization files:

- `libraries/nestjs-libraries/src/openai/openai.service.ts`
- `libraries/nestjs-libraries/src/database/prisma/autopost/autopost.service.ts`
- `libraries/nestjs-libraries/src/agent/agent.graph.service.ts`
- `libraries/nestjs-libraries/src/agent/agent.graph.insert.service.ts`
- `.env.example`

## 3) Typical Dev Validation

Use root-level commands only:

```bash
pnpm -v
pnpm install
pnpm run build
```

If needed:

```bash
pnpm run test
```

## 4) Push Workflow

```bash
git add .
git commit -m "feat: support OPENAI_BASE_URL for OpenAI-compatible endpoints"
git push -u origin dev/openai-baseurl
```

## 5) Rollback Strategy

- Hard rollback by branch:

```bash
git checkout <stable-branch>
git pull
```

- Selective rollback by file:

```bash
git checkout -- <path>
```

## 6) Session Handoff Template

When starting a new conversation, share:

1. Current branch name.
2. Target goal (example: continue OpenAI base URL customization).
3. `git status` output.
4. Any runtime/deployment errors.
