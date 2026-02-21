# North Star Website — Implementation Plan

This plan is milestone-based and meant to be updated as we work through the project. Each milestone is a coherent deliverable. Check off tasks as they're completed.

---

## Dependency Graph

```
M0 (Setup)
 └─> M1 (Core Page)
      └─> M2 (Polish & Assets)
           └─> M3 (Deploy & Go Live)
```

---

## Milestone 0: Project Setup

**Goal:** Repo initialized with Astro, Tailwind, TypeScript, documentation, and a working dev server.

### Tasks

- [x] **0.1 Initialize repo**
  - Create `/Users/lars/git/northstar/northstar-website/`
  - `git init` with remote `https://github.com/larsvedo/northstar-website.git`
  - `.gitignore` for node_modules, dist, .astro, .vercel, .env, .DS_Store

- [x] **0.2 Astro + Tailwind setup**
  - Install Astro v5, Tailwind CSS v4 via `@tailwindcss/vite`, `@astrojs/sitemap`
  - Configure `astro.config.mjs` with site URL and integrations
  - TypeScript strict mode via `tsconfig.json`

- [x] **0.3 Formatting**
  - Prettier with `prettier-plugin-astro` and `prettier-plugin-tailwindcss`
  - `.prettierrc` and `.prettierignore`

- [x] **0.4 Project structure**
  - Create directory structure: layouts, pages, components, styles, assets
  - `BaseLayout.astro` with HTML shell, meta tags, dark mode script
  - `global.css` with Tailwind imports and CSS custom properties

- [x] **0.5 Documentation**
  - `CLAUDE.md` following the main repo's pattern
  - `documentation/OVERVIEW.md` — messaging strategy
  - `documentation/TECHNICAL_STRATEGY.md` — stack and design system
  - `documentation/IMPLEMENTATION_PLAN.md` — this file
  - `documentation/DECISION_LOG.md` — initial decisions W001–W006

**Exit Criteria:** `npm run dev` serves a page, `npm run build` produces static output, all docs in place.

---

## Milestone 1: Core Page Content

**Goal:** All page sections implemented with real copy, responsive layout, and dark mode.

### Tasks

- [x] **1.1 Navigation** — Sticky nav with logo, section links, download CTA, dark mode toggle, mobile hamburger
- [x] **1.2 Hero section** — Headline, subhead, two CTAs, product screenshot placeholder
- [x] **1.3 Problem section** — "Speed without direction" narrative
- [x] **1.4 Features grid** — 6 feature cards with icons, responsive grid
- [x] **1.5 How It Works** — 3-step flow with descriptions
- [x] **1.6 Use Cases** — 3 persona cards
- [x] **1.7 Pricing** — 4 tiers with feature lists
- [x] **1.8 Download CTA** — Full-width section with download button and system requirements
- [x] **1.9 Footer** — Logo, links, copyright
- [x] **1.10 Dark mode** — CSS custom properties, toggle component, localStorage persistence
- [x] **1.11 SEO** — Meta tags, Open Graph, sitemap, robots.txt

**Exit Criteria:** All sections render on desktop and mobile, dark mode works, build succeeds.

---

## Milestone 2: Polish & Assets

**Goal:** Product screenshots, animations, and visual refinement. Production-ready.

### Tasks

- [ ] **2.1 Product screenshots** — Capture and optimize real app screenshots
- [ ] **2.2 Logo and brand assets** — Logo, favicon set, OG image
- [ ] **2.3 Typography and color refinement** — Final visual polish
- [ ] **2.4 Animations** — Subtle scroll-triggered fade-ins
- [ ] **2.5 Accessibility audit** — Contrast, semantic HTML, keyboard nav
- [ ] **2.6 Performance optimization** — Lighthouse 95+ target
- [ ] **2.7 404 page** — Custom 404 with navigation home

**Exit Criteria:** Lighthouse 95+ all categories, polished in both light and dark modes.

---

## Milestone 3: Deploy & Go Live

**Goal:** Site live on custom domain with analytics.

### Tasks

- [ ] **3.1 Vercel setup** — Connect repo, configure build
- [ ] **3.2 Custom domain** — DNS, SSL, redirects
- [ ] **3.3 Analytics** — Privacy-respecting analytics (Plausible or Vercel Analytics)
- [ ] **3.4 Download link** — Point CTA to latest DMG release
- [ ] **3.5 Final review** — Cross-browser testing, spell check, link validation
- [ ] **3.6 Launch** — Merge to main, verify live site

**Exit Criteria:** Site live at custom domain, download works, analytics collecting.
