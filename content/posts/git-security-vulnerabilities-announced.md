---
title: "Git security vulnerabilities announced"
date: 2025-01-15
tags: 
  - "development"
  - "git"
  - "github"
  - "gitlab"
  - "software"
---

A new set of Git releases were published to address a variety of security vulnerabilities. All users are encouraged to upgrade. Take a look at GitHub’s view of the latest round of releases.

The post Git security vulnerabilities announced appeared first on The GitHub Blog.

Today, the Git project released new versions to address a pair of security vulnerabilities, CVE-2024-50349 and CVE-2024-52006, that affect all prior versions of Git.

## CVE-2024-50349

When Git needs to fill in credentials interactively without the use of a credential helper, it prints out the hostname and asks the user to fill in the appropriate username/password pair for that host. However, Git prints out the hostname after URL-decoding it. This allows an attacker to craft URLs containing ANSI escape sequences that may be used to construct an intentionally misleading prompt. The attacker may then tweak the prompt to trick a user into providing credentials for a different Git host back to the attacker.

\[source\]

## CVE-2024-52006

When using a credential helper (as opposed to asking the user for their credentials interactively as above), Git uses a line-based protocol to pass information between itself and the credential helper. A specially-crafted URL containing a carriage return can be used to inject unintended values into the protocol stream, causing the helper to retrieve the password for one server while sending it to another.

This vulnerability is related to CVE-2020-5260, but relies on behavior where single carriage return characters are interpreted by some credential helper implementations as newlines.

\[source\]

## Upgrade to the latest Git version

The most effective way to protect against these vulnerabilities is to upgrade to Git 2.48.1. If you can’t upgrade immediately, reduce your risk by taking the following steps:

- Avoid running `git clone` with `--recurse-submodules` against untrusted repositories.
- Avoid using the credential helper by only cloning publicly available repositories.

In order to protect users against attacks related to these vulnerabilities, GitHub has taken proactive steps. Specifically, we have scheduled releases of GitHub Desktop (CVE-2025-23040), Git LFS (CVE-2024-53263), and Git Credential Manager (CVE-2024-50338) that prevent exploiting this vulnerability for today, January 14.

GitHub has also proactively patched our products that were affected by similar vulnerabilities, including GitHub Codespaces and the GitHub CLI.

* * *

CVE-2024-50349 and CVE-2024-52006 were both reported by RyotaK. The fixes for both CVEs were developed by Johannes Schindelin, with input and review from members of the private git-security mailing list.

The post Git security vulnerabilities announced appeared first on The GitHub Blog.

Go to Source
