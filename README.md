# Midnight Detailing

A single-page marketing site for **Midnight Detailing** — a luxury car detailing business serving the Brookfield, WI area.

**Precision · Care · Perfection**

## Highlights

- **One file, zero build** — the entire site is `index.html` (plain HTML/CSS with ~50 lines of vanilla JS). No frameworks, no build step, no dependencies to install. Open it in a browser and it works.
- **Interactive pricing** — a Cars / SUVs & Trucks / Large & Vans toggle live-updates prices across all three service tiers.
- **Before/after slider** — drag the divider in the gallery to wipe the polished wheel over the untouched one.
- **Monochrome design system** — true-black palette, Space Grotesk / Inter / IBM Plex Mono type, hairline "shut-line" section dividers, film grain, scroll-driven reveals, and a per-letter animated hero.
- **Conversion-focused** — every CTA funnels to the [Cal.com booking page](https://cal.com/midnight-detailing).
- **Accessible & responsive** — mobile-first (verified at 360 / 768 / 1440 px), WCAG AA contrast, keyboard-focus styles, `prefers-reduced-motion` support, semantic HTML, and LocalBusiness structured data for SEO.

## Project structure

```
index.html              The whole site (markup, styles, and scripts inline)
assets/
  logo/
    logo.png            Circular MD badge (nav)
    lockup.png          Square wordmark lockup (footer)
    favicon.png         64px favicon
  gallery/
    web/                Web-ready JPEGs served by the gallery + before/after slider
    mazda/, mercedes/   Original HEIC photos (gitignored — source material only)
  og/
    og-image.jpg        1200×630 social share preview (Open Graph / Twitter)
```

## Services & pricing

| Service | Cars | SUVs / Trucks | Large Trucks / Vans |
|---|---|---|---|
| Interior Detail | $50 | $70 | $90 |
| Exterior Detail | $60 | $85 | $105 |
| The Midnight Standard (full) | $90 | $120 | $160 |

Add-ons: exterior paint wax +$20 · odor removal +$15 · rain-repellent windshield +$20 · engine bay cleaning +$30.
Referral: 10% off your next detail when someone you refer becomes a customer.

## Editing guide

- **Prices** live in two places that must stay in sync: the default `$` values in the services markup and the `PRICES` object in the `<script>` at the bottom of `index.html`.
- **Gallery photos**: drop web-ready JPEGs into `assets/gallery/web/` and update the `<img>` tags in the `#work` section. Photos display in grayscale and reveal color on hover — no pre-processing needed. Note: iPhone HEIC files must be converted to JPEG *and* have their EXIF orientation stripped, or browsers will show them rotated.
- **Booking link**: search for `cal.com/midnight-detailing` (nav, hero, mega CTA, footer, structured data).
- **Contact info**: phone and email appear in the `#contact` grid, the footer "Reach us" column, and the JSON-LD block in `<head>`.
- **Instagram**: the footer link is a `href="#"` placeholder — marked with a `TODO` comment.

## Deploying

Any static host works (GitHub Pages, Netlify, Vercel, Cloudflare Pages). Two things to do at deploy time:

1. Make `og:image` / `twitter:image` absolute URLs (e.g. `https://yourdomain.com/assets/og/og-image.jpg`) — an HTML comment in `<head>` marks the spot.
2. The Google Fonts stylesheet is the site's only external dependency; system font fallbacks keep the page fully legible if it's unavailable.

## The team

Aryav Agarwal · Rohit Shetty · Ayush Damodar

---

Website built by [@shiva-dev-229](https://github.com/shiva-dev-229)
