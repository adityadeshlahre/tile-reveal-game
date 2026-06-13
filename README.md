# tile-reveal-game

Tile-reveal guess-who web app. Host clicks to reveal tiles on a portrait — watchers guess the person.

## Stack

- **Astro 6** + **`@astrojs/cloudflare`** adapter — SSR on Cloudflare Workers
- **Tailwind v4** — all CSS
- **Bun** — package manager
- **Cloudflare Workers AI** — AI-powered hints (binding via `import { env } from "cloudflare:workers"`)

## Commands

| Action              | Command                                           |
| ------------------- | ------------------------------------------------- |
| Dev server          | `bun dev` (localhost:4321)                        |
| Build               | `bun build` → `dist/`                             |
| Preview             | `bun preview` (builds first)                      |
| Deploy              | `bun deploy` (build + `wrangler deploy`)          |
| Regenerate CF types | `bun generate-types` (alias: `bun cf-typegen`)    |

## Project Structure

```
public/
├── game-config.json    — Round data (image paths, answers, hints URLs)
├── images/             — Portrait images (JPEG/PNG)
└── fonts/              — Roslindale font files
src/
├── pages/index.astro   — Game UI and logic
├── components/         — Astro components
├── layouts/            — Page layouts
├── styles/global.css   — Tailwind entry, @font-face, theme tokens
└── env.d.ts            — Astro+Cloudflare runtime types
```

## Workers AI

AI binding is configured in `wrangler.jsonc` and available in SSR components as `Astro.locals.env.AI`. Run `bun generate-types` after changing bindings.
