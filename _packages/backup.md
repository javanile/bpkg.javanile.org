---
title: bash-backup
description: Backup automation for Bash projects and Linux servers.
categories: utilities
keywords:
  - backup
  - s3
---

`bash-backup` automates filesystem and MySQL backups, then ships the resulting archives to S3-compatible storage.

## Usage

```bash
$ git clone git@github.com:newsdict/bash-backup.git
$ cd bash-backup
$ cp env-example .env
```

Edit the `.env` file with your backup settings.

```bash
$ bash backup.sh [--debug]
```

### Multiple Targets

```bash
$ git clone git@github.com:newsdict/bash-backup.git
$ cd bash-backup
$ cp env-example .env-sample1
```

Edit `.env-sample1` with the first target configuration.

```bash
$ cp env-example .env-sample2
```

Edit `.env-sample2` with the second target configuration.

```bash
$ sh backup.sh [--debug] sample1
$ sh backup.sh [--debug] sample2
```

## Flow

1. Archive the selected files and directories.
2. Dump the MySQL database, if enabled.
3. Bundle the generated artifacts into a final backup archive.
4. Upload the result to S3 storage with retention management.

## Environments

### Temporary Directory

```bash
temporary_directory=tmp
```

### Log name

```bash
log_name=logs/backup.$now.log
```

### Backup filename

```bash
backup_filename=backup
```

### Display messages

```bash
display_messages=1
```

### Execute archive

```bash
archive=1
```

### Archive paths or files

```bash
declare -a archive_paths=(
    "/var/www/html"
    "/etc/nginx"
)
```

### Compression type of backup

```bash
commpression_type=gzip
```

* _gzip: *.tar.gz_
* _zip: *.zip_
* _bzip2: *.tar.bz2_

### Execute database

```bash
database=1
```

### Database Type for Dump

```bash
declare -A database_conf=(
    ["engine"]="mysql" # mysql only
    ["name"]="sample1_database" # database name
    ["username"]="user1" # username
    ["password"]="pass" # password
    ["host"]="127.0.0.1" # host
    ["port"]=3306 # port
)
```

### Storage type for backup files

```bash
storage_type=s3
```

* _`s3` only_

### S3 settings

```bash
declare -A s3_conf=(
    ["keep"]=5
    ["access_key"]=""
    ["secret"]=""
    ["bucket"]="backup"
    ["path"]="test"
    ["region"]="ap-northeast-1"
)
```

## Links

* [Source Code (GitHub)](https://github.com/newsdict/bash-backup)
* Author: [yubele](https://github.com/yubele)
