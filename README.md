# sumittiware.dev

Personal website and blog for [sumittiware.in](https://sumittiware.in), built with [Hugo](https://gohugo.io/).

## Overview

This repository contains:

- A portfolio-style homepage
- Blog posts under `content/post/`
- Static assets and images under `static/`
- Theme/layout templates under `layouts/`

Core site settings are defined in `config.toml`.

## Tech Stack

- **Static site generator:** Hugo
- **Markup:** Markdown + TOML front matter
- **Styling:** Sass/SCSS pipeline via Hugo
- **Search index:** Implemented as part of the site build/theme
- **CMS:** Decap CMS config available at `static/admin/config.yml`

## Prerequisites

Install Hugo first (extended version recommended for SCSS support):

- macOS (Homebrew): `brew install hugo`
- Other platforms: see [official install docs](https://gohugo.io/installation/)

## Local Development

From the project root:

```bash
hugo server
```

Then open `http://localhost:1313`.

## Build for Production

```bash
hugo
```

Generated files are written to `public/`.

## Content Workflow

### Add a New Post

Create a markdown file in `content/post/` (or use your preferred template/automation) with front matter like:

```toml
+++
title = "Post title"
description = "Short summary"
date = 2026-04-28
updated = 2026-04-28
draft = false
slug = "post-slug"

[taxonomies]
tags = ["tag1", "tag2"]
+++
```

Then add your markdown content below the front matter.

### Media

- Shared images: `static/images/`
- Post-related images: typically `static/img/` (as configured for Decap CMS)

## Domain

Custom domain is configured through `static/CNAME`.

## Useful Directories

- `content/` - Pages and posts
- `layouts/` - Templates
- `assets/` - Source assets (including Sass)
- `static/` - Static files copied as-is
- `public/` - Generated site output
- `resources/` - Hugo generated/cached assets
