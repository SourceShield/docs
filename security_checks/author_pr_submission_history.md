---
layout: default
title: Author PR Submission History
parent: Security Checks
---

# Author PR Submission History
Ensures the PR author has contributed to the repository previously

```yaml
author_pr_submission_history:
  behavior: review
  config:
    lookback_days: 90
    threshold: 1
    merged_only: true
    comment: true
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `lookback_days` | How many days of history to consider when determining whether an author is considered active | integer | 90 |
| `threshold` | How many matching PRs is considered a signal of an active, trusted contributor. For example, if set to 5, then fewer than 5 pull requests for the author will fail this check. | integer | 1 |
| `merged_only` | Only count PRs that were successfully merged | boolean | true |
| `comment` | If set to true, SourceShield will comment on the PR with a message summarizing the author contribution history | boolean | true |

## Description
Previous contributions are one of many important security signals to consider when reviewing a pull request. Pull requests submitted by authors that have significant contribution history to the repository are less likely to be malicious. It is also important to consider the merge success rate of previous contributions.

## References
_None_
