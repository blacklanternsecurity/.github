# Git and Review

Tags and releases: [releases.md](releases.md).

## Branches

| Branch | Meaning |
|---|---|
| `stable` | The trunk. Production. What users get. |
| `dev` | Active development. Almost all pull requests target this. |
| feature | Cut from `dev`, one concern, deleted after merge |

- Work reaches `stable` through a deliberate release, never by accident.
- Any other long-lived branch names what it integrates. Not moved in months means abandoned: tag it, delete it.
- Contributors work from a fork. Contributed branches do not live upstream.

## Merging

- We merge. We never rebase shared history. Rebasing rewrites commits out from under anyone who fetched them.
- Squash merging a reviewed pull request into the trunk is a merge. That is the normal path.
- No force pushing during review. The reviewer loses the diff since their last pass. Address feedback with new commits.

## Commit messages

[Conventional Commits](https://www.conventionalcommits.org/). Version bumps and changelogs derive from the prefix, so it is load-bearing.

```
<type>(<optional scope>): <subject>

<body: what changed and why>

<optional footers: Closes #123, BREAKING CHANGE: ...>
```

| Type | Use for |
|---|---|
| `feat` | A new capability |
| `fix` | A bug fix |
| `docs` | Documentation only |
| `test` | Tests only |
| `refactor` | Behavior-preserving restructuring |
| `perf` | A performance change |
| `build` | Build system or dependencies |
| `ci` | CI configuration |
| `chore` | Everything else |

- Subject: what changed. Imperative. No trailing period.
- Body: why. Quote real output when output is the evidence.
- Breaking changes get a `BREAKING CHANGE:` footer regardless of type.
- No bot or AI co-author trailers. No generated tool footers. AI attribution goes in the pull request body, see [CONTRIBUTING.md](../CONTRIBUTING.md).

## Pull requests

- One concern each. A pull request that fixes a bug and refactors a subsystem gets reviewed twice as slowly and reverted twice as often.
- The body says what changed, why, and how it was validated. Validation means commands run and their real output, not a claim that tests pass.
- A change that needs agreement before the work starts is an RFC, not a pull request opened in hope. See [rfc.md](rfc.md).

## Review

- One approving review before merge, enforced by branch protection. See [repository-setup.md](repository-setup.md).
- A reviewer owns the change after it lands. That is why the bar is where it is.
- Name what is good as specifically as what is wrong. Generic praise teaches nothing.
- Separate the work from the person.
- Do not re-raise a settled point without saying it is settled.
- Nobody approves over another reviewer's outstanding request for changes. That reviewer approves or dismisses their own.
