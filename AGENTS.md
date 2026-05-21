# AGENTS.md — Clan World Landing

Repository-level instructions for AI agents and contributors. Re-injected into Claude Code's context every turn — keep terse.

## Canonical File Convention

- `AGENTS.md` is the canonical instruction file. It follows the open `AGENTS.md` standard.
- `CLAUDE.md` is a symlink pointing to `AGENTS.md`. Never rename, replace, or remove `AGENTS.md` in favor of `CLAUDE.md`.

## Scope

This repo contains the standalone marketing landing site for Clan World (formerly `apps/landing` in `clan-world/clan-world-game`). Extracted 2026-05-21 to ship + version + deploy independently of the main game monorepo.

## Branching

Gitflow-light: feature work on `feat/*` branches → PRs to `main`. Tags `v*` on `main` trigger Vercel deploy.

## Release procedure

1. Land all changes on `main`.
2. Bump `package.json` version to the new semver.
3. Tag: `git tag vX.Y.Z && git push origin vX.Y.Z`.
4. The `Deploy to Vercel (tags only)` workflow fires automatically and prebuilds + deploys to production.
5. Verify the deploy in the Vercel dashboard or by visiting the production URL.

If the workflow fails on `Project not found`, the `VERCEL_PROJECT_ID` repo secret is stale — refresh from the Vercel project's General → Project ID.

## Local dev

```bash
npm install
npm run dev    # http://localhost:5173 by default
npm run build  # builds to dist/
```

No tests in this repo. The site is content-driven (lore + landing copy) — no business logic to unit-test. Add Playwright e2e tests in a separate PR if/when content templates emerge that warrant them.

## Stack constraints

- Vite + React 19 + TypeScript. Do not introduce a UI framework (Tailwind, Chakra, Mantine, etc.) — keep the parchment/manuscript visual style under hand-written CSS.
- React Router v7. Two top-level routes today: `/` and `/lore`.
- No backend. All content is statically generated at build time.

## Out of scope

- Game state, on-chain reads, runner logic — those all live in `clan-world/clan-world-game`.
- Convex hooks, wallet connect, Solana ATA — also live in the main game repo.
