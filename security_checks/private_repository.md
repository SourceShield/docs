---
layout: default
title: Private Repository
parent: Security Checks
---

# Private Repository
Ensures the repository is private

```yaml
private_repository:
  behavior: review
```

## Configuration

_None_

## Description
Repositories marked as private should not be made public. This check ensures that the repository visibility settings are checked on each pull request.

## References
* [https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)

