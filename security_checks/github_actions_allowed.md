---
layout: default
title: GitHub Actions Allowed
parent: Security Checks
---

# GitHub Actions Allowed
Ensures GitHub Actions are only used if allowed and approved

```yaml
github_actions_allowed:
  behavior: review
  config:
    comment: true
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `comment` | If set to true, SourceShield will comment on the PR with a message summarizing the GitHub Actions workflow changes | boolean | true |

## Description
The use of GitHub Actions can expand the attack surface of your supply chain and their configuration should be carefully reviewed. This check, if enabled, monitors for the addition of files to the repository that indicate the addition or modification of GitHub Actions.

## References
* [https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)
* [https://engineering.salesforce.com/github-actions-security-best-practices-b8f9df5c75f5/](https://engineering.salesforce.com/github-actions-security-best-practices-b8f9df5c75f5/)

