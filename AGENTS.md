# AGENTS.md

Organization-wide GitHub configuration. Layout and inheritance rules: [README.md](README.md).

## Standards

Read the one your task touches, not all of them.

| Document | Read it when |
|---|---|
| [principles.md](standards/principles.md) | Always |
| [toolchain.md](standards/toolchain.md) | Touching dependencies, linting, formatting, or language versions |
| [git.md](standards/git.md) | Branching, commit messages, opening or reviewing a pull request |
| [rfc.md](standards/rfc.md) | A change needs agreement before work starts, or an RFC is ending |
| [testing.md](standards/testing.md) | Writing or changing tests, or anything that has them |
| [ci.md](standards/ci.md) | Touching a workflow, an action pin, or a permissions block |
| [releases.md](standards/releases.md) | Versioning, tagging, or publishing |
| [repository-setup.md](standards/repository-setup.md) | Creating a repository, or auditing one |

## Working here

No build, no test suite. Validation is reading the YAML and confirming a change does what it claims for every repository that inherits it.

Copy `LICENSE` verbatim. Never retype or generate it.
