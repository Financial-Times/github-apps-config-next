## The [`manage-github-apps/`](https://github.com/Financial-Times/github-apps-config-next/tree/master/manage-github-apps) folder

Each configuration file in this folder contains a list of one or more GitHub App *installations*. We've installed the [Settings](https://probot.github.io/apps/settings), [Stale](https://github.com/probot/stale),  [Renovate](https://github.com/apps/renovate) and [Tako](https://github.com/Financial-Times/tako/blob/master/README.md) Apps in the Financial Times organisation in GitHub. Each of these has an *installation ID*. 

*Why?* Unfortunately, you can't add repositories to GitHub App installations without assess to the GitHub administration area (which most developers don't have).

So we use [manage-github-apps](https://github.com/Financial-Times/manage-github-apps), which is a command-line tool for adding repositories to GitHub App installations. 

> Further reading: [How can we keep our code up to date in all our repositories?](https://github.com/Financial-Times/next/wiki/How-We-Manage-Our-GitHub-Repositories#how-can-we-keep-our-code-up-to-date-in-all-our-repositories)
