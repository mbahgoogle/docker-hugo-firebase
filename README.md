# docker-hugo-firebase [![Docker Repository](https://img.shields.io/badge/Docker%20Repository-Docker%20Hub-blue.svg)](https://hub.docker.com/r/jnyo/docker-hugo-firebase/)

## Using on CircleCI 2.0

Using following configuration in `.circleci/config.yml `

```
version: 2
jobs:
  build:
    docker:
      - image: jnyo/docker-hugo-firebase:latest
    working_directory: ~/project
    steps:
      - checkout
      - run:
          name: "Run Hugo"
          command: hugo -t slim
      - deploy:
          branch: master
          command: firebase deploy --token "$FIREBASE_TOKEN"
```
The environment variable `FIREBASE_TOKEN` stores the Firebase authentication token and is saved in `Build Setting > Environment Variables` on CircleCI console.