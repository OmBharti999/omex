# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Commands

```bash
pnpm dev        # Start development server
pnpm build      # Production build
pnpm start      # Start production server
pnpm lint       # Run ESLint
```

This project uses **pnpm** as the package manager. Do not use npm or yarn.

## Architecture

- **Framework:** Next.js 16.2.2 with App Router (no Pages Router)
- **Router root:** `app/` at the project root (no `src/` directory)
- **Styling:** Tailwind CSS v4 — configured via `@import "tailwindcss"` and `@theme` in `app/globals.css`. There is no `tailwind.config.js`; all theme customization goes in CSS.
- **Fonts:** Geist and Geist Mono loaded via `next/font/google` in `app/layout.tsx`
- **Path alias:** `@/*` resolves to the project root

## Key tooling notes

- **ESLint 9** uses flat config (`eslint.config.mjs`), not `.eslintrc`. Extend it using the flat config API.
- **TypeScript** strict mode is on; module resolution is `bundler`.
- **PostCSS** uses `@tailwindcss/postcss` (Tailwind v4 plugin), not `tailwindcss` directly.

## Next.js 16 documentation

Before writing any Next.js-specific code, consult the bundled docs at `node_modules/next/dist/docs/`. Key paths:
- `01-app/01-getting-started/` — core concepts (routing, data fetching, caching, etc.)
- `01-app/02-guides/` — features like PPR, instant navigation (`unstable_instant`), ISR, streaming
- `01-app/03-api-reference/` — API reference
- `01-app/02-guides/upgrading/version-16.md` — breaking changes from v15
