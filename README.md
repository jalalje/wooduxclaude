# Woodux — Static Affiliate Site

Woodux is a pure static HTML site. There is no build step, no Node.js runtime, no database, and no environment variables required.

Live at: **https://woodux.online** (custom domain — not the `.vercel.app` subdomain; `www.woodux.online` and `woodux.vercel.app` both 308-redirect to it)

---

## Deploy to Vercel (recommended)

### Option A — GitHub import (easiest)

1. Push this folder to a GitHub repository.
2. Go to [vercel.com/new](https://vercel.com/new) and import the repository.
3. On the **Configure Project** screen:
   - **Framework Preset:** select **Other** (not Next.js, not Create React App)
   - **Build Command:** leave blank (delete any pre-filled value)
   - **Output Directory:** leave blank (Vercel serves from the root)
   - **Install Command:** leave blank
4. Click **Deploy**.

Vercel detects `vercel.json` automatically and applies all routing and header rules, including `cleanUrls: false` — this is intentional. Every canonical tag, sitemap entry, and internal link on the site uses the `.html` extension; `cleanUrls: true` will make Vercel auto-redirect away from those URLs and break every canonical tag on the site. Leave it `false`.

### Option B — Vercel CLI

```bash
npm i -g vercel
cd woodux-deploy
vercel --prod
```

When prompted:
- Set up and deploy? **Y**
- Which scope? your account
- Link to existing project? **N** (first time) or **Y** if re-deploying
- Framework? **Other**
- Build command? **(leave blank, press Enter)**
- Output directory? **(leave blank, press Enter)**

---

## No environment variables required

This site has zero runtime dependencies. No `.env` file is needed. Nothing to configure in the Vercel dashboard under Settings → Environment Variables.

---

## Site structure

```
woodux-deploy/
├── index.html                  # Homepage
├── articles/
│   ├── index.html              # All guides hub
│   └── *.html                  # 40 individual guide pages
├── sitemap.xml                 # Full sitemap, 42 URLs, all with lastmod
├── robots.txt                  # Allows all crawlers, points to sitemap
├── llms.txt                    # AI/LLM crawler index
├── vercel.json                 # Routing, rewrites, security headers, cache rules
├── favicon.ico, favicon-16x16.png, favicon-32x32.png
├── apple-touch-icon.png, android-chrome-192x192.png, android-chrome-512x512.png
├── site.webmanifest
├── og-image.png                # Social share image, 1200x630
├── .gitignore
└── README.md
```

---

## After deployment

1. **Confirm the sitemap** is reachable at `https://woodux.online/sitemap.xml` and submitted in both Google Search Console and Bing Webmaster Tools.
2. **Confirm `og-image.png` resolves** at `https://woodux.online/og-image.png` — if it 404s despite a successful Vercel deployment, check the Deployments tab for the exact deployment and open its unique `*.vercel.app` URL directly to see whether the file is present on that build output before assuming it's a code problem.
3. If you ever add another custom domain, keep exactly one as Production in Vercel → Settings → Domains, with every other domain set to redirect to it — matching canonical tags to actual server behavior is what keeps search engines from treating the site as duplicate content.

---

## Affiliate links

Affiliate links currently point to `go.saidelmardi.com` (ClickBank). No changes needed after deployment — they are hardcoded in the HTML files. If these are ever replaced with different affiliate programs, update the links directly in each article's body and in the homepage's collection cards.

---

## Adding new pages

1. Create a new `.html` file in `articles/`, using the exact head/header/footer pattern from any existing article file — including the canonical tag, `og:image`/`twitter:card` meta, `BreadcrumbList` JSON-LD, and favicon links.
2. Add the new URL to `sitemap.xml` with a `lastmod` date.
3. Link to it from `articles/index.html` (add it to the right topic section) and from at least one existing, related article.
4. Redeploy (push to GitHub, Vercel deploys automatically).
