> Modern, composable building blocks for **WordPress** development in **PHP 8** — plus a handful of framework-agnostic libraries and React tooling for the Block Editor.

Everything we ship is small, single-purpose, strictly typed, and installable via Composer or npm. Pick the pieces you need; they're designed to work together but never assume each other.

**Full package reference and guides → [kaiseki.dev](https://kaiseki.dev)**

## What we build

- **WordPress modules** (`kaiseki/wp-*`) — forty-odd focused packages: hooks as classes, type-safe config, ACF DTOs, custom post types, REST, cron, meta, asset and font pipelines, WP-CLI helpers, performance tuning, and integrations with the plugins you already use.
- **Framework-agnostic PHP** — config access, PSR-11 container building, composable string filters, and nested-array merging, with no WordPress dependency.
- **Block Editor (npm)** (`@kaiseki/gutenberg-*`) — React components, hooks, and design tokens for building in the WordPress Block Editor.
- **Scaffolding and standards** — generators that spin up a new package from our template, and the shared coding standard every package lints against.

Browse every package, with usage examples, at **[kaiseki.dev](https://kaiseki.dev)**.

## How we work

- **PHP 8.2+**, strictly typed, PSR-friendly.
- **One concern per package** — install only what you use.
- **Shared CI** — every package calls our reusable [Checks workflow](https://github.com/kaisekidev/.github/blob/master/.github/workflows/checks.yml): coding-standard checks, PHPStan, and PHPUnit with a **100% coverage gate**.
- **MIT licensed.**

## Get started

```bash
composer require kaiseki/wp-hook
npm install @kaiseki/gutenberg-components
```
