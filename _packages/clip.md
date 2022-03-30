---
layout: post
title: "clip"
description: "Silly terminal clipboard"
category: default
tags: [clipboard]
---


Really simple clipboard manager in Bash.
You can access it via command-line or inside shell scripts.

{% highlight bash %}
$ bpkg install -g clip
{% endhighlight %}

## Usage

**Store**: *only stores single value:*
{% highlight bash %}
$ echo foo | clip
{% endhighlight %}

**Read**: *read stored value:*
{% highlight bash %}
$ clip
{% endhighlight %}

*NOTE:* It does not interface with the _actual_ system clipboard. It has it's own.

## Links

* [Source Code (GitHub)](https://github.com/bpkg/clip);
* Author: [Joseph Werle](https://github.com/jwerle);


