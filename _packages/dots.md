---
layout: post
title: "dots"
description: "Bootstrapping library for OS/X & Ubuntu (and maybe others!)"
category: default
tags: [configuration]
---


![image](https://i.cloudup.com/RCpB-ASfme.png)

The goal of `dots` is to automate the process of getting your operating system from a stock build to a fully functional machine.

`dots` should be the first thing you download and run to get your computer set up. Dots differs from dotfiles, beacause dots installs and configures applications as well as builds your profile.

{% highlight bash %}
$ bpkg install dots
{% endhighlight %}

### Supported Operating systems:

#### Mac OS X

The OSX build does the following:

- install homebrew
- installs binaries (graphicsmagick, python, sshfs, ack, git, etc.)
- sets OSX defaults
- installs applications via `homebrew-cask` (one-password, sublime-text, virtualbox, nv-alt, iterm2, etc.)
- sets up the ~/.bash_profile

#### Ubuntu (server)

The Ubuntu build does the following:

- dash => bash
- creates a user
- installs git and curl
- sets up the ssh keys
- configures fail2ban
- sets up the firewall
- installs docker

## Usage

{% highlight bash %}
Usage: dots [options] [command] [args ...]

Options:

-v, --version Get the version
-h, --help This message

Commands:

reload        Reload the dotfiles
boot <os>     Bootstrap the given operating system
update        Update dots
{% endhighlight %}

## Links

* [Source Code (GitHub)](https://github.com/bpkg/dots);
* Author: [Matthew Mueller](https://github.com/MatthewMueller);
* Packager: [Joseph Werle](https://github.com/jwerle);
* Logo by [Piotrek Chuchla](http://www.thenounproject.com/pchuchla/)


