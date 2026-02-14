# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic personal website for Moritz Seebacher (PhD student, ifo Institute / LMU Munich). Hosted on GitHub Pages at `moseeb98.github.io`.

## Tech Stack

- **Jekyll** static site generator using the **Minimal Mistakes** remote theme (`mmistakes/minimal-mistakes`)
- Markdown (Kramdown with GFM) for content
- SCSS for custom styling (`assets/css/main.scss`)
- Plugins: `jekyll-include-cache`, `jekyll-sitemap`, `jekyll-seo-tag`

## Build & Preview

```bash
bundle exec jekyll serve        # Local dev server (default: http://localhost:4000)
bundle exec jekyll build        # Build static site to _site/
```

No Gemfile is currently committed — if adding one, include `github-pages` gem or `jekyll` + `minimal-mistakes-jekyll` for local builds.

## Architecture

This is a single-page academic site with one additional detail page:

- **`index.md`** — Main page. All primary content (publications, working papers, CV link, etc.) lives here as sections with anchor IDs (`#publications`, `#working-papers`, etc.).
- **`abstract_facebook.md`** — Standalone abstract page linked from the Work in Progress section. Uses permalink `/abstract_facebook`.
- **`_data/navigation.yml`** — Top nav bar entries, all pointing to anchor sections on the index page.
- **`_config.yml`** — Jekyll config: author profile (name, avatar, bio, links), theme settings, plugins, skin (`default`).
- **`assets/css/main.scss`** — Custom overrides for avatar sizing/cropping. Desktop (≥1024px): circular avatar at 70% sidebar width. Mobile (≤800px): rectangular, centered, capped at 220px.

## Content Conventions

- Each publication/paper entry is a Markdown bullet with the title link and coauthors on the first line, followed by two trailing spaces (`  `) for a line break, then the citation in `<small><strong>...</strong>...</small>` on the next indented line. The trailing spaces are critical — they produce the `<br>` that separates the title from the citation.
- Section headings use `## Title {#anchor-id}` for navigation targeting.
- Static files (CV PDF, profile photo) are served from the repo root.

## Deployment

Push to `main` branch → GitHub Pages builds and deploys automatically. No CI/CD config needed.
