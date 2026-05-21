# Clan World: Ælder Whispers — Landing & Chronicle

Marketing site for Clan World, themed as an illuminated manuscript. Two pages:

- **`/`** — landing folio: hero map, premise, demo hook, codex of powers (sponsor tech), tales of emergent behaviour, path to the chronicle
- **`/lore`** — the chronicle: lore (4 chapters) + game rules (9 sections), combined as a single long scroll

Repo history: extracted out of `clan-world/clan-world-game` (the monorepo) on 2026-05-21 to ship + version + deploy independently.

## Running locally

```bash
npm install
npm run dev
```

Production build + preview:

```bash
npm run build
npm run preview
```

## Stack

- Vite + React 19 + TypeScript
- React Router (`/` and `/lore`)
- Plain CSS with custom properties — no Tailwind, no UI libraries

## Deploy

Production deploys fire on `v*` tag push via `.github/workflows/deploy-prod.yml` → Vercel prebuilt deploy. See AGENTS.md for the tag-and-release procedure.

Requires GitHub repo secrets:
- `VERCEL_TOKEN` — Vercel personal access token
- `VERCEL_ORG_ID` — team id (`team_...`)
- `VERCEL_PROJECT_ID` — the Vercel project for this landing site

## Versioning

Versions are simple semver tags `vX.Y.Z`. Bump the `package.json` version on each release; the CI workflow stamps `VITE_APP_VERSION` from `github.ref_name` into the build for parity with the main app.
