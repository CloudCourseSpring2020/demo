---
version: 2
jobs:
  pr_check:
    docker:
      - image: circleci/node:8.10.0
    steps:
      - checkout # check out source code to working directory
      - run:
          name: Gradle build
          command: |
            npm install
  build:
    docker:
      - image: circleci/node:8.10.0
    steps:
      - checkout # check out source code to working directory
      - run:
          name: Gradle build
          command: |
            echo "hello World!"
workflows:
  version: 2
  pr-check-workflow:
    jobs:
      - pr_check
  build:
    jobs:
      - build
