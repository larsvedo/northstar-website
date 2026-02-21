# North Star Website — Decision Log

Key technical and design decisions, with context and rationale. Updated as decisions are made throughout the project.

---

## W001 — Astro over Next.js (2026-02-21)

**Decision:** Use Astro v5 for static site generation.

**Context:** Need a framework for a marketing landing page. No dynamic data, no auth, no user state. Evaluated Astro, Next.js, and plain HTML.

**Rationale:** Astro ships zero JavaScript by default, producing near-instant page loads. It's purpose-built for content sites. Next.js would add a React runtime, client-side routing, and hydration cost for zero benefit on a static marketing page. Astro's island architecture lets us add interactivity (dark mode toggle, pricing toggle) only where needed.

**Alternatives:** Next.js (overkill, unnecessary JS bundle), Hugo/11ty (less ergonomic for component-based layouts), plain HTML (no component reusability or build tooling).

---

## W002 — Separate repo (2026-02-21)

**Decision:** The website lives in its own repo (`northstar-website`) rather than inside the main `northstar` monorepo.

**Context:** The main repo contains a Swift macOS app and TypeScript server packages. The website is a standalone Astro/JS project with independent deployment.

**Rationale:** Different tech stack, independent deployment pipeline. Website changes should not trigger macOS app builds. Mirrors the pattern of `northstar-ios/` being its own repo. Keeps CI/CD simple.

**Alternatives:** Subdirectory in monorepo (couples deployment, complicates CI).

---

## W003 — Single-page layout (2026-02-21)

**Decision:** All content on one scrollable page with anchor-linked sections. No multi-page routing.

**Context:** Marketing sites can be single-page or multi-page. Our content fits a linear narrative.

**Rationale:** Marketing sites convert better as scrollable narratives. The visitor reads through the story — problem, solution, features, pricing, action — without clicking. Reduces bounce from page transitions. Multi-page can be added later (blog, docs, changelog) if needed.

**Alternatives:** Multi-page with separate routes for features, pricing, etc. (splits the narrative, adds navigation friction).

---

## W004 — Tailwind CSS v4 (2026-02-21)

**Decision:** Use Tailwind CSS v4 via the `@tailwindcss/vite` plugin.

**Context:** The main North Star repo uses Tailwind. v4 uses CSS-first configuration and integrates via a Vite plugin rather than PostCSS.

**Rationale:** Matches the main repo's styling approach. Team familiarity. CSS-first config is simpler than v3's JS config. The Vite plugin integrates natively with Astro's build pipeline.

**Alternatives:** Tailwind v3 (requires `@astrojs/tailwind` integration, older config format), vanilla CSS (loses utility-class productivity), CSS Modules (unnecessary abstraction for a marketing site).

---

## W005 — Vercel for hosting (2026-02-21)

**Decision:** Deploy to Vercel with auto-deploy from the `main` branch.

**Context:** Need a CDN-backed host for a static site with zero server-side logic.

**Rationale:** Zero-config deployment. Free tier is more than sufficient. Automatic SSL, global CDN, preview deploys on PRs. The main repo already shows Vercel familiarity (`.vercel/` in `.gitignore`).

**Alternatives:** Netlify (equally good, slightly different UI), GitHub Pages (no preview deploys), Cloudflare Pages (good but less Astro-specific tooling).

---

## W006 — No CMS (2026-02-21)

**Decision:** Content is hardcoded in Astro components. No headless CMS.

**Context:** The site has one page with a known, stable structure maintained by a single developer.

**Rationale:** A CMS adds complexity (API calls, content modeling, auth) without benefit for a single-page site with one maintainer. Content changes happen via code commits. If content iteration becomes frequent or non-technical contributors need to edit, Astro Content Collections or a headless CMS (Sanity, Contentful) can be added later.

**Alternatives:** Sanity (overkill for one page), Contentful (same), Astro Content Collections (good upgrade path but premature for now).
