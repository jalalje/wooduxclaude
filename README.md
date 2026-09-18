# Woodux — Static Affiliate Site

Woodux is a pure static HTML site. There is no build step, no Node.js runtime, no database, and no environment variables required.

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

Vercel detects `vercel.json` automatically and applies all routing and header rules.

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
├── index.html              # Homepage
├── articles/
│   ├── index.html          # All guides hub
│   └── *.html              # 23 individual guide pages
├── sitemap.xml             # Full sitemap for all 25 pages
├── robots.txt              # Allows all crawlers, points to sitemap
├── llms.txt                # AI/LLM crawler index
├── vercel.json             # Routing, rewrites, security headers, cache rules
├── .gitignore
└── README.md
```

---

## After deployment

1. **Submit your sitemap** to Google Search Console:
   `https://woodux.vercel.app/sitemap.xml`
2. **Check your custom domain** in Vercel → Settings → Domains if you want to move off the `.vercel.app` subdomain.
3. **Update `sitemap.xml` and canonical URLs** if you switch to a custom domain — replace every instance of `woodux.vercel.app` with your new domain.

---

## Affiliate links

All four affiliate links point to `go.saidelmardi.com`. No changes needed after deployment — they are hardcoded in the HTML files.

---

## Adding new pages

1. Create a new `.html` file in `articles/`.
2. Copy the header/footer pattern from any existing article file.
3. Add the new URL to `sitemap.xml`.
4. Link to it from `articles/index.html` and at least one existing article.
5. Redeploy (push to GitHub, Vercel deploys automatically).
