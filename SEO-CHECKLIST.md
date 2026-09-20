# Woodux SEO/GEO Checklist

Running list, updated as items get done. Check items off in place and commit,
so this stays the single source of truth instead of scattered chat history.

## Done

- [x] Domain redirects fixed: `www.woodux.online` and `woodux.vercel.app` both 308 to `woodux.online`, matching every canonical tag
- [x] `cleanUrls` disabled in `vercel.json` — Vercel no longer fights the `.html` canonical URLs
- [x] Beginner-projects cluster (8 pages) + tool-buying-guide cluster (9 pages) written and live
- [x] Titles shortened sitewide to under 60 characters
- [x] `og:image` / `twitter:card` meta added to all 40 article pages, homepage, guides index
- [x] `BreadcrumbList` schema added to all 40 article pages
- [x] `Organization` + `WebSite` schema added to homepage
- [x] `sitemap.xml`: all 42 URLs have `lastmod`
- [x] Favicon, apple-touch-icon, android icons, `site.webmanifest` generated and wired into all pages
- [x] `og-image.png` generated (branded, matches site palette)
- [x] Vercel Web Analytics installed
- [x] Google Search Console verification file present

## Needs verification (may already be fine — just unconfirmed)

- [ ] Confirm `og-image.png` actually resolves live (was still 404 on production as of the last check, despite being merged to `main` — check the Vercel Deployments tab for a stuck or failed deploy)
- [ ] Confirm favicon renders in an actual browser tab after a hard refresh
- [ ] Run the same canonical-URL indexing check in **Google Search Console** directly — every check so far has been through Bing Webmaster Tools only, and Google doesn't always agree with Bing

## Flagged, not yet done

- [ ] **Tailwind CDN vs. a real build step.** `<script src="https://cdn.tailwindcss.com">` is not meant for production per Tailwind's own docs — can hurt Core Web Vitals. Trade-off against the site's "no build step" design goal; needs a decision, not just a fix.
- [ ] **No images anywhere on the site.** Zero `<img>` tags site-wide. Real gap for a visual craft niche — no Google Images presence, no Pinterest-shareable content. At minimum, a labeled diagram for pages like the lumber-size chart would help.
- [ ] **Third content cluster** (general/authority topics: history of woodworking, benefits, basics, joints) — scoped from keyword data early on, never built.
- [ ] **Deeper internal linking.** The 17 new pages link to each other and to only 3 of the original 23 articles. The other ~20 (sheds, homesteading, furniture, materials) have no links pointing into the new clusters yet.
- [ ] **FAQ schema on individual articles.** Several articles already answer FAQ-style questions in their H2s (dust collectors, table saws, etc.) but don't carry matching schema. Currently only the homepage has `FAQPage` markup.
- [ ] **Privacy policy / terms page.** Not strictly required, but common practice and sometimes expected by affiliate networks.

## Never addressed — real, and usually the biggest lever

- [ ] **Backlinks.** No off-page link-building has happened. For competitive keywords this is typically the single biggest ranking factor, and it's fully untouched.
- [ ] **Actual performance testing.** Everything about Core Web Vitals here has been theoretical. Run PageSpeed Insights or Lighthouse against the live site to get real numbers instead of guessing from the Tailwind CDN concern alone.
