# Creating documentation with uv and MkDocs

For preparing documentation, we will use [MkDocs](https://www.mkdocs.org/) with the [Material theme](https://squidfunk.github.io/mkdocs-material/). The Material theme is first class for MkDocs, and in fact many plugins are set up for Material and not the default MkDocs theme.

## Get MkDocs locally

```bash
uv init
uv add mkdocs-material
```

or

```bash
uv pip install mkdocs-material
```

## Initialize a new MkDocs project

```bash
uv run mkdocs new .
uv run mkdocs serve
```

Follow the [setup instructions](https://squidfunk.github.io/mkdocs-material/creating-your-site/) from mkdocs-material.

## Create Documentation Locally

Add documentation to `docs/`. Save, and watch a live update in your browser.

Make commits and push to your repo, preferably with a PR. (See [Recommended Github Repo Settings](gh_repo_settings.md) for more details on how to set up your repo.)

To build the documentation locally, use

```bash
uv run mkdocs build
```

And it will create a `site/` directory with the built documentation.

While you *can* manage a static site by locally building and uploading the `site/` directory, it is much easier to use a service like [GitHub Pages](https://pages.github.com/) or [Read the Docs](https://readthedocs.org/) to host your documentation. For this reason, I add `site/` to `.gitignore` so that it is not committed to the repo.

## Deploy Documentation

We are easily able to deploy documentation to Github Pages where it will be found at `https://<username or org-name>.github.io/<repo-name>/`. This is a great way to host documentation as a static site, and it is free! On your main repo page, go to the Description settings and check `Use your Github Pages website`. Your documentation, by default, will be served from the `gh-pages` branch.

MkDocs provides a way to locally, manually deploy to `gh-pages` with `mkdocs gh-deploy`, but again, this requires local management *and* goes against the ethos of using PRs to manage changes to the codebase.

Instead, we will use a GitHub Action to automatically build the documentation in PRs and commits to main, and deploy the docs to GitHub Pages when a PR is merged to main. MkDocs-Materials provides an action to do this, which is documented in the [MkDocs-Material documentation](https://squidfunk.github.io/mkdocs-material/publishing-your-site/), but we will use a custom action.

First, create a `.github/workflows/` directory in your repo. Then, create a file called `deploy_docs.yml` in that directory with the following content:

```yaml
name: Deploy Docs

on:
  push:
    branches: [main]
  pull_request:

permissions:
  contents: write

concurrency:
  name: Cancel in-progress jobs for same trigger
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

jobs:
  docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v6

      - name: Test that docs build without error
        if: github.event_name == 'pull_request'
        run: uv run mkdocs build --strict

      - name: Deploy docs to GitHub Pages
        if: github.event_name == 'push'
        run: uv run mkdocs gh-deploy --strict --force

```

Now, when you create a PR the docs will be tested to ensure they build without error. When you merge a PR to main, the docs will be built and deployed to GitHub Pages.

While writing this, I got the error in my [action on the PR](https://github.com/TimMonko/urssi-docs/actions/runs/16708940401/job/47291006777?pr=1). Helpful!

```bash
WARNING -  Doc file 'docs-setup.md' contains a link 'docs/gh_repo_settings.md', but the target is not found among documentation files.
```
