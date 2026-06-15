# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A pure static HTML/CSS website for AI-guided learning of 《新概念英语第二册》(NCE Book 2, L.G. Alexander). No build tools, no JavaScript frameworks, no package manager. Deployed to Cloudflare Pages.

Live URL: `https://nce-book2.pages.dev`

## Deploy

```bash
npx wrangler pages deploy . --project-name nce-book2
```

No `npm install` is needed — wrangler runs via `npx`. The site is served from the repo root; `wrangler.toml` sets `pages_build_output_dir = "."`.

## File structure and naming

```
├── index.html                # Home page — progress stats + lesson/reference cards
├── lessons/                  # One HTML file per lesson
│   ├── 0001-welcome-and-lesson1.html
│   ├── 0002-breakfast-or-lunch.html
│   └── ...                   # Pattern: {NNNN}-{lesson-slug}.html
├── reference/                # Grammar & topic reference pages (HTML)
├── learning-records/         # Markdown notes per lesson/session
│   ├── 0001-*.md
│   └── ...                   # Pattern: {NNNN}-{slug}.md
├── MISSION.md                # Learning goals, pace, success criteria
├── NOTES.md                  # Teaching methodology & learner preferences
├── README.md                 # Project README with progress table
├── wrangler.toml             # Cloudflare Pages config
└── .gitignore                # Ignores .wrangler/ and node_modules/
```

## Page template conventions

All HTML pages share:
- Inline `<style>` in `<head>` with a consistent `:root` CSS variable set
- Max-width container (860px lessons, 960px index/reference)
- Lesson page structure: breadcrumb → `<h1>` title → `.lesson-meta` → 课文 (`.text-box` with `.en` + `.zh`) → vocabulary (`.vocab-grid`) → key structures (`.ks-box`) → exercises (`.exercise` with collapsible `.answer-box`)

## Adding a new lesson

1. Create `lessons/{NNNN}-{slug}.html` following the existing lesson template
2. Add a `<a class="lesson-card">` entry to `index.html` in the lesson grid
3. Update the stats counter in `index.html` (the `.stat-item .num` for completed lessons)
4. Update the progress table in `README.md`
5. Create `learning-records/{NNNN}-{slug}.md` with frontmatter

## Adding a new reference page

1. Create `reference/{slug}.html` following the reference template
2. Add a `<a class="ref-card">` entry to `index.html` in the reference grid
3. Update the reference count in `index.html`

## Learning records frontmatter

Each `.md` in `learning-records/` starts with:
```yaml
---
name: <kebab-case-id>
description: <one-line summary>
metadata:
  type: project
---
```
