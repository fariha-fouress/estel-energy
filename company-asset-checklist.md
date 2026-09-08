# Company Asset Checklist — New Website Build

Everything a company needs to supply before development can finish and the site can go live. Send this as-is to the client; anything they can't provide should be flagged so we either use a placeholder ("We are updating this information, stay tuned!") or commission/source the asset.

---

## 1. Brand identity

- **Primary logo** — PNG or SVG, transparent background, minimum 500px wide. SVG strongly preferred (scales for every screen).
- **Logo variant for dark backgrounds** (white/inverse version) — same format. Used in any future dark-themed surface or social previews.
- **Favicon source** — square PNG or SVG, minimum 512×512px, single recognizable mark (initial or icon, not the full wordmark — it has to be readable at 16px).
- **Brand color** — exact hex code or RGBA value for the primary accent color. If they have an existing brand book, request it.
- **Secondary/accent color** (optional) — hex code for any complementary hue they want used sparingly (tags, eyebrows, decorative elements).
- **Typography preferences** (optional) — if they have brand fonts. Otherwise we default to Google Fonts (Inter + Space Grotesk + JetBrains Mono).
- **Tagline / one-liner** — the company's elevator pitch in one sentence. Used in hero headline and meta descriptions.

## 2. Photography & video

For each of these, **landscape orientation, minimum 1600px wide, high resolution, unwatermarked, licensed for commercial use** (if stock):

- **Hero media** — either:
  - A short looping video (10–30 seconds, .mp4 or .m4v, under 10MB, no audio needed — it auto-plays muted), OR
  - A single hero image showing the company's product/operation in context
- **6× service/capability card images** — one per service or vertical the company offers. These sit behind the cards with a translucent white gradient overlay, so they don't need to be hero-quality, but they should be visually distinct from each other (different scenes, not six photos of the same warehouse).
- **3× principle/values images** — for the about page values section. Can repeat or vary from the service images.
- **1× about page intro image** — establishes what the company does. Wide framing.
- **1× about page values section image** — used alongside the principles heading.
- **1× contact form background image** — soft enough to sit under a translucent overlay. Handshake, office, abstract texture all work.
- **1× brand visual for the homepage "Why us" split section** — often this is just the logo again on a tinted backdrop, but a contextual photo works too.

**If they don't have photography**: we can source from stock libraries (Unsplash for free, Adobe Stock or Getty if licensed visuals are required). Flag if budget for stock is needed.

## 3. Written content

For each section the company needs to provide either final copy or rough notes — anything missing we'll draft and they review.

**Company-wide:**
- Company name (full legal + shortened version for the wordmark)
- Industry / sector
- Year founded (if older entity) OR positioning statement (if newer entity claiming experienced backing)
- Mission / what makes them different in 2–3 sentences

**Home page:**
- Hero headline (one strong sentence — we'll wrap one word in accent color)
- Hero sub-paragraph (2–3 sentences)
- "What we do" lead paragraph (2 sentences)
- 6× service card titles and descriptions (one-line title + 2-line body each)
- "Why us" headline and 1-paragraph explanation

**About page:**
- About lead headline + 2–3 paragraph company story
- 3× guiding principles (title + 2-line description each)
- Generic leadership statement framing experience and backing of stakeholders (no team photos needed unless they have them)

**Services / Products page:**
- For each product or service vertical (typically 3–6 verticals):
  - Vertical name
  - 1-paragraph description
  - 3–5 bullet specifics (specs, certifications, varieties, etc.)
- 6× end-to-end capability descriptions (title + 2-line body each)

**Contact page:**
- Page lead paragraph (what to expect when they submit)
- Form category options (matching the product verticals)

**Footer (every page):**
- Footer tagline (1 sentence summarizing the company)

## 4. Contact information

- **Primary business email** (e.g. `admin@company.com` or `contact@company.com`) — this is what the contact form submissions will land in and what's shown on every page
- **Phone number** (international format with country code)
- **Headquarters address** — street, city, country. If undecided, we use a "stay tuned" placeholder.
- **Trading / business hours** — timezone + open/close times. Same placeholder option if undecided.
- **Social media handles** (optional) — LinkedIn, Instagram, X/Twitter, YouTube. Provide full URLs.

## 5. Legal & compliance

These are linked from the footer on every page. **If the company doesn't have these yet, they'll need to draft them before the bank/regulator/serious client clicks through.**

- **Privacy policy** — what data is collected (the contact form collects name/email/phone/company/message), how it's stored, who it's shared with, retention period. Generators like Termly or iubenda produce compliant boilerplate in 15 minutes.
- **Terms of service / Terms of use** — basic conditions for using the site.
- **Compliance statement** — depends on industry. For a commodity trading firm: KYC/AML stance, sanctions screening policy, trade compliance acknowledgment. For a financial firm: regulatory licenses. For an e-commerce site: refund/return policy.
- **Cookie policy** (only if analytics or marketing trackers are added later — not needed for a purely informational site).

## 6. Domain & hosting decisions (client-side)

These aren't files but they need a decision from the company before launch:

- **Domain name** — do they own it? If yes, who's the registrar (Namecheap, GoDaddy, Cloudflare, etc.) — we'll need access to DNS settings.
- **Email hosting** — who's running their email (Google Workspace, Microsoft 365, Zoho)? The form submission email and `mailto:` links depend on this.
- **Where the site will be hosted** — Vercel, Netlify, Cloudflare Pages, or their own server. Affects how files are deployed.
- **Form submission service** — Formspree, Web3Forms, custom backend? Determines what the contact form does after submit.

## 7. Optional but recommended

- **Open Graph / social share preview image** — 1200×630px image shown when the site link is shared on LinkedIn, WhatsApp, email. Usually the logo on a branded background.
- **Press kit / one-pager PDF** — if the company has marketing collateral, useful for the bank submission package.
- **Existing testimonials or client logos** — if the company already has partners willing to be named, these add credibility. We removed this section for the new-entity positioning but can add it later.
- **Case studies or completed transactions** (anonymized if needed) — useful for a future "Track record" or "Recent deals" page.
- **Team photos and bios** — if/when leadership is ready to be public. Headshots should be square, neutral background, professional.
- **Founding documents / incorporation certificate** — not for the site itself but typically needed alongside the website for bank submissions.

---

## Quick-send version

If the client wants a one-paragraph version to scan, this is the minimum to start:

> Please send us your **logo** (PNG or SVG, transparent background), **brand color** (hex code), **company tagline** (one sentence), **contact email + phone**, **6–8 product/service photos** (landscape, 1600px+ wide), and **rough copy or bullet points** for: home page hero, about story, each product vertical, and contact info. If you don't have **privacy policy / terms / compliance statement** drafted yet, please flag — those need to exist before the site can go live for a serious audience.
