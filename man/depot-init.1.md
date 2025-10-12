---
title: depot-init
section: 1
header: User Commands
footer: depot-init(1)
date: 2025-08-11
author:
    Michael Schaecher <michaelschaecher@mlstidbits.com>
    MLS Tidbits <development@mlistidbits.com>
---

# SYNOPSIS

`depot init` *flags*  arg...

# DESCRIPTION

The `depot init` command initializes a new DEB package repository in the current directory. It sets up the necessary directory structure and configuration files required for managing DEB packages. This command is typically the first step in creating a new DEB repository. You can customize various aspects of the repository using the available flags.

## FLAGS

`-o`, `--origin` <org>
: Specifies the name of the organization or individual responsible for this repository.

`-l`, `--label` <label>
: Sets the label field in the Release file.

`-s`, `--suite` <label>
: Defines the codename for the release version, e.g., Focal or Buster. Defaults to 'stable' if not specified.

`-c`, `--codename` <codename>
: Sets the codename field; this is often the same as suite.

`-a`, `--arch` <arch,arch2>
: Specifies the architectures supported by this repository. Defaults to the output of 'dpkg --print-architecture'.

`-C`, `--components` <component>
: Defines the components for this repository. Defaults to 'main'. Multiple components can be specified separated by spaces. For example: `main`, `contrib non-free`.

`-d`, `--description` <description>
: Provides a short description of the repository.

`-p`, `--pool` <structure>
: Determines the type of pool structure to use. Options are: alphabet, library or flat. The default is `is flat`.

`-h`, `--help`
: Displays help information about the `depot init` command.

## EXAMPLES

To initialize a new DEB repository with default settings, run the following command in the desired directory without any flags:

```bash
depot init
```

To initialize a new DEB repository with custom settings, use the following command to specify the origin and description:

```bash
depot init -o "My Company" -d "My custom DEB repository"
```

In most cases the *codename* matches the *suite*. However, if you want to set a different codename, you can do so by using the `-c` or `--codename` flag. For example, to set the suite to "stable" and the codename to "focal", you would run:

```bash
depot init -s stable -c focal
```

Setting up the pool structure can help organize packages in a way that suits your needs. For example, to use the "library" pool structure, you would run:

```bash
depot init -p library
```

- `alphabet`: Organizes packages by the first letter of the package name and individual package directories.

- `library`: Organizes packages by library name and individual package directories.

- `flat`: All packages are stored directly in the pool directory without additional subdirectories.

# SEE ALSO

`depot(1)`, `depot-add(1)`, `depot-remove(1)`, `depot-update(1)`, `depot-sign(1)`, `depot-config(1)`

# LICENSE

This software is licensed under the GPLv3.0+ license or greater all rights reserved.
