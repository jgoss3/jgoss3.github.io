# Jacob Goss Personal Website

## Overview
Academic personal website for Jacob Goss, Economics PhD student at UW-Madison. Built with Hugo using the "academimal" theme (originally from gautamrao.github.io). Deployed to GitHub Pages at https://jgoss3.github.io/ via GitHub Actions.

## Tech Stack
- **Static site generator**: Hugo (v0.155.2+)
- **Theme**: academimal (in `themes/academimal/`, originally a git submodule from yangl1996/academimal)
- **Deployment**: GitHub Actions (`.github/workflows/hugo.yml`) → GitHub Pages
- **Repo**: github.com/jgoss3/jgoss3.github.io (branch: `main`)

## Key Files to Edit

### Content
- `content/sections/aboutme.md` — Bio text and CV link
- `content/sections/contact.md` — Email and contact info
- `content/goss_cv.pdf` — CV PDF (linked from bio)
- `content/prof_pic.jpg` — Profile photo (shown in sidebar)
- `content/favicon.ico` — Tab icon (Bucky Badger)

### Publication Data (YAML)
- `data/publications/list.yaml` — Peer-reviewed publications (1 paper: Education Finance and Policy 2024)
- `data/work_in_progress/list.yaml` — Working papers (2 papers: betting/sports, refinancing)
- `data/working_papers/list.yaml` — Policy & Blogs section (3 Liberty Street Economics articles, each with media coverage links)

YAML structure for publications:
```yaml
works:
- title: "Paper Title"
  pdflink: "https://..."
  book: "Journal Name, Year"
  coauthors: "Name1 and Name2"
  abstract: >
    Abstract text here
  media:
    - text: "Outlet Name"
      url: "https://..."
```

### Layout Overrides (override theme without modifying submodule)
- `layouts/index.html` — Main page structure. Section order: Bio → Contact → Publications → Working Papers → Policy & Blogs
- `layouts/partials/header.html` — Page header with title, short bio, sidebar, photo, and Google Scholar/LinkedIn SVG icons below photo
- `layouts/partials/sidebar.html` — Navigation links: Bio, Contact, CV, Publications, Working Papers, Policy & Blogs
- `layouts/partials/publication.html` — Renders each paper entry. Supports expandable abstracts and per-paper "Media Coverage" dropdown via `<details>` element
- `layouts/partials/foot.html` — Footer with JS toggle function for abstract expand/collapse

### Config
- `config.toml` — Site title ("Jacob Goss"), short bio, profile photo path, Google Scholar URL, LinkedIn URL. Has `[markup.goldmark.renderer] unsafe = true` to allow HTML in markdown.

## Deployment
Push to `main` branch triggers GitHub Actions build and deploy automatically. To deploy:
```bash
cd ~/Library/CloudStorage/Dropbox/website
git add -A && git commit -m "description" && GH_CONFIG_DIR=~/.gh git push
```

## Local Development
```bash
cd ~/Library/CloudStorage/Dropbox/website
hugo server
# Visit http://localhost:1313/
```

## GitHub CLI
`gh` is authenticated as jgoss3. Requires `export GH_CONFIG_DIR=~/.gh` before any `gh` commands (the default `.config/gh` dir has root ownership issues).

## TODOs
- Fill in abstract for "Betting Across Borders" paper (currently ABSTRACT PLACEHOLDER)
- Favicon: Bucky Badger ICO is in place but browser caching may show old W icon. Try incognito/new browser.
- Add media coverage links to more papers as needed
