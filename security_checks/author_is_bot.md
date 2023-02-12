---
layout: default
title: Author is Bot
parent: Security Checks
---

# Author is Bot
Flags automated PRs that have been opened by bots

```yaml
author_is_bot:
  behavior: review
  config:
    allowed_bots: 
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `allowed_bots` | Bots that are approved to open PRs. | array |  |

## Description
Only trusted bots should be allowed to commit code to the repository.

## References
_None_
