---
title: Home
layout: home
nav_order: 1
image: /assets/images/cover.png
---

# SourceShield Documentation

{: .warning }
SourceShield is currently in beta and only functions on public repositories. Some of the functionality described in the documentation may be limited to specific users, or change without notice. To participate in our beta program, please submit your interest [here](https://docs.google.com/forms/d/e/1FAIpQLSeHOxckS_aCSu5rzsYHVTrEEjInfNcTAngzZF2BwDAozb7RpQ/viewform?usp=sf_link).

## What is SourceShield?
[SourceShield](https://sourceshield.io) is a software supply chain security platform that integrates directly into build and deploy tooling to detect security risks and enforce supply chain best practices. SourceShield is installed as a GitHub Application, which is the sole interface for interacting with the platform. There are no SaaS dashboards, logins, APIs, or other sites that you, or your organization's developers, need to manage. SourceShield's model is to pragmatically surface supply chain risks before they are introduced rather than overwhelming developers and security teams with alerts.

## What does SourceShield do?
SourceShield secures your software build and deploy environments by surfacing potential supply chain security risks, enforcing best practices, and gently nudging your developers to adopt better security practices.

There are three main components of SourceShield:
1. PR Review and Enforcement
    1. SourceShield can be configured to enforce certain supply chain security requirements using GitHub checks, either by blocking pull request merges or by requiring a review from one or more reviewers.
2. SourceShield Commands
    1. SourceShield supports a variety of slash commands ("/sourceshield") in comments on GitHub pull requests and issues that provide contextual security information about the pull request or repository.
3. Real-Time Event Monitoring (Coming Soon)
    1. SourceShield has visibility into real-time events as they occur in your SCM, build, and deploy tooling and can take action in response to events that are deemed to be a security risk.

## What does that mean in practice?
SourceShield is highly configurable and the entirety of its configuration is defined as code directly within the repositories it secures. Some of the many scenarios that SourceShield can support include:

* Preventing new pull requests from being merged if a repository has been made public
* Requiring additional PR reviews from the security team if a repository's dependencies are being downgraded
* Enforcing best practices on GitHub Actions (locking to known image SHAs, avoiding parameter injection, etc.)
* Requiring additional PR reviews if a pull request is being made on a public repository by a GitHub user outside of the organization
* Ensuring that commits that are signed using [gitsign](https://github.com/sigstore/gitsign) are properly recorded on the Rekor transparency log
* Providing additional context on a PR author's contribution history and familiarity with the codebase when submitting PRs
* Preventing "shadow IT" in the form of unapproved build tooling or third-party applications in the SCM
* Enforcing organization best practices on code changes, such as requiring PR descriptions
* Flagging certain files and file types as "sensitive" and requiring additional review when they are modified

For a full list of capabilities, see: [Security Checks](/security_checks.html) and [Commands](/commands.html).