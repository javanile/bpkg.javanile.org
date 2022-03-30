---
layout: post
title: "markdown"
description: "Markdown interpreter using only traditional Unix tools"
category: default
tags: [markdown, parser]
---

markdown.bash is a Markdown interpreter using only traditional Unix tools. Specifically, it only uses `bash`, `sed`, `grep`, and `cut` (in one small instance).

{% highlight bash %}
$ bpkg install markdown.bash
{% endhighlight %}

## Usage

Use it just like any other Unix program - by either passing files to it or piping input into it.

{% highlight bash %}
# Converts `test.md` to HTML and sends to
# standard output
markdown.sh samples/test.md

# Concatenates all the files and converts
# them all from Markdown to HTML into `output.html`
markdown.sh file1 file2 file3 > output.html

# Also accepts Markdown piped into it
echo "# heading1\n\nparagraph" | markdown.sh
{% endhighlight %}

## Links

* [Source Code (GitHub)](https://github.com/bpkg/markdown.bash);
* [Author: Chad Braun-Duin](https://github.com/chadbraunduin);
* [Packager: Joseph Werle](https://github.com/jwerle);

