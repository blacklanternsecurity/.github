# Continuous Integration

Tooling: [toolchain.md](toolchain.md). What a test is: [testing.md](testing.md). Release triggers: [releases.md](releases.md).

## Naming

- `tests.yml` tests. `publish.yml` publishes. `docs.yml` deploys documentation.
- No publish, tag, or deploy step in a file named for testing. Nobody reviews a release path they cannot find.
- No lint-only workflow named `ci` or `test`.

## Shared workflows

Workflows every repository needs live in `blacklanternsecurity/.github` and are called, not copied. See [principles.md](principles.md).

```yaml
jobs:
  cla:
    uses: blacklanternsecurity/.github/.github/workflows/cla-reusable.yml@<full-40-character-sha>
```

Repository-specific workflows stay put. Publishing paths genuinely differ between registries.

## Pin everything to a SHA

```yaml
- uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2
```

- Every `uses:` is a full 40-character SHA with the tag as a trailing comment. Including actions we own.
- `@v4`, `@main`, `@latest` resolve third-party code at run time. A retagged or compromised upstream lands in the pipeline with no commit to review.
- Dependabot's `github-actions` ecosystem maintains the pins and opens a pull request for real updates.
- Pin runners to a concrete image. Never `ubuntu-latest`.

## Permissions

Every workflow declares an explicit `permissions:` block. Start from nothing, add what the job needs. Inheriting the default means privilege changes when a setting elsewhere changes.

```yaml
permissions:
  contents: read
```

`pull_request_target` runs with a privileged token in the base repository's context while checking out contributor refs. Use it only when a job needs write access on a fork pull request. Never check out and execute the pull request's code inside it.

## Secrets

- Prefer OIDC trusted publishing over long-lived registry tokens. A stored token is valid until somebody rotates it, and every workflow in the repository can read it.
- Nothing publishes on a branch push. See [releases.md](releases.md).

## Every repository has CI

Runs its tests, or states plainly that it has none.
