# Pokopia Strategy Blog

A bilingual (English + 中文) strategy blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. Deployed automatically to GitHub Pages with Pagefind search.

## Quick Start

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.145.0+)
- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/) 22+ (for Pagefind, optional for local dev)

### Setup

```bash
# Clone and init submodules
git clone https://github.com/YOUR_USER/pokopia-blog.git
cd pokopia-blog
git submodule update --init --recursive

# Run locally
hugo server -D
# → http://localhost:1313/en/
```

### First-time setup (new repo)

```bash
cd pokopia-blog
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git add .
git commit -m "Initial commit: Pokopia blog scaffold"
git remote add origin https://github.com/YOUR_USER/pokopia-blog.git
git branch -M main
git push -u origin main
```

## Writing Posts

### Create a new English post

```bash
hugo new content/en/strategies/my-new-guide.md
```

### Create a new Chinese post

```bash
hugo new content/zh/strategies/my-new-guide.md
```

### Frontmatter template

```yaml
---
title: "Your Title Here"
date: 2026-03-13
draft: false
tags: ["tag1", "tag2"]
categories: ["Team Building"]
description: "Short description for SEO and previews."
ShowToc: true
TocOpen: true
cover:
  image: "images/cover.png"  # optional
  alt: "Cover image description"
---
```

### Linking translations

Posts with the **same filename** in `content/en/` and `content/zh/` are automatically linked as translations. For example:

- `content/en/strategies/rain-team-guide.md` ↔ `content/zh/strategies/rain-team-guide.md`

The language switcher will appear automatically when a translation exists.

## Content Structure

```
content/
├── en/
│   ├── strategies/         # English strategy guides
│   │   ├── _index.md       # Section page
│   │   └── rain-team-guide.md
│   └── search.md           # Search page
└── zh/
    ├── strategies/         # Chinese strategy guides
    │   ├── _index.md
    │   └── rain-team-guide.md
    └── search.md
```

## Deployment (GitHub Pages)

Deployment is **fully automatic** via GitHub Actions.

### One-time GitHub setup

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. That's it. Push to `main` and the site builds + deploys automatically.

### What happens on push

1. Hugo builds the site
2. Pagefind indexes all HTML for search
3. Site deploys to GitHub Pages

### Custom domain (optional)

1. Add a `CNAME` file in `static/` with your domain:
   ```
   blog.pokopia.com
   ```
2. Configure DNS (CNAME to `YOUR_USER.github.io`)
3. Enable HTTPS in GitHub Pages settings

## Search

Search is powered by [Pagefind](https://pagefind.app/), which runs at build time and creates a static search index. No external services needed.

The search page is available at:
- English: `/en/search/`
- Chinese: `/zh/search/`

## Local Development

```bash
# Start dev server with drafts
hugo server -D

# Build for production (without Pagefind)
hugo --gc --minify

# Build with Pagefind (full production build)
hugo --gc --minify && npx pagefind --site public
```

## Theme Customization

The site uses PaperMod with minimal overrides:

- `layouts/partials/extend_head.html` — Pagefind CSS/JS
- `layouts/partials/extend_footer.html` — Language switcher widget

To customize further, see the [PaperMod docs](https://adityatelange.github.io/hugo-PaperMod/).

## License

Content is © Pokopia. Theme is MIT licensed.
