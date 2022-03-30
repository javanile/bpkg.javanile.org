---
layout: post
title: "rtail"
description: "Easily tail a file over SSH"
category: default
tags: [internet, ssh]
---


Sometimes you just want to quickly access the final contents of a file on a remote SSH host.
Well, now you can do it.

{% highlight bash %}
$ bpkg install -g rtail
{% endhighlight %}

## Usage

{% highlight bash %}
# The following will open `/var/log/host.log` on
# on `somehost.com` as if it was on our machine
$ rtail user@somehost.com -f /var/log/host.log

# All options
$ rtail --help
rtail [-hvV] [ssh_options] [user@] [tail_options] [files...]
-v, --verbose   enable verbose output
-h, --help      display this message
-V, --version   output version

[ssh_options]   ssh options
[tail_options]  tail options
{% endhighlight %}

## Links

* [Source Code (GitHub)](https://github.com/bpkg/rtail);
* Author: [Joseph Werle](https://github.com/jwerle);
* ["Sister project" *recho*](http://bpkg.sh/pkg/recho)

