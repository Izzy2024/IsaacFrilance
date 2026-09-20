# Isaac Castillo Landing Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a fast, static Astro landing page for Isaac Castillo Freelance with a bold neobrutalist visual system and a clear contact funnel.

**Architecture:** Use Astro components and one global stylesheet. `BaseLayout.astro` owns document metadata and global CSS; `index.astro` composes focused section components. Keep client JavaScript at zero unless a mobile menu requires it, and render all decorative visuals with CSS/SVG.

**Tech Stack:** Astro, vanilla CSS, semantic HTML, CSS custom properties, CSS animations, npm scripts.

## Global Constraints

- Project is static Astro in `/home/fedora26/Documentos/Freelanceweb`.
- Use white-crude `#f7f3ea`, black `#111111`, yellow `#ffda44`, cyan `#55d8ff`, pink `#ff75b8`, and neon green `#c8ff3d`.
- Use `3px solid #111111` borders and solid shadows such as `6px 6px 0 #111111`.
- Use semantic headings with one H1, visible focus states, labeled form fields, and reduced-motion support.
- Do not add React, a UI library, CMS, analytics, authentication, backend, or fake form submission.
- Demo projects, testimonials, and social URLs must be visibly easy to edit in `index.astro`.

---

### Task 1: Scaffold the Astro project

**Files:**
- Create: `package.json`
- Create: `astro.config.mjs`
- Create: `tsconfig.json`
- Create: `src/layouts/BaseLayout.astro`
- Create: `src/pages/index.astro`

**Interfaces:**
- `BaseLayout.astro` accepts `title`, `description`, and a page slot.
- `index.astro` renders the complete landing page through the layout.

- [ ] **Step 1: Write the minimal package manifest and Astro config**

  Define Astro as the only runtime dependency and scripts for `dev`, `build`, and `preview`. Configure static output explicitly.

- [ ] **Step 2: Add the document shell**

  Add `BaseLayout.astro` with language `es`, responsive viewport, title/description props, skip link, and import of `src/styles/global.css`.

- [ ] **Step 3: Add the page entry**

  Render an initial semantic shell in `src/pages/index.astro` with `main`, placeholder section headings, and the layout wrapper so the project can build before visual sections land.

- [ ] **Step 4: Run the build**

  Run `npm install` and `npm run build`.

  Expected: Astro installs and produces a static build in `dist/` with exit code 0.

---

### Task 2: Build the visual system and responsive foundation

**Files:**
- Create: `src/styles/global.css`

**Interfaces:**
- Exposes global tokens, reset, typography, `.brutal-button`, `.brutal-card`, `.section-heading`, focus styles, and responsive layout utilities used by section components.

- [ ] **Step 1: Add tokens and base reset**

  Define the palette, border width, shadow, radius, content width, spacing scale, box sizing, body background, selection color, and heading/body font stacks.

- [ ] **Step 2: Add physical controls and cards**

  Implement solid-shadow buttons/cards with hover, active, focus-visible, and reduced-motion rules. Active controls must translate enough to cover their own shadow.

- [ ] **Step 3: Add layout primitives**

  Implement `.container`, section spacing, responsive grids, tags, text balance, and small-screen breakpoints without introducing a utility framework.

- [ ] **Step 4: Run the build**

  Run `npm run build`.

  Expected: exit code 0 and no stylesheet parsing errors.

---

### Task 3: Implement the page sections and conversion content

**Files:**
- Modify: `src/pages/index.astro`

**Interfaces:**
- The page exposes anchors `#servicios`, `#proyectos`, `#sobre-mi`, and `#contacto`.
- Decorative project visuals use inline SVG/CSS only; no external image dependency is required.

- [ ] **Step 1: Implement navbar and hero**

  Add brand lockup, navigation links, availability eyebrow, H1, direct Spanish copy, primary/secondary CTAs, and a right-side abstract visual with black outlines and accent blocks.

- [ ] **Step 2: Implement services**

  Add three brutal cards for frontend/web, mobile apps, and tech/UI-UX consulting. Each card needs a short benefit statement and a minimal inline icon.

- [ ] **Step 3: Implement portfolio cases**

  Add two horizontally structured case cards with project title, technology tags, challenge/solution copy, case-study CTA, and distinct CSS/SVG preview art. Alternate the visual side on large screens.

- [ ] **Step 4: Implement social proof**

  Add an overflow-hidden CSS marquee with duplicated technology labels and three testimonial cards with yellow stars, names, roles, and concise demo quotes.

- [ ] **Step 5: Implement about and contact/footer**

  Add personal copy for Isaac, the “Código limpio. Entregas a tiempo.” philosophy, coffee/CSS detail, large yellow contact block, labeled form fields, and editable email/social links.

- [ ] **Step 6: Run the build**

  Run `npm run build`.

  Expected: exit code 0, one H1 in generated HTML, and no unresolved imports.

---

### Task 4: Verify accessibility, responsive behavior, and visual fidelity

**Files:**
- Modify: `src/pages/index.astro` if semantic or content fixes are needed.
- Modify: `src/styles/global.css` if responsive or focus fixes are needed.

- [ ] **Step 1: Run diagnostics**

  Run `lsp_diagnostics` on every changed `.astro`, `.mjs`, `.ts`, and `.css` file.

  Expected: no errors in project-authored files.

- [ ] **Step 2: Run the production build again**

  Run `npm run build`.

  Expected: exit code 0.

- [ ] **Step 3: Perform browser QA**

  Start the Astro preview server, inspect desktop and mobile widths in Playwright, verify anchor navigation, visible CTAs, hover/active button movement, marquee clipping, form labels, keyboard focus, and no horizontal overflow.

  Expected: all sections render, the neobrutalist system is consistent, and mobile remains readable without clipped text.

- [ ] **Step 4: Check reduced motion and document structure**

  Emulate reduced motion and inspect the accessibility tree.

  Expected: marquee/entrance motion is suppressed, landmarks are present, and the page has a single H1.
