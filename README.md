# discord-dispatch

[![Docker](https://img.shields.io/docker/cloud/build/clarencetw/discord-dispatch?label=Docker&style=flat)](https://hub.docker.com/r/clarencetw/discord-dispatch/builds)

A discord dispatch tool for docker

## How to push in GitLab CI

1. build file to dist folder

2. set APPLICATION_ID, BOT_TOKEN and BRANCH_ID token

3. copy this to .gitlab-ci.yml

```
publish:
  stage: release
  image: clarencetw/discord-dispatch:latest
  before_script:
    - mkdir /root/.dispatch
    - echo "{\"BotCredentials\":{\"application_id\":\"$APPLICATION_ID\",\"token\":\"$BOT_TOKEN\"}}" > /root/.dispatch/credentials.json
  script:
    - dispatch build push $BRANCH_ID ./config.json dist -p
```
