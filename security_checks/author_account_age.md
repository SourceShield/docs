---
layout: default
title: Author Account Age
parent: Security Checks
---

# Author Account Age
Ensures the PR author account age is not too new

```yaml
author_account_age:
  behavior: review
  config:
    min_age_days: 1
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `min_age_days` | The minimum age, in days, for an account to author PRs | integer | 1 |

## Description
The pull request author's GitHub account age is one of many potential signals to consider when reviewing a proposed change. Malicious actors can create new GitHub accounts, without contribution history, and use them to submit malicious changes. Pull requests submitted by new accounts should be more heavily-scrutinized.

## References
_None_
