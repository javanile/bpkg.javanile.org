---
title: gdub
description: Smart Gradle wrapper that prefers `./gradlew` and falls back to `gradle`.
categories: utilities
keywords:
  - gradle
  - command wrappers
---

`gdub` exposes `gw`, a small wrapper around `gradle` and `./gradlew`.

It prefers the Gradle Wrapper when a project provides one and falls back to the `gradle` binary from your `PATH` when it does not.

[Gradle]:  http://www.gradle.org
[Wrapper]: http://www.gradle.org/docs/current/userguide/gradle_wrapper.html

You can run Gradle tasks from anywhere inside a project tree with `gw <tasks>`, without worrying about where the wrapper lives.

`gw` works by looking upwards from your current directory and will run the
nearest `build.Gradle` file with the nearest `gradlew`. If a `gradlew` cannot be
found, it will run the nearest `build.Gradle` with the system Gradle installation.

## Links

* [Project Page](http://gdub.rocks)
* [Source Code (GitHub)](https://github.com/dougborg/gdub)
* Author: [Doug Borg](http://dougborg.org)
