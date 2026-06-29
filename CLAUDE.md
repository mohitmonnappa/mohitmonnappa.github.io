# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
hugo server        # local dev server at http://localhost:1313
hugo server -D     # include draft posts
hugo --minify      # production build (what CI runs)
```

Deployment is automatic: push to `main` → GitHub Actions runs `hugo --minify` → deploys `public/` to GitHub Pages. Do not edit `public/` manually.

## Architecture

Hugo site using the **PaperMod theme** (git submodule at `themes/PaperMod/`). Requires Hugo ≥ 0.146.0 (site runs 0.163.3 extended). No npm, no build tools beyond Hugo.

### Theme override pattern

PaperMod partials live in `themes/PaperMod/layouts/_partials/`. Project files in `layouts/` take precedence over the theme via Hugo's lookup order. The key overrides are:

- `layouts/_default/baseof.html` — adds the hero banner (shown on all pages except home and individual content pages), sets `has-hero` body class, controls `$showHero` logic
- `layouts/index.html` — home page: renders `index_profile.html` partial + last 5 posts from `mainSections`
- `layouts/posts/single.html` — custom single post template with category/difficulty badges, prev/next level nav (front matter driven), flag box, shuffled related posts
- `layouts/posts/list.html` — uses `.RegularPagesRecursive` (not `.Pages`) so nested subsections appear in the listing
- `layouts/projects/list.html` / `layouts/projects/single.html` — projects section templates

### CSS

All custom styles live in **`assets/css/extended/custom.css`**. PaperMod automatically loads every file in `assets/css/extended/` after its own CSS. Do not create `static/css/` files — they won't integrate with PaperMod's variable system.

Dark mode uses `.dark` body class (PaperMod convention, not `[data-theme="dark"]`). CSS custom properties: `--accent` (teal), `--accent-soft`, `--primary`, `--secondary`, `--border`, `--entry` from PaperMod; `--main-width: 860px` set in custom.css.

### Content structure

```
content/
  about.md                        # standalone page
  posts/
    _index.md                     # section title shown in hero banner
    overthewire/
      bandit/
        bandit01.md … bandit33.md # individual level writeups
        walkthrough.md            # index listing all levels
```

`mainSections = ["posts"]` in `hugo.toml` — only this section appears on the home page and in PaperMod's built-in nav links.

### Front matter for posts

```yaml
title: "OverTheWire: Bandit — Level N"
date: YYYY-MM-DD
category: "Linux"          # drives related posts matching
difficulty: "Easy"         # pill badge (optional)
tags: ["ctf", "bandit"]    # tag taxonomy pages
flag: "flag{...}"          # renders highlighted flag box (optional)
prev:                      # sequential nav rendered above content
  title: "Level N-1"
  url: "/posts/overthewire/bandit/banditNN/"
next:                      # sequential nav rendered below content
  title: "Level N+1"
  url: "/posts/overthewire/bandit/banditNN/"
```

Prev/next are front matter driven (not PaperMod's `post_nav_links.html`) so order is explicit, not date-based.

### Render hooks

- `layouts/_default/_markup/render-codeblock.html` — custom code block: traffic-light dots, optional `{filename="x"}` attribute, line-number gutter, Chroma highlighting
- `layouts/_default/_markup/render-blockquote.html` — GitHub-style callouts: `> [!note]` → `.note`, `> [!warning]`/`> [!caution]` → `.warn`

`markup.goldmark.renderer.unsafe = true` is set, so raw HTML in Markdown is rendered.

### Security constraints

- `resume.md` and `bandit_writeup.md` are gitignored — never commit them
- `content/about.md` must only contain information from `resume.md` — no phone number, no Class XII education
- Profile photo is at `static/images/` and referenced via `/images/...` in `hugo.toml` `profileMode.imageUrl`
