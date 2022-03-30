---
layout: post
title: "umq"
description: "TCP message pushing and receiving in Bash"
category: default
tags: [internet, tcp, client, server]
---


This package makes easy to handle TCP requests on the command-line.

You can both send and receive messages with the portability only Bash can offer.

{% highlight bash %}
$ bpkg install umq -g
{% endhighlight %}

## Usage

`umq` is quite a toolbox - there are several ways you can use it.

Let's take a **server**, for example.
The following will create a server and listen on `localhost` port `3000` for all incoming TCP messages.

{% highlight bash %}
$ umq recv 3000 | { \
  while read -r line; do \
    echo "got: '$line'"; \
  done; \
}
{% endhighlight %}

You can **connect** and read from the server by using `umq` itself:

{% highlight bash %}
$ umq recv localhost 3000
{% endhighlight %}

**Pushing** data is just as easy:

{% highlight bash %}
$ echo "ping" | umq push localhost 3000

# It should yield the following response
# on the umq server:
got: 'ping'
{% endhighlight %}

### umq's API

{% highlight bash %}
usage: umq <command> [-hV]

examples:
$ echo "hello world" | umq push localhost 3000
$ umq recv localhost 3000 | while read line; do \
  echo "msg: $line"; done

commands:
  push <host> <port>      push message to host with port
  recv <host> <port>      receive message on host with port
  help <command>          see more information on a command

options:
  -h, --help              display this message
  -V, --version           output version
{% endhighlight %}

### Real-life Examples

### CPU Histogram

Using `umq` with the [histo](https://github.com/visionmedia/histo) viewer allows for data to be streamed via TCP to a histogram chart.
See [cpu-stream](https://gist.github.com/jwerle/8076956) for a preview.

### `wall` server

Streaming messages to all users via the `wall` program. See [wall-server](https://github.com/jwerle/umq/blob/master/examples/wall-server.sh).

## Links

* [Source Code (GitHub)](https://github.com/bpkg/umq);
* Author: [Joseph Werle](https://github.com/jwerle);

