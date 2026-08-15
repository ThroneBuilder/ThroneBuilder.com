# ThroneBuilder

Personal site and blog at [thronebuilder.com](https://thronebuilder.com) — ramblings of an unreasonable engineer.

This project is an experiment in AI-assisted coding and personal branding. It has four goals:

1. Built using [Claude Code](https://claude.com/claude-code) with [SpecKit](https://github.com/github/spec-kit)
2. Explore website design patterns and technologies
3. Consolidate content currently scattered across Substack, YouTube, and Facebook
4. Encourage more writing

## Tech Stack

- **[Astro 5](https://astro.build)** — static site generator, `output: 'static'`
- **TypeScript** — content schemas and site config
- **Markdown** — blog content via Astro Content Collections
- **Vanilla HTML/CSS/JS** — no UI framework or CSS framework; interactive bits (filtering, carousel) are hand-written scoped scripts
- **[@astrojs/sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/)** — sitemap generation
- **[@astrojs/rss](https://docs.astro.build/en/guides/rss/)** — RSS feed at `/rss.xml`
- **Node.js 22** (see [.node-version](.node-version))
- **[Render](https://render.com)** — static hosting, auto-deployed from `main` (see [render.yaml](render.yaml))

Framework and dependency choices favor plain web standards; new tooling is only introduced when a concrete problem justifies it (see [Project Constitution](.specify/memory/constitution.md)).

## Project Structure

```text
src/
├── consts.ts               # Site-wide constants: title, tags, footer links
├── content/
│   ├── config.ts            # Blog collection schema (title, tags, cover image, etc.)
│   └── blog/                 # Markdown blog posts
├── data/
│   └── carousel.ts          # Homepage carousel slide configuration
├── layouts/
│   └── BaseLayout.astro     # Shared page shell: head, nav, footer
├── pages/
│   ├── index.astro          # Homepage — carousel, tag filters, article grid
│   ├── rss.xml.ts           # RSS feed endpoint
│   └── blog/[...slug].astro # Blog post template
├── styles/
│   └── global.css           # Global styles and CSS custom properties
└── utils/
    └── youtube.ts            # YouTube embed helpers

public/
└── images/                  # Static images, favicon, OG image

specs/                       # SpecKit feature specs, plans, and tasks
.specify/                    # SpecKit workflow config, templates, constitution
```

## Documentation

This project follows the [SpecKit](https://github.com/github/spec-kit) workflow: every feature is specified, planned, and broken into tasks before implementation.

- [Project Constitution](.specify/memory/constitution.md) — core principles governing this project (incremental delivery, accessibility, deployment integrity, etc.)
- [`specs/`](specs/) — one directory per feature, each containing:
  - `spec.md` — user stories and acceptance criteria
  - `plan.md` — technical approach and structure decisions
  - `tasks.md` — dependency-ordered implementation tasks
  - `research.md`, `data-model.md`, `quickstart.md`, `contracts/` — supporting design docs

See [`CLAUDE.md`](CLAUDE.md) for the pointer Claude Code uses to find current feature context.

## Development

### Prerequisites

- Node.js 22 (see [.node-version](.node-version))

### Setup

```bash
npm install
```

### Commands

| Command | Action |
| --- | --- |
| `npm run dev` | Start the local dev server with hot reload |
| `npm run build` | Build the static site to `dist/` |
| `npm run preview` | Serve the built `dist/` output locally |

## Deployment

Render auto-deploys from the `main` branch on GitHub (see [render.yaml](render.yaml)). GitHub is the single source of truth — there is no direct editing on the host. Pushing to `main` is the only deployment path.

## Repository

https://github.com/jeffjames-pnw/ThroneBuilder
