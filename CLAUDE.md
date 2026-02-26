# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal blog ("Amit.Brews.Code") built on the Tailwind Nextjs Starter Blog template (v2.1.0). Static site covering Docker, Kubernetes, Terraform, Linux, Python, networking, and system design topics.

**Stack:** Next.js 14 (App Router), TypeScript, MDX via Contentlayer, Tailwind CSS v3, deployed on Vercel.

## Commands

- **Dev server:** `yarn dev`
- **Build:** `yarn build` (runs `next build` + `scripts/postbuild.mjs` for RSS generation)
- **Serve production:** `yarn serve`
- **Lint:** `yarn lint` (ESLint with `--fix` across app/components/lib/layouts/scripts)
- **Bundle analysis:** `yarn analyze`

Package manager is **Yarn 3.6.1** (Berry, node-modules linker).

## Architecture

- **`app/`** — Next.js App Router pages. No `pages/` directory.
- **`data/blog/*.mdx`** — Blog posts processed by Contentlayer into typed TypeScript objects at build time.
- **`data/siteMetadata.js`** — Central site config (URL, analytics via Umami, comments via Giscus, search via kbar, newsletter via Buttondown).
- **`contentlayer.config.ts`** — Defines Blog/Authors document types and the remark/rehype plugin pipeline (GFM, KaTeX, Prism, citation, autolink headings).
- **`layouts/`** — Blog post layout templates (PostLayout, PostSimple, PostBanner, ListLayout, ListLayoutWithTags, AuthorLayout).
- **`components/`** — Reusable React components (Header, Footer, Comments, MDXComponents, etc.).
- **`scripts/rss.mjs`** — Generates RSS feeds (main + per-tag) during post-build.
- **`pliny`** library provides content sorting, MDX plugins, newsletter forms, and search utilities.

## Path Aliases (tsconfig)

- `@/components/*`, `@/data/*`, `@/layouts/*`, `@/css/*`

## Code Style

- **Prettier:** No semicolons, single quotes, 100 char width, `prettier-plugin-tailwindcss` for class sorting.
- **ESLint:** Extends `next/core-web-vitals`, `@typescript-eslint/recommended`, `jsx-a11y/recommended`.
- **Pre-commit hook:** Husky + lint-staged runs ESLint fix and Prettier on staged files.

## Adding a Blog Post

Create a new `.mdx` file in `data/blog/`. Frontmatter fields: `title`, `date`, `tags`, `draft`, `summary`, `layout` (defaults to PostLayout). Set `layout: PostSimple` or `layout: PostBanner` for alternate layouts. The `images` field takes an array of paths relative to `public/static/images/`.

## Content Security Policy

`next.config.js` defines strict CSP headers. When adding new external resources, update the CSP directives there. Currently allows giscus.app and Umami analytics domains.
