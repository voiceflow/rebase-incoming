# GitHub Action to rebase incoming PRs

Attempts to rebase all pull requests targeting the current branch.

## Usage

### Inputs

- `token`: The GitHub token to allow authenticated actions
- `comment-on-failure`: When set to `'true'`, if any pull request fails to rebase, a comment will be made on that pull request with details of the failure.
- `label-on-failure`: When set to `'true'`, if any pull request fails to rebase, a label that blocks further failure comments will be added to that pull request.

### Example Workflow

```yaml
# Keeps all incoming branches up-to-date by rebasing to main when necessary
name: Automatic Rebase All Branches
on:
  push:
    branches: [ main ]

jobs:
  # When main updates, rebase all open pull requests
  rebase-all-to-main:
    name: Rebase All to Master
    runs-on: ubuntu-latest
    steps:
      - name: Rebase All Incoming PRs
        uses: voiceflow/rebase-incoming@main
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          comment-on-failure: 'true'
          label-on-failure: 'false'
```

## License

MIT
