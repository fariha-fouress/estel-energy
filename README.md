# Estel Energy — Website

Static marketing site for Estel Energy, a global import-export firm trading agricultural products, polymers, cosmetics, and metals.

## Stack

Plain HTML / CSS / JavaScript. No build step, no framework, no package manager. Every page is a standalone file and can be opened directly in a browser or served from any static host (Vercel, Netlify, Cloudflare Pages, GitHub Pages, S3, etc.).

## Pages

| File | Purpose |
| --- | --- |
| `index.html` | Home — hero, service preview, why-us split, stats band, CTA |
| `about.html` | About — company story, three principles, stats, leadership statement |
| `services.html` | Products — four verticals (Agro, Polymers, Cosmetics, Metals), end-to-end capabilities |
| `careers.html` | Careers — Zoho Recruit embed for open roles |
| `contact.html` | Contact — form + trade desk info |
| `styles.css` | All site styles — design tokens, layout primitives, components, responsive rules |
| `script.js` | Reveal animations, stat counters, mobile menu, contact form mock, card spotlight |

## Design system

- **Brand color:** `#12A7A4` (teal) with `#7B6FA6` (muted purple) as secondary accent
- **Fonts:** Inter (body), Space Grotesk (display), JetBrains Mono (eyebrows / captions) — all via Google Fonts
- **Radius:** 18px cards, 10px buttons
- **Breakpoints:** 980px (hero stacks, nav becomes hamburger), 880px (grids collapse), 540px (typography shrinks)

Design tokens live at the top of `styles.css` as CSS custom properties — change them there to re-theme the whole site.

## Third-party integrations

- **Zoho Recruit** embed on `careers.html` — pulls open roles from `https://estel-energy.zohorecruit.com` via Zoho's JS widget
- **Google Fonts** — Inter + Space Grotesk + JetBrains Mono loaded via `<link>` in every page's head

## Known TODOs before production

- Contact form is a client-side mock — wire up Formspree/Web3Forms/backend so submissions actually reach `admin@estel-energy.com`
- Footer `Privacy`, `Terms`, `Compliance` links point to `#` — need actual policy pages
- Add Open Graph / social preview meta tags for LinkedIn/WhatsApp shares
- Compress the hero video (`Diagonaltrucks.m4v`) and PNGs for faster load
- Add favicon variants (apple-touch-icon, favicon.ico) alongside `estellogo.png`

## Local development

Because there's no build step, just open `index.html` in a browser — or serve the folder with any static server, e.g.:

```bash
# Python 3
python -m http.server 8000

# Node
npx serve .
```

The Zoho embed on `careers.html` only renders when served over http(s), not from `file://`.

## Deployment

Recommended: connect this repo to **Vercel** or **Cloudflare Pages** — both auto-deploy on every push to `main`, provision SSL, and serve via CDN with no configuration.

## Docs in this repo

- `website-replication-prompt.md` — reusable AI prompt to spin up a parallel site for a different company
- `company-asset-checklist.md` — everything a company needs to supply before we build them a similar site
