# Blog Control — Centralized Template Management for Security Medic Blogs

**Owner:** Blog Content Agent  
**Version:** 0.1.0 (planning)  
**Status:** Design Phase  

---

## What This Is

A CLI tool and template library that manages the look, feel, and structure of all Security Medic blog sites hosted on GitHub Pages. One command applies a template to any blog. One config file controls which template each blog uses. Templates are versioned, interchangeable, and designed to work on any blog without modification.

## The Problem

Today, each blog has a unique, hand-crafted format created at different times. There's no way to:
- Apply a consistent update across all blogs
- Swap the visual theme of a blog without manually editing every HTML file
- Ensure new posts match the blog's current style
- Rotate featured content on index pages intelligently

## The Solution

A **global template library** with versioned, interchangeable templates that can be applied to any blog via CLI.

---

## Architecture

```
blog-control/
├── README.md
├── blog-control.sh              # Main CLI tool
├── config.json                  # Which template each blog uses
├── templates/
│   ├── modern-editorial/        # Template 1
│   │   ├── v1.0/
│   │   │   ├── index.html       # Index page template
│   │   │   ├── post.html        # Blog post template
│   │   │   ├── style.css        # Shared stylesheet
│   │   │   ├── components/
│   │   │   │   ├── header.html
│   │   │   │   ├── footer.html
│   │   │   │   ├── post-card.html
│   │   │   │   ├── featured-series.html
│   │   │   │   └── category-nav.html
│   │   │   └── preview.png      # Visual preview
│   │   └── CHANGELOG.md
│   ├── clean-professional/      # Template 2
│   │   ├── v1.0/
│   │   │   └── (same structure)
│   │   └── CHANGELOG.md
│   └── bold-minimal/            # Template 3
│       ├── v1.0/
│       │   └── (same structure)
│       └── CHANGELOG.md
├── themes/                      # Color/font palettes per blog
│   ├── data-security.json
│   ├── compliance.json
│   ├── leadership.json
│   ├── cfs-2.json
│   ├── data-privacy.json
│   ├── cloud-architecture.json
│   └── ai-security.json
├── legacy/                      # Preserved original formats
│   ├── leadership-original/
│   ├── compliance-original/
│   ├── data-security-original/
│   ├── cfs-2-original/
│   ├── data-privacy-original/
│   └── cloud-architecture-original/
├── scripts/
│   ├── generate-index.py        # Rebuilds index.html from post metadata
│   ├── apply-template.py        # Applies template + theme to a blog repo
│   ├── rotate-featured.py       # Smart featured content rotation
│   └── audit-templates.py       # Checks all blogs for template compliance
└── docs/
    ├── PLAN.md                  # This design document
    ├── runbooks/
    │   ├── featured-rotation.md # Smart rotation criteria
    │   └── template-upgrade.md  # How to version-bump a template
    └── examples/
        └── screenshots/
```

---

## Global Template Library

### Three Templates (v1.0)

Each template provides a complete visual system: index page, post page, header, footer, navigation, and components. All templates are designed to work on ANY blog with a theme file providing the color/font customization.

#### Template 1: `modern-editorial`
- **Vibe:** Clean, magazine-style editorial layout. Playfair Display headlines, generous whitespace, warm tones.
- **Inspired by:** Current leadership blog (refined and generalized)
- **Index:** Hero section with blog identity, featured series banner, categorized post cards with dates and read times
- **Posts:** Article-focused, wide reading column, pull quotes, subtle accent colors
- **Best for:** Leadership, strategy, governance content

#### Template 2: `clean-professional`
- **Vibe:** Corporate-clean, data-forward. Inter/system font stack, crisp borders, structured grid.
- **Index:** Compact card grid, filter bar by category, date-sorted with clear metadata
- **Posts:** Structured with sidebar TOC, code blocks styled for technical content, reference sections
- **Best for:** Compliance, technical, data-heavy content

#### Template 3: `bold-minimal`
- **Vibe:** Bold headlines, dark mode option, striking contrast. Modern tech aesthetic.
- **Index:** Full-width post previews with bold titles, category pills, urgency indicators
- **Posts:** Immersive reading experience, dark/light toggle, minimal chrome
- **Best for:** Security alerts, AI/emerging tech, incident analysis

### Template Structure

Each template uses **placeholder variables** that get replaced by the theme file:

```html
<!-- In template -->
<style>
  :root {
    --primary: {{PRIMARY_COLOR}};
    --secondary: {{SECONDARY_COLOR}};
    --accent: {{ACCENT_COLOR}};
    --bg: {{BG_COLOR}};
    --text: {{TEXT_COLOR}};
    --font-heading: {{FONT_HEADING}};
    --font-body: {{FONT_BODY}};
    --font-mono: {{FONT_MONO}};
    --site-name: "{{SITE_NAME}}";
    --site-tagline: "{{SITE_TAGLINE}}";
    --site-url: "{{SITE_URL}}";
  }
</style>
```

### Theme Files

Each blog has a JSON theme file:

```json
{
  "blog_id": "data-security-blog",
  "site_name": "Data Security",
  "site_tagline": "Software Security, AI & Security, Compliance",
  "site_url": "https://data-security.blog/",
  "base_url": "https://data-security.blog",
  "repo": "sm911/data-security-blog",
  "local_path": "~/projects/data-security-blog",
  "colors": {
    "primary": "#1e3a5f",
    "secondary": "#2c5282",
    "accent": "#e53e3e",
    "bg": "#f7fafc",
    "text": "#1a202c"
  },
  "fonts": {
    "heading": "'Inter', 'Segoe UI', sans-serif",
    "body": "'Inter', 'Segoe UI', sans-serif",
    "mono": "'JetBrains Mono', monospace"
  },
  "categories": [
    "AI & Security",
    "Software Security",
    "Supply Chain Risk",
    "Compliance",
    "Cybersecurity",
    "Healthcare"
  ],
  "meta": {
    "og_site_name": "Security Medic - Data Security",
    "author": "Jim Venuto",
    "keywords_base": "data security, cybersecurity, SMB security"
  }
}
```

---

## CLI Usage

### Apply a template to a blog

```bash
./blog-control.sh apply --blog data-security-blog --template modern-editorial
```

This:
1. Reads the blog's theme file (`themes/data-security.json`)
2. Loads the template (`templates/modern-editorial/v1.0/`)
3. Merges theme variables into template placeholders
4. Regenerates `index.html` from post metadata
5. Optionally applies post template to all/new posts
6. Commits and pushes to the blog repo

### Preview a template

```bash
./blog-control.sh preview --blog data-security-blog --template bold-minimal
```

Generates a local preview without pushing.

### Switch a blog's template

```bash
./blog-control.sh switch --blog data-security-blog --template clean-professional
```

Updates `config.json` and applies the new template.

### Rebuild index only

```bash
./blog-control.sh index --blog data-security-blog
```

Regenerates `index.html` with current featured rotation, new posts, categories. Uses the blog's active template.

### Rotate featured content

```bash
./blog-control.sh rotate --blog data-security-blog
```

Runs the smart rotation logic (see Featured Rotation below).

### Audit all blogs

```bash
./blog-control.sh audit
```

Checks all blogs for:
- Template version currency
- Missing meta tags
- Missing dates on posts
- Featured content staleness
- Category consistency

### List templates

```bash
./blog-control.sh list
```

Shows all templates with version, preview, and which blogs use them.

---

## Config File

`config.json` — single source of truth for blog-template mapping:

```json
{
  "blogs": {
    "data-security-blog": {
      "template": "modern-editorial",
      "version": "v1.0",
      "featured_rotation": true,
      "apply_to_posts": "new_only"
    },
    "compliance-blog": {
      "template": "clean-professional",
      "version": "v1.0",
      "featured_rotation": true,
      "apply_to_posts": "new_only"
    },
    "leadership": {
      "template": "legacy",
      "version": "current",
      "featured_rotation": false,
      "apply_to_posts": "none"
    }
  }
}
```

The `"legacy"` template means "don't touch — use the existing format."

---

## Featured Content Rotation

### Smart Rotation Criteria

The `rotate-featured.py` script selects featured posts based on weighted scoring:

| Factor | Weight | Description |
|---|---|---|
| Recency | 30% | Newer posts score higher. Decay curve: full score < 7 days, half score < 30 days, minimal > 60 days |
| Urgency | 25% | Posts tagged P1/P2 in the publishing schedule score higher |
| Vertical relevance | 20% | Posts targeting the blog's primary vertical(s) score higher |
| Series membership | 15% | Posts that are part of an active series get a boost (maintains narrative momentum) |
| Gap filling | 10% | Posts in underrepresented categories get a boost |

### Rotation Cadence
- Runs on every `index` rebuild or explicitly via `rotate`
- Featured section shows 1-3 posts (configurable per template)
- Posts rotate out after 14 days unless urgency keeps them pinned
- Manual pin: add `"featured_pin": true` to post metadata to keep a post featured

### Runbook
Detailed rotation runbook at `docs/runbooks/featured-rotation.md`.

---

## Backward Compatibility

### Strategy: Progressive Enhancement

- **Existing posts** keep their current inline `<style>` and structure
- **New posts** use the external template + theme CSS
- **Index pages** get fully regenerated (they're just listings, no unique content to preserve)
- **Backward-compatible detection:** The `apply-template.py` script detects whether a post uses legacy inline styles or the new template system, and handles each accordingly

### Migration Path (per blog)

1. **Phase 1:** Apply new template to `index.html` only — immediate visual upgrade with zero risk to posts
2. **Phase 2:** Apply new template to new posts going forward
3. **Phase 3 (optional):** Retrofit existing posts if the blog owner wants full consistency

Each blog can be at a different phase. Config tracks this via `apply_to_posts`: `none` | `new_only` | `all`.

---

## Post Metadata

Each blog post needs a metadata block (HTML comment at top of file) for the template system to work:

```html
<!-- blog-control-meta
title: Your AI Vendor's Supply Chain Just Became Your Biggest Attack Surface
author: Jim Venuto
date: 2026-03-25
category: AI & Security
tags: supply chain, LiteLLM, PyPI, TeamPCP
read_time: 8 min
series: LiteLLM Supply Chain Attack Series
priority: P1
description: On March 24, a backdoor was planted in LiteLLM — a Python package downloaded 95 million times per month...
-->
```

The template system reads this to:
- Generate index.html listings (title, date, category, read time)
- Build meta tags (description, OG, Twitter)
- Determine featured rotation scoring
- Sort and categorize posts

---

## Development Plan

### Phase 1: Foundation (Week 1)
- [ ] Set up project structure
- [ ] Create theme files for all 7 blogs
- [ ] Preserve all existing blog formats in `legacy/`
- [ ] Build `generate-index.py` — reads post metadata, generates index.html
- [ ] Build `apply-template.py` — merges template + theme
- [ ] Fix cloud-architecture missing dates (immediate)

### Phase 2: Templates (Week 2)
- [ ] Design and build Template 1: `modern-editorial`
- [ ] Design and build Template 2: `clean-professional`
- [ ] Design and build Template 3: `bold-minimal`
- [ ] Test each template against 3+ different blog themes
- [ ] Generate previews

### Phase 3: CLI & Rotation (Week 3)
- [ ] Build `blog-control.sh` CLI wrapper
- [ ] Build `rotate-featured.py` with smart scoring
- [ ] Build `audit-templates.py`
- [ ] Write all runbooks
- [ ] Test end-to-end: apply template → rebuild index → push to GitHub Pages

### Phase 4: Production (Week 4)
- [ ] Apply Template 1 to data-security-blog as first production deployment
- [ ] Jim reviews and approves
- [ ] Roll out to remaining blogs as approved
- [ ] Set up heartbeat integration for automated featured rotation

---

## Versioning

Templates use semantic versioning:

- **v1.0** → Initial release
- **v1.1** → Bug fixes, minor style tweaks
- **v1.2** → New component (e.g., search bar, dark mode toggle)
- **v2.0** → Major layout change (may require post metadata updates)

CHANGELOG.md in each template directory tracks all changes.

---

## Blogs Managed

| Blog | Repo | URL | Current Template |
|---|---|---|---|
| NIST CSF 2.0 | sm911/CFS-2.0 | https://sm911.github.io/CFS-2.0/ | Legacy (CSF-specific) |
| Leadership | sm911/leadership-blog | https://sm911.github.io/leadership-blog/ | Legacy (editorial) |
| Compliance | sm911/compliance-blog | https://sm911.github.io/compliance-blog/ | Legacy |
| Cloud Architecture | sm911/cloud-architecture-blog | https://cloud-architecture.blog/ | Legacy |
| Data Security | sm911/data-security-blog | https://data-security.blog/ | Legacy |
| Data Privacy | sm911/data-privacy-blog | https://sm911.github.io/data-privacy-blog/ | Legacy |
| AI Security (planned) | TBD | https://smcgrc.ai/ | TBD |
