# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Overview

- This repository is the source for the personal site hosted at `https://jiangbingo.github.io` via GitHub Pages.
- The site is a fully static HTML/CSS site; there is no build pipeline, bundler, or client-side framework.
- The repository root is served directly by GitHub Pages (no `docs/` or `dist/` subdirectory).

## Local development

The only requirement to preview the site is a basic static file server (Python ≥ 3.12 is configured via `.python-version` and `pyproject.toml`).

- From the project root, start a local HTTP server:

  ```bash
  python -m http.server 8000
  ```

- Then open `http://localhost:8000` in a browser to view the site as GitHub Pages would serve it.

There is a trivial `main.py` that just prints a greeting and is currently unrelated to the static site. You generally do not need to run it when working on the pages.

## Deployment to GitHub Pages

The site is intended to be deployed from this repository to the `jiangbingo/jiangbingo.github.io` GitHub repo, using the `master` branch and the repository root as the Pages source.

High level deployment flow (see `README.md` for exact commands):

1. Initialize the repo (if not already) and set `master` as the default branch.
2. Add the `jiangbingo/jiangbingo.github.io` remote and push the current contents to the `master` branch.
3. In GitHub → **Settings → Pages**, configure:
   - Source: `Deploy from a branch`
   - Branch: `master`
   - Directory: `/ (root)`

Once configured, pushing changes to `master` will update `https://jiangbingo.github.io` after a short delay.

## Project structure and architecture

High-level layout (only key pieces):

- `index.html`: main landing page / résumé-style homepage (Chinese), linking to sections such as skills, projects, experience, and contact.
- `assets/style.css`: single global stylesheet defining layout, typography, color scheme, and both homepage and blog styles.
- `blog/`
  - `index.html`: blog listing page with cards linking to individual articles.
  - `rag-backend-fastapi.html`: example article page, using the same header/footer and CSS as the listing.
- `江斌-Python.pdf`: downloadable PDF résumé linked from the homepage.
- `pyproject.toml`: minimal Python project metadata (name, version, Python ≥ 3.12), currently without dependencies or tooling configuration.

Key architectural points:

- **No build step**: HTML and CSS files under the repository root are exactly what GitHub Pages serves. Any structural change (navigation, sections, SEO metadata) requires editing the HTML directly.
- **Shared styling**: `assets/style.css` is the single source of truth for visual design across both the homepage and blog. When adding new pages, re-use existing utility classes and layout patterns rather than introducing new inline styles.
- **Blog pattern**:
  - `blog/index.html` acts as a manually maintained index of article cards.
  - Individual posts live in `blog/*.html` and follow the same header/footer and container structure as `rag-backend-fastapi.html`.
  - To add a new article, create a new HTML file under `blog/` based on the existing article template and add a corresponding card/link in `blog/index.html`.
- **SEO and Chinese content**: The documents include Chinese titles and descriptions tailored for search and readability. When modifying `<title>` or `<meta name="description">`, preserve the intent and language.

## Working with Python tooling

- `pyproject.toml` and `.python-version` specify Python 3.12, but there is no configured test, lint, or formatting toolchain yet, and `dependencies` is empty.
- There are currently **no automated tests or linters** to run for this project; if you add them (e.g., `pytest`, `ruff`, `black`), ensure their invocation commands are documented in `README.md` and consider updating this `WARP.md` with the canonical commands.