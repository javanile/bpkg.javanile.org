---
layout: post
title: "shpec"
description: "Test your shell scripts"
category: bash
tags: [bash testing bdd]
---

This package provides a command for testing your shell scripts.

## Using shpec
[shpec's repo](https://github.com/rylnd/shpec) itself is using shpec, so feel free to use it as an example.
Here is the basic structure that you'll want:

    └── shpec
        └── an_example_shpec.sh
        └── another_shpec.sh

Then to run your tests:

{% highlight bash %}
shpec [shpec_files]
{% endhighlight %}

If you'd like your tests to run automatically when they change, we recommend the [entr](http://entrproject.org/) utility:

{% highlight bash %}
find . -name "*_shpec.sh" | entr shpec
{% endhighlight %}

### Examples
[shpec's own tests](https://github.com/rylnd/shpec/tree/master/shpec/shpec_shpec.sh)
are a great place to start. For more examples, see the [wiki page](https://github.com/rylnd/shpec/wiki/Examples)

### Matchers
The general format is:

    assert matcher arguments

where `matcher` is one of the following:

#### Binary Matchers
{% highlight bash %}
equal         # equality
unequal       # inequality
gt            # algebraic '>'
lt            # algebraic '<'
match         # regex match
no_match      # lack of regex match
{% endhighlight %}

#### Unary Matchers
{% highlight bash %}
present       # string presence
blank         # string absence
file_present  # file presence
file_absent   # file absence
symlink       # tests a symlink's target
test          # evaluates a test string
{% endhighlight %}

#### Custom Matchers
Custom matchers are loaded from `shpec/matchers/*.sh`.

For example, here's how you'd create a `still_alive` matcher:

{% highlight bash %}
# in shpec/matchers/network.sh
still_alive() {
  ping -oc1 "$1" > /dev/null 2>&1
  assert equal "$?" 0
}
{% endhighlight %}

Then you can use that matcher like any other:

{% highlight bash %}
# in shpec/network_shpec.sh
describe "my server"
  it "serves responses"
    assert still_alive "my-site.com"
  end
end
{% endhighlight %}

## Installation
You can either install with bpkg
{% highlight bash %}
$ bpkg install rylnd/shpec
{% endhighlight %}
or with curl
{% highlight bash %}
sh -c "`curl -L https://raw.github.com/rylnd/shpec/master/install.sh`"
{% endhighlight %}

or with [antigen](https://github.com/zsh-users/antigen) for zsh by
putting `antigen bundle rylnd/shpec` in your `.zshrc`

## Links
* [Source Code (GitHub)](https://github.com/rylnd/shpec);
* Author: [Ryland Herrick](https://github.com/rylnd);
