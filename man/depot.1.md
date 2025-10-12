---
title: depot
section: 1
header: User Commands
footer: depot(1)
date: 2025-08-11
author:
    Michael Schaecher <michaelschaecher@mlstidbits.com>
    MLS Tidbits <development@mlistidbits.com>
---

# SYNOPSIS

`depot` [*options*] *flags*  arg...

# DESCRIPTION

The `depot` command is a command line interface for managing personal, team, and organization DEB package repositories. It provides a simple way to create, update, and maintain DEB repositories, making it easy toc share and distribute DEB packages. In-order to run `depot` commands, you need to be in the root directory of the DEB repository.

If the repository is hosted on a web server, ensure that the server is configured to serve the repository files correctly. This may involve setting up appropriate MIME types and directory listings. For secure repositories, consider using HTTPS and setting up authentication if necessary.

## OPTIONS

`init`
: Initializes a new DEB repository in the current directory.

`add`
: Adds a DEB package to the repository. For more information, see `depot add --help`.

`remove` *package-name*
: Removes a DEB package from the repository. For more information, see `depot remove --help`.

`update`
: Updates the repository metadata. This should be run after adding or removing packages. For more information, see `depot update --help`.

`sign`
: Creates a GPG signature for the repository.

`config`
: Configures repository settings. For more information, see `depot config --help`.

`version`, `-v`, `--version`
: Displays the version of the `depot` command.

`help`
: Displays help information about the `depot` command.

# SEE ALSO

* `depot-init(1)`, `depot-add(1)`, `depot-remove(1)`, `depot-update(1)`, `depot-sign(1)`, `depot-config(1)`

# LICENSE

This software is licensed under the GPLv3.0+ license or greater:
    copyright (C) 2025 Michael Schaecher <michaelleeschaecher@mlstidbits.com>
    copyright (C) 2025 MLS Tidbits <contact@mlstidbits.com>

You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.
