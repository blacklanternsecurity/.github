# Repository Setup

## Required

| Item | Why |
|---|---|
| `LICENSE` | AGPL-3.0, in the repository itself, see below |
| `AGENTS.md` | Names the toolchain, indexes the standards |
| `CLAUDE.md` | One line pointing at `AGENTS.md` |
| CI that runs tests | Or a plain statement there are none, see [ci.md](ci.md) |
| Branch protection on the trunk | See below |

Templates: [`templates/`](../templates/).

## License

- Every repository carries its own `LICENSE` with the full AGPL-3.0 text. It cannot be inherited. GitHub serves no default license, and a license must travel with the code when cloned, packaged, or downloaded.
- Copy the text. Never retype or generate it.
- The manifest declares it too: `license = "AGPL-3.0"`. Disagreement between the two means consumers get different answers.

## Inherited, do not duplicate

[CONTRIBUTING.md](../CONTRIBUTING.md), [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md), [SECURITY.md](../SECURITY.md), [SUPPORT.md](../SUPPORT.md), the pull request template, and issue templates are served org-wide.

A local file wins over the default. Define one only when it genuinely differs. Copying a default in unchanged means it stops tracking the org version.

Issue templates are the exception, and the trap. They inherit as a set, not file by file. A repository with its own `.github/ISSUE_TEMPLATE/` folder loses every org template, including the `config.yml` that routes questions and vulnerability reports. Needing one template of your own means carrying copies of all of them.

## Labels

An issue template that sets a label fails if the label does not exist in the repository. `bug`, `enhancement`, and `rfc` exist everywhere. So does `adr`, which an RFC is relabeled to when it ends, see [rfc.md](rfc.md).

## Branch protection

- The trunk requires a pull request, requires one approving review, and blocks force pushes and deletion.
- Bypass lists are empty. A rule named accounts can bypass describes a habit, not an invariant.
- Grant access to teams, not individuals. Access is then correct the day someone joins and the day they leave.
- Protection rules, required checks, and access are configuration that can be reviewed and reproduced. A clicked checkbox cannot be audited, diffed, or restored.

## Documentation

`README.md` says what the project is, how to install it, how to use it.

It is not a deploy runbook. Operational procedure is versioned alongside what it deploys. A runbook in a README is never tested and is always stale.
