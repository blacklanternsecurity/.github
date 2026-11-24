# Releases and Versioning

Commit conventions: [git.md](git.md).

**BBOT family repositories follow the publishing policy** (`.github-config` `docs/policy/publishing.md`), which takes precedence over this file where they differ. There, a reviewed merge into `stable` releases; a lead approves before anything publishes (at the protected `release` environment, or on the `stable` pull request in a private repository); CI publishes with trusted publishing or credentials held only in that environment; and the release App creates the `v*` tag and the GitHub release. Nobody tags by hand. Everything below still applies to those repositories where it doesn't conflict (versions, tag format, artifacts), and in full to every other repository.

## Versions

- The version lives in `pyproject.toml` or `Cargo.toml`. It changes by a reviewed commit.
- CI reads the version. CI never computes it. A version that exists only inside a workflow run cannot be looked up, reproduced, or bisected against.

## Tags

`v` prefixed, [semantic versioning](https://semver.org/). Release `v3.0.2`, prerelease `v3.0.2-rc.79`.

- A tag is created deliberately. CI never tags on merge.
- The `archive/` namespace holds retired branches preserved as tags. Publishing workflows carry a `tags-ignore` filter for `archive/**` from their first commit, so draining old branches never fires a publish.

## Publishing

- Publish on tag push. Never on branch push.
- Branch-push publishing makes every merge a release, exercises the release path with ordinary development traffic, and puts a long-lived registry token in a workflow that runs on every merge.
- Prereleases are tags too. One publishing path.
- Workflow naming and secrets: [ci.md](ci.md).

## Cutting a release

1. Open a pull request setting the version in the manifest. Under this process, it carries the `release`-scope test artifacts for that commit. See [qa.md](qa.md).
2. Review and merge it.
3. Tag that commit on the trunk.
4. Push the tag.

The changelog derives from conventional commit messages between the previous tag and this one.

## Artifacts

- Anyone can check out the tag and rebuild what was published.
- Image tags are immutable and specific. A floating tag means two people running the same tag are running different code, and neither can say which.
