---
title: "Blog: Improve your changelogs"
date: 2025-01-03
categories: 
  - "cloud"
  - "cloudnative"
  - "devops"
  - "general"
  - "linux"
tags: 
  - "jenkins"
---

## Background

A standard part of the Jenkins X pipelines since a long time is the execution of `jx changelog create` that takes the commit messages between the release currently being created and the previous one and creates a change log from these. The change log is then stored as a release note in GitHub or other git provider.

During the last year some improvements have landed in various Jenkins X components to improve the changelogs and their usefulness. So I’ll take this opportunity to describe these improvements and also in general give hints to how to get useful changelogs.

## Overview of major improvements

Changelogs haven’t been very informative with regard to upgrades, ie those applied with `jx promote` or `jx updatebot`. One example of this is the release notes of jx after the split out of most functionality to plugins. Lately these have improved due to new functionality to propagate changelogs via pull requests.

One place where changelogs have been completely lacking is in cluster repositories. But using the functionality for propagation of changelogs and some changes in jx boot job you can now a get a changelog for every successful application of changes in a cluster.

## Example

An example of what this functionality achieves can be seen in a release of jx:

https://github.com/jenkins-x/jx/releases/tag/v3.10.81

If you scroll past the boilerplate installation instructions you first see the changelog of jx itself generated from commit messages: https://github.com/jenkins-x/jx/compare/v3.10.80...v3.10.81

Then there is a separator followed by the changelog of jx-gitops. If you look in the commit messages referred to above you will see a link to the pull request on jx for this upgrade: https://github.com/jenkins-x/jx/pull/8564. As you can see this pull request includes the changelog for version 0.14.8 of jx-gitops as generated by `jx changelog create`.

Essentially what happens is that `jx changelog create` apart from storing the release information of jx-gitops also stores it in a file. This file is then put in the pull request on jx by `jx updatebot`. Finally `jx changelog create` looks for changelogs in the pull requests referred to in the merge commit.

## How to write commit messages

To get a good changelog the first requisite is to write good commit messages. `jx changelog create` expects commit messages to adhere to the Conventional commits standard. It is the first line of each commit message that is used, with a couple of exceptions I’ll describe below.

When following this standard the first line should adhere to this format:

`<type>[optional scope]: <description>`

While `jx changelog create` can handle any type some will be expanded for a better looking changelog:

- `feat`: New Features
- `fix`: Bug Fixes
- `perf`: Performance Improvements
- `refactor`: Code Refactoring
- `docs`: Documentation
- `test`: Tests
- `revert`: Reverts
- `style`: Styles

Since the description is used verbatim in the changelog it should be meaningful to the audience of the changelog. Is for example `fixed typo` meaningful? Maybe it is better to write what you try to achieve. While doing this it is good to know that duplicate descriptions are ignored by changelog. So if you add the same description again when doing a fix doesn’t mean that you get duplicate lines in the changelog.

An optional scope is prefixed to the description in the changelog.

The other common part of the commit message that is reflected in the changelog are references to issues. These can be put anywhere in the commit message. These issues are then linked to both for the specific commit and in a separate list of affected issues.

An example:

```
feat: support dependency updates

fixed typo

relates to #1234
```

A less common part of a commit message that affects the changelog regards breaking changes. A footer to a commit message of the format `BREAKING CHANGE: <description>` can be added and this description will be put at the top of the changelog under the heading BREAKING CHANGES. If you add an exclamation mark before the colon in the first line without the breaking change footer the ordinary description will be put under this heading.

A couple of examples regarding braking changes:

```
fix: upgraded library foo

BREAKING CHANGE: don't support http anymore

#98765
```

```
fix!: removed insecure method fubar

resolves #56789
```

Good to know is that `jx release version` also conforms to Conventional Commits so the commit messages also affects which part of the semantic version is increased for a release.

There are of course other uses of good commit messages than to generate changelogs. While code itself together with comments should be self-explanatory with regard to what is done and how I often resort to commit messages to understand why a change was made. I typically use the git blame functionality for this. This is another reason to not use messages only saying something like `fixed typo`, since that typically isn’t a useful answer to the question of why for a future developer.

For more tips regarding writing good commit messages see for example How to Write Better Git Commit Messages.

## Manually edit changelog

Note that since changelogs for dependencies are propagated through pull requests you can edit the changelog for an application manually in the pull request before it is merged.

## Configuration

Some of the features described above work out-of-the-box while others require some tweaking.

### Changelog for cluster repository

Apart from the other advantages of switching from `kubectl apply` to `kpt live apply` for reconciliation of cluster repository with the cluster you also get a changelog generated for each successful reconciliation.

This changelog also includes a list of upgraded / added / deleted releases and the associated versions.

See a previous blogpost for more information.

### Reuse pull requests

With the default settings one pitfall with the propagating the changelog via pull requests is if not all pull requests are merged. Let’s say version 1.0.0 of an application is released and pull request with a big changelog is created for the production namespace. But before it is merged an error is detected and version 1.0.1 is released and a PR for the version is created which only includes the changelog for the bug fix. When that PR is merged only the changelog for the bug fix ends up in the changelog for the cluster.

To mitigate this you can enable reuse of pull requests. This means that if a PR for upgrading a dependency already exists when executing `jx promote` or `jx updatebot` the commits for that PR are replaced with one for the new upgrade. The existing changelog in the PR is kept though and the changelog for the new version is appended. This way no changelog is missed.

Enabling reuse of pull requests for `jx promote` is done in `jx-requirements.yaml` by setting `reusePullRequest` to `true` for an environment. It can also be done in the same way when configuring environments others ways. See https://jenkins-x.io/v3/develop/environments/config/ for more details about configuring environments.

More information about reuse of pull requests in a future blog post.

### Custom pipelines

In the pipelines defined in https://github.com/jenkins-x/jx3-pipeline-catalog/ the necessary incantations of `jx changelog`, `jx promote` and `jx updatebot` are made for promoting changelogs. But if you have a custom release pipeline you might need to do some modifications. In particular `jx changelog create` need to save the changelog to a file. This is done by adding an argument like `--output-markdown=../changelog.md`. To have this changelog added to the PR the option `--add-changelog=../changelog.md` needs to be added to `jx promote` (or `jx updatebot` if applicable).

### Jira as issue tracker

In the examples of commit messages above the references to issues are to the git provider. This is the default, so if you for example are using GitHub as your git provider and also use the issue tracker in GitHub no extra configuration is needed.

But there also is support for Jira as issue tracker. If you enable this support you can refer to issues both at the git provider and in Jira.

You enable Jira support and configure it in the jx-requirements.yaml of the cluster repository. The `issueProvider` field is added under `spec.cluster`:

```diff
@@ -13,5 +13,9 @@ spec:
     gitKind: github
     gitName: github
     gitServer: https://github.com
+    issueProvider:
+      jira:
+        serverUrl: https://myjira.atlassian.net
+        userName: jirauser@example.com
     project: "123456789"
     provider: eks
```

For security reasons the credentials for the user that will fetch data from Jira is not put there. Instead `jx changelog` expects it in the environment variable `JIRA_API_TOKEN`. The easiest way to supply this environment variable is by adding it to the secret `jx-boot-job-env-vars` in namespace `jx` since the content av this secret are exposed as environment variables to all standard build pipelines. If the secret doesn’t exist you can create it yourself like this:

```bash
# lets make sure we are in the jx-git-operator namespace
jx ns jx-git-operator

kubectl create secret generic jx-boot-job-env-vars --from-literal=JIRA_API_TOKEN='S!B*d$zDsb'
```

The Terraform module for Jenkins X in EKS also have support for adding variables to `jx-boot-job-env-vars`.

### More customizations

In the documentations for `jx changelog create` information about more customisations can be found.

## References

The enhancement proposal for propagation of changelogs

## Background

A standard part of the Jenkins X pipelines since a long time is the execution of `jx changelog create` that takes the commit messages between the release currently being created and the previous one and creates a change log from these. The change log is then stored as a release note in GitHub or other git provider.

During the last year some improvements have landed in various Jenkins X components to improve the changelogs and their usefulness. So I’ll take this opportunity to describe these improvements and also in general give hints to how to get useful changelogs.

## Overview of major improvements

Changelogs haven’t been very informative with regard to upgrades, ie those applied with `jx promote` or `jx updatebot`. One example of this is the release notes of jx after the split out of most functionality to plugins. Lately these have improved due to new functionality to propagate changelogs via pull requests.

One place where changelogs have been completely lacking is in cluster repositories. But using the functionality for propagation of changelogs and some changes in jx boot job you can now a get a changelog for every successful application of changes in a cluster.

## Example

An example of what this functionality achieves can be seen in a release of jx:

https://github.com/jenkins-x/jx/releases/tag/v3.10.81

If you scroll past the boilerplate installation instructions you first see the changelog of jx itself generated from commit messages: https://github.com/jenkins-x/jx/compare/v3.10.80...v3.10.81

Then there is a separator followed by the changelog of jx-gitops. If you look in the commit messages referred to above you will see a link to the pull request on jx for this upgrade: https://github.com/jenkins-x/jx/pull/8564. As you can see this pull request includes the changelog for version 0.14.8 of jx-gitops as generated by `jx changelog create`.

Essentially what happens is that `jx changelog create` apart from storing the release information of jx-gitops also stores it in a file. This file is then put in the pull request on jx by `jx updatebot`. Finally `jx changelog create` looks for changelogs in the pull requests referred to in the merge commit.

## How to write commit messages

To get a good changelog the first requisite is to write good commit messages. `jx changelog create` expects commit messages to adhere to the Conventional commits standard. It is the first line of each commit message that is used, with a couple of exceptions I’ll describe below.

When following this standard the first line should adhere to this format:

`<type>[optional scope]: <description>`

While `jx changelog create` can handle any type some will be expanded for a better looking changelog:

- `feat`: New Features
- `fix`: Bug Fixes
- `perf`: Performance Improvements
- `refactor`: Code Refactoring
- `docs`: Documentation
- `test`: Tests
- `revert`: Reverts
- `style`: Styles

Since the description is used verbatim in the changelog it should be meaningful to the audience of the changelog. Is for example `fixed typo` meaningful? Maybe it is better to write what you try to achieve. While doing this it is good to know that duplicate descriptions are ignored by changelog. So if you add the same description again when doing a fix doesn’t mean that you get duplicate lines in the changelog.

An optional scope is prefixed to the description in the changelog.

The other common part of the commit message that is reflected in the changelog are references to issues. These can be put anywhere in the commit message. These issues are then linked to both for the specific commit and in a separate list of affected issues.

An example:

```
feat: support dependency updates

fixed typo

relates to #1234
```

A less common part of a commit message that affects the changelog regards breaking changes. A footer to a commit message of the format `BREAKING CHANGE: <description>` can be added and this description will be put at the top of the changelog under the heading BREAKING CHANGES. If you add an exclamation mark before the colon in the first line without the breaking change footer the ordinary description will be put under this heading.

A couple of examples regarding braking changes:

```
fix: upgraded library foo

BREAKING CHANGE: don't support http anymore

#98765
```

```
fix!: removed insecure method fubar

resolves #56789
```

Good to know is that `jx release version` also conforms to Conventional Commits so the commit messages also affects which part of the semantic version is increased for a release.

There are of course other uses of good commit messages than to generate changelogs. While code itself together with comments should be self-explanatory with regard to what is done and how I often resort to commit messages to understand why a change was made. I typically use the git blame functionality for this. This is another reason to not use messages only saying something like `fixed typo`, since that typically isn’t a useful answer to the question of why for a future developer.

For more tips regarding writing good commit messages see for example How to Write Better Git Commit Messages.

## Manually edit changelog

Note that since changelogs for dependencies are propagated through pull requests you can edit the changelog for an application manually in the pull request before it is merged.

## Configuration

Some of the features described above work out-of-the-box while others require some tweaking.

### Changelog for cluster repository

Apart from the other advantages of switching from `kubectl apply` to `kpt live apply` for reconciliation of cluster repository with the cluster you also get a changelog generated for each successful reconciliation.

This changelog also includes a list of upgraded / added / deleted releases and the associated versions.

See a previous blogpost for more information.

### Reuse pull requests

With the default settings one pitfall with the propagating the changelog via pull requests is if not all pull requests are merged. Let’s say version 1.0.0 of an application is released and pull request with a big changelog is created for the production namespace. But before it is merged an error is detected and version 1.0.1 is released and a PR for the version is created which only includes the changelog for the bug fix. When that PR is merged only the changelog for the bug fix ends up in the changelog for the cluster.

To mitigate this you can enable reuse of pull requests. This means that if a PR for upgrading a dependency already exists when executing `jx promote` or `jx updatebot` the commits for that PR are replaced with one for the new upgrade. The existing changelog in the PR is kept though and the changelog for the new version is appended. This way no changelog is missed.

Enabling reuse of pull requests for `jx promote` is done in `jx-requirements.yaml` by setting `reusePullRequest` to `true` for an environment. It can also be done in the same way when configuring environments others ways. See https://jenkins-x.io/v3/develop/environments/config/ for more details about configuring environments.

More information about reuse of pull requests in a future blog post.

### Custom pipelines

In the pipelines defined in https://github.com/jenkins-x/jx3-pipeline-catalog/ the necessary incantations of `jx changelog`, `jx promote` and `jx updatebot` are made for promoting changelogs. But if you have a custom release pipeline you might need to do some modifications. In particular `jx changelog create` need to save the changelog to a file. This is done by adding an argument like `--output-markdown=../changelog.md`. To have this changelog added to the PR the option `--add-changelog=../changelog.md` needs to be added to `jx promote` (or `jx updatebot` if applicable).

### Jira as issue tracker

In the examples of commit messages above the references to issues are to the git provider. This is the default, so if you for example are using GitHub as your git provider and also use the issue tracker in GitHub no extra configuration is needed.

But there also is support for Jira as issue tracker. If you enable this support you can refer to issues both at the git provider and in Jira.

You enable Jira support and configure it in the jx-requirements.yaml of the cluster repository. The `issueProvider` field is added under `spec.cluster`:

```diff
@@ -13,5 +13,9 @@ spec:
     gitKind: github
     gitName: github
     gitServer: https://github.com
+    issueProvider:
+      jira:
+        serverUrl: https://myjira.atlassian.net
+        userName: jirauser@example.com
     project: "123456789"
     provider: eks
```

For security reasons the credentials for the user that will fetch data from Jira is not put there. Instead `jx changelog` expects it in the environment variable `JIRA_API_TOKEN`. The easiest way to supply this environment variable is by adding it to the secret `jx-boot-job-env-vars` in namespace `jx` since the content av this secret are exposed as environment variables to all standard build pipelines. If the secret doesn’t exist you can create it yourself like this:

```bash
# lets make sure we are in the jx-git-operator namespace
jx ns jx-git-operator

kubectl create secret generic jx-boot-job-env-vars --from-literal=JIRA_API_TOKEN='S!B*d$zDsb'
```

The Terraform module for Jenkins X in EKS also have support for adding variables to `jx-boot-job-env-vars`.

### More customizations

In the documentations for `jx changelog create` information about more customisations can be found.

## References

The enhancement proposal for propagation of changelogs

Go to Source
