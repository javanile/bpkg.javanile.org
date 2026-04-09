# bpkg website

`bpkg` is a package manager for Bash scripts and shell tooling.
This repository contains the source for its website and package catalog.

## Links:

* [`bpkg` homepage][home];
* [`bpkg` source code on GitHub][hub];
* [`bpkg` organization on GitHub][org];

## Site stack

The site is built with [Jekyll][jekyll]. Install the required gem first:

    $ gem install jekyll

## How to edit

Clone the repository, install the dependency above, then edit pages and preview the site locally. Common commands:

---

    $ rake preview

Builds the site into `_site` and launches a local preview server.

Open `localhost:40000` in your browser.

Changes are rebuilt automatically while the preview server is running.

---

    $ rake post title="Hello, World!"

Creates a new post at `_posts/YYYY-MM-DD-title.md`.

The generated post is automatically included in the site.

---

    $ rake page name="about"

Creates a new page at `./about/index.html`.

    $ rake page name="about.html"

Alternative form that creates `./about.html`.

## Notes

* When writing content, use the [Jekyll post guide][posts] for images, excerpts, and code highlighting.
* For broader Jekyll customization, the [introduction guide][intro] is still a useful reference.
* If you change `_config.yml`, restart `rake preview` because Jekyll will not hot-reload config changes.

## Credits

This site uses [Jekyll Bootstrap][boots] with a heavily customized version of
[the_program][theme] theme, originally made by [Yuya Saito][saito].

[home]:    http://bpkg.sh/
[hub]:     https://github.com/bpkg/bpkg
[org]:     https://github.com/bpkg
[jekyll]:  http://jekyllrb.com/
[tuto]:    http://jekyllbootstrap.com/usage/jekyll-quick-start.html
[intro]:   http://jekyllbootstrap.com/lessons/jekyll-introduction.html
[boots]:   http://jekyllbootstrap.com/
[theme]:   https://github.com/jekyllbootstrap/theme-the-program
[saito]:   http://css.studiomohawk.com/
[posts]:   http://jekyllrb.com/docs/posts/
