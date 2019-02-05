# github-apps-config-next

[![CircleCI](https://circleci.com/gh/Financial-Times/github-apps-config-next.svg?style=svg)](https://circleci.com/gh/Financial-Times/github-apps-config-next)

Customer Products configurations for our shared GitHub configuration files.

## The `.github/` folder

This folder contains shared configuration for GitHub Apps.

Read more about [how we're using this in our wiki](https://github.com/Financial-Times/next/wiki/GitHub#Probot).

This depends on the [`probot-config`](https://github.com/probot/probot-config) extension for loading configuration.

### Usage

Within a repository, extend our shared configuration like so.

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: probot-config-next
```

You can also overwrite configuration after extending it.

```yaml
# This is Financial-Times/next-article:.github/settings.yaml.
_extends: probot-config-next

repository:
  has_wiki: true
  has_projects: true
```

## The `manage-github-apps/` folder

This folder contains our configuration for the [`manage-github-apps` command line tool](https://github.com/Financial-Times/manage-github-apps).

Each configuration provides the tool with a list of GitHub App installations. It can then add the appropriate repositories to these installations.

See the [Financial-Times/manage-github-apps README](https://github.com/Financial-Times/manage-github-apps#readme) for more information.
