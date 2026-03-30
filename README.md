# .github

Organization-wide GitHub configurations for [Black Lantern Security](https://github.com/blacklanternsecurity).

## Workflow Templates

### CLA Assistant

Requires contributors to sign the [Individual Contributor License Agreement](https://github.com/blacklanternsecurity/CLA/blob/main/ICLA.md) before PRs can be merged.

**To add to a repo:**

1. Go to the repo's Actions tab
2. Click "New workflow"
3. Find "CLA Assistant" under the organization templates
4. Click "Configure" and commit to `main`

**Or** copy `workflow-templates/cla.yml` to `.github/workflows/cla.yml` in your repo.

**Required setup:** Create an org-level secret named `CLA_TOKEN` with a PAT that has `repo` scope, so the action can write signatures to the central `blacklanternsecurity/CLA` repo.
