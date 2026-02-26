# Amit.Brews.Code

Personal software engineering blog by [Amit Bisht](https://amitbrewscode.in) covering Docker, Kubernetes, Terraform, Linux, Python, networking, and system design.

Built on the [Tailwind Nextjs Starter Blog](https://github.com/timlrx/tailwind-nextjs-starter-blog) template (v2.1.0).

## Stack

- **Framework:** Next.js 16 (App Router) with React 19
- **Content:** MDX via [Contentlayer2](https://github.com/timlrx/contentlayer2)
- **Styling:** Tailwind CSS v3
- **Search:** kbar (client-side)
- **Comments:** Giscus
- **Analytics:** Umami
- **Newsletter:** Buttondown
- **Deployment:** Vercel

## Getting Started

**Prerequisites:** Node.js 20+ and Yarn 3.6.1 (via Corepack)

```bash
# Install dependencies
yarn install

# Start dev server
yarn dev
```

The site will be available at [http://localhost:3000](http://localhost:3000).

## Commands

| Command | Description |
|---------|-------------|
| `yarn dev` | Start development server |
| `yarn build` | Production build + RSS feed generation |
| `yarn serve` | Serve production build |
| `yarn lint` | Lint with ESLint (auto-fix) |
| `yarn analyze` | Bundle size analysis |

## Project Structure

```
app/                  # Next.js App Router pages
data/
  blog/*.mdx          # Blog posts (MDX)
  authors/*.mdx       # Author profiles
  siteMetadata.js     # Site configuration
components/           # Reusable React components
layouts/              # Blog post and list layout templates
scripts/              # Post-build scripts (RSS generation)
contentlayer.config.ts # Contentlayer document types and MDX plugin pipeline
```

## Writing a Blog Post

Create a new `.mdx` file in `data/blog/` with this frontmatter:

```mdx
---
title: 'Your Post Title'
date: '2026-01-15'
tags: ['docker', 'kubernetes']
draft: false
summary: 'A brief description of the post.'
---

Your content here...
```

**Optional frontmatter fields:** `lastmod`, `images`, `authors`, `layout` (`PostLayout` | `PostSimple` | `PostBanner`), `bibliography`, `canonicalUrl`.

## Environment Variables

Create a `.env` file for optional integrations:

```bash
NEXT_UMAMI_ID=                          # Umami analytics website ID
NEXT_PUBLIC_GISCUS_REPO=                # Giscus GitHub repo
NEXT_PUBLIC_GISCUS_REPOSITORY_ID=       # Giscus repo ID
NEXT_PUBLIC_GISCUS_CATEGORY=            # Giscus category
NEXT_PUBLIC_GISCUS_CATEGORY_ID=         # Giscus category ID
```

## License

[MIT](LICENSE)
