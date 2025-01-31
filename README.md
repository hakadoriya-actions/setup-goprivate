# Setup `GOPRIVATE` for GitHub Actions

A GitHub Action for configure git config to clone private repositories under `GOPRIVATE`.

## Example

```yml
name: example

on:
  pull_request:

jobs:
  example:
    if: github.actor != 'dependabot[bot]' && github.actor != 'renovate[bot]'
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - uses: hakadoriya-actions/setup-goprivate@v0.0.1
        with:
          goprivate: "github.com/hakadoriya"
          token: ${{ secrets.GITHUB_TOKEN }}
      - name: Check global gitconfig
        shell: bash
        run: |
          cat ~/.gitconfig
```
