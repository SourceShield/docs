---
title: Home
layout: home
nav_order: 1
---

# SourceShield Documentation

## What is SourceShield?
[SourceShield](https://sourceshield.io) is a software supply chain security platform that integrates directly into build and deploy tooling to detect security risks and enforce supply chain best practices. SourceShield is installed as a GitHub Application, which is the sole interface for interacting with the platform. There are no SaaS dashboards, logins, APIs, or other sites that you, or your organization's developers, need to manage.

## What does SourceShield do?
SourceShield secures your build and deploy environments by surfacing potential supply chain security risks, enforcing best practices, and gently nudging your developers to adopt better security practices.

There are three main components of SourceShield:
1. PR Review and Enforcement
    1. SourceShield can be configured to enforce certain supply chain security requirements, either by blocking pull request merges or by requiring a review from one or more reviewers.
2. SourceShield Commands
    1. SourceShield supports a variety of slash commands ("/sourceshield") in comments on GitHub pull requests and issues that provide contextual security information about the pull request or repository.
3. Real-Time Event Monitoring (Coming Soon)
    1. SourceShield has visibility into real-time events as they occur in your SCM, build, and deploy tooling and can take action in response to events that are deemed to be a security risk.