# CLAUDE.md — North Star Website

This file is your reference when working on the marketing website. Read it at the start of every session.

## Project

North Star Website is the marketing site for North Star, a native macOS product management tool that records calls, transcribes them locally, and uses AI to extract product insights. The website communicates the value proposition and drives downloads.

See `documentation/OVERVIEW.md` for the messaging strategy and `documentation/TECHNICAL_STRATEGY.md` for all architectural decisions.

## North Star Ecosystem

This repo is one part of a multi-platform project. All repos live under `/Users/lars/git/northstar/`.

| Repo | Path | Purpose |
|------|------|---------|
| `northstar-website` | `/Users/lars/git/northstar/northstar-website/` | **This repo** — marketing website |
| `northstar` | `/Users/lars/git/northstar/northstar/` | macOS app + server packages (source of truth for product features) |
| `northstar-ios` | `/Users/lars/git/northstar/northstar-ios/` | iOS companion app |
| `northstar-releases` | `/Users/lars/git/northstar/northstar-releases/` | Public repo for macOS auto-updater |

**Shared resources** (at the parent level `/Users/lars/git/northstar/`):
- `STYLE_GUIDE.md` — colors (Polaris Deep Space), typography (Inter/Instrument Serif), spacing, effects. **Use this as the design reference for the website.**
- `.claude/commands/` — slash commands: `/build-web`, `/build-mac`, `/build-ios`, `/check`

## Documentation

All project documentation lives in `documentation/`. These files are living documents — read them, use them, and update them as part of your work.

| File | Purpose | When to reference |
|------|---------|------------------|
| `documentation/OVERVIEW.md` | Website purpose, audience, messaging strategy, content hierarchy | Before writing or changing any copy or page content |
| `documentation/TECHNICAL_STRATEGY.md` | Stack, architecture, performance targets, design system | Before making any technical decision |
| `documentation/IMPLEMENTATION_PLAN.md` | Milestone-based task list with checkboxes | Before starting work and after completing tasks |
| `documentation/DECISION_LOG.md` | Key decisions with context and rationale | When making a non-trivial technical or design decision |

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
│   │   └── BaseLayout.astro      # HTML shell, meta tags, fonts, dark mode script, scroll reveal
│   ├── pages/
│   │   ├── index.astro            # Main page (composes all section components)
│   │   └── 404.astro
│   ├── components/                # Page sections (in display order)
│   │   ├── Nav.astro              # Sticky header with logo, links, CTA, theme toggle
│   │   ├── Hero.astro             # Headline, email signup, product mockup
│   │   ├── Problem.astro          # Vibe coding narrative
│   │   ├── Features.astro         # 6-card grid (record, transcribe, AI, dictation, screenshots, clipboard)
│   │   ├── HowItWorks.astro       # 3-step flow (Record, Transcribe, Analyze)
│   │   ├── UseCases.astro         # 3 persona cards
│   │   ├── EarlyAccess.astro      # Email signup CTA (active — replaces Pricing + Download)
│   │   ├── Footer.astro           # Links & copyright
│   │   ├── ThemeToggle.astro      # Dark/light mode toggle (client:load island)
│   │   ├── Pricing.astro          # (inactive — kept for reference, not in index.astro)
│   │   └── Download.astro         # (inactive — kept for reference, not in index.astro)
│   ├── styles/
│   │   └── global.css             # Tailwind imports, CSS custom properties, animations, utilities
│   └── assets/
│       ├── images/                # Product screenshots (Astro-optimized)
│       ├── icons/                 # SVG icons (inlined)
│       └── logo/                  # Logo variants
├── public/
│   ├── favicon.svg
│   ├── favicon.ico
│   ├── apple-touch-icon.png
│   └── robots.txt
├── astro.config.mjs               # Site URL, sitemap, Tailwind vite plugin
├── tsconfig.json                   # TypeScript strict mode
├── package.json
├── .prettierrc                     # Prettier with Astro + Tailwind plugins
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
4. **To deploy**, use the `/build-web` slash command or push to main (Vercel auto-deploys).

## Build & Deploy

```bash
npm run dev      # Start dev server at localhost:4321
npm run build    # Build static site to dist/
npm run preview  # Preview the built site locally
npm run format   # Format all files with Prettier
```

**Deployment:** Vercel auto-deploys on push to `main`. Domain: `northstar.app`. No manual deploy step needed — just push to main.

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
