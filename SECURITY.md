# Security notes

- The site is static and does not process account credentials or payments.
- External destinations are opened in a new tab with `rel="noopener noreferrer"`.
- Dynamic catalogue text is HTML-escaped before rendering.
- Provider URLs in `data/tools.json` are editorial data; review them before publishing changes.
- Cloudflare Pages `_headers` applies a restrictive Content Security Policy and common browser security headers.
- Local storage is not encrypted. Do not store secrets in saved-tool metadata or browser preferences.
- Do not add API keys to `app.js`, `data/tools.json` or any public frontend file. A real AI API integration requires a backend/worker that protects credentials and validates requests.
- Before adding user submissions, accounts, push notifications or analytics, write a data-retention policy and implement server-side validation, access control and abuse protection.
