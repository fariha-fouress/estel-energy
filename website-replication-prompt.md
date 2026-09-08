# AI Prompt — Replicate this website for a different company

Paste the prompt below into a fresh AI coding session (Claude, ChatGPT, Cursor, etc.). Fill in the bracketed `[VARIABLES]` at the top with your company's details before submitting. The AI will build a four-page static site (`index.html`, `about.html`, `services.html`, `contact.html`, plus `styles.css` and `script.js`) matching the structure, design system, and interaction patterns described below.

---

## PROMPT START

You are a senior product designer + frontend engineer. Build a four-page static marketing website (vanilla HTML/CSS/JS, no frameworks, no build step) for the company described in the brand brief below. Match the design system, page structure, and content patterns specified — but write the actual copy fresh for this company. Output six files in a single directory: `index.html`, `about.html`, `services.html`, `contact.html`, `styles.css`, `script.js`. All images are referenced relatively (`./image.png`) and assumed to exist — write `onerror` fallbacks on every `<img>` so missing images render as labeled placeholder frames instead of broken icons.

### 1 — Brand brief (fill these in)

- Company name: `[COMPANY NAME]` (used in titles, header wordmark, footer)
- One-word or two-word version for compact wordmark: `[SHORT NAME]` + `[ACCENT WORD]` (the accent word gets the brand color treatment in the header/footer wordmark)
- Industry / what they do in one sentence: `[ONE-LINER]`
- Brand positioning: `[NEW ENTITY / ESTABLISHED PLAYER / BOUTIQUE / SCALE LEADER]` — adjust copy tone accordingly. If "new entity backed by experienced stakeholders", lean on experience/backing language and avoid claiming historical client/shipment numbers
- Primary brand color (hex or rgba): `[#XXXXXX]`
- Secondary accent color (optional): `[#XXXXXX]` — a muted contrast hue
- Product/service verticals (typically 3–6): `[VERTICAL 1, VERTICAL 2, VERTICAL 3, ...]`
- For each vertical, a 1–2 sentence description and 3–5 bullet specifics
- Six end-to-end capability cards (e.g. shipping, logistics, sourcing, QA, distribution, compliance — adapt to industry)
- Contact email: `[admin@company.com]`
- Contact phone: `[+1 (XXX) XXX-XXXX]`
- Headquarters: `[CITY, COUNTRY]` or "We are updating this information, stay tuned!" if undecided
- Three guiding principles for the about page (e.g. quality, timeliness, partnership)
- Three stats for the stats band (avoid historical claims if positioning is "new entity"; use stakeholder experience years, vertical count, response time instead)
- Logo file path: `./[companylogo].png`
- Hero media: either a video file `./[hero].m4v` or hero image `./[hero].png`

### 2 — Design system

**Tokens (define as CSS custom properties on `:root`):**

```css
--bg-0: #FFFFFF;       /* page background */
--bg-1: #F7FAFC;       /* subtle off-white for bands */
--bg-2: #ECF3F7;       /* slightly deeper neutral */
--surface: #FFFFFF;    /* card surfaces */
--text: #0F1B22;       /* primary text */
--text-muted: #4A5965; /* body text */
--text-dim: #7A8894;   /* tertiary */
--border: #E1E8ED;
--accent: [BRAND PRIMARY];           /* main accent — buttons, links, glow */
--accent-deep: [DARKER SHADE];       /* hover states */
--accent-2: [SECONDARY ACCENT];      /* used sparingly for variety — tags, eyebrows */
--accent-glow: [RGBA with low alpha of accent]; /* for soft shadows/glows */
--radius: 18px;
--radius-sm: 10px;
--font-display: 'Space Grotesk', system-ui, sans-serif;
--font-body: 'Inter', system-ui, sans-serif;
--font-mono: 'JetBrains Mono', monospace;
```

Pull all three fonts from Google Fonts via `<link>` in every page's `<head>`.

**Layout primitives:**
- `.container` — max-width 1200px, horizontal padding 24px, centered
- `.section` — vertical padding 96px (clamp down to 56px on mobile)
- `.grid.grid-3` — three-column grid with `minmax(0, 1fr)`, gap 24px, collapses to single column below 880px
- `.card` — radius 18px, padding 36px, light gradient background, soft shadow, top-left card number in mono font, icon, title, body. Cards support an inline `background: linear-gradient(180deg, rgba(255,255,255,0.88) 0%, rgba(236,243,247,0.88) 100%), url('./IMAGE.png') center / cover no-repeat;` recipe for layered photo backgrounds.

**Header wordmark:**
- Logo image (height 54px desktop, 42px mobile) + wordmark on its right
- Wordmark structure: `<span class="brand-name">[SHORT NAME] <span>[ACCENT WORD]</span></span>`
- Outer span carries a moving linear-gradient with `background-clip: text` creating a left-to-right shimmer animation (220% background-size, animated background-position, 4s loop)
- Inner span overrides fill with solid `--accent` color (no shimmer on the accent word)

**Buttons:**
- `.btn.btn-primary` — solid accent background, white text, arrow icon, soft drop shadow, lifts on hover
- `.btn.btn-ghost` — transparent with border, accent text on hover
- Both contain inline SVG arrow icons

**Eyebrows:**
- `.eyebrow` — mono font, uppercase, letter-spacing 0.12em, accent-2 color, small size (11–12px)

**Stats band:**
- `.stats-grid` — `repeat(3, 1fr)` desktop, single column under 880px
- `.stat-num` — large display font (clamp 2.4rem–3.5rem), `data-count` attribute drives an IntersectionObserver-triggered counter animation, `data-suffix` appends "+", "%", " BD", etc.

**Animations:**
- `.reveal` class — opacity 0 + translateY(20px), transitions to opacity 1 + translateY(0) when IntersectionObserver detects it. Optional `data-delay="1|2|3"` adds 100ms/200ms/300ms transition-delay.
- Cards have a subtle hover lift (`translateY(-4px)`) with shadow intensify
- Optional `.grad` class — gradient text using `background-clip: text` for a highlighted word in the hero headline

### 3 — Page structure

Each page shares the same `<nav>` and `<footer>`. The active nav link gets `class="active"`. Nav has a hamburger toggle for mobile that slides the link list down with `transform: translate(0, calc(-100% - 80px))` when closed, `translate(0, 0)` when `.open`.

#### index.html

1. **Hero** — left column has eyebrow + h1 (with one word wrapped in `.grad` for color highlight) + sub-paragraph + two CTAs (primary "Contact us" + ghost "Our services"). Right column has the hero media (video autoplay/muted/loop/playsinline OR image), wrapped in `.hero-visual` with subtle accent glow `::before`/`::after`. On desktop, hero-visual has `margin-top: -160px` to pull up; scoped inside `@media (min-width: 981px)`.
2. **Services preview section** — section head (eyebrow "What we do" + h2 + lead paragraph), then six `.card` items in a 3-column grid. Each card has a different background image using the layered gradient + image recipe.
3. **About split** — two-column section: brand logo on left in a tinted frame, copy on right with eyebrow "Why [COMPANY]" + h2 + paragraph + ghost button "About [COMPANY]".
4. **Stats band** — three stats. For "new entity backed by experienced stakeholders" positioning, use: years of combined stakeholder experience, count of core verticals, "1 BD" typical response time.
5. **CTA band** — large gradient card with eyebrow + h2 ("Tell us what you need.") + paragraph + two CTA buttons. Card uses the layered gradient + image background recipe.
6. **Footer**.

#### about.html

1. **Page header** — eyebrow "About [COMPANY]" + h1 + lead paragraph.
2. **Intro split** — heading on its own line above, then two-column: image (4:3 framed) on left, two paragraphs on right. Top-aligned.
3. **Values** — section head with image on the right, then three principle cards in a grid. Each card has a number (01/02/03), icon SVG, title, body. Backgrounds use the layered photo recipe.
4. **Stats band** — same three stats as homepage.
5. **Leadership** — generic paragraph framing experience/backing of stakeholders. No team photos, no names. Heading like "Decades of [INDUSTRY] experience, one disciplined desk."
6. **CTA band**.
7. **Footer**.

#### services.html

1. **Page header** — eyebrow "What we [trade/offer/build]" + h1 + lead paragraph.
2. **Product verticals** — one `.product-split` row per vertical, alternating image-left and image-right (`.product-split.reverse`). Image is a square (`aspect-ratio: 1/1`) framed at ~290px width. Right column has a "Vertical 01" tag, product name (display font, ~2rem), description paragraph, and a bullet list with custom dash markers. Use the page-scoped `<style>` block for `.product-split` definitions (don't put these in styles.css).
3. **End-to-end capabilities** — section head + six cards in 3-column grid (same pattern as homepage services preview, different copy).
4. **CTA band**.
5. **Footer**.

#### contact.html

1. **Page header** — eyebrow "Contact" + h1 ("Tell us what you need to move." or similar) + lead paragraph.
2. **Contact grid** — two columns:
   - Left: four info blocks (Trade desk email + phone, Phone, Headquarters, Trading hours). Each block has a small `<h4>` label + content. For unknown info use "We are updating this information, stay tuned!"
   - Right: contact form with `id="contact-form"`. Fields: full name (required), company, email (required), phone, product category select (required, populated from the vertical list), message textarea (required). Submit button with arrow icon. A hidden `.form-success` message that appears after submit. Form has layered gradient + image background.
3. **Footer**.

### 4 — script.js behaviors

```
- Add 'scrolled' class to .nav when window.scrollY > 12
- Mobile menu toggle: clicking .menu-toggle toggles .open on .nav-links
- IntersectionObserver on .reveal — adds .in class when 15% visible, applying transform: translateY(0) + opacity: 1
- IntersectionObserver on .stat-num — runs a 1.6s ease-out counter from 0 to data-count, appending data-suffix
- Card spotlight effect: on .card mousemove, set CSS custom properties --mx and --my to mouse position so a radial gradient highlights under the cursor
- Contact form submit: e.preventDefault(), fake 700ms "Sending…" state on the button, show .form-success, reset form, hide success after 6s. (This is a client-side mock — wire up real submission separately via Formspree/Web3Forms/backend.)
- Year stamp: document.querySelector('#year').textContent = new Date().getFullYear()
```

### 5 — Tone & copy guidance

- Confident, specific, anti-fluffy. Trade-desk voice, not corporate-marketing voice.
- Concrete verbs over abstract claims ("we ship 9000 cargoes" is fine if true; "we believe in synergy" is not).
- Short sentences. Em dashes are encouraged. No exclamation marks.
- The hero h1 should pick one noun and one verb that defines the company. Wrap one strong word in `.grad` for color highlight.
- Section headings are statements, not labels. "We close the loop, from producer to buyer." not "What We Do".
- For "new entity" positioning: never claim historical numbers. Lean on stakeholder experience, infrastructure, processes, partnerships-in-network. Phrasing like "backed by stakeholders with decades of..." works well.
- All "Get a quote" / "Request a quote" CTAs should say "Contact us" instead.

### 6 — Responsive requirements

- Breakpoints: 980px (hero stacks, nav becomes hamburger), 880px (grids collapse to single column, product-split collapses), 540px (font sizes shrink, logo height drops to 42px).
- Global safety net: `img, video { max-width: 100%; height: auto; }`
- Mobile menu: when closed, fully off-screen using `transform: translate(0, calc(-100% - 80px))` to guarantee clearance regardless of menu height.
- Hero-visual's negative margin-top must be scoped to `@media (min-width: 981px)` only — never apply on mobile.

### 7 — Output

Deliver six files. Brief inline comments are welcome but keep the source clean. Do not minify. Do not introduce frameworks, build tools, package.json, or external CSS frameworks beyond Google Fonts. Use semantic HTML (`<nav>`, `<section>`, `<footer>`, `<form>`). Include a favicon link in `<head>` pointing to the logo PNG.

## PROMPT END

---

## Tips for reusing this prompt

1. **Fill in the bracketed variables first** — the AI will produce best results when the brand brief is concrete.
2. **For the brand color**, give a specific hex/rgba and explicitly name the related shades (deeper/glow) so the AI doesn't invent contrasting hues.
3. **For images**, name the files you plan to provide so the AI references them correctly. The `onerror` fallbacks mean missing files won't crash the layout during preview.
4. **The contact form is a mock** — even if the prompt produces it perfectly, you'll need to wire it up to Formspree/Web3Forms/a backend separately to actually receive submissions. Mention this at the end of your prompt if you want the AI to leave a TODO comment in `script.js`.
5. **If your industry has different page needs** (e.g. case studies, pricing, blog), describe those sections in the same level of detail as the existing pages.
6. **Positioning matters** — "new entity backed by experienced stakeholders" leads to very different copy than "established 30-year operator". Be explicit.
