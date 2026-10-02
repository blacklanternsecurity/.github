# Toolchain

Repositories do not pick their own formatter, package manager, or test runner.

Bump a pin deliberately, in a commit that also fixes what the new version breaks.

## Python

| Concern | Tool |
|---|---|
| Package manager | [uv](https://docs.astral.sh/uv/) |
| Lint and format | [ruff](https://docs.astral.sh/ruff/) |
| Tests | [pytest](https://docs.pytest.org/) with pytest-asyncio |
| Versions | 3.10 through 3.14 |

- Pin `ruff` with `==`, never `>=`. A floor lets a new release change formatting with no commit to review.
- ruff only. No black, no isort, no flake8.
- Install pre-commit hooks: `uv sync --group dev && uv run pre-commit install`.
- The ruff version in `pyproject.toml` and the revision in `.pre-commit-config.yaml` must match, or the hook and CI disagree.

```bash
ruff check
ruff format --check
```

## Rust

| Concern | Tool |
|---|---|
| Toolchain | pinned in `rust-toolchain.toml` |
| Linter | clippy, warnings denied |
| Formatter | rustfmt |
| Edition | 2024 |

Pin the channel to an exact version, with `clippy` and `rustfmt` as components. A pin keeps a new clippy lint from breaking every open dependency update at once.

```bash
cargo fmt --all -- --check
cargo clippy --all-targets -- -D warnings
cargo test
```

## Anything else

Document it in the repository's `AGENTS.md`. Exact version, one line on why.
