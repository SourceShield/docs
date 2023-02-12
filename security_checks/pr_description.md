---
layout: default
title: PR Description
parent: Security Checks
---

# PR Description
Ensures the PR contains a valid description of the change

```yaml
pr_description:
  behavior: review
  config:
    regex: .+
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `regex` | Regex to match a valid PR description. The default matches any non-empty string, but it is recommended to customize this pattern according to your organization's best practices. | string | .+ |

## Description
Pull requests should be submitted with a comprehensive description that includes details about the changes made and why those changes were required.

## References
* [https://www.pullrequest.com/blog/writing-a-great-pull-request-description/](https://www.pullrequest.com/blog/writing-a-great-pull-request-description/)

