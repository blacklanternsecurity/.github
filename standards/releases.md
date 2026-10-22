# Releases and Versioning

Commit conventions: [git.md](git.md).

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

1. Open a pull request setting the version in the manifest.
2. Review and merge it.
3. Tag that commit on the trunk.
4. Push the tag.

The changelog derives from conventional commit messages between the previous tag and this one.

## Artifacts

- Anyone can check out the tag and rebuild what was published.
- Image tags are immutable and specific. A floating tag means two people running the same tag are running different code, and neither can say which.
