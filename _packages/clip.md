---
title: clip
description: Terminal clipboard for short-lived values and shell pipelines.
categories: utilities
keywords:
  - clipboard
---

`clip` is a tiny clipboard-like buffer for the terminal. It is useful when you want to pass values between commands or shell scripts without relying on a desktop clipboard.

## Install

```bash
$ bpkg install -g clip
```

## Usage

**Store**: *only stores single value:*

```bash
$ echo foo | clip
```

**Read**: *read stored value:*
```bash
$ clip
```

*Note:* it does not integrate with the system clipboard. It maintains its own value store.

## Links

* [Source Code (GitHub)](https://github.com/bpkg/clip)
* Author: [Joseph Werle](https://github.com/jwerle)
