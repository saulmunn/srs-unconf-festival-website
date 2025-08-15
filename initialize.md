## LLM Implementation Directions

- Goal: Generate a **static**, single-page event website with no sections or anchor navigation.
- Files: `index.html`, `styles.css`, optional `/assets/` for images.
- Tech: HTML5 + CSS3 + vanilla JS (only if truly needed).
- Fonts: **IBM Plex Sans** only, loaded via Google Fonts `<link>` in `<head>`.
- Colors: Use the CSS variables defined in **Design Tokens** below.
- Style constraints: square corners (0px radii), small shadows, no animations or transitions.
- Layout: single continuous flow (header → key details → CTA → footer).
- Accessibility: WCAG 2.1 AA, visible focus ring, semantic landmarks.
- Performance: optimized images, minimal DOM, defer any optional JS.
- CTA: external RSVP link only (`{{cta_href}}`); **no backend**.
- Output format: produce final `index.html` and `styles.css` code blocks using the tokens and class names specified below. Avoid extraneous commentary in code output.

## Event Website Concept

### Purpose

A simple, clean, and aesthetically pleasing website for showcasing event details, encouraging attendance, and providing essential information.

---

## Stylistic Design

**Visual Style:**

- Minimalist design with plenty of white space
- Off-white background (#FDFDF5)
- Primary accent color: blue (#86CEFA)
- Secondary accent color: darker blue (#1750AC)
- Square buttons and square cards with small shadows
- Large, easy-to-read typography

**Layout:**

- Single-page layout
- No distinct content sections, all content presented in a continuous flow
- Responsive design for mobile and desktop

**Typography:**

- All fonts: IBM Plex Sans (for all text)

**Imagery:**

- Minimal imagery only; avoid hero/video backgrounds
- Use small, tasteful photos or icons only if they add clarity
- Compress images and provide meaningful `alt` text

---

## Technical Specifications

**Frontend:**

- HTML5 and CSS3; vanilla JavaScript only if absolutely necessary
- Tailwind CSS allowed but optional; keep utility classes minimal
- No animations or transitions
- Fonts: IBM Plex Sans loaded via `<link>` (Google Fonts) in `<head>`

**Backend:**

- No backend; static site only

**Hosting:**

- Vercel (static deployment)
- Build Command: none
- Output Directory: root
- Production branch: `main`
- Preview deployments on pull requests

**Performance & Accessibility:**

- Optimized images and lazy loading
- WCAG 2.1 AA compliance
- Fast load times (<1.5 seconds target)

---

## Design Tokens (LLM-ready)

- `--color-bg: #FDFDF5;`  /* off-white background */
- `--color-accent: #86CEFA;`  /* primary blue */
- `--color-accent-2: #1750AC;`  /* darker blue */
- `--radius-card: 0px;`
- `--radius-button: 0px;`
- `--shadow-card: 0 2px 8px rgba(0,0,0,0.08);`
- `--shadow-button: 0 1px 4px rgba(0,0,0,0.06);`
- `--font-family: 'IBM Plex Sans', system-ui, -apple-system, Segoe UI, Roboto, 'Helvetica Neue', Arial, 'Noto Sans';`

## DOM Structure (no sections)

- `<header>`: brand/logo text, primary CTA button
- `<main>`: concise event summary (what / when / where), details block, RSVP CTA
- `<footer>`: contact info, minimal legal text

## Components

- **Button (Primary):**
  - Corners: 0px
  - Background: `var(--color-accent-2)`; text: white
  - Hover: darken by ~6%
  - Focus: 2px ring using `var(--color-accent)`
  - Shadow: `var(--shadow-button)`
- **Button (Secondary):** outline with `var(--color-accent-2)`, text `var(--color-accent-2)`, transparent background
- **Card:** 0px radius, `var(--shadow-card)`, 16–24px padding, light border `rgba(0,0,0,0.06)`
- **Badge:** square corners, subtle background `rgba(23,80,172,0.06)`, text `var(--color-accent-2)`

## Content Placeholders (for LLM)

- **Event Name:** `{{event_name}}`
- **Date & Time:** `{{event_datetime}}`
- **Location:** `{{event_location}}`
- **Short Blurb (140–200 chars):** `{{event_blurb}}`
- **Primary CTA label:** `{{cta_label}}` (e.g., "RSVP")
- **Primary CTA href:** `{{cta_href}}` (external form link)