# Heroku Docker - Anypoint Flex Gateway

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

Deploy the official [MuleSoft Anypoint Flex Gateway Docker image](https://hub.docker.com/r/mulesoft/flex-gateway) to Heroku

![Heroku with Flex Gateway Architecture](public/heroku-flex-gateway.png)

## Requirements

- A [Heroku](https://signup.heroku.com/) account
- A [MuleSoft Anypoint Platform](https://www.mulesoft.com/platform/enterprise-integration) account
- [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
- [Docker](https://docs.docker.com/get-docker/)

## Manual Deployment

Make sure you have installed the `@heroku-cli/plugin-manifest` plugin by running:

``` sh
heroku plugins:install @heroku-cli/plugin-manifest
```

Create an application on a Private Space with the Heroku CLI using the `--manifest` and `--space` flags:

``` sh
heroku create <gw-app-name> --manifest --space <private space>
```

Set the `registration.yaml` configuration contents in the `FLEX_CONFIG` environment variable:

``` sh
heroku config:set FLEX_CONFIG="$(cat registration.yaml)" -a <gw-app-name>
```

Deploy the Flex Gateway by running:

``` sh
git push heroku main
```
