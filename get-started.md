---
title:    Get Started
permalink: /get-started/
---

## A package manager for Bash scripts

JavaScript has `npm`, Ruby has `gem`, Python has `pip`. `bpkg` brings the same workflow to Bash: discoverable packages, repeatable installs, and a shared distribution model for shell tooling.

Use **bpkg** to install command-line tools, reusable shell libraries, and small automation utilities without inventing a custom setup step for every repository.

It handles installation, removal, and executable permissions so a package can be consumed like any other CLI tool:

```shell
# Install `term` into `/usr/local/bin`
$ bpkg install term -g
$ term
```

`bpkg` also works well at project scope, where dependencies live alongside the code that uses them:

```shell
# Install `term` inside the local `deps/` directory
$ bpkg install term
$ ./deps/term/term.sh
```

## Install

There are three common ways to install **bpkg**.

### 1. Install Script

The bootstrap script installs `bpkg` with minimal setup:

```shell
$ curl -sLo- http://get.bpkg.sh | bash
```

If you want to inspect it first, open [get.bpkg.sh](http://get.bpkg.sh) or review [`setup.sh`](https://raw.githubusercontent.com/bpkg/bpkg/master/setup.sh) in the repository.

### 2. clibs

If you already use [clibs][clib], you can install **bpkg** from there as well:

```shell
$ clib install bpkg/bpkg
```

### 3. Source Code

If you prefer to install from source:

```shell
$ git clone https://github.com/bpkg/bpkg.git
$ cd bpkg
$ ./setup.sh install
```

## Why bpkg exists

Shell ecosystems often end up as disconnected gists, dotfiles, and one-off repositories. `bpkg` aims to make Bash tooling more reusable by giving packages a standard shape and a standard installation flow.

That makes it easier to:

* publish small utilities without building a full language runtime around them;
* consume shell scripts as dependencies inside projects;
* discover tools by category instead of by chance.

[gem]: https://rubygems.org/
[npm]: https://www.npmjs.org/
[pip]: https://pypi.python.org/pypi/pip
[clib]: https://github.com/clibs/clib
