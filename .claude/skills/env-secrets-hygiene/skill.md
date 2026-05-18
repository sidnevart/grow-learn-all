---
name: env-secrets-hygiene
description: Root .env and secret-handling workflow for this repository. Use whenever you add, rotate, document, or consume secrets, API tokens, tunnel URLs, database URLs, or VITE-prefixed public env values.
---

# Env Secrets Hygiene

Use this skill whenever configuration values or secrets are involved.

## Rules

- Real secrets live only in the root `.env`.
- `.env.example` contains placeholders or safe demo defaults only.
- Backend-only secrets must never be exposed to the frontend.
- Frontend may receive only explicitly public `VITE_*` values.
- Never print, log, or paste secret values into source files, tests, screenshots, or docs.

## Workflow

1. Add or update the real value in root `.env`.
2. Add the matching placeholder to `.env.example`.
3. If the frontend needs the value, create a `VITE_*` public counterpart instead of leaking the private variable directly.
4. Update any config loader, docs, and startup commands that depend on the variable.
5. Verify the secret is ignored by `.gitignore`.

## Typical Variables

- Private:
  - `TELEGRAM_BOT_TOKEN`
  - `JWT_SECRET`
  - `DATABASE_URL`
  - `REDIS_URL`
- Public:
  - `VITE_API_BASE_URL`
  - `VITE_MINI_APP_PUBLIC_URL`
  - `VITE_TELEGRAM_BOT_USERNAME`
  - `VITE_YANDEX_MAPS_API_KEY`

## Anti-Patterns

- Using backend secrets in `VITE_*`.
- Committing a filled `.env.example`.
- Logging tokens to debug auth problems.
- Forgetting to restart the relevant process after `.env` changes.

