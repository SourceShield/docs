---
layout: default
title: Webhook SSL
parent: Security Checks
---

# Webhook SSL
Ensures repository webhooks have SSL enabled

```yaml
webhook_ssl:
  behavior: review
```

## Configuration

_None_

## Description
Repository webhooks should be configured to use SSL to ensure encryption in transit.

## References
* [https://docs.github.com/en/webhooks-and-events/webhooks/securing-your-webhooks](https://docs.github.com/en/webhooks-and-events/webhooks/securing-your-webhooks)

