# Quality Assurance

What a test is: [testing.md](testing.md). What CI runs: [ci.md](ci.md). When a release ships: [releases.md](releases.md).

A test artifact is the proof that a change works at the boundary a user touches. Some of that proof is automated today. Much of it, especially functional, performance and security testing, is still done by hand. This standard names every artifact the same way whichever it is, so moving one into CI changes how it is produced, never what is asked for.

## An artifact

| Field | Values |
|---|---|
| `id` | Stable name. It never changes when the method does. `install-runtime`, `docs-build`, `perf-scan-throughput` |
| `class` | `functional`, `performance`, `security`, `install` (packaging, dependencies, docs build) |
| `scope` | `pr`: needed to merge into `dev`. `release`: needed at the promotion to `stable`, for the release-candidate commit |
| `when` | The change that triggers it: path globs, or `always` |
| `boundary` | The surface it proves, in a sentence |
| `method` | `ci`, `scripted`, or `manual`. The maturity ladder |
| `evidence` | What acceptable output looks like |

## The ladder

- `manual`: a written procedure a person follows. The evidence is the procedure, the real results, and the commit it ran at.
- `scripted`: a command or script anyone can run. The reviewer runs it, where § Rules says it may run, and reads the result. The author supplies the means, not a paste of the output.
- `ci`: a named check that runs on the pull request. The evidence is that check passing at the head commit. A skipped job proves nothing.

Moving up the ladder changes `method` and adds `ci_check` or `command`. The `id`, `when` and `scope` stay. If the proof can be automated, it should be a CI check, not text somebody has to write.

Security checks that already run in CI are `ci` artifacts from day one: CodeQL, secret scanning, dependency review, and dry-run scans on pull requests. Pentests and fuzzing campaigns stay `manual` until they are automated.

## The matrix

Each repository lists its artifacts in `.github/qa.json`. Start from [templates/qa.json](../templates/qa.json). The matrix is JSON so CI and review tooling read it with no extra dependencies.

A repository with no matrix still owes proof at the boundary its change touches. The matrix makes the ask explicit and lets tooling check it.

## Where evidence goes

Anywhere attached to the pull request at its head commit:
- a check run
- a comment
- an uploaded log or file
- a link to a CI run or a record
- the description

The description is one place, never the required place.

## Rules

- A pull request owes an artifact for every `pr`-scope entry its change triggers.
- A release owes every `release`-scope entry, for the release-candidate commit, before it is promoted to `stable`.
- A reviewer who can run the proof runs it. Only what the reviewer cannot run (a manual procedure, or an environment the reviewer cannot reach) is the author's to supply.
- For a pull request whose author has no write access, a reviewer runs scripted proof only in CI or a disposable environment with no credentials, never on a workstation. That covers a command given in the pull request as well as one from the matrix. A reviewer with neither environment asks the author for the output.
- The matrix is read at the base commit. A pull request that changes `.github/qa.json` is checked against the base version, except the one that adds it.
- Format is never a merge condition. A description that does not follow the template gets a note, never a rejection. A missing artifact is a different question from a missing heading.

## Enforcement phase

Trial, from 2026-11-10. A missing artifact is called out by name in the review and recorded, but it does not block a merge. This holds in a repository with no matrix too. The owner moves this to enforced after reviewing what the trial recorded.

The `release` scope applies only to releases cut under the tag-based process in [releases.md](releases.md). A release already in flight under the earlier process is exempt. bbot 3.1.0 is one.
