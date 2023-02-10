---
title: Config File Reference
layout: default
nav_order: 3
---

# Config File Reference

## The Config File
SourceShield is configured entirely via code using a configuration file, `.github/sourceshield.yml` placed in each repository in which SourceShield should function. If this file is not placed in this exact location, is not committed to the main branch, or does follow the format described below, SourceShield will not take any action on the given repository.

## File Structure
The config file must be valid YAML and follow the general structure outlined below:

```yaml
# The "reviews" section defines what review requirements need to be met to override failing checks
reviews:
  count: 2
  required:
    - user
  pool:
    - team/security
    - otheruser

# The "commands" section defines custom configuration options for SourceShield slash commands
commands:
  command_name:
    config:
        config_name: value

# The "security_checks" section defines security checks that will run on pull requests and commits
security_checks:
  check_name:
    behavior: review
    config:
      config_name: value
```

## Behaviors
SourceShield supports two behaviors when a security check fails:
* `review` - The PR checks will be marked as pending until the requisite reviews are met as defined in the `reviews` section of the config file.
* `block` - The PR will be marked as failing and, if configured via GitHub branch protection, cannot be merged until the check passes.

You can read more about these behaviors [here](/security_checks.html#required-reviews).

## Operation Modes
It is possible to use specific features of SourceShield without using others. For example, you can utilize slash commands by configuring the `commands` section of the config file while not defining any `security_checks` that should run, or vice versa.

## Example Config File
The example config file below shows a set of security checks currently supported by SourceShield. For more details on any of these supported functions, see the [Security Checks](/security_checks.html) and [Commands](/commands.html) pages.

```yaml
reviews:
  count: 2
  required:
    - userAbc

security_checks:
  # Require a review if the PR author account age is < 30 days old
  author_account_age:
    behavior: review
    config:
      min_age_days: 30
  # Block the PR if the PR author email address does not belong to acme.com or example.com
  author_domain:
    behavior: block
    config:
      allowed_domains:
        - acme.com
        - example.com
```
