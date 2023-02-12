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
    comment: true
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `allowed_domains` | List of email domains. Ex: acme.org | array |  |
| `comment` | If set to true, SourceShield will comment on the PR with a message containing the author email domain | boolean | true |

## Description
GitHub user account email addresses can be set to corporate or organization domains, which can be used as one signal during a pull request review. This check ensures that a GitHub account belongs to one of a set of pre-approved domains.

## References
* [https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account)

