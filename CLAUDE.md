# CLAUDE.md — North Star Website

This file is your reference when working on the marketing website. Read it at the start of every session.

## Project

North Star Website is the marketing site for North Star, a native macOS product management tool that records calls, transcribes them locally, and uses AI to extract product insights. The website communicates the value proposition and drives downloads.

See `documentation/OVERVIEW.md` for the messaging strategy and `documentation/TECHNICAL_STRATEGY.md` for all architectural decisions. See `~/git/northstar/STYLE_GUIDE.md` for the shared visual identity (colors, typography, spacing, effects) used across all North Star projects.

## Documentation

All project documentation lives in `documentation/`. These files are living documents — read them, use them, and update them as part of your work.

| File | Purpose | When to reference |
|------|---------|------------------|
| `OVERVIEW.md` | Website purpose, audience, messaging strategy, content hierarchy | Before writing or changing any copy or page content |
| `TECHNICAL_STRATEGY.md` | Stack, architecture, performance targets, design system | Before making any technical decision |
| `IMPLEMENTATION_PLAN.md` | Milestone-based task list with checkboxes | Before starting work and after completing tasks |
| `DECISION_LOG.md` | Key decisions with context and rationale | When making a non-trivial technical or design decision |

## Related Repos

| Repo | Path | Purpose |
|------|------|---------|
| `northstar` | `~/git/northstar/northstar/` | macOS app + server packages (source of truth for product features and docs) |
| `northstar-ios` | `~/git/northstar/northstar-ios/` | iOS companion app |
| `northstar-releases` | `~/git/northstar/northstar-releases/` | macOS auto-updater releases |
| `northstar-website` | `~/git/northstar/northstar-website/` | This repo — marketing website |

## Tech Stack

- **Framework:** Astro v5 (static site generation, zero JS by default)
- **Styling:** Tailwind CSS v4 (via `@tailwindcss/vite` plugin)
- **Language:** TypeScript (strict mode)
- **Deployment:** Vercel (auto-deploy on push to main)
- **Sitemap:** `@astrojs/sitemap`

## Repo Structure

```
northstar-website/
├── CLAUDE.md
├── documentation/
│   ├── OVERVIEW.md
│   ├── TECHNICAL_STRATEGY.md
│   ├── IMPLEMENTATION_PLAN.md
│   └── DECISION_LOG.md
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   └── 404.astro
│   ├── components/
│   │   ├── Nav.astro
│   │   ├── Hero.astro
│   │   ├── Problem.astro
│   │   ├── Features.astro
│   │   ├── HowItWorks.astro
│   │   ├── UseCases.astro
│   │   ├── Pricing.astro
│   │   ├── Download.astro
│   │   ├── Footer.astro
│   │   └── ThemeToggle.astro
│   ├── styles/
│   │   └── global.css
│   └── assets/
│       ├── images/
│       ├── icons/
│       └── logo/
├── public/
│   ├── favicon.svg
│   └── og-image.png
├── astro.config.mjs
├── tsconfig.json
├── package.json
├── .prettierrc
└── .gitignore
```

## Working Rules

### Before writing code

1. Read `documentation/TECHNICAL_STRATEGY.md` to confirm the relevant stack choices and design system.
2. Check `documentation/IMPLEMENTATION_PLAN.md` to understand where this work fits.
3. Look for existing components and patterns before creating new ones.

### While writing code

- Use Astro components (`.astro` files) for all static content. Only use framework components (React/Svelte) if the component requires client-side interactivity beyond what a `<script>` tag can handle.
- Follow the design system defined in `documentation/TECHNICAL_STRATEGY.md` for colors, spacing, and typography.
- Keep all copy/messaging aligned with `documentation/OVERVIEW.md`.
- Use Tailwind utility classes. No custom CSS unless Tailwind cannot express the style.
- Images go in `src/assets/` (processed by Astro) or `public/` (served as-is).

### After completing work

1. Mark completed tasks in `documentation/IMPLEMENTATION_PLAN.md`.
2. If you made a non-trivial decision, add an entry to `documentation/DECISION_LOG.md`.
3. Verify the build passes: `npm run build`

## Build Commands

```bash
npm run dev      # Start dev server at localhost:4321
npm run build    # Build static site to dist/
npm run preview  # Preview the built site locally
npm run format   # Format all files with Prettier
```

## Git Workflow

**Repo:** `https://github.com/larsvedo/northstar-website.git`

### Branches

- `main` — production. Deploys to Vercel on push. Never force push.
- Feature branches — branch off `main`, merge back via PR.

### Branch naming

Use the pattern `type/short-description`:
- `feat/hero-section`
- `fix/mobile-nav`
- `chore/update-deps`
- `docs/update-overview`

### Commit messages

Follow Conventional Commits:
```
feat: add hero section with download CTA
fix: mobile nav hamburger menu
chore: update Astro to v5.x
docs: update messaging strategy
```
