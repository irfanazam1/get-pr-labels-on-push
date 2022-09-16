# Get PR Labels on Push Action

This action lists all the labels attached to a PR when it was pushed.

## Inputs

### `github-token`

**Required** The repository token, i.e. `secrets.GITHUB_TOKEN`

## Outputs

### `result`

An array of labels attached to the PR.

## Example Usage

```
uses: irfanazam1/get-pr-labels-on-push-action@v1
with:
  github-token: ${{ secrets.GITHUB_TOKEN }}
```

### Example Workflow
e.g. [.github/workflows/main.yml](https://github.com/irfanazam1/get-pr-labels-on-push-action/blob/master/.github/workflows/main.yml)
```
on:
  push:
    branches:
      - master

jobs:
  get_pr_labels_job:
    runs-on: ubuntu-latest
    name: Get PR labels job
    steps:
    - name: Get PR labels step
      id: get_pr_labels
      uses: irfanazam1/get-pr-labels-on-push-action@v1
      with:
        github-token: ${{ secrets.GITHUB_TOKEN }}

    - name: See result
      run: echo "${{ steps.get_pr_labels.outputs.result }}"
```
