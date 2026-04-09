---
title: bash-db
description: Lightweight key-value store for Bash scripts.
categories: bash
keywords:
  - utils
  - utility
  - db
---

`bash-db` is a minimal key-value database for Bash scripts. It relies only on common Unix tools and is designed for lightweight local storage.

Dependencies:
* sed
* bash
* grep
* base64
* xargs

## Install

## bpkg (global package)
```bash
bpkg install reddec/bash-db
```

## Make (`/usr/local/bin`)
```bash
make install
``` 

## Manual Installation 
```bash
git clone https://github.com/reddec/bash-db
cd bash-db
chmod +x db.sh
cp db.sh /usr/local/bin/db
```

## Usage

## Command-line Tool
`db <method> <database> [arguments...]`

Methods:

### PUT

Insert or update record.

| Arg               | Description  |
|-------------------| -------------|
| `key` (required)  | Unique key. Can be used any value (also spaces if value in bracets)
| `value` (optional)| Value of record.  Can be used any value (also spaces if value in bracets). If value not set, STDIN will be used.

#### Example:

```bash
db put test.db name 'Red Dec'
```

### GET

Get value of record by key

| Arg               | Description  |
|-------------------| -------------|
| `key` (required)  | Unique key. Can be used any value (also spaces if value in bracets)

#### Example:

```bash
db get test.db name
```

### LIST

Get all keys in database

**No arguments**

#### Example:

```bash
db list test.db
```

### LAST

Get the value of the last added record

**No arguments**

#### Example:

```bash
db last test.db
```

### DELETE

Delete record by key

| Arg               | Description  |
|-------------------| -------------|
| `key` (required)  | Unique key. Can be used any value (also spaces if value in bracets)

#### Example:

```bash
db delete test.db name
```

## Links
- [Source Code (GitHub)](https://github.com/reddec/bash-db)
- [Author: Aleksandr Baryshnikov](https://github.com/reddec)
