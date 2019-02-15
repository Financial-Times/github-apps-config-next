# github-apps-config-next

[![CircleCI](https://circleci.com/gh/Financial-Times/github-apps-config-next.svg?style=svg)](https://circleci.com/gh/Financial-Times/github-apps-config-next)

## What's this?
This repository is where [FT Customer Products](https://biz-ops.in.ft.com/Group/customerproducts) keeps our shared configuration files for our GitHub Apps. 
> We use GitHub Apps to [help manage our hundreds of GitHub repositories](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories).

* Configuration for each GitHub App: [The `.github/` folder](https://github.com/Financial-Times/github-apps-config-next#the-github-folder)
* Configuration for managing GitHub Apps: [The `manage-github-apps/` folder](https://github.com/Financial-Times/github-apps-config-next#the-manage-github-apps-folder)

### The [`.github/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/.github) folder
This folder contains configuration files for different [GitHub Apps](https://developer.github.com/apps/).

#### [`settings.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/master/.github/settings.yml)
This configures the settings for your GitHub repository. For example, we disable the repository wiki setting, because we already have [a central wiki](https://github.com/Financial-Times/next/wiki). These settings are applied by the ["Settings" GitHub App](https://probot.github.io/apps/settings).

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
```

#### [`stale.yml`](https://github.com/Financial-Times/github-apps-config-next/blob/master/.github/stale.yml)  
These settings are for the ["Stale" GitHub App](https://github.com/probot/stale). It closes abandoned issues and pull requests after a period of inactivity. 🚀*Tip:* You can see all of our open GitHub issues and pull requests in [the Houston.ft.com repositories page](https://houston.ft.com/repositories).
 
### The [`manage-github-apps/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/manage-github-apps) folder

Each configuration file in this folder contains a list of one or more GitHub App *installations*. We've installed the [Settings](https://probot.github.io/apps/settings), [Stale](https://github.com/probot/stale),  [Renovate](https://github.com/apps/renovate) and [Tako](https://github.com/Financial-Times/tako/blob/master/README.md) Apps in the Financial Times organisation in GitHub. Each of these has an *installation ID*. 

*Why?* Unfortunately, we can't add repositories to GitHub App installations without assess to the GitHub administration area (which most developers don't have).

So we use [manage-github-apps](https://github.com/Financial-Times/manage-github-apps), which is a command-line tool for adding repositories to GitHub App installations. 

> Further reading: [How can we keep our code up to date in all our repositories?](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories#how-can-we-keep-our-code-up-to-date-in-all-our-repositories)
