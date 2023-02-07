---
layout: default
title: Author Domain
parent: Security Checks
---

# Author Domain
Ensures the PR author email address belongs to an allowlisted domain

```yaml
author_domain:
  behavior: review
  config:
    allowed_domains: 
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `allowed_domains` | List of email domains. Ex: acme.org | array |  |

## Description
The pull request author's GitHub account age is one of many potential signals to consider when reviewing a proposed change. Malicious actors can create new GitHub accounts, without contribution history, and use them to submit malicious changes. Pull requests submitted by new accounts should be more heavily-scrutinized.

## References
* [https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/about-organization-membership](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/about-organization-membership)
