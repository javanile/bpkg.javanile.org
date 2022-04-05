---
title: "gdub"
description: "A gradlew / gradle wrapper to make life easier."
category: default
tags: [gradle, command wrappers]
---
gdub (`gw` on the command line) is a `gradle` / `gradlew` wrapper. Not to be
confused with the [Gradle][] [Wrapper][], `gw` uses the Gradle Wrapper on
projects where one is configured, and falls back to use the `gradle` from the
`$PATH` if a wrapper is not available. Also, `gw` is 66% shorter to type than
`gradle` and 78% shorter to type than `./gradlew`. That's science.

[Gradle]:  http://www.gradle.org
[Wrapper]: http://www.gradle.org/docs/current/userguide/gradle_wrapper.html

Anywhere you happen to be on your project, you can run the Gradle tasks of your
project by typing `gw <tasks>`, regardless of whether you use the Gradle Wrapper
in your project or not.

`gw` works by looking upwards from your current directory and will run the
nearest `build.Gradle` file with the nearest `gradlew`. If a `gradlew` cannot be
found, it will run the nearest `build.Gradle` with your system's Gradle. This is
probably always what you want to do if you are running Gradle from within a
project tree that uses the Gradle build system.

## Links
* [Project Page](http://gdub.rocks)
* [Source Code (GitHub)](https://github.com/dougborg/gdub)
* [Author: Doug Borg](http://dougborg.org)

