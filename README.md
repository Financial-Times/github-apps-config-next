# github-apps-config-next

[![CircleCI](https://circleci.com/gh/Financial-Times/github-apps-config-next.svg?style=svg)](https://circleci.com/gh/Financial-Times/github-apps-config-next)

## What's this?
This repository is where [FT Customer Products](https://biz-ops.in.ft.com/Group/customerproducts) keeps our shared configuration files for our GitHub Apps. *Why?* We use GitHub Apps to [help manage our hundreds of GitHub repositories](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories).

* Configuration for each GitHub App: [The `.github/` folder](https://github.com/Financial-Times/github-apps-config-next#the-github-folder)
* Configuration for managing GitHub Apps: [The `manage-github-apps/` folder](https://github.com/Financial-Times/github-apps-config-next#the-manage-github-apps-folder)

### The [`.github/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/.github) folder
This folder contains configuration files for different [GitHub Apps](https://developer.github.com/apps/).

* [`settings.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/master/.github/settings.yml) — The settings for your GitHub repository. For example, we disable repository wikis because we already have [a central wiki](https://github.com/Financial-Times/next/wiki). These settings are applied by the ["Settings" GitHub App](https://probot.github.io/apps/settings).

* [`stale.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/master/.github/stale.yml) — These settings are for the ["Stale" GitHub App](https://github.com/probot/stale). It closes abandoned Issues and Pull Requests after a period of inactivity. 🚀*Tip:* You can see all of our GitHub Issues and Pull Requests in [the Houston.ft.com repositories page](https://houston.ft.com/repositories).
 
> Developer Note: We use the [`probot-config`](https://github.com/probot/probot-config) extension to load these configurations. 
> Within a repository, extend our shared configuration like so:

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: github-apps-config-next
```

> You can also overwrite configuration after extending it.

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: github-apps-config-next

repository:
  has_wiki: true
  has_projects: true
```

### The [`manage-github-apps/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/manage-github-apps) folder

This folder contains our configuration for the [`manage-github-apps` command line tool](https://github.com/Financial-Times/manage-github-apps).

Each configuration provides the tool with a list of GitHub App installations. It will then add the GitHub repository that you specify to these installations.

See the [Financial-Times/manage-github-apps README](https://github.com/Financial-Times/manage-github-apps#readme) for more information.
