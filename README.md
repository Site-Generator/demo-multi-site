# Demo Multi Club — site content

This repo holds **Demo Multi Club's** website content only: `club.json` and
`images/`. Edit them via [Pages CMS](https://pagescms.org) (see `.pages.yml`)
or directly on GitHub.

**Do not hand-edit anything under `generator/`.** That folder is a synced
copy of the shared [club-site-generator-core](../club-site-generator-core)
engine, pulled in via `git subtree`. Engine bugs/features are fixed there and
propagated here — a local edit under `generator/` risks a conflict the next
time that sync runs.

## Building locally

```bash
npm --prefix generator install
CLUB_DATA_DIR=.. CLUB_SLUG=demo-multi node generator/build.js
npm --prefix generator run preview   # serves generator/dist/ via wrangler dev
```

## Deploying

This repo's Cloudflare Workers project is configured with:
- Root directory: `generator/`
- Build variables: `CLUB_SLUG=demo-multi`, `CLUB_DATA_DIR=..`
- Build command: `node build.js`
- Deploy command: `npm run deploy`
