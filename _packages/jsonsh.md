---
layout: post
title: "json.sh"
description: "A pipeable JSON parser written in Bash"
category: default
tags: [json, parser]
---


yo, so it's a json parser written in bash

Pipe json to it, and it traverses the json objects and prints out the path to the current object (as a JSON array) and then the object, without whitespace.

{% highlight bash %}
$ bpkg install -g json.sh
{% endhighlight %}

## Usage

{% highlight bash %}
$ json_parse < package.json
["name"]  "JSON.sh"
["version"]  "0.0.0"
["description"]  ""
["homepage"]  "http://github.com/dominictarr/JSON.sh"
["repository","type"]  "git"
["repository","url"]  "https://github.com/dominictarr/JSON.sh.git"
["repository"]  {"type":"git","url":"https://github.com/dominictarr/JSON.sh.git"}
["bin","json_parse"]  "./JSON.sh"
["bin"]  {"json_parse":"./JSON.sh"}
["dependencies"]  {}
#  ... etc

# Here's a more complex example:
#... try it and see
curl registry.npmjs.org/express | ./JSON.sh | egrep '\["versions","[^"]*"\]'
{% endhighlight %}

### Options

* -b
  Brief output. Combines 'Leaf only' and 'Prune empty' options.
* -l
  Leaf only. Only show leaf nodes, which stops data duplication.
* -p
  Prune empty. Exclude fields with empty values.
* -h
  Show help text.

## Links

* [Source Code (GitHub)](https://github.com/bpkg/JSON.sh);
* Author: [Dominic Tarr](https://github.com/dominictarr);
* Packager: [Joseph Werle](https://github.com/jwerle);


