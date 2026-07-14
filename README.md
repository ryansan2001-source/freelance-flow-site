# freelance-flow-site

The marketing + support site for **Freelance Flow** — a private, on-device tax-savings
tracker for freelancers. Plain static HTML/CSS: no build step, no framework. Hosted free
on GitHub Pages.

**Pricing (as of the StoreKit paywall added July 2026):** 7-day free trial, then $4.99/mo
or $29.99/yr, or a one-time $59.99 Lifetime purchase — no free tier. See
`../Freelance Finance/monetization-plan.md` for the full reasoning. `index.html` was
updated to match; if you change pricing again, update the 3 spots in `index.html` that
mention price (`pricing-note` under the hero, the "why" comparison list, and the
signup section's `pricing-note`).

## Files
```
freelance-flow-site/
  index.html            Landing page (hero, features, screenshots, why, email capture)
  support.html          Support page (contact + FAQ) — linked from the nav and App Store
  assets/               App icon + web-optimized screenshots used by both pages
  screenshots-appstore/ Full-resolution 1320×2868 (6.9") captures for App Store Connect
  .nojekyll             Tells GitHub Pages to serve files as-is (don't run Jekyll)
```

## App Store link
The "Download on the App Store" buttons point to the live listing:
`https://apps.apple.com/us/app/freelance-flow-tax-income/id6787905548`.

## Screenshots

`assets/screen-*.png` are downscaled (640px wide) versions for the website.
`screenshots-appstore/*.png` are the full **1320×2868 (6.9" iPhone)** captures — the size
App Store Connect requires. Upload those directly to App Store Connect; if you don't
provide smaller sizes, App Store Connect scales the 6.9" set down automatically.

To re-capture later: the app has a DEBUG-only demo-data seeder. Build & run on a 6.9"
simulator (e.g. iPhone 17 Pro Max) with the `-seedDemoData` launch argument, set a clean
status bar (`xcrun simctl status_bar <udid> override --time 9:41 ...`), and grab each screen
with `xcrun simctl io <udid> screenshot`.

## Publish to GitHub Pages

Create an empty repo named `freelance-flow-site` on github.com first (no README), then run
these from inside this folder:

```sh
git init
git add .
git commit -m "Freelance Flow landing + support site"
git branch -M main
git remote add origin https://github.com/ryansan2001-source/freelance-flow-site.git
git push -u origin main
```

Then on github.com: **Settings → Pages → Build and deployment → Source: Deploy from a
branch → Branch: `main` / `/ (root)` → Save.** Your site goes live in ~1 minute at:

```
https://ryansan2001-source.github.io/freelance-flow-site/
```

## Updating later
```sh
git add .
git commit -m "Update site"
git push
```
GitHub redeploys automatically within a minute.

## Use as your App Store Connect URLs
- **Marketing URL:** `https://ryansan2001-source.github.io/freelance-flow-site/`
- **Support URL:** `https://ryansan2001-source.github.io/freelance-flow-site/support.html`

## Custom domain (optional, later)
Buy a domain, add a `CNAME` file containing just the domain, and point the domain's DNS at
GitHub Pages. Not needed for launch — the `github.io` URL is fine.
