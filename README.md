# github-apps-config-next

Customer Products configurations for the [manage-github-apps](https://github.com/Financial-Times/manage-github-apps) CLI tool.

The configurations are in a separate repository because the manage-github-apps CLI tool can be used by teams outside of Customer Products.

## How it works

Each configuration provides the manage-github-apps CLI tool with a list of GitHub apps ('installations'). The manage-github-apps CLI tool adds the appropriate repositories to these installations.

## Custom configuration

You may create a custom GitHub app configuration. The configuration must have an owner and installation(s) in the following format:

```json
  "owner": "some-github-organization",
  "installations": [
    {
      "id": 123456,
      "comment": "Some bot"
    }
  ]
}
```
