# .github

Organization-wide GitHub configuration: default community health files, engineering standards, shared reusable workflows.

Two rules that are easy to get wrong:

- This repository must stay public. GitHub serves default community health files only from a public `.github`. Nothing confidential belongs here.
- A default is inherited only by repositories that do not define their own. Adding a file here does not override a repository that already has one.

Changes here reach every repository on merge.

## Layout

| Path | What it is |
|---|---|
| [CONTRIBUTING.md](CONTRIBUTING.md), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md), [SECURITY.md](SECURITY.md), [SUPPORT.md](SUPPORT.md) | Defaults inherited org-wide |
| [standards/](standards/) | The engineering standard, one concern per file |
| [templates/](templates/) | `AGENTS.md` and `CLAUDE.md` for other repositories |
| [.github/workflows/](.github/workflows/) | Reusable workflows other repositories call |
| [workflow-templates/](workflow-templates/) | Starter workflows in the Actions picker |
| [profile/README.md](profile/README.md) | The organization profile page |

A license cannot be inherited. See [standards/repository-setup.md](standards/repository-setup.md).

## Standards

The engineering standard lives in [standards/](standards/), one concern per file. [AGENTS.md](AGENTS.md) indexes it and says when to read each one.

## Reusable workflows

[cla-reusable.yml](.github/workflows/cla-reusable.yml) requires the CLA from external contributors and exempts org members and bots.

Call it with [workflow-templates/cla.yml](workflow-templates/cla.yml), which is also offered in the Actions picker. Replace the placeholder with a full commit SHA, never `@main`. See [standards/ci.md](standards/ci.md).

Needs an org-level GitHub App with `APP_ID` and `APP_PRIVATE_KEY` available to the calling repository. Signatures are written to [blacklanternsecurity/CLA](https://github.com/blacklanternsecurity/CLA).

## Working here

How to validate a change here: [AGENTS.md](AGENTS.md).
