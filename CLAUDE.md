# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
hugo server        # local dev server at http://localhost:1313
hugo server -D     # include draft posts
hugo               # build to public/
hugo --minify      # production build (what CI runs)
hugo new writeups/<slug>.md  # scaffold a new writeup
```

Deployment is automatic: push to `main` → GitHub Actions runs `hugo --minify` → deploys `public/` to GitHub Pages.

## Architecture

This is a **custom Hugo site with no theme** — all layouts, CSS, and JS are hand-written. There are no npm dependencies or build tools beyond Hugo itself.

### Layouts

- `layouts/_default/baseof.html` — HTML shell; loads fonts (Sora, Inter, JetBrains Mono), `main.css`, and an inline theme-init script that reads `localStorage` before paint to prevent flash
- `layouts/index.html` — homepage: intro blurb + last 5 writeups from `content/writeups/`
- `layouts/_default/single.html` — handles two cases via `{{ if eq .Section "writeups" }}`: full writeup layout (breadcrumb, badges, TOC, prev/next nav, flag box, tags, related) or a minimal generic page layout (About, etc.)
- `layouts/_default/list.html` — writeups index page
- `layouts/partials/header.html` / `footer.html` — site chrome

### Render hooks (Markdown extensions)

- `layouts/_default/_markup/render-codeblock.html` — replaces standard fenced code blocks with a custom component: traffic-light dots, optional `filename` attribute, line-number gutter, Hugo Chroma highlighting. Usage: ` ```bash {filename="exploit.sh"} `
- `layouts/_default/_markup/render-blockquote.html` — maps GitHub-style callouts to styled divs. `> [!note]` → `.note`, `> [!warning]` / `> [!caution]` → `.warn`, `> [!tip]` → `.note`

### Static assets

- `static/css/main.css` — all styles; uses CSS custom properties for theming. Two palettes: `[data-theme="dark"]` (default, set on `<html>`) and `[data-theme="light"]`. Accent color is teal `#41C7B0` (`--accent`). Code blocks always use a dark background regardless of theme.
- `static/js/theme.js` — toggles `data-theme` on `<html>` and persists to `localStorage`

### Content

All writeups live in `content/writeups/`. Front matter fields:

```yaml
title: "Challenge Name — Short description"
date: YYYY-MM-DD
category: "Web Exploitation"   # drives breadcrumb & related writeups
difficulty: "Easy"             # pill badge
tags: ["web", "idor"]          # tag pages + pill links at bottom
flag: "CTF{...}"               # rendered in a highlighted flag box
prev:                          # optional sequential navigation
  title: "Previous post title"
  url: "/writeups/slug/"
next:
  title: "Next post title"
  url: "/writeups/slug/"
```

New posts are created as drafts (`draft: true`); remove that field to publish.

### Deployment

`.github/workflows/deploy.yml` uses `peaceiris/actions-hugo` + `peaceiris/actions-gh-pages`. The `public/` directory is the build output and is committed/deployed by CI — do not edit files there manually.
