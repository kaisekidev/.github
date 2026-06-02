# kaisekidev/.github

Organization-level repository for **[kaisekidev](https://github.com/kaisekidev)**. It hosts shared GitHub configuration — a reusable **Checks** workflow that every `kaiseki/*` PHP package calls instead of duplicating its own CI, and the canonical org **`.editorconfig`**.

## What's here

| Path | Purpose |
| --- | --- |
| [`.github/workflows/checks.yml`](.github/workflows/checks.yml) | Reusable `workflow_call` workflow running the standard lint/static-analysis/test/coverage pipeline. |
| [`.editorconfig`](.editorconfig) | Canonical org editor settings (PHP 4-space, JS/TS/JSON 2-space, LF, final newline). Copied into each repo. |
| [`profile/README.md`](profile/README.md) | Organization profile shown on the [org landing page](https://github.com/kaisekidev). |

## Usage

Each consuming package keeps a thin caller at `.github/workflows/checks.yml`:

```yaml
name: Checks

on:
  push:
  pull_request:

jobs:
  checks:
    uses: kaisekidev/.github/.github/workflows/checks.yml@v1
```

Pin to the `@v1` tag so callers get fixes without breaking on major changes.

### What the workflow does

Per PHP version in the matrix it:

1. Checks out the repo and sets up PHP via [`shivammathur/setup-php`](https://github.com/shivammathur/setup-php) (Composer v2).
2. Restores/saves the Composer cache.
3. Runs `composer update --prefer-dist`.
4. Runs `composer check-deps`, `composer cs-check`, and `composer phpstan`.
5. Runs `vendor/bin/phpunit` with Clover coverage (when `run-tests` is enabled).
6. Reports/gates coverage on the designated PHP leg for pull requests via [`slavcodev/coverage-monitor-action`](https://github.com/slavcodev/coverage-monitor-action).

The default is **strict**: PHPUnit runs and a **100% coverage gate** is enforced on the `8.4` matrix leg.

### Inputs

| Input | Type | Default | Description |
| --- | --- | --- | --- |
| `php-versions` | string (JSON array) | `["8.2","8.3","8.4"]` | PHP versions to run the matrix against. |
| `run-tests` | boolean | `true` | Whether to run PHPUnit. |
| `coverage-threshold` | number | `100` | Coverage gate percentage; `0` disables the gate. |
| `coverage-php` | string | `8.4` | The single matrix leg that reports and gates coverage. |

### Overrides

Packages not yet at full coverage relax the defaults in their caller:

```yaml
jobs:
  checks:
    uses: kaisekidev/.github/.github/workflows/checks.yml@v1
    with:
      coverage-threshold: 0      # disable the coverage gate
      # run-tests: false         # or skip PHPUnit entirely
      # php-versions: '["8.3","8.4"]'
```

### Permissions

The workflow declares `contents: read`, `pull-requests: write`, and `statuses: write` (the latter two so the coverage monitor can post a PR comment and set a commit status). The calling workflow inherits these.

## Requirements for consuming packages

The pipeline expects these Composer scripts to exist:

- `composer check-deps`
- `composer cs-check`
- `composer phpstan`

…and a PHPUnit setup runnable via `vendor/bin/phpunit` when `run-tests` is on.

## Editor configuration

[`.editorconfig`](.editorconfig) is the canonical org editor baseline. Unlike the
Checks workflow, EditorConfig has no remote-include mechanism — editors read the
literal `.editorconfig` in the working tree — so each repo keeps a **copy** rather
than a reference. Treat this file as the source of truth: when it changes, propagate
the copy to consuming repos and keep them byte-identical.

## Versioning

Released via the `v1` git tag. Backwards-compatible changes move the `v1` tag forward; breaking changes get a new major tag (`v2`, …). See [`CHANGELOG.md`](CHANGELOG.md).
