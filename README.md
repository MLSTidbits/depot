<div align="center">
 <image
  src="images/logo.svg"
  alt="Depot Logo"
  width=auto
  height=512px
  />
</div>

## ABOUT DEPOT

If you're like me, you probably have a ton scripts and/or binary applications that you have written over the years.  These scripts and applications are often scattered across your filesystem that you have to install and manage manually.  Depot is a simple `bash` based application that helps you manage your scripts and applications into [Debian](https://www.debian.org/) style APT repositories.  Depot is designed to be simple and easy to use, so you can focus on writing your scripts and applications, rather than managing how to install them.

Use the power of `apt` to install and manage your scripts and applications.

## FEATURES

- Simple and easy to use `bash` based application.
- Create and manage your own APT repositories.
- Git integration for easy version control.
- Support for multiple repositories.
- Support for multiple architectures, `amd64`, `arm64`, `armhf`, etc.
- Support for multiple distributions, `stable`, `noble`, `focal`, etc.
- Support for multiple components, `main`, `contrib`, `non-free`, etc.
- Support for GPG signing of packages and repositories.

## REQUIREMENTS

- `bash` version 4 or higher.
- `dpkg-dev` for building Debian packages.
- `gnupg` for GPG signing of packages and repositories.
- `apt` and `apt-utils` for managing APT repositories.
- `git` for version control (optional).

## INSTALLATION

To install Depot the easy way is to add the [MLS Tidbits APT repository](https://archive.mlstidbits.com) to your system and install it via `apt`. Then you can keep it up to date via `apt` as well.

### Manual Installation

To install Depot manually, you can clone the repository and run the following commands:

```bash
git clone https://github.com/MLSTidbits/depot.git
cd depot
```

You can then run the `install` command to install Depot.

```bash
sudo install -Dm755 src/depot /usr/bin/depot
sudo install -Dm755 src/lib/* /usr/lib/depot/
```

## USAGE

To use Depot, you can run the `depot` command followed by the desired subcommand.  You can see a list of available subcommands by running:

```bash
depot help
```

### Creating a Repository

To create a new APT repository `cd` into the directory where you want to create the repository and run: `depot init --origin <og` command. This will create the necessary directory structure and configuration files for the repository with default values.

| Command                                                                                 | Description                                                        |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| `depot init --origin <org>`                                                             | Initializes a new APT repository in the current directory with the specified origin. |
| `depot --origin "My Company" --suite "focal" --pool "flat"`                             | Initializes a new APT repository with a custom origin, suite, and pool structure. |
| `depot init --origin "My Company" --suite "focal" --components "main contrib non-free"` | Initializes a new APT repository with multiple components.          |
| `depot init --origin "My Company" --suite "focal" --arch "amd64 arm64"`                 | Initializes a new APT repository supporting multiple architectures. |

### Adding Packages

To add a package to the repository, you can use the `add` subcommand. For example, to add a package located at `/path/to/package.deb`, you can run:

```bash
depot add --single /path/to/package.deb
```

This will copy the package to the appropriate location in the repository and update the package index files. You can also add multiple packages at once by specifying a directory:

```bash
depot add --all /path/to/directory
```

If you are building the package via `dpkg-buildpackage` and both the changes and buildinfo files are present those can be added by applying the appropriate flags.

```bash
depot add --all /path/to/directory --changes --buildinfo
```

The above command will add the buildinfo and changes files for the package if they are present in the specified directory.

### Removing Packages

Be careful when removing packages as this action cannot be undone. To remove a package from the repository, you can use the `rm` subcommand. For example, to remove all versions of a package named `mypackage`, you can run:

```bash
depot rm <package-name>
```

This will remove all versions of the package from the repository and update the package index files. You can also remove a specific version of a package by specifying the version number:

```bash
depot rm <package-name> --version <version>
```

To remove a package based on its architecture, you can use the `--arch` flag:

```bash
depot rm <package-name> --arch <architecture>
```

### Creating a GPG Key

To create a GPG key for signing packages and repositories, you can use the `key` subcommand. For example, to create a new GPG key, you can run the command below. This will create a new GPG key with default values.

```bash
depot key
```

To create a GPG key with custom values, you can specify the desired options:

| Flag                        | Description                                              |
|-----------------------------|----------------------------------------------------------|
| `-r, --realname <name>`     | Real name for the GPG key.                               |
| `-e, --email <email>`       | Email address for the GPG key.                           |
| `-l, --length <length>`     | Key length for the GPG key (default: 2048).              |
| `-c, --comment <comment>`   | Comment for the GPG key.                                 |
| `-E, --expires <days>`      | Expiration period for the GPG key in days (0 for never). |

**Example:*

```bash
depot key --realname "John Doe" --email "johndoe@email.com" --length 4096 --comment "My Key" --expires 365
```

### Configure Settings

You can configure Depot settings using the `config` subcommand. For example, to set the default GPG key for signing packages and repositories, you can run:

```bash
depot config --local gpg.id <key-id>
```

Replacing `--local` with `--global` will set the configuration globally for the user. This means that the configuration will be applied to all repositories managed by Depot for that user.

To add Maintainer information to the configuration, you can run:

```bash
depot config --local maintainer.name "John Doe"
depot config --local maintainer.email "johndoe@email.com"
```

## CONTRIBUTING

Contributions are welcome! If you find a bug or have a feature request, please open an issue on the [GitHub repository](https://github.com/MLSTidbits/depot). If you would like to contribute code, please fork the repository and create a pull request.

## LICENSE

Depot is licensed under the GPL-3.0+ License. See the [LICENSE](COPYING) file for more information.
