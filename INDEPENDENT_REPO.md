# iFarted — Independent Repo

**Version:** v0.14.0-alpha (Final v1.0 Alpha scaffold)
**Repo:** https://github.com/lin2mm/testing *(placeholder name — will be renamed to `lin2mm/ifarted`)*
**Date:** 2026-09-11

> 💨 Send a friend exactly one thing: **"I farted."** Notification IS the message. No inbox, no feed.

This is the **standalone iFarted monorepo** — server + web + mobile + shared contracts + docs.
It contains **only iFarted**: no UDL book payload, no dev-session artifacts, no sandbox-platform references.

## Provenance

Imported from `lin2mm/udlbook` branch `ifarted` @ `78699b7`
("Remove all platform references — replace with ifarted clean branches"):

- `apps/` (73 files) + `packages/contracts/` (2 files) — copied verbatim
- 14 root docs (`README_v4.md` promoted to `README.md`, `README_v4.md` kept)
- Editor configs (`.editorconfig`, `.eslintrc.cjs`, `.prettierrc.cjs`, `.prettierignore`)
- 4 remaining platform mentions in `SHARE.md` / `SHARE_CLEAN.md` sanitized to neutral wording
- New in this repo: `package.json` (npm workspaces), `.gitignore`, `LICENSE` (MIT),
  `tsconfig.json` (base), `.nvmrc`, `docker-compose.yml`, `CHANGELOG.md`, this file

**101 files total.** Tags `v0.13.0-alpha` + `v0.14.0-alpha` mirror the source branch tags.

## Structure

```
apps/server/     Bun + Hono + SQLite relay → Expo Push API (13 endpoints, API_DOCS.md, SECURITY.md)
apps/web/        Vite React standalone web client + PWA (port 5174)
apps/mobile/     Expo (React Native + TS) client, 7 screens (APP_REVIEW.md, STORE_CHECKLIST.md)
packages/contracts/  Shared API types (@ifarted/contracts)
*.md             README (v4), PRIVACY, TERMS, DEPLOYMENT(+CHECKLIST), CONTRIBUTING,
                 ROADMAP, RELEASE_NOTES(+v11/v13), SHARE(+CLEAN), IMPORT_NOTES
docker-compose.yml   One-command API server (see below)
```

## Quickstart

```bash
git clone https://github.com/lin2mm/testing.git ifarted
cd ifarted

# API server (Bun 1.4+ recommended; Node 20+ also works via tsx)
cd apps/server && cp .env.example .env
bun install && bun src/index.ts
# → http://localhost:3000/health
# → http://localhost:3000/admin.html?key=YOUR_ADMIN_KEY

# ...or with Docker Compose (from repo root)
docker compose up --build
# → http://localhost:3000/health

# Web client (new terminal, repo root)
npm install
npm run dev:web
# → http://localhost:5174

# Mobile (new terminal; Expo manages its own tree, intentionally NOT in npm workspaces)
cd apps/mobile && npm install && npx expo start
```

Details: `apps/server/README.md`, `apps/mobile/README.md`, `DEPLOYMENT.md`,
`DEPLOYMENT_CHECKLIST_v1.md`, `apps/server/API_DOCS.md`.

## Intentionally excluded (not iFarted runtime)

- UDL book website + book payload (`src/`, `Notebooks/`, `Slides/`, PDFs, …) — stayed in `lin2mm/udlbook`
- `src/components/IFarted/` (2 files) — UDL-site demo section, stayed in source branch
- `memory-bank/`, `.clinerules/` — dev-session planning notes, stayed in source branch
- Original `LICENSE` (UDL book) — replaced by iFarted MIT `LICENSE` in this repo

Historical docs (`IMPORT_NOTES.md`, `SHARE*.md`, `RELEASE_NOTES*.md`) still mention the
`udlbook` origin — that is accurate history, not a dependency: this repo builds and runs alone.

## Notes

- Root `package.json` workspaces: `apps/server`, `apps/web`, `packages/contracts`.
  `apps/mobile` (Expo) is intentionally outside npm workspaces — install/run it separately.
- Legal docs (`PRIVACY.md`, `TERMS.md`) are alpha templates — finalize + host at
  `https://ifarted.app/privacy` and `https://ifarted.app/terms` before store submission.
- After GitHub rename `testing` → `ifarted`, update the clone URL above
  (`https://github.com/lin2mm/ifarted.git`); no code changes needed.
