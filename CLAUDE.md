# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
pnpm dev          # Start local dev server
pnpm build        # Type-check (astro check) then build to dist/
pnpm preview      # Preview the production build locally
pnpm check        # Lint and format with Biome (--apply-unsafe)
```

No test suite exists in this project.

## Architecture

This is a personal portfolio/blog site built with **Astro 4** and **Tailwind CSS**, originally based on the `ccbikai/astro-aria` template.

### Content

Blog posts live in `src/content/post/` as Markdown files with this frontmatter schema (defined in `src/content/config.js`):

```yaml
layout: ../../layouts/post.astro
title: string
description: string
dateFormatted: string   # e.g. "February 5, 2026"
```

### Data Collections

Non-post structured data lives in `src/collections/` as JSON files:
- `projects.json` — portfolio projects (name, description, image, url)
- `clients.json` — client list
- `experiences.json` — career history
- `logos.json` / `menu.json` — site config data

### Routing

Pages are in `src/pages/`. Individual posts use dynamic routing via `src/pages/post/[slug].astro`, which reads from the `post` content collection.

### Styling & JS

- Tailwind with the Typography plugin handles all styling; dark mode uses the `dark:` class strategy toggled via `src/assets/js/main.js`
- `main.js` also handles sticky header, mobile menu, and active menu highlighting
- Custom CSS is in `src/assets/css/main.css`

### Tooling

- **Biome** (`biome.json`) handles linting and formatting (replaces ESLint + Prettier)
- **TypeScript** via `astro check` (runs as part of `pnpm build`)
- Node.js v20 required (see `.node-version`)
- Package manager: **pnpm** v9
