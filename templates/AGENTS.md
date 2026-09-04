# AGENTS.md

<!-- Template. Replace bracketed parts, delete this comment, delete rows that do not apply. -->

[One or two sentences: what this project is.]

## Toolchain

| Concern | This repository |
|---|---|
| Language | [Python 3.10 through 3.14 / Rust, edition 2024] |
| Package manager | [uv / cargo] |
| Lint and format | [ruff, pinned in pyproject.toml / clippy and rustfmt, pinned in rust-toolchain.toml] |
| Tests | [pytest / cargo test] |

## Setup

```bash
[commands taking a fresh clone to a working dev environment]
```

## Tests

```bash
[full suite]
[single test]
```

## Standards

Org-wide, in [blacklanternsecurity/.github/standards](https://github.com/blacklanternsecurity/.github/tree/main/standards). Read the one your task touches, not all of them.

| Document | Read it when |
|---|---|
| [principles.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/principles.md) | Always |
| [toolchain.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/toolchain.md) | Touching dependencies, linting, formatting, or language versions |
| [git.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/git.md) | Branching, commit messages, opening or reviewing a pull request |
| [rfc.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/rfc.md) | A change needs agreement before work starts, or an RFC is ending |
| [testing.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/testing.md) | Writing or changing tests, or anything that has them |
| [ci.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/ci.md) | Touching a workflow, an action pin, or a permissions block |
| [releases.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/releases.md) | Versioning, tagging, or publishing |
| [repository-setup.md](https://github.com/blacklanternsecurity/.github/blob/main/standards/repository-setup.md) | Creating a repository, or auditing one |

Never restate a standard here. If this file and a standard disagree, the standard wins and this file is the bug.

## Repository specifics

[What is true here and nowhere else: architecture notes, a subsystem worth explaining, a footgun somebody hit twice.

Keep it short. This file loads into every bot context on every turn. Long-form documentation goes in docs/ and gets linked.]
