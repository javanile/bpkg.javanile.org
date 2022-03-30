---
layout: post
title: "wifi"
description: "Bash script that connects to wifi"
category: default
tags: [internet, wifi]
---


This package provides convenient commands to manage your wifi networks.

{% highlight bash %}
$ bpkg install -g wifi
{% endhighlight %}

## Usage

Some commands require root privileges to access wifi info.

{% highlight bash %}
# List currently available wifi networks.
sudo wifi.sh scan

# Connect to best network
sudo wifi.sh connect

# Add a network to file.
sudo wifi.sh add <SSID> <passphrase>

# Show current interface
wifi.sh interface

# this defaults to the LAST interface
# it finds, for me, this is the most recent USB wifi
# dongle I plugged in.

# Set interface manually like this:
sudo INTERFACE=wlan0 wifi.sh connect

# Set wpa_supplicant.conf location
sudo WPA_CONF=/etc/wpa_supplicant.conf wifi.sh connect
{% endhighlight %}

## Links

* [Source Code (GitHub)](https://github.com/bpkg/wifi);
* Author: [Dominic Tarr](https://github.com/dominictarr);
* Packager: [Joseph Werle](https://github.com/jwerle);
