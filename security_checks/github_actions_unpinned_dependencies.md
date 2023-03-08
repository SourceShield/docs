---
layout: default
title: GitHub Actions Unpinned Dependencies
parent: Security Checks
---

# GitHub Actions Unpinned Dependencies
Ensures dependencies in GitHub Actions workflow files are pinned to commit SHAs, not tags.

```yaml
github_actions_unpinned_dependencies:
  behavior: review
  config:
    comment: true
    annotate: true
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `comment` | If set to true, SourceShield will comment on the PR with a message detailing any unpinned GitHub Actions | boolean | true |
| `annotate` | If set to true, SourceShield will annotate the PR inline with suggested changes to pin dependencies to known SHAs | boolean | true |

## Description
GitHub Actions that point to branches or tags can be changed by their owners with no notice. Pinning GitHub Actions to commit SHAs ensures that the upstream source of the Action does not change. This SourceShield check can automatically discover the corresponding commit SHA for a given tag and annotate the PR with the suggested change.

## References
* [https://devopsjournal.io/blog/2021/12/11/GitHub-Actions-Maturity-Levels](https://devopsjournal.io/blog/2021/12/11/GitHub-Actions-Maturity-Levels)

