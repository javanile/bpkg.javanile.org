---
layout : page
title  : bpkg Package Guidelines
header : Post Archive
group  : navigation
---

## Build packages that are easy to install and easy to trust

`bpkg` works best when packages are small, explicit, and unsurprising. These guidelines describe the minimum metadata expected by the registry and the conventions that make a Bash package pleasant to adopt.

## package.json

Every package must include a `package.json` file with package metadata in [JSON][json] format.

Example:

```json
{
  "name": "term",
  "version": "0.0.1",
  "description": "Terminal utility functions",
  "scripts": [ "term.sh" ],
  "install": "make install"
}
```

All fields are required unless noted otherwise.

### name

Required. `bpkg` uses `name` to determine where the package will live under `deps/`.

```json
  "name": "my-script"
```

### version (optional)

Optional, but recommended. It should match the version associated with the published package.

```json
  "version": "0.0.1"
```

### description

A short, human-readable summary of what the package does.

```json
  "description": "Terminal helpers for colors, cursor movement, and animations"
```

### global

Indicates that the package is intended to be installed as an executable command. When `global` is `true`, users do not need to pass `-g` or `--global` explicitly.

```json
  "global": "true"
```

### install

The shell command to run during installation. This is required if `global` is `true` or if the package is being installed with `-g` / `--global`.

```json
  "install": "make install"
```

### scripts

An array of scripts to install into a project dependency directory.

```json
  "scripts": ["script.sh"]
```

### files

An array of additional files that should be installed with the package.

```json
  "files": ["bar.txt", "foo.txt"]
```

### dependencies (optional)

Optional. A map of package dependencies where keys are package names and values are version specifiers. Use `"master"` to track the latest code, or a tagged release for a stable dependency. This follows the same version syntax accepted by `bpkg install`.

```json
  "dependencies": {
    "term": "0.0.1"
  }
```


## Packaging best practices

Beyond metadata, package quality matters. Good `bpkg` packages are composable, documented, and usable both interactively and in automation.

### Package exports

Whenever possible, design your package so it can be used both as a command and as a sourced shell function. A common pattern is:

```sh
if [[ ${BASH_SOURCE[0]} != $0 ]]; then
  export -f my_script
else
  my_script "${@}"
  exit $?
fi
```

This lets users either execute the script directly or `source` it and reuse the same functionality inside other scripts.

```sh
# Running as a script
$ ./my_script.sh some args --blah
# Sourcing the script
$ source my_script.sh
$ my_script some more args --blah
```

### Additional recommendations

* Keep installation side effects minimal and explicit.
* Prefer clear defaults over interactive setup when possible.
* Document required environment variables and external dependencies.
* Include at least one usage example in the repository README.
* Treat portability as a feature: the smaller the dependency surface, the more useful the package becomes.

[json]: http://json.org/example
