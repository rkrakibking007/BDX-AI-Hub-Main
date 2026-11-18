# Deploy BDX AI HUB with a custom domain

This project is a static website. It does not need a paid server or database for the features included in this release. The recommended route is **Cloudflare Pages + your own domain**. The domain registration/renewal is separate and may cost money; static Pages hosting can fit within Cloudflare's Free plan limits.

## 1. Preview locally

From the project root, run:

```powershell
py -m http.server 8000
```

Open `http://localhost:8000`. Do not open `index.html` directly with `file://`; the catalogue JSON and service worker require HTTP/HTTPS.

## 2. Deploy to Cloudflare Pages

1. Create a GitHub repository and upload the complete contents of this project folder.
2. In Cloudflare, open **Workers & Pages → Create → Pages → Connect to Git**.
3. Select the repository and use these settings:
   - Framework preset: **None**
   - Build command: leave blank (or use `exit 0` if the setup flow requires a command)
   - Build output directory: `.`
   - Root directory: `/` (the repository root)
4. Deploy. Confirm the temporary `https://<project-name>.pages.dev` URL works before attaching your domain.

Direct Upload is also possible from the Cloudflare Pages dashboard; upload the contents of the project folder, not the parent folder.

## 3. Connect your custom domain

1. Buy/register the domain through a registrar of your choice. The domain is not included in this ZIP.
2. In Cloudflare, add the domain as a zone if you want to use the apex/root domain such as `bdxaihub.com`.
3. Open **Workers & Pages → your Pages project → Custom domains → Set up a domain** and enter the domain.
4. For an apex domain, follow Cloudflare's instructions to point the domain's nameservers to Cloudflare. Cloudflare then provisions the DNS record and TLS certificate.
5. For a subdomain (for example `www.example.com`) using external DNS, first add it through the Pages **Custom domains** flow, then create the required CNAME pointing to `<project-name>.pages.dev`. Do not only create a DNS CNAME without associating the hostname with the Pages project.
6. Wait for the dashboard to show the domain as active, then test HTTPS and both the root and `www` hostname if you use them.

Exact dashboard labels can change. Follow the current Cloudflare Pages custom-domain instructions linked below.

## 4. Configure SEO for the final domain

After deciding the exact hostname, run this from the project root:

```powershell
py tools/configure-domain.py --domain bdxaihub.com
```

Replace `bdxaihub.com` with the domain you actually own. This generates the canonical URL and Open Graph URL in `index.html`, and writes `sitemap.xml`, `robots.txt` and `site-domain.txt`. Commit and redeploy those changes.

Do not run this with a domain you do not control. Do not use a temporary Pages URL as the permanent canonical domain.

## 5. Pre-launch checklist

- [ ] Replace the example domain in the domain configuration command with your registered domain.
- [ ] Confirm the Cloudflare Pages custom domain shows as active and HTTPS loads.
- [ ] Test search, category filters, task recommendations, saved tools and comparison on desktop and mobile.
- [ ] Test PWA install and offline refresh on supported browsers.
- [ ] Confirm outbound tool and pricing links open the intended official providers.
- [ ] Review tool free-plan details and commercial-use terms before publishing any promotional claim.
- [ ] Add a real support/contact channel before inviting public feedback.

## Current boundaries

- No account/login, cloud sync, backend database, admin panel or remote notification service is included.
- Saved tools and comparison choices live only in the current browser's local storage.
- The bell panel can request browser notification permission and send a local test notification; it does not send background push alerts.
- AI provider quotas and prices are not live-synced. The directory intentionally avoids promising exact quotas because providers change their plans often.
- This project has not been deployed to a public URL. You must connect your own GitHub/Cloudflare account and domain to publish it.
