---
title: Security Checks
layout: default
nav_order: 4
has_children: true
---

# Security Checks
{: .no_toc }

Security checks are one of SourceShield's main features. Security checks run when a pull request is opened and help enforce supply chain security best practices and surface potential risks. Security checks are configured entirely via code within the `.github/sourceshield.yml` configuration file in a repository.

## Setting up Checks
{: .no_toc }

Setting up a security check is as simple as adding its configuration to the repository's `.github/sourceshield.yml` config file. Select one or more SourceShield checks that are defined in the [reference section](#security-checks-reference), add them to the `security_checks` section of the `sourceshield.yml` file, and commit the change to the main branch of your repository.

## Enforcing Checks on Pull Requests
{: .no_toc }

For SourceShield to effectively block pull requests until the required security checks are met, you must configure GitHub's branch protection rules accordingly, using these steps (as a GitHub repository administrator or organization owner).

{: .warning }
These steps cannot be completed until SourceShield pull request checks run at least once on the specified repository.

1. Navigate to your repository and click "Settings"
1. Under "Code and automation" select "Branches"
1. Under "Branch protection rules" click "Add branch protection rule"
  ![Add branch protection rule](assets/images/add-branch-protection.png)
1. Enter your branch name pattern (e.g., "main")
1. Under "Protect matching branches" check the box that says "Require a pull request before merging"
1. Check "Require status checks to pass before merging"
1. Search for the check "SourceShield - Supply Chain Security Checks" and select it
  ![Add required status check](assets/images/add-status-check.png)
1. Scroll to the bottom of the page and click "Save"

Now, when a pull request is opened, SourceShield's status check must pass before the PR can be merged.
![Required status check](assets/images/pr-check.png)

## Comments
{: .no_toc }

Some security checks support "comments" in which SourceShield will add a comment on the pull request summarizing information discovered while running the check. This is designed to provide more context for pull request reviewers.

![Required status check](assets/images/check-comments.png)

This feature can be disabled by setting `comment: false` in the config of checks that support comments.

```yaml
security_checks:
  author_account_age:
    behavior: review
    comment: false
```

{: .warning }
Currently, if comments are enabled, SourceShield will comment after each commit on a PR. A feature is in progress to customize this behavior.

## Required Reviews
{: .no_toc }

When a SourceShield security check fails, it can either block the pull request, or the check can enter a pending state until the pull request is reviewed. This feature allows you to "soft block" a pull request until additional it has been reviewed further. For example, you could require that any failed checks be reviewed by someone from the security team before the PR can be merged.

SourceShield uses the `reviews` section of the `.github/sourceshield.yml` file to determine the review criteria:

```yaml
reviews:
  count: 2
  required:
    - userA

security_checks:
  author_account_age:
    behavior: review
```

This config tells SourceShield to require two approvals, one of which must be from the user `userA`, if the `author_account_age` check fails. If the `author_account_age` check passes, then no review is required (you may still configure GitHub to require reviews on PRs separately from SourceShield's checks).

## Security Checks Reference
{: .no_toc }

See the full list of supported checks below:

1. TOC
{:toc}