---
layout: post
title: "rmate"
description: "Remote TextMate 2 implemented as shell script"
category: utility
tags: [osx, utility, utils]
---

## Description

This shell script needs to be installed on a remote machine to allow editing files
using TextMate 2 (TM2). TM2 needs to be configured accordingly to accept either local
or remote clients.

### Local clients

It's a good idea to allow access to TM2 only for local clients. In this case it's required
to open a SSH connection to the remote system and specify a remote tunnel in addition:

    ssh -R 52698:localhost:52698 user@example.com

After log-in on the remote system a file can be edited by just executing

    rmate test.txt

### Remote clients

On some machines, where port forwarding is not possible, for example due to a missing ssh
daemon, it's required to set TM2 to allow access for "remote clients". After log-in on the
remote machine a file can be edited by executing

    rmate -H textmate-host test.txt

## Requirements

A bash with compiled support for "/dev/tcp" is required.

## Usage

Edit specified file

    $ ./rmate [arguments] [--] file-path

Read text from stdin

    $ echo "hello TextMate" | ./rmate [arguments] -

### Arguments

    -H, --host HOST  Connect to HOST. Use 'auto' to detect the host from SSH.
    -p, --port PORT  Port number to use for connection.
    -w, --[no-]wait  Wait for file to be closed by TextMate.
    -l, --line LINE  Place caret on line number after loading file.
    +N               Alias for --line, if N is a number (eg.: +5).
    -m, --name NAME  The display name shown in TextMate.
    -t, --type TYPE  Treat file as having specified type.
    -n, --new        Open in a new window (Sublime Text).
    -f, --force      Open even if file is not writable.
    -v, --verbose    Verbose logging messages.
    -h, --help       Display this usage information.
        --version    Show version and exit.


### Default parameter configuration

Some default parameters (_host_ and _port_) can be configured by defining them
as the environment variables `RMATE_HOST` and `RMATE_PORT` or by putting them
in a configuration file. The configuration files loaded are `/etc/rmate.rc`
and `~/.rmate.rc`, e.g.:

    host: auto  # prefer host from SSH_CONNECTION over localhost
    port: 52698

Alternative notation for configuration file is:

    host=auto
    port=52698

The precedence for setting the configuration is (higher precedence counts):

1. default (localhost, 52698)
2. /etc/rmate.rc
3. ~/.rmate/rmate.rc
4. ~/.rmate.rc
5. environment variables (RMATE\_HOST, RMATE\_PORT)

## Links

* [Source Code (GitHub)][https://github.com/aurora/rmate]
* [Author: Harald Lapp](https://github.com/aurora)


