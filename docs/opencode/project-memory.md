# Project Memory (Postiz)

## Repository

- Upstream project: Postiz monorepo.
- Fork owner: `YaoGUanquan`.
- Default local path used in current session: `/home/ubuntu/postiz-app-custom`.

## Monorepo Structure

- `apps/backend`: NestJS API.
- `apps/orchestrator`: NestJS Temporal workers/workflows.
- `apps/frontend`: Next.js frontend.
- `libraries/*`: shared services, helpers, DTOs, UI packages.

## Tech Stack

- Workspace: `pnpm` (only package manager to use).
- Runtime core: Next.js + NestJS + Prisma + PostgreSQL + Redis + Temporal.
- Deployment commonly uses Docker Compose.

## Code Conventions (from project guidance)

- Use only `pnpm` commands.
- Backend layering: Controller -> Service -> Repository.
- Frontend data fetching: prefer SWR via `useFetch` helper.
- Run linting from repo root.

## Active Customization (current session)

Branch: `dev/openai-baseurl`

Goal: support OpenAI-compatible endpoints via `OPENAI_BASE_URL`.

Files changed:

- `libraries/nestjs-libraries/src/openai/openai.service.ts`
- `libraries/nestjs-libraries/src/database/prisma/autopost/autopost.service.ts`
- `libraries/nestjs-libraries/src/agent/agent.graph.service.ts`
- `libraries/nestjs-libraries/src/agent/agent.graph.insert.service.ts`
- `.env.example`

Change details:

- Keep existing `OPENAI_API_KEY` behavior.
- Add optional `OPENAI_BASE_URL` support.
- For OpenAI SDK usage: pass `baseURL` when env var exists.
- For LangChain OpenAI wrappers: pass `configuration.baseURL` when env var exists.

## Environment Variables Relevant to AI

- `OPENAI_API_KEY`: required for AI calls.
- `OPENAI_BASE_URL`: optional OpenAI-compatible API endpoint (usually ends with `/v1`).

## Notes for Continuity

- Avoid committing real secrets into repository files.
- Keep deployment secrets in runtime `.env` outside git.
- If adding more AI providers later, centralize client creation to reduce duplicated config.
