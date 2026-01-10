# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Common Commands

```bash
# Start development server (includes drafts)
hugo server -D

# Create new post
hugo new content/posts/my-new-post.md

# Build for production
hugo --minify

# Initialize theme submodule if missing
git submodule update --init --recursive
```

## Architecture

This is a Hugo static blog using the PaperMod theme (as a git submodule). The site is in Chinese (zh-Hans) and deploys to GitHub Pages via Actions.

**Key customizations:**

- `layouts/partials/extend_head.html` - Loads LXGW WenKai font and conditionally loads KaTeX
- `layouts/partials/math.html` - KaTeX configuration (only loaded when `math: true` in frontmatter)
- `assets/css/extended/fonts.css` - Cross-platform font stack with LXGW WenKai as primary

**Content structure:**

- Posts go in `content/posts/`
- New posts are created as drafts by default (set `draft = false` to publish)

**Math support:**

Add `math: true` to frontmatter to enable KaTeX. Uses `$...$` for inline and `$$...$$` for display math.
