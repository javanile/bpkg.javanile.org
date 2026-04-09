---
title: wifi
description: Command-line helper for scanning and connecting to Wi-Fi networks.
categories: networking
keywords:
  - internet
  - wifi
---

`wifi` provides a small command-line interface for discovering networks, choosing an interface, and connecting from Bash.

## Install

```bash
$ bpkg install -g wifi
```

## Usage

Some commands require elevated privileges to access network interfaces and update configuration files.

```bash
# List currently available wifi networks.
sudo wifi.sh scan

# Connect to best network
sudo wifi.sh connect

# Add a network to file.
sudo wifi.sh add <SSID> <passphrase>

# Show current interface
wifi.sh interface

# By default the script uses the last detected interface.
# You can override that choice explicitly:

# Set interface manually like this:
sudo INTERFACE=wlan0 wifi.sh connect

# Set wpa_supplicant.conf location
sudo WPA_CONF=/etc/wpa_supplicant.conf wifi.sh connect
```

## Links

* [Source Code (GitHub)](https://github.com/bpkg/wifi)
* Author: [Dominic Tarr](https://github.com/dominictarr)
* Packager: [Joseph Werle](https://github.com/jwerle)
