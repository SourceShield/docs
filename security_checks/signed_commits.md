---
layout: default
title: Signed Commits
parent: Security Checks
---

# Signed Commits
Ensures the PR commits are cryptographically signed

```yaml
signed_commits:
  behavior: review
  config:
    gitsign_support: disabled
    rekor_url: https://rekor.sigstore.dev/api/v1
```

## Configuration

| Setting | Description | Type | Default |
| ------- | ----------- | ---- | ------- |
| `gitsign_support` | Whether gitsign should be enabled, disabled, or enforced. If set to enabled, the check will pass for both commits signed by gitsign and traditional keys. If set to disabled, gitsigned commits will fail. If set to enforced, only gitsigned commits will pass. | string | disabled |
| `rekor_url` | The base API URL to use for Rekor signature validation. You should not need to change this setting unless you are running your own Rekor transparency log. If so, ensure the endpoint is reachable publicly. | string | https://rekor.sigstore.dev/api/v1 |

## Description
Signing commits helps provide additional guarantees that the commit was submitted by the stated author. GitHub supports commit signing using GPG, SSH, or S/MIME. More recently tools such as gitsign have enabled keyless signing via sigstore. However, these tools are not yet natively supported by GitHub. This SourceShield check expands support for these tools by checking pull request commits for the presence of a gitsigned commit and verifying that signature on the Rekor transparency log.

## References
* [https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)
* [https://github.com/sigstore/gitsign](https://github.com/sigstore/gitsign)

