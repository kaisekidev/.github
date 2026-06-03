# Organization starter workflows

These appear in **Actions → New workflow → "By kaisekidev"** for every repo in
the org. Each is a **thin caller** of a reusable workflow that lives in this same
repo under [`.github/workflows/`](../.github/workflows) — adopting one drops a few
lines into your repo and the shared workflow does the work, so the action
versions are maintained centrally (nothing for Dependabot to bump in your repo).

| Template | Calls | What it does |
|----------|-------|--------------|
| **Checks** (`checks.yml`) | `checks.yml@v1` | CI on every PR/push: PHP 8.2/8.3/8.4 matrix running check-deps, cs-check, phpstan, phpunit + a coverage gate. Uncomment the `with:` block to relax coverage or skip tests per package. |
| **Update Changelog** (`update-changelog.yml`) | `update-changelog.yml@v1` | On a published GitHub Release, updates `CHANGELOG.md` from the release notes via an auto-merging PR. Needs the `kaiseki-doc-bot` App + the `APP_ID`/`APP_PRIVATE_KEY` org secrets and "Allow auto-merge" — see the comments at the top of the file. |

These are the **canonical** caller definitions for the org. Adopt them from the
Actions UI, or copy the `.yml` straight into your repo's `.github/workflows/`.
