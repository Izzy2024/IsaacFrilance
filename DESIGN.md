# Isaac Castillo Freelance Design System

## 0. Research Log

- Embedded refs: shortlisted `nike.md`, `vercel.md`, and `wired.md` from the curated library; picked Layer A `brutalist-skill` plus `nike.md` as tonal source because the brief asks for bold monochrome structure, oversized type, and hard-edged composition, then adapted the palette to Isaac's neobrutalist brief.
- Lazyweb: skipped because no live product or site reference was supplied; the page is an original personal brand direction rather than a clone.
- Imagen drafts: skipped because the brief requests implementation directly and the hero is intentionally CSS/SVG for speed and editability.

## 1. Atmosphere & Identity

A high-energy workshop poster for a developer who ships. The page feels tactile, direct, and slightly loud without becoming chaotic. The signature is the “workbench card”: oversized black typography, paper substrate, one saturated color block, and a hard shadow that physically collapses when pressed.

## 2. Color

### Palette

| Role | Token | Value | Usage |
|---|---|---:|---|
| Surface / paper | `--paper` | `#f7f3ea` | Primary page canvas |
| Surface / white | `--white` | `#ffffff` | Cards, inputs, contrast surfaces |
| Ink / primary | `--ink` | `#111111` | Text, borders, shadows |
| Accent / yellow | `--yellow` | `#ffda44` | Primary CTA, contact block |
| Accent / cyan | `--cyan` | `#55d8ff` | Hero art, service surfaces |
| Accent / pink | `--pink` | `#ff75b8` | Portfolio art, labels |
| Accent / green | `--green` | `#c8ff3d` | Service surface, status marker |
| Muted ink | `--muted` | `#5b5851` | Supporting copy |
| Focus | `--focus` | `#1151ff` | Keyboard focus ring |

Rules: use `--ink` for all structural lines; saturated colors are intentional surface accents, never low-opacity decoration; no gradients, glass, or blur surfaces.

## 3. Typography

### Scale

| Level | Size | Weight | Line Height | Usage |
|---|---:|---:|---:|---|
| Display | `clamp(3.5rem, 9vw, 8.5rem)` | 800 | 0.9 | Hero H1 |
| H1 | `clamp(2.5rem, 6vw, 5.5rem)` | 800 | 0.92 | Large section title |
| H2 | `clamp(2rem, 4vw, 3.5rem)` | 800 | 0.98 | Section heading |
| H3 | `1.5rem` | 800 | 1.05 | Card heading |
| Body/lg | `1.25rem` | 500 | 1.45 | Lead copy |
| Body | `1rem` | 500 | 1.55 | Standard copy |
| Body/sm | `0.875rem` | 600 | 1.4 | Metadata |
| Overline | `0.75rem` | 800 | 1.2 | Labels and eyebrow |

### Font Stack

- Display/body: `Space Grotesk`, `Arial Black`, `Helvetica Neue`, sans-serif.
- Mono: `IBM Plex Mono`, `SFMono-Regular`, Consolas, monospace.

Rules: headings are tight and can use uppercase for structural labels; normal sentence case stays for explanatory copy; body text never drops below `0.875rem`.

## 4. Spacing & Layout

Base unit is 4px.

| Token | Value | Usage |
|---|---:|---|
| `--space-1` | `4px` | Icon gaps |
| `--space-2` | `8px` | Inline groups |
| `--space-3` | `12px` | Compact padding |
| `--space-4` | `16px` | Standard padding |
| `--space-6` | `24px` | Card padding |
| `--space-8` | `32px` | Grid gaps |
| `--space-12` | `48px` | Section inner spacing |
| `--space-16` | `64px` | Page rhythm |
| `--space-20` | `80px` | Hero/section separation |

- Max content width: `1280px`.
- Desktop grid: 12 columns with `24px` gaps.
- Breakpoints: `640px`, `768px`, `1024px`, `1280px`.
- Corners are square by default. A small `4px` radius is allowed only for controls where it improves focus visibility.

## 5. Components

### Brutal Button

- **Structure**: anchor or button with text and optional arrow SVG.
- **Variants**: `primary` yellow, `dark` black, `outline` paper.
- **Spacing**: `12px 20px`, minimum height `48px`.
- **States**: default hard shadow; hover translates `2px 2px`; active translates `6px 6px` and removes the shadow; focus-visible uses a blue outer ring; disabled lowers contrast and removes pointer interaction.
- **Accessibility**: native `<a>`/`<button>`, visible text, keyboard focus.
- **Motion**: 120ms ease-out transform only.
- **Layout**: inline cluster.

### Brutal Card

- **Structure**: bordered article with header/meta, content, and optional footer CTA.
- **Variants**: paper, cyan, pink, green.
- **Spacing**: `24px` internal padding, `24px` grid gap.
- **States**: default solid shadow; hover shifts `4px 4px` and compresses the shadow; focus-visible applies a ring when interactive.
- **Accessibility**: cards remain readable without color; links are explicit.
- **Motion**: 160ms ease-out transform.
- **Layout**: grid item or stacked article.

### Tag

- **Structure**: inline `span` with mono label.
- **Variants**: ink, yellow, paper.
- **Spacing**: `4px 8px`.
- **States**: static; interactive tags inherit button focus/active behavior.
- **Accessibility**: decorative tags are not interactive.
- **Motion**: none unless interactive.
- **Layout**: inline cluster.

### Marquee

- **Structure**: clipped track with duplicated label group.
- **Variants**: ink strip with paper text.
- **Spacing**: `16px` vertical padding.
- **States**: continuous 22s linear movement; pauses on hover/focus-within.
- **Accessibility**: `aria-hidden` on duplicate decorative items; reduced motion freezes the track.
- **Motion**: transform only, reduced motion disables movement.
- **Layout**: full-width band.

## 6. Motion & Interaction

| Type | Duration | Easing | Usage |
|---|---:|---|---|
| Micro | `120ms` | `ease-out` | Button press |
| Standard | `180ms` | `ease-out` | Card hover |
| Emphasis | `500ms` | `cubic-bezier(0.16, 1, 0.3, 1)` | Hero reveal |
| Marquee | `22s` | `linear` | Technology strip |

- Mechanisms adapted from beui.dev `button` and `marquee`: tactile press translates the control into its shadow; marquee uses duplicated content and transform-only looping.
- Animate only `transform` and `opacity`.
- `prefers-reduced-motion: reduce` removes reveal/hover transitions and freezes the marquee.

## 7. Depth & Surface

Strategy: **mixed**, with hard borders as structure and hard-offset shadows as physical elevation.

| Level | Value | Usage |
|---|---|---|
| Structural | `3px solid var(--ink)` | Cards, controls, art frames |
| Default | `6px 6px 0 var(--ink)` | Cards and buttons |
| Emphasis | `10px 10px 0 var(--ink)` | Hero art and contact block |

No blur, soft shadows, or translucent glass. Layering comes from offset blocks, accent panels, hatch patterns, and black rules.

## 8. Accessibility Constraints & Accepted Debt

### Constraints

- WCAG 2.2 AA target: body contrast at least 4.5:1 and large text at least 3:1.
- Every interactive element has visible focus and full keyboard reachability.
- Form controls use visible labels.
- Main content has one H1 and landmarks for header, nav, main, sections, and footer.
- `prefers-reduced-motion` is respected.

### Accepted Debt

| Item | Location | Why accepted | Owner / Exit |
|---|---|---|---|
| Contact form has no backend | `src/pages/index.astro` | Scope is a static first version; avoid fake success states | Isaac / wire to Formspree or API before launch |
| Demo portfolio URLs | `src/pages/index.astro` | Copy is placeholder content until real cases are selected | Isaac / replace before publishing |
