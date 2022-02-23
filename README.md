# github-apps-config-next

[![CircleCI](https://circleci.com/gh/Financial-Times/github-apps-config-next.svg?style=svg)](https://circleci.com/gh/Financial-Times/github-apps-config-next)

## What's this?
This repository is where [FT Customer Products](https://biz-ops.in.ft.com/Group/customerproducts) keeps our shared configuration files for our GitHub Apps.

We use GitHub Apps to [help manage our hundreds of GitHub repositories](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories).

> Note: The above links are only accessible to FT.com employees.

* The configuration files for each of our GitHub Apps are in the `.github/` folder.
* The configuration files for managing our GitHub Apps are in the `manage-github-apps/` folder.

## The [`.github/`](https://github.com/Financial-Times/github-apps-config-next/tree/main/.github) folder

This folder contains configuration files for different [GitHub Apps](https://developer.github.com/apps/).

#### [`settings.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/main/.github/settings.yml)

This configures the settings for your GitHub repository. The settings are applied by the ["Settings" GitHub App](https://probot.github.io/apps/settings).

> We use the [`probot-config`](https://github.com/probot/probot-config) extension to share `settings.yml`. This way we can change it here — and it'll automatically extend to all our other repositories.
>
> Within your repository, load our shared settings like so:

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: github-apps-config-next
```

> You can overwrite the settings after loading them.

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: github-apps-config-next

repository:
  has_wiki: true
  has_projects: true
branches:
  - name: main
    protection:
      # Take the base rules but also require 1 approval
      required_pull_request_reviews:
        required_approving_review_count: 1
      # Also require some status checks to pass
      required_status_checks:
        contexts:
          - build-test
          - "ci/circleci: build"
          - "ci/circleci: test"
```

##### Important Note About Status Checks

You **must** include the status checks you expect to pass in the overriding config, otherwise no checks will be required to pass before merging. For example, if you expect CircleCI's `test` job to be passing before you'd consider merging a PR branch you might have a simple `.github/settings.yml` file like
```yaml
_extends: github-apps-config-next
branches:
  - name: main
    protection:
      required_status_checks:
        checks:
          - "ci/circleci: test"
```
Pleasingly, the Probot app will merge the overridden `main` setting with the rest of the inherited settings for `main` via [`deepmerge`](https://github.com/TehShrike/deepmerge), as documented in their [README](https://github.com/probot/settings#inheritance).

#### [`stale.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/main/.github/stale.yml)

These settings are for the ["Stale" GitHub App](https://github.com/probot/stale). It closes abandoned issues and pull requests after a period of inactivity.

## The [`manage-github-apps/`](https://github.com/Financial-Times/github-apps-config-next/tree/main/manage-github-apps) folder

Each configuration file in this folder contains a list of one or more GitHub App _installations_. We've installed the [Settings](https://probot.github.io/apps/settings), [Stale](https://github.com/probot/stale), and [Renovate](https://github.com/apps/renovate) Apps in the Financial Times organisation in GitHub. Each of these has an _installation ID_.

_Why?_ Unfortunately, you can't add repositories to GitHub App installations without access to the GitHub administration area (which most developers don't have).

So we use [manage-github-apps](https://github.com/Financial-Times/manage-github-apps), which is a command-line tool for adding repositories to GitHub App installations.

> Further reading: [How can we keep our code up to date in all our repositories?](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories#how-can-we-keep-our-code-up-to-date-in-all-our-repositories)
