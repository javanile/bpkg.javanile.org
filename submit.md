---
layout: page
title: Submit your Package
header: Post Archive
group: navigation
permalink: /submit/
---

If you maintain a package that follows the [bpkg package guidelines][guide], you can submit it to the catalog and make it discoverable to the rest of the shell community.

The process is simple: add a Markdown entry for your package in [the site repository][site] and open a pull request.

## Submission flow

### 1. Fork the website repository

Click: [Fork bpkg on github](https://github.com/bpkg/bpkg.github.io/fork)

If you do not already have a GitHub account, create one first.

### 2. Clone your fork

Clone the repository locally:

```shell
$ git clone http://github.com/bpkg/bpkg.github.io
$ cd bpkg.github.io
```

Create a dedicated branch for your package entry:

```shell
$ git checkout -b your-package-name
```

### 3. Add your package entry

Create a new entry:

Replace `PACKAGE_NAME` by your package name.

```shell
$ rake post title="PACKAGE_NAME"
Creating new post: ./_posts/2014-06-02-package-name.md
```

Open the generated file and replace the placeholder content.

It will look like this:

    layout: post
    title: "PACKAGE_NAME"
    description: ""
    category:
    tags: []
    ---

At minimum, provide:

* **title**: the package name, in a Unix-friendly format such as `this-name`;
* **description**: a one-line summary of what the package does;
* **category**: one category from [the catalog](/packages/category);
* **tags**: a short list in `[this, format]` form to help discovery;
* **source code link**: add a link to the repository;
* **author**: add your name and at least one contact method.

Keep the remaining structure intact so the site can render the page correctly.

Below the front matter, you can add a short Markdown description with install notes, examples, and links.

Example:

    layout: post
    title: "fortune-fun"
    description: "Random message generator for the command line"
    category: game
    tags: [fun, random, cute]
    ---
    `fortune-fun` prints a random message-of-the-day in the terminal.

    ## Usage

    `fortune-fun`

    ## Links

    * [Source Code (GitHub)](https://github.com/your/repository)
    * [Author](http://your.homepage.com)

### 4. Open the pull request

Push your branch to GitHub and open a pull request against the site repository.

The GitHub web interface will guide you through the final step.

## Before you submit

Review the entry once before submitting. Clear metadata, a concise description, and a working repository link make approval much faster.

[guide]: /guidelines
[site]:  https://github.com/bpkg/bpkg.github.io
