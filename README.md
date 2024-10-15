# Template publishing Julia-kerneled Jupyter notebooks with dynamic matrix and Quarto

Click `Use this template` button to copy this repository.

See also:

- [template-juliabook](https://github.com/ww-jl/template-juliabook): runs notebooks concurrently *in one runner* and use [jupyter-book][] to build the website.
- [template-juliabook-matrix](https://github.com/sosiristseng/template-juliabook-matrix): mostly the same as this repository, but it uses [jupyter-book][] to render the website.

[quarto]: https://quarto.org/
[jupyter-book]: https://jupyterbook.org/

## Notebook execution and publish

- Workflow file: [ci.yml](.github/workflows/ci.yml)

The notebooks under the `docs` folder are executed in parallel, and then [Quarto][quarto] creates a beautiful website from Markdown and Jupyter notebook files.

## Enable GitHub pages

Open your repository settings => Pages => GitHub Pages => Build and deployment => Source, select `GitHub actions`.

## Automatic dependency updates

### Dependabot and Kodiak Bot

See [dependabot.yml](.github/dependabot.yml) and [.kodiak.toml](.github/.kodiak.toml) configuration files.

You need to enable the [Kodiak Bot](https://kodiakhq.com/docs/quickstart) APP to automatically merge updates.

### Julia dependencies

The GitHub workflow [update-manifest.yml](.github/workflows/update-manifest.yml) regularly updates Julia dependencies, make a PR with the updated dependencies, and automatically merge the updates if the notebooks are executed smoothly.

See [creating tokens](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#triggering-further-workflow-runs) to trigger CI workflows in a PR. This repo uses a custom [GitHub APP](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#authenticating-with-github-app-generated-tokens) to generate a token on the fly.

## Checking HTTP links

[linkcheck.yml](.github/workflows/linkcheck.yml) uses GitHub actions to regularly check if the web links in the notebooks are valid.
