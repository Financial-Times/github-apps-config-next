## The [`.github/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/.github) folder

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
 
