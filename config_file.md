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
  # Ensures the PR author account age meets the minimum requirement
  check_name:
    behavior: review
    config:
      config_name: value
```

## Operation Modes
It is possible to use specific features of SourceShield without using others. For example, you can utilize slash commands by configuring the `commands` section of the config file while not defining any `security_checks` that should run, or vice versa.

## Full Reference File
The example config file below shows a complete set of all available options for all commands and security checks currently supported by SourceShield. For more details on any of these supported functions, see the [Security Checks](/security_checks.html) and [Commands](/commands.html) pages.

```yaml

```