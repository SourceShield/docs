---
title: FAQ
layout: default
nav_order: 8
---

# FAQ

## Q. What are the requirements to use SourceShield?
SourceShield works on any GitHub account or organization (although it does not currently support GitHub Enterprise). It can be configured to run on any public repository. Private repository support is limited to specific design partners as we continue building out additional functionality (if interested, please click [here](https://docs.google.com/forms/d/e/1FAIpQLSeHOxckS_aCSu5rzsYHVTrEEjInfNcTAngzZF2BwDAozb7RpQ/viewform?usp=sf_link)).

## Q. What should I expect while SourceShield is in beta?
SourceShield is under active development. While in beta, features may change, or be removed. We may add or remove permissions, which may require updates to your GitHub application installation. You may encounter bugs. We encourage you to [file](https://github.com/SourceShield/support/issues/new/choose) bug reports and feature requests.

## Q. How much will SourceShield cost?
We're not sure yet. However, the current plan is to make most features of SourceShield free for public (open source) repositories while requiring a paid plan for usage on private repositories. When our pricing model is finalized, it will be transparent and public on our website and subscribing will not require any calls with a sales team.

## Q. Who is SourceShield designed for?
SourceShield is designed for both open source maintainers as well as security and development teams. For open source maintainers, SourceShield has a variety of features to help surface potential risks that arise from changes submitted to repositories (e.g., flagging contributions from authors with no history with the project or from accounts made recently with no other GitHub profile details). For security teams, SourceShield can help flag potential supply chain risks for further review (e.g., the introduction of new build tools, addition of risky dependencies, anomalous developer behavior) or outright block code changes that violate a security policy.

## Q. What makes SourceShield different?
Software supply chain security is complex, and there are many products trying to "solve" these problems. SourceShield is not a CVE scanner, and isn't designed to audit for traditional code-based vulnerabilities (e.g., XSS, SQLi). Instead, SourceShield's approach is to integrate directly with developer tooling, like GitHub, to prioritize proactive remediation to security risks that affect pipelines, build systems, and SCM platforms. SourceShield also aims to surface signals and context related to risks (both directly via pull requests and upstream in dependencies), empowering developers and security teams to make pragmatic risk-tradeoff decisions. SourceShield is highly customizable, so that each organization can define the exact security posture that is appropriate for them.

## Q. What is on the roadmap?
A lot! The current beta release of SourceShield is limited to a handful of security checks and commands so that we can carefully test SourceShield's core functionality. However, there are many additional features we have planned, including:
* Dependency reputation checking - when new dependencies are added to a codebase, SourceShield will check upstream sources, such as [OpenSSF Scorecards](https://github.com/ossf/scorecard) and [deps.dev](https://deps.dev/) for additional context about the security posture of those dependencies.
* Access monitoring - SourceShield has visibility into the users, teams, access permissions, third-party applications, and other entities that can access and modify code and SCM settings and can alert on risky access or changes.
* Automated code suggestions - SourceShield can annotate pull request code as part of its checks, which can be used to suggest more secure alternatives. For example, if a developer adds a GitHub action mapped to a tag (`@v1`), SourceShield can suggest that tag's SHA instead (a best practice for Actions).
* So much more! The software supply chain surface area is massive and SourceShield has a lot of potential expansion areas. We welcome feedback!

## Q. What are some limitations of SourceShield?
We're continually looking into ways to expand SourceShield, however the areas below are more technically challenging due to choices and tradeoffs we've explicitly made or in-development feature work:

* SBOMs - At the moment, we don't believe there is value in having SourceShield generate SBOMs. There are plenty of tools already on the market (open source and commercial) that can do this.
* Visualizations and Searching - because SourceShield does not have a SaaS interface, visualizations such as charts and graphs are more challenging to generate. Additionally, searching through an inventory of dependencies and supply chain components is also not currently supported.
* Code Changes - Due to its security model, SourceShield does not currently write changes to code via pull requests or inline pull request review suggestions. This will likely change if we're able to ensure this write-level access is limited in scope.
* Rate Limits and Pagination - GitHub has aggressive rate limiting in place for many of its APIs. Some of SourceShield's checks require it to request lots of data (e.g., a list of all files being changed in a PR), which may be limited while we work out pagination while observing the necessary rate limits.