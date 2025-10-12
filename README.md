# Gitea Auto-PR (Gitea Compatible)

Create a new PR on Gitea using Gitea or Github Actions. Derived from https://github.com/arifer612/Gitea-PR-action which uses `success()` and `failure()` expressions which [Gitea does not support (only supports `always`)](https://docs.gitea.com/usage/actions/comparison#expressions). Thus, this version has been tweaked to work with both Github and Gitea Actions.

### Requirements

This action recipe requires a token with the following permissions:

```yaml
issue: read
repository: write
user: read
```

## Inputs

### url

**Required** URL to the Gitea instance

### token

**Required** Personal access token to the Gitea instance

### tea-version

Tea CLI version (Default: 0.10.1)

### pr-title
Custom title. Defaults to using subject of the most recent commit (`git log -n 1 --format=%s`).

### pr-description
Custom description. Defaults to using body of the most recent commit (`git log -n 1 --format=%b`).

### pr-label

Issues label for the PR

### assignee

User to assign the PR to

## Example

```yaml
- name: Create PR
  uses: https://git.trez.wtf/Trez/gitea-auto-pr@main
  with:
    url: https://git.domain.tld
    token: abcdefghijklmnopqrstuvwxyz
    tea-version: 0.11.0
    pr-label: foobar
    assignee: ${{ github.actor }}
```
