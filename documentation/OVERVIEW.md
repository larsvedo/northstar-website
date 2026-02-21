# North Star Website — Overview

## What Is This Website?

The North Star marketing website communicates what the product does, who it's for, and why it matters. It drives downloads of the macOS app and establishes credibility for the product.

This is not a web app. There is no authentication, no dynamic data, no user accounts. It is a single-page marketing site that tells a story and provides a download link.

## Target Audience

The website targets potential North Star users:

**Solo founders and indie hackers.** They are building, selling, and supporting their product simultaneously. They're often vibe coding — moving fast, making decisions based on gut and recent memory. They need a tool that gives them direction without adding overhead.

**Product managers at software companies.** They run multiple customer calls per week and need to track themes across all of them. They want to stop copying quotes into spreadsheets and start having the system surface patterns.

**Small teams without a dedicated PM.** Engineers talk to customers. Designers run usability tests. Everyone has pieces of the picture, but there's no system to assemble them.

## Core Narrative

**"Vibe coding has made us 10x faster, but without a north star we're getting lost and building the wrong things."**

This is the central tension the website addresses. The visitor understands speed — they live it. What they lack is direction. North Star gives them that direction by capturing and synthesizing what customers actually tell them.

The narrative arc of the page:

1. **Hook** (Hero) — You're building fast. Are you building right?
2. **Problem** (Problem) — Speed without customer signal means building the wrong things faster.
3. **Solution** (Features) — North Star turns conversations into structured product intelligence.
4. **How** (How It Works) — Record, transcribe, analyze. Three steps, zero overhead.
5. **Who** (Use Cases) — People like you already use this.
6. **Value** (Pricing) — Free to start, scales with your team.
7. **Action** (Download) — Download now.

## Messaging Guidelines

### Tone

- **Direct.** No buzzwords, no enterprise fluff. Say what the product does.
- **Developer-friendly.** The audience writes code. Respect their intelligence.
- **Confident but not arrogant.** State facts. Don't oversell.
- **Specific.** "On-device transcription via WhisperKit" is better than "AI-powered transcription."

### Key Phrases

- "Build what matters" — the primary tagline
- "Speed without direction" — the problem statement
- "Your product management compass" — positioning
- "Every conversation becomes structured product intelligence" — the value
- "Local-first. Your audio never leaves your Mac." — privacy positioning
- "Free for individuals. No account required." — low friction

### What We Don't Say

- No "AI-first" or "AI-native" — everyone says this, it means nothing.
- No "revolutionary" or "game-changing" — let the product speak.
- No feature comparisons with competitors — position on our own merits.
- No pressure tactics — no "limited time" or "act now."

## Content Sections

See the component files in `src/components/` for the actual implementation. The sections flow as a single scrollable page:

1. **Nav** — Logo, section links, download CTA, dark mode toggle
2. **Hero** — Headline, subhead, two CTAs, product screenshot
3. **Problem** — The vibe coding narrative
4. **Features** — 6-card grid of key capabilities
5. **How It Works** — 3-step flow (Record, Transcribe, Analyze)
6. **Use Cases** — 3 persona cards
7. **Pricing** — 4 tiers with feature lists
8. **Download** — Full-width CTA section
9. **Footer** — Links and legal
