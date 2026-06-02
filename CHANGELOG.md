# Changelog

All notable changes to this repository are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
This repo is consumed by tag, so the major tag (`v1`) is treated as the version line: backwards-compatible changes move `v1` forward, breaking changes introduce a new major tag.

## [Unreleased]

### Added

- Canonical org `.editorconfig`, adopted from the retired `kaisekidev/editorconfig` repo. This repo is now its source of truth; consuming repos keep a byte-identical copy.
- Organization profile (`profile/README.md`) shown on the org's GitHub landing page.
- Repository `README.md` and this `CHANGELOG.md`.

## [v1] - 2026-05-29

### Added

- Reusable **Checks** workflow (`.github/workflows/checks.yml`) callable via `uses: kaisekidev/.github/.github/workflows/checks.yml@v1`.
  - PHP matrix (default `["8.2","8.3","8.4"]`) with `fail-fast: false`.
  - PHP setup via `shivammathur/setup-php` (Composer v2) and a cached Composer install.
  - `composer update`, then `composer check-deps`, `composer cs-check`, and `composer phpstan`.
  - PHPUnit with Clover coverage, gated at 100% on the `8.4` leg for pull requests via `slavcodev/coverage-monitor-action`.
  - Inputs `php-versions`, `run-tests`, `coverage-threshold`, and `coverage-php` for per-package overrides.

[Unreleased]: https://github.com/kaisekidev/.github/compare/v1...HEAD
[v1]: https://github.com/kaisekidev/.github/releases/tag/v1
