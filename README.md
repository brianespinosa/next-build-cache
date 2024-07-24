# next-build-cache

![Last Updated](https://img.shields.io/github/last-commit/brianespinosa/next-build-cache?label=Last%20Updated&cacheSeconds=120)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

Set up NextJS build cache for faster GitHub Actions build times

```
brianespinosa/next-build-cache@main
```

## Usage

```yaml ci.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:

concurrency:
  group: ${{ github.workflow }}-${{ github.event.pull_request.number || github.ref }}
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: brianespinosa/checkout-setup-node-install@main
      - uses: brianespinosa/next-build-cache@main
      - run: yarn build
```

## Assumptions

- We are handling install caching with other tools like `node-setup` or `brianespinosa/checkout-setup-node-install`
- We are using `yarn` as our package manager so we can leverage a `yarn.lock` file to generate part of our build cache hash
- This action runs immediately **before** a NextJS build command to look for a build cache (post-job actions will automatically save the build cache upon build completion)