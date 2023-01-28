---
title: Security
layout: default
nav_order: 6
---

# Security
SourceShield is configured to process and store the least amount of data necessary for it to function, and is operated with a minimal infrastructure footprint in a secure cloud environment.

## Infrastructure Architecture
SourceShield is hosted on Amazon Web Services (AWS) as a single Lambda function. The function is given a URL, which is fronted by a CloudFront CDN. This CloudFront CDN is configured to only allow inbound requests from IP addresses that [belong to GitHub](https://api.github.com/meta) (only GitHub `hooks` IP addresses are allowed; SourceShield is not directly accessible from Actions runners).

There are no traditional data stores; SourceShield does not store any customer data in a database, cache, persistent disk storage, or other location. Data is processed in-memory only. SourceShield does collect logs, which include information such as the GitHub installation ID, organization name, and debug information associated with processing requests, and these logs are retained for 365 days.

SourceShield does not have any other interface besides its GitHub Application; there is no SaaS environment or user credentials.

## Data Access
When SourceShield is installed on a GitHub account or organization, it can be configured with access to "All Repositories" or "Select Repositories." When the former option is selected, SourceShield has access to all repositories in the account, including private repositories (see below for a list of specific permissions). When the latter option is selected, SourceShield can only access the repositories selected at installation time. This configuration can be changed at any time by going to the application installation settings page.

## GitHub Permissions
The SourceShield GitHub Application listens for specific events that occur within the GitHub account or organization. Additionally, it requests specific permissions to support its functionality.

### Events
SourceShield listens for the following events:
* `check_run` - A GitHub "check" is run. The primary functionality of SourceShield is to create passing or failing checks on pull requests.
* `check_suite` - A GitHub check suite is requested. This happens when a new commit is pushed or a pull request is opened.
* `issue_comment` - A comment is created on a GitHub issue or pull request. This allows SourceShield to listen for `/sourceshield` slash commands. Note: if the comment does not contain the `/sourcehshield` keyword, the request is dropped and processing is stopped immediately.
* `issues` - A new issue is opened. Similar to the above, no processing occurs unless the `/sourceshield` keyword is used in the issue body.
* `pull_request` - A pull request is opened. This allows SourceShield to check for the `/sourceshield` keyword in the pull request body.
* `pull_request_review` - A pull request review is submitted. SourceShield processes the review to determine whether the criteria is met for pull request checks to pass.

### Permissions
SourceShield requests the following permissions. Note that, due to GitHub's permission design, some permissions may appear overly-broad. SourceShield only uses the permissions for the reasons stated below.
* [administration: read](https://developer.github.com/v3/apps/permissions/#permission-on-administration) - Allows SourceShield to view configuration settings for the organization and selected repositories, including member permissions and teams. This information is used by some of SourceShield's security checks, as well as when a pull request review is submitted (to determine the team membership of the reviewer).
* [checks: write](https://developer.github.com/v3/apps/permissions/#permission-on-checks) - When a pull request is opened, SourceShield creates GitHub checks to indicate compliance with the defined best practices for that pull request.
* [contents: read](https://developer.github.com/v3/apps/permissions/#permission-on-contents) - Read-only access to repository content. This allows SourceShield to access the configuration file (located in each repository at `.github/sourceshield.yml`), as well as to parse files for security risks (such as GitHub action files, package.json dependency files, etc.).
* [issues: write](https://developer.github.com/v3/apps/permissions/#permission-on-issues) - Allows SourceShield to create issues in selected repositories in the event that a configured security check fails (for example, SourceShield can open a GitHub issue and tag the security team if the repository is accidentally made public).
* [metadata: read](https://developer.github.com/v3/apps/permissions/#metadata-permissions) - Allows SourceShield to read details about repositories, search user activity, and get collaborator permissions as part of its security checks.
* [pull_requests: write](https://developer.github.com/v3/apps/permissions/#permission-on-pull-requests) - SourceShield can be configured to comment on pull requests, as well as to request reviews from specific users or teams (when configured to do so). These actions require write access. SourceShield does not currently create pull requests in any repository.
* [members: read](https://developer.github.com/v3/apps/permissions/#permission-on-members) - SourceShield uses the list of members in an organization as part of some security checks and commands (such as the "PR Author Reputation Report" which includes information about a pull request author's membership in the provided organization).

## Billing
All account billing is managed by our PCI-compliant third-party payment provider, Stripe. SourceShield does not have visibility into user payment account numbers.

## Responsible Disclosure
If you discover a security concern with SourceShield, please email `security@sourceshield.io` with a detailed description of the issue. We will respond within 24 hours.