# BDX AI HUB

A responsive, free-first AI tool discovery and comparison website. Static HTML, CSS and JavaScript; no build step, paid API or database is required for the included functionality.

## Features

- Curated AI tool directory with provider links and plan links
- Search across names, categories, tags and use cases
- Category navigation and sorting
- Task-based recommendation shortlist
- Detailed tool profiles and side-by-side comparison (up to 3 tools)
- Saved tools using browser local storage
- PWA manifest and offline static-asset caching
- Browser notification permission + local test notification (not background push)
- SEO metadata, privacy/about pages, security headers and domain configuration helper
- Responsive layout, keyboard search shortcut (`Ctrl/⌘ + K`) and reduced-motion support

## Run locally

Requires Python 3:

```powershell
py -m http.server 8000
```

Open `http://localhost:8000`.

## Validate

```powershell
py tools/validate.py
node --check app.js
```

## Configure a custom domain

See [DEPLOYMENT.md](DEPLOYMENT.md). For Cloudflare Pages, the output directory is the repository root (`.`) and no compile step is needed. Once you have registered a domain, run:

```powershell
py tools/configure-domain.py --domain your-domain.com
```

## Important notes

- “Free” means a free plan/access path or open-source option is listed; it does not mean unlimited use.
- Free-plan quotas, models, commercial rights, supported countries and pricing change. Confirm terms on the official provider pages.
- The site is an independent directory and is not affiliated with the tools listed.
- The current release has no backend, login, cloud sync, analytics or ad scripts. User favourites/compares are local to one browser.
- Notification support is a local browser-permission/test feature only. No server push is configured.
- No domain has been purchased or connected and no public deployment has been performed.

## Project structure

```text
BDX-AI-Hub/
├── index.html
├── styles.css
├── app.js
├── data/tools.json
├── assets/
├── privacy.html
├── about.html
├── 404.html
├── manifest.webmanifest
├── service-worker.js
├── _headers
├── robots.txt
├── DEPLOYMENT.md
├── tools/
└── tests/
```
