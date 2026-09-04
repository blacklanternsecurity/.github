# Contributing

Applies to every repository that does not define its own.

## Before you start

1. Open an issue first for anything larger than a bug fix.
2. A change that needs agreement before work starts is an RFC, see [standards/rfc.md](standards/rfc.md).
3. One concern per pull request.
4. Read the repository's `AGENTS.md`.

External contributors sign the [ICLA](https://github.com/blacklanternsecurity/CLA/blob/main/ICLA.md) before merge. The check runs automatically and comments with instructions. Org members and bots are exempt.

## Making a change

1. Fork and clone.
2. Branch from `dev`, not `stable`.
3. Make the change, with tests.
4. Run lint and tests locally.
5. Open the pull request against `dev`.

Branches and commits: [standards/git.md](standards/git.md). Tests: [standards/testing.md](standards/testing.md). Tooling: [standards/toolchain.md](standards/toolchain.md).

## Ready for review

The pull request template carries the checklist. Every box ticked, honestly.

One approving review is required. Address feedback with new commits, not a force push.

## AI use disclosure

AI use is not prohibited, and is often encouraged. Reviewers need to know its extent and which model.

External contributors fill in the `AI Use Disclosure` section of the pull request template, stating the extent of AI use, fully autonomous, collaborative, or review only, and the model.

## Bugs and features

Use the issue templates. A bug report without a reproduction is a question, and questions go to [SUPPORT.md](SUPPORT.md).

Quote output verbatim, for the reason in [standards/principles.md](standards/principles.md).

Never a public issue for a vulnerability. See [SECURITY.md](SECURITY.md).
