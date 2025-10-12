---
title: depot-config
section: 1
header: User Commands
footer: depot-config(1)
date: 2025-08-11
author:
    Michael Schaecher <michaelschaecher@mlstidbits.com>
    MLS Tidbits <development@mlistidbits.com>
---

# SYNOPSIS

`depot config` *flags*  arg...

# DESCRIPTION

`depot config` command allows you to configure various settings for *GPG* signing and repository maintainer information, both globally (ei user-wide) or locally (for a specific repository). This command is essential for setting up secure and properly attributed DEB package repositories.

## FLAGS

`-l`, `--local`
: Applies the configuration changes to the local repository only. **Note:**  Setting local configuration well override global settings for the specific repository.

`-g`, `--global`
: Applies the configuration changes globally for the user. This is the default behavior if neither `--local` nor `--global` is specified.

`-h`, `--help`
: Displays help information about the `depot config` command.

## OPTIONS

`maintainer.name` \<*full-name*\>
: Sets the full name of the repository maintainer. This information is used in the repository metadata. If not set, it defaults is to correct system user name.

`maintainer.email` \<*email-address*\>
: Sets the email address of the repository maintainer. This information is used in the repository metadata. If not set, it defaults to the correct system user email + hostname (e.g., user@hostname).

`gpg.id` \<*gpg-key-id*\>
: Specifies the GPG key ID to use for signing the repository. This is important for ensuring the authenticity and integrity of the packages in the repository. To learn more about GPG keys, see `depot-key(1)`. **Hint:** You can list your available GPG keys using the command `gpg --list-keys`.

# EXAMPLES

To set the maintainer's name and email globally, you can use the following commands:

```bash
depot config --global maintainer.name "John Doe"
depot config --global maintainer.email "johndoe@email.com"
```

To set the GPG key ID for signing locally in a specific repository, navigate to the repository directory and run:

```bash
depot config --local gpg.id "ABCD1234"
```

All configurations can be ran in one command as well:

```bash
depot config --global maintainer.name "John Doe" maintainer.email "johndoe@email.com" gpg.id "ABCD1234"
```

# SEE ALSO

`depot(1)`, `depot-init(1)`, `depot-add(1)`, `depot-remove(1)`, `depot-update(1)`, `depot-key(1)`

# LICENSE

This software is licensed under the GPLv3.0+ license or greater all rights reserved.
