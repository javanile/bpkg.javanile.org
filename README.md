# bpkg website

[![CI](https://github.com/javanile/bpkg.javanile.org/actions/workflows/ci.yml/badge.svg)](https://github.com/javanile/bpkg.javanile.org/actions/workflows/ci.yml)
[![Catalog](https://github.com/javanile/bpkg.javanile.org/actions/workflows/catalog.yml/badge.svg)](https://github.com/javanile/bpkg.javanile.org/actions/workflows/catalog.yml)
[![Links](https://github.com/javanile/bpkg.javanile.org/actions/workflows/links.yml/badge.svg)](https://github.com/javanile/bpkg.javanile.org/actions/workflows/links.yml)
[![Local Dev: Docker](https://img.shields.io/badge/local%20dev-docker-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/get-docker/)
[![Jekyll](https://img.shields.io/badge/site-jekyll-CC0000?logo=jekyll&logoColor=white)](https://jekyllrb.com/)

`bpkg` is a package manager for Bash scripts and shell tooling.
This repository contains the source for the website, the package catalog, and the editorial pages around the `bpkg` ecosystem.

## Links

* [`bpkg` website](http://bpkg.sh/)
* [`bpkg` source code](https://github.com/bpkg/bpkg)
* [`bpkg` organization](https://github.com/bpkg)

## What is in this repository

This site is a Jekyll-based catalog for shell packages.

It contains:

* editorial pages such as getting started, submission rules, and packaging guidelines;
* package entries under `_packages/`;
* category pages under `_categories/`;
* Jekyll configuration and theming for local preview and production publishing.

## Local development

Local development is Docker-based.
You do not need a Ruby toolchain installed on your machine: the `Makefile` generates a temporary `Gemfile`, prepares a local development config, and runs Jekyll inside the official `jekyll/builder:3.8` container.

### Requirements

* Docker installed
* Docker daemon running

### Start the site locally

```bash
make serve
```

The site will be available at `http://localhost:4000`.

During startup, `make serve`:

* verifies that Docker is installed and available;
* writes a local `Gemfile` with the gems required by this site;
* writes `_config_dev.yml` with development-specific overrides;
* mounts the repository into the Jekyll builder container;
* caches Bundler dependencies in `.bundles_cache/`;
* runs `jekyll serve` with `_config.yml,_config_dev.yml`.

## Makefile reference

The current `Makefile` is intentionally small and focused on day-to-day maintenance.

### `make check-env`

Checks that Docker is installed and that the Docker daemon is running.
Use this if `make serve` fails before the container starts.

### `make serve`

Boots the full local development environment in Docker and starts the Jekyll preview server on port `4000`.
This is the main entry point for working on the site locally.

## Content model

Most of the repository value lives in Markdown.

* `_packages/*.md`: package entries exposed in the catalog
* `_categories/*.md`: category landing pages
* `get-started.md`, `guidelines.md`, `submit.md`: core editorial pages

Each package entry should keep its front matter complete and accurate, especially:

* `title`
* `description`
* `categories`
* repository and author links where applicable

## GitHub Actions

This repository includes a small but useful workflow set:

* `CI`: builds the site with Jekyll in Docker so content or config regressions are caught early.
* `Catalog`: validates package and category Markdown structure so the registry stays coherent.
* `Links`: runs a scheduled and on-demand link check across Markdown and HTML files.

These workflows are designed to protect the catalog without making contribution flow unnecessarily heavy.

## Notes

* Production settings live in [`_config.yml`](./_config.yml).
* Local development overrides are generated into `_config_dev.yml` by `make serve`.
* Bundler cache is stored in `.bundles_cache/` to speed up repeated local runs.

## Credits

This site is powered by Jekyll and a remote theme based on `javanile/package-manager`.
