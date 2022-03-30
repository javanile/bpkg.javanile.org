---
layout: post
title: "github"
description: "Github API from the command line"
category: default
tags: [library, github]
---

This package allows you to perform GitHub actions on your shell scripts.

{% highlight bash %}
$ bpkg install github
{% endhighlight %}

## Usage

This is how you'd use it via command-line. Note that to use some commands you need to authenticate first.

{% highlight bash %}
# Authentication
$ github auth jwerle
Enter host password for user 'jwerle':
  info: Storing access token

# Read token:
$ github token get
cf02301afdsfsbff6b06fdsfsbad2c225fdsfdsf

# Request feeds with authenticated user:
$ github request GET /feeds
{
  "timeline_url": "https://github.com/timeline",
  "user_url": "https://github.com/{user}",
  "current_user_public_url": "https://github.com/jwerle",
  "_links": {
    "timeline": {
      "href": "https://github.com/timeline",
      "type": "application/atom+xml"
    },
    "user": {
      "href": "https://github.com/{user}",
      "type": "application/atom+xml"
    },
    "current_user_public": {
      "href": "https://github.com/jwerle",
      "type": "application/atom+xml"
    }
  }
}
{% endhighlight %}

To see an example of a shell script and more info, go to the GitHub repository below.

## Links

* [Source Code (GitHub)](https://github.com/bpkg/github);
* [Author: Joseph Werle](https://github.com/jwerle);

