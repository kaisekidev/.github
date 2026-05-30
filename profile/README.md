# Kaiseki

Modern, composable building blocks for **WordPress** development in **PHP 8** — plus a handful of framework-agnostic libraries and React tooling for the Block Editor.

Everything we ship is small, single-purpose, strictly typed, and installable via Composer or npm. Pick the pieces you need; they're designed to work together but never assume each other.

## What we build

### 🧩 WordPress modules — `kaiseki/wp-*`

Forty-odd focused packages for building WordPress sites the modern way: register hooks as classes, type-safe config, ACF DTOs, custom post types, REST, cron, asset pipelines, and integrations with the plugins you already use.

| Package | What it does |
| --- | --- |
| [`kaiseki/wp-hook`](https://github.com/kaisekidev/kaiseki-wp-hook) | Register classes as `add_action` / `add_filter` listeners |
| [`kaiseki/wp-config`](https://github.com/kaisekidev/kaiseki-wp-config) | Type-safe access to array configuration |
| [`kaiseki/wp-acf`](https://github.com/kaisekidev/kaiseki-wp-acf) · [`wp-acf-dto`](https://github.com/kaisekidev/kaiseki-wp-acf-dto) | ACF helpers and DTOs straight from your field groups |
| [`kaiseki/wp-post-types`](https://github.com/kaisekidev/kaiseki-wp-post-types) | Companion module for `jjgrainger/posttypes` |
| [`kaiseki/wp-rest-api`](https://github.com/kaisekidev/kaiseki-wp-rest-api) · [`wp-cron`](https://github.com/kaisekidev/kaiseki-wp-cron) · [`wp-meta`](https://github.com/kaisekidev/kaiseki-wp-meta) | First-class wrappers around core WordPress APIs |
| [`kaiseki/wp-vite`](https://github.com/kaisekidev/kaiseki-wp-vite) · [`wp-inpsyde-assets`](https://github.com/kaisekidev/kaiseki-wp-inpsyde-assets) · [`wp-font-loader`](https://github.com/kaisekidev/kaiseki-wp-font-loader) | Modern asset and font pipelines |
| [`kaiseki/wp-cli-util`](https://github.com/kaisekidev/kaiseki-wp-cli-util) | WP-CLI helpers: colorized output, logging, timers |

…plus performance helpers (`wp-bunny-optimizer`, `wp-wp-rocket`, `wp-preload-featured-image`) and plugin integrations (`wp-plugin-yoast`, `wp-plugin-ninja-forms`, `wp-plugin-the-events-calendar`).

### ⚙️ Framework-agnostic PHP

| Package | What it does |
| --- | --- |
| [`kaiseki/config`](https://github.com/kaisekidev/kaiseki-config) | Type-safe access to array configurations |
| [`kaiseki/container-builder`](https://github.com/kaisekidev/kaiseki-container-builder) | Build a PSR-11 container with `laminas-servicemanager` + `laminas-di` |
| [`kaiseki/string-filter`](https://github.com/kaisekidev/kaiseki-string-filter) | Composable string filters with a filter pipeline |
| [`kaiseki/nested-array`](https://github.com/kaisekidev/kaiseki-nested-array) | Recursive deep-merge for nested arrays |

### ⚛️ Block Editor (npm) — `@kaiseki/gutenberg-*`

[`gutenberg-components`](https://github.com/kaisekidev/gutenberg-components), [`gutenberg-hooks`](https://github.com/kaisekidev/gutenberg-hooks), and [`gutenberg-styles`](https://github.com/kaisekidev/gutenberg-styles) — React components, hooks, and design tokens for building in the WordPress Block Editor (Gutenberg).

### 🏗️ Scaffolding & standards

[`kaiseki/scaffold-wp-module`](https://github.com/kaisekidev/kaiseki-scaffold-wp-module) and [`scaffold-module`](https://github.com/kaisekidev/kaiseki-scaffold-module) generate a new package from our template; [`kaiseki/php-coding-standard`](https://github.com/kaisekidev/php-coding-standards) is the shared coding standard every package lints against.

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

> Browse the repositories below to find the module you need — each ships with its own README and usage examples.
