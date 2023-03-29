# Deploy to GitHub Pages and Deploy PR Preview

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![Release version badge](https://img.shields.io/github/v/release/chvmvd/github-pages-deploy-and-preview-action.svg?logo=github)](https://github.com/chvmvd/github-pages-deploy-and-preview-action/releases)
[![license](https://img.shields.io/badge/license-MIT-informational.svg)](LICENSE)
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

GitHub Action that deploys a static site to GitHub Pages and creates a PR preview.

## Table of Contents

- [Deploy to GitHub Pages and Deploy PR Preview](#deploy-to-github-pages-and-deploy-pr-preview)
  - [Table of Contents](#table-of-contents)
  - [About](#about)
  - [Usage](#usage)
  - [Configuration](#configuration)
    - [Inputs](#inputs)
    - [Outputs](#outputs)
  - [License](#license)
  - [Contributing](#contributing)

## About

This action deploys a static site to GitHub Pages and creates a PR preview.

## Usage

You can use this action in your workflow by writing like this:

```yaml
name: Deploy to GitHub Pages and Deploy PR Preview

on:
  push:
    branches: [main, master]
  pull_request:
    types:
      - opened
      - reopened
      - synchronize
      - closed

permissions:
  contents: write
  pull-requests: write

concurrency: ci-${{ github.ref }}

jobs:
  deploy-and-preview:
    name: Deploy to GitHub Pages and Deploy PR Preview
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Deploy to GitHub Pages and Deploy PR Preview
        uses: chvmvd/github-pages-deploy-and-preview-action@v1
        with:
          folder: test
```

## Configuration

### Inputs

| Name           | Description                        | Default       |
| -------------- | ---------------------------------- | ------------- |
| `folder`       | The folder to deploy.              | `.`           |
| `pr-preview`   | Whether to deploy a PR preview.    | `true`        |
| `branch`       | The branch to be deployed.         | `gh-pages`    |
| `umbrella-dir` | Directory containing all previews. | `pr-previews` |

### Outputs

None.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Issues and pull requests are always welcome.
