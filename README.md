# WIP: Sailfish OS Build Action

## About

A [GitHub Action](https://github.com/features/actions) for building [Sailfish OS](https://sailfishos.org/) packages.

## Usage

Quick start:

```yaml
name: ci

on:
  push:
    branches:
      - 'master'

jobs:
  sailfishos:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        arch: ['aarch64', 'armv7hl', 'i486']
    steps:
      -
        name: Checkout
        uses: actions/checkout@v2
      -
        name: Build
        uses: dseight/sailfishos-build-action@v1
        with:
          version: 4.1.0.24
          arch: ${{ matrix.arch }}
```

## Customizing

### inputs

Following inputs can be used as `step.with` keys

| Name         | Type     | Description                      |
|--------------|----------|----------------------------------|
| `version`    | String   | Sailfish OS version to build for |
| `arch`       | String   | Target architecture |
| `spec`       | String   | Path to the spec file (optional) |
| `validate`   | Bool     | Run [Harbour](https://harbour.jolla.com/faq) validator (default `false`) |
