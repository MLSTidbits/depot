---
title: depot-key
section: 1
header: User Commands
footer: depot-key(1)
date: 2025-08-11
author:
    Michael Schaecher <michaelschaecher@mlstidbits.com>
    MLS Tidbits <development@mlistidbits.com>
---

# SYNOPSIS

`depot key` *flags*  arg...

# DESCRIPTION

The `depot key` command is used to manage GPG keys for signing the `Release` files in a DEB package repository. Signing the `Release` file ensures the authenticity and integrity of the packages in the repository, allowing users to verify that the packages have not been tampered with and are from a trusted source. This command provides options to create and/or list GPG keys.

## FLAGS

`-r`, `--real-name` <full-name>
: Specifies the full name of the key owner. This is a required field when creating a new GPG key.
`-e`, `--email` <email-address>
: Specifies the email address associated with the GPG key. This is a required field when creating a new GPG key.
`-l`, `--length` <length>
: Sets the key length for the GPG key. The default length is 2048 bits.
`-c`, `--comment` <comment>
: Adds a comment to the GPG key. This is an optional field.
`-E`, `--expires` <days>
: Sets the expiration period for the GPG key in days. A value of 0 means the key will never expire. The default is 365 days (1 year).
`-L`, `--list-keys`
: Lists existing GPG keys in the user's keyring.
`-h`, `--help`
: Displays help information about the `depot key` command.

## EXAMPLES

To create a new GPG key with the specified real name, email, key length, comment, and expiration period, use the following command:

```bash
depot key -r "John Doe" -e "johndoe@email.com" -l 4096 -c "My DEB Repo Key" -E 730
```

To list existing GPG keys in the user's keyring, use the following command:

```bash
depot key --list-keys
```

# SEE ALSO

`depot(1)`, `depot-init(1)`, `depot-add(1)`, `depot-remove(1)`, `depot-update(1)`, `depot-config(1)`

# LICENSE

This software is licensed under the GPLv3.0+ license or greater all rights reserved.
