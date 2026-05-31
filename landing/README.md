# The Adventurer's Atlas — public landing site

Public download page + GitHub Releases for **The Adventurer's Atlas**.

- **Live site:** https://daemon-ic.github.io/the-adventurers-atlas-public-landing/
- **Installers:** [Releases](https://github.com/daemon-ic/the-adventurers-atlas-public-landing/releases)

Application source lives in a **private** repo. This repo is updated automatically by the private repo's Release workflow (`sync-landing-site` + `publish-public` jobs).

## One-time setup (private app repo)

1. Create a fine-grained PAT with **Contents: Read and write** on **this** repo only.
2. In the **private** app repo → **Settings → Secrets → Actions**, add:
   - `PUBLIC_REPO_TOKEN` = that PAT
3. In **this** repo → **Settings → Pages → Build and deployment → Source:** GitHub Actions.
4. Bootstrap (first time only): push the contents of `landing/` from the private repo to this repo's default branch, **or** run the private Release workflow once (it syncs `landing/` here after building).

## What gets synced each release

| Path | Purpose |
|------|---------|
| `docs/` | GitHub Pages site (download buttons via Releases API) |
| `.github/workflows/pages.yml` | Deploy Pages on push |

Installers (`.dmg` / `.exe`) are **not** committed — they are uploaded to **GitHub Releases** on this repo by the private workflow.
