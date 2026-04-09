---
title: node-reinstall
description: Reinstall Node.js, npm, and global packages with NVM or Nave.
categories: nodejs
keywords:
  - osx
  - nodejs
---

`node-reinstall` removes an existing Node.js setup and rebuilds it using NVM or Nave, including global npm packages.

## Usage

`node-reinstall` can typically be run as-is, though you can specify several arguments to customize to your liking.

```bash
$ node-reinstall -h
node-reinstall
        completely re-installs Node & NPM and any global node modules.
        It re-installs Node using NVM or Nave

Usage:  node-reinstall [--nave|--nvm|--nvm-latest] [-h|--help] [-v|--version] [NODE_VERSION]

Commands:

        node-reinstall                  re-install node and npm using nvm
        node-reinstall [-h|--help]      show help
        node-reinstall [-v|--version]   show the node-reinstall version number
        node-reinstall [-f|--force]     installs defaults without user confirmation
        node-reinstall --nave           re-install using nave
        node-reinstall --nvm            re-install using stable nvm - the default
        node-reinstall --nvm-latest     re-install using latest nvm - creationix/nvm:master
        node-reinstall 0.12             specify a default node version - currently

```

## Links

* [Source Code (Github)](https://github.com/brock/node-reinstall)
* Author: [Brock Angelo](https://github.com/brock)
