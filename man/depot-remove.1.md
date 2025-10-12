---
title: depot-remove
section: 1
header: User Commands
footer: depot-config(1)
date: 2025-08-11
author:
    Michael Schaecher <michaelschaecher@mlstidbits.com>
    MLS Tidbits <development@mlistidbits.com>
---

# NAME

`depot rm` - Remove a DEB package from APT repository

# SYNOPSIS

`depot rm` [*options*] *package_name...*

# DESCRIPTION

The `depot rm` command removes a DEB package from the APT repository managed by `depot`. It deletes the package files and updates the repository metadata accordingly. If no *option* is specified, the command removes all version and architecture variants of the specified package.

## OPTIONS

`-v`, `--version` *version*
: Specifies the version of the package to remove. If not provided, all versions of the package will be removed.

`-a`, `--arch` *architecture*
: Specifies the architecture of the package to remove (e.g., `amd64`, `i386`). If not provided, all architectures of the package will be removed.

`-h`, `--help`
: Displays help information about the `depot rm` command.

# EXAMPLES

Remove all versions and architectures of the package `example-package`:

```bash
depot rm example-package
```

Remove a specific version of `example-package`:

```bash
depot rm -v 1.2.3 example-package
```

Remove a specific architecture of `example-package`:

```bash
depot rm -a amd64 example-package
```

Remove a specific version and architecture of `example-package`:

```bash
depot rm -v 1.2.3 -a amd64 example-package
```

# SEE ALSO

`depot add`(1), `depot update`(1), `depot init`(1), `depot config`(1), `depot key`(1), `depot`(1)

# COPYRIGHT

This software is licensed under the GPLv3.0+ license or greater all rights reserved.
