---
title: dbu
description: Command-line client for uploading and managing files on Dropbox.
categories: utilities
keywords:
  - sync
  - dropbox
---

![logo](http://www.andreafabrizi.it/images/dropbox_logo.png)

`dbu` (Dropbox Uploader) is a Bash client for uploading, downloading, listing, and deleting files in Dropbox.

It is written in Bash and only depends on **cURL**.

**Why use this script?**

* **Portable:** it only requires Bash and `curl`, both commonly available on Unix-like systems.
* **Secure:** it uses the official Dropbox API, so you do not need to store your Dropbox password in the script.

Please refer [to the Wiki](https://github.com/andreafabrizi/Dropbox-Uploader/wiki) for tips and additional information about this project. The Wiki is also the place where you can share your scripts and examples related to Dropbox Uploader.

```bash
$ bpkg install -g dbu
```

## Usage

The `dbu` package comes with two executables - `dropbox_uploader.sh` and `dropShell.sh`.

### Dropbox Uploader

This executable is command-oriented, similar to `git`:

```
dropbox_uploader.sh COMMAND [PARAMETERS]...

[%%]: Optional param
<%%>: Required param
```

#### Available commands

* **upload** <LOCAL_FILE/DIR ...> <REMOTE_FILE/DIR>
  Upload a local file or directory to a remote Dropbox folder.
  If the file is bigger than 150Mb the file is uploaded using small chunks (default 4Mb);
  in this case a . (dot) is printed for every chunk successfully uploaded and a * (star) if an error occurs (the upload is retried for a maximum of three times).
  Only if the file is smaller than 150Mb, the standard upload API is used, and if the -p option is used
  the default curl progress bar is displayed during the upload process.
  The local file/dir parameter supports wildcards expansion.
* **download** <REMOTE_FILE/DIR> [LOCAL_FILE/DIR]
  Download file or directory from Dropbox to a local folder
* **delete** <REMOTE_FILE/DIR>
  Remove a remote file or directory from Dropbox
* **move** <REMOTE_FILE/DIR> <REMOTE_FILE/DIR>
  Move or rename a remote file or directory
* **copy** <REMOTE_FILE/DIR> <REMOTE_FILE/DIR>
  Copy a remote file or directory
* **mkdir** <REMOTE_DIR>
  Create a remote directory on DropBox
* **list** [REMOTE_DIR]
  List the contents of the remote Dropbox folder
* **share** <REMOTE_FILE>
  Get a public share link for the specified file or directory
* **info**
  Print some info about your Dropbox account
* **unlink**
  Unlink the script from your Dropbox account

#### Optional parameters

* **-f <FILENAME>**
  Load the configuration file from a specific file
* **-s**
  Skip already existing files when download/upload. Default: Overwrite
* **-d**
  Enable DEBUG mode
* **-q**
  Quiet mode. Don't show progress meter or messages
* **-p**
  Show cURL progress meter
* **-k**
  Doesn't check for SSL certificates (insecure)

### Examples

```bash
dropbox_uploader.sh upload /etc/passwd /myfiles/passwd.old
dropbox_uploader.sh upload *.zip /
dropbox_uploader.sh download /backup.zip
dropbox_uploader.sh delete /backup.zip
dropbox_uploader.sh mkdir /myDir/
dropbox_uploader.sh upload "My File.txt" "My File 2.txt"
dropbox_uploader.sh share "My File.txt"
dropbox_uploader.sh list
```

## DropShell

DropShell is an interactive DropBox shell, based on DropBox Uploader:

```bash
# Launching the DropShell...
$ dropShell.sh
DropShell v0.2
The Interactive Dropbox SHELL
Andrea Fabrizi - andrea.fabrizi@gmail.com

Type help for the list of the available commands.

andrea@Dropbox:/$ ls
[D] 0       Apps
[D] 0       Camera Uploads
[D] 0       Public
[D] 0       scripts
[D] 0       Security
[F] 105843  notes.txt
andrea@DropBox:/ServerBackup$ get notes.txt
```

## Links

* [Homepage](https://www.andreafabrizi.it/2016/01/01/Dropbox-Uploader/)
* [Source Code (GitHub)](https://github.com/bpkg/dbu)
* Author: [Andrea Fabrizi](https://www.andreafabrizi.it/)
* Packager: [Joseph Werle](https://github.com/jwerle)
