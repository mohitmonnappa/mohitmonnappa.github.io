# Personal Cybersecurity Writeup Blog - Project Brief

## Overview

Build a personal blog for CTF and cybersecurity challenge writeups.
Modelled after [mayadevbe.me](https://mayadevbe.me) in structure and layout,
but with a fresh design, and a light/dark mode toggle.

---

## Tech Stack

| Layer | Choice |
|-------|--------|
| Static site generator | Hugo |
| Hosting | GitHub Pages |
| Deployment | GitHub Actions (auto-deploy on push to `main`) |
| DNS / Domain | Custom domain - registrar TBD (Namecheap / Cloudflare / Porkbun) |
| Writing | Markdown `.md` files |

---

## Decisions Still Needed From Owner

Before starting, confirm these two things with Naren:

1. **Accent colour** - indigo `#5145CD` or teal `#41C7B0`? (used in both light and dark mode)
2. **Display / heading font** - `Space Grotesk` or `Sora`?
3. **GitHub username** - needed for Pages and Actions config
4. **Domain name** - already purchased, or still to buy?

---

## Design

### Theme

Clean, structured writeup blog. Readable and professional.
Not dark/terminal/hacker aesthetic - no neon-on-black, no glitch effects.

### Light / Dark Mode

- Single CSS variable set, swapped via `data-theme` attribute on `<html>`
- Toggle button in the site header
- On first load: respect OS `prefers-color-scheme`
- Save preference to `localStorage`

### Colour Tokens

| Token | Light mode | Dark mode |
|-------|-----------|-----------|
| `--bg` | `#F7F8FB` | `#0F141A` |
| `--surface` | `#FFFFFF` | `#161D25` |
| `--surface-2` | - | `#1B232C` |
| `--ink` | `#181C28` | `#E8ECF1` |
| `--ink-soft` | `#4A5167` | `#AAB4C0` |
| `--muted` | `#8A92A6` | `#6E7884` |
| `--line` | `#E6E9F0` | `#242E38` |
| `--accent` | *(chosen colour, same in both)* | *(same)* |
| `--accent-soft` | light tint of accent | dark tint of accent |
| `--code-bg` | `#1B1E2B` | `#0B0F14` |
| `--code-ink` | `#E7E9F2` | `#D6DEE7` |
| `--code-gutter` | `#5A6178` | `#4A5562` |

### Typography

| Role | Font |
|------|------|
| Display / headings | `Space Grotesk` or `Sora` *(confirm with owner)* |
| Body | `Inter` |
| Code / monospace | `JetBrains Mono` |

Load all three from Google Fonts.

### Reference HTML Samples

Two fully designed reference pages are provided alongside this brief:

- `writeup-A-light-indigo.html` - light skin with indigo accent
- `writeup-B-dark-teal.html` - dark skin with teal accent

Use these as the visual and structural reference for the Hugo theme.
Pixel-match the layout, spacing, components, and code block styling from these files.

---

## Site Structure

```
/                        Homepage - intro + latest writeups
/writeups/               All writeups index (filterable by tag/category)
/writeups/[slug]/        Individual writeup post
/tags/                   Tag index
/tags/[tag]/             Writeups filtered by that tag
/about/                  About page
```

---

## Hugo Project Structure

```
.
├── config.toml                  # Site config (title, baseURL, paginate, etc.)
├── content/
│   ├── writeups/
│   │   ├── _index.md
│   │   ├── happyvault-idor.md   # Example writeup
│   │   └── ...
│   └── about.md
├── layouts/
│   ├── _default/
│   │   ├── baseof.html          # Base template - header, footer, theme toggle
│   │   ├── list.html            # Writeups index
│   │   └── single.html         # Individual writeup post
│   ├── index.html               # Homepage
│   └── partials/
│       ├── header.html
│       ├── footer.html
│       └── theme-toggle.html
├── static/
│   ├── css/
│   │   └── main.css
│   └── js/
│       └── theme.js
└── .github/
    └── workflows/
        └── deploy.yml           # GitHub Actions - build and deploy to gh-pages
```

---

## Individual Writeup Post - Page Structure

Every writeup page must include these sections in this order:

1. **Breadcrumb** - `writeups / [category] / [slug]`
2. **Category + difficulty badges** - e.g. `Web Exploitation · Easy`
3. **Title** - `h1`, display font
4. **Post meta row** - published date · read time · flag captured ✓
5. **Prev / Next strip** - links to adjacent challenges
6. **Table of contents** - "On this page", generated from `##` headings
7. **Prose body** - sections with `##` headings, hash prefix styled in accent colour
8. **Line-numbered syntax-highlighted code blocks** - with filename + language label in header
9. **Callout boxes** - two variants:
   - `> [!note]` - accent colour left border
   - `> [!warning]` - amber left border
10. **Flag box** - dashed border, monospace flag value, "FLAG" label
11. **Tags strip** - pill tags linking to `/tags/[tag]/`
12. **Related writeups** - 2-column card grid, pulled from same category or shared tags

---

## Writeup Frontmatter

Every writeup `.md` file uses this frontmatter:

```yaml
---
title: "HappyVault - Reading other people's notes (IDOR)"
date: 2026-06-22
category: "Web Exploitation"
difficulty: "Easy"
tags: ["web", "idor", "access-control", "beginner"]
flag: "CTF{idor_is_an_access_control_bug}"
prev:
  title: "SimpleLogin - Auth bypass"
  url: "/writeups/simplelogin-auth-bypass/"
next:
  title: "TokenForge - JWT none-alg"
  url: "/writeups/tokenforge-jwt/"
---
```

---

## Light / Dark Toggle Logic

Create `static/js/theme.js`:

```javascript
// On page load - respect OS preference, then saved preference
const saved = localStorage.getItem('theme');
const preferred = window.matchMedia('(prefers-color-scheme: dark)').matches
  ? 'dark' : 'light';
document.documentElement.setAttribute('data-theme', saved || preferred);

// Toggle function - called by the button in the header
function toggleTheme() {
  const current = document.documentElement.getAttribute('data-theme');
  const next = current === 'dark' ? 'light' : 'dark';
  document.documentElement.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
}
```

The toggle button should show a sun icon in dark mode and a moon icon in light mode.
No page reload - the swap is instant via the CSS variable system.

---

## Code Block Styling

Code blocks are a core feature of every writeup. They must have:

- Dark background (`--code-bg`) in both light and dark mode
- A header bar showing: three decorative dots + filename on the left + language label on the right
- A gutter column with line numbers (non-selectable, separated by a faint vertical rule)
- Syntax highlighting using these token colours:

| Token | Colour |
|-------|--------|
| Keywords | `#7FB4FF` |
| Strings | `#7FE3A0` |
| Comments | `#5C6773` (italic) |
| Numbers / constants | `#E8B05B` |
| Functions | accent colour |

Use Hugo's built-in Chroma syntax highlighting configured in `config.toml`,
styled to match the token colours above via custom CSS.

---

## GitHub Actions Deploy

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: true
      - uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: 'latest'
          extended: true
      - run: hugo --minify
      - uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

---

## Custom Domain Setup (after GitHub Pages is live)

1. In the repo → Settings → Pages → set custom domain to `yourdomain.com`
2. GitHub will create a `CNAME` file in the repo automatically
3. At the DNS registrar, add these records:

| Type | Host | Value |
|------|------|-------|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `[github-username].github.io` |

4. Wait up to 30 minutes for DNS to propagate
5. Enable "Enforce HTTPS" in Pages settings once the certificate is issued

---

## Example Writeup File

Create `content/writeups/happyvault-idor.md` as the first working post
to validate the template. Use this content:

```markdown
---
title: "HappyVault - Reading other people's notes (IDOR)"
date: 2026-06-22
category: "Web Exploitation"
difficulty: "Easy"
tags: ["web", "idor", "access-control", "beginner"]
flag: "CTF{idor_is_an_access_control_bug}"
prev:
  title: "SimpleLogin - Auth bypass"
  url: "/writeups/simplelogin-auth-bypass/"
next:
  title: "TokenForge - JWT none-alg"
  url: "/writeups/tokenforge-jwt/"
---

## The challenge

HappyVault is a small "private notes" web app. You get an account,
you save notes, nobody else can see them. Our job is to read the
note belonging to the admin, which contains the flag.

Target: `https://happyvault.chal.example/`

## Recon

After logging in, opening a note makes a GET request with a numeric id:

```bash
$ curl -s -b "session=eyJ1aWQiOj4..." \
       https://happyvault.chal.example/api/note?id=4081

{"id":4081,"owner":"naren","body":"grocery list"}
\```

The server returns the note based on id alone - no ownership check.

> [!note]
> Whenever an app fetches a resource by an id you control,
> ask: does the server verify you are allowed to see it?

## Why this works

This is a textbook **IDOR** - Insecure Direct Object Reference.
The app exposes an internal identifier directly to the user and
forgets the authorization step.

## Getting the flag

```bash
$ for id in $(seq 1 10); do
    curl -s -b "session=eyJ1aWQiOjQ..." \
         https://happyvault.chal.example/api/note?id=$id
  done

{"id":3,"owner":"admin","body":"flag: CTF{idor_is_an_access_control_bug}"}
\```

## How you'd fix it

On every lookup, verify the note's owner matches the logged-in user
before returning it.

> [!warning]
> UUIDs instead of sequential ids make enumeration harder,
> but an IDOR is still an IDOR. Authorization is the real fix.
```

---

## Build Order for Claude Code

Work in this order:

1. Scaffold Hugo project (`hugo new site`)
2. Set up `config.toml` with site title, baseURL placeholder, Chroma config
3. Build `main.css` - CSS variables, light/dark tokens, all component styles
4. Build `theme.js` - toggle logic
5. Build `baseof.html` - base layout with header, nav, theme toggle, footer
6. Build `single.html` - individual writeup post template (most complex)
7. Build `list.html` - writeups index
8. Build `index.html` - homepage
9. Create the example writeup `happyvault-idor.md` and verify it renders correctly
10. Create `about.md` with placeholder content
11. Set up `.github/workflows/deploy.yml`
12. Verify `hugo server` runs clean with no errors or warnings
