# Release process

Here is a concise document explaining our release process.

It is done in two steps:

1. The PyPi publication.
2. Follow OS-specific steps to send patches downstream.

**Important:** when committing changes downstream, please sign-off all commits (`git commit -s`).

## First, PyPi

Before thinking about anything, let's do the release on [PyPi](https://pypi.org/project/httpie/).
That is done quite easily by triggering manually the [release workflow](https://github.com/httpie/httpie/actions/workflows/release.yml).

## Then, spread dowstream

Here is the current state of versions available per OS (including Linux, Mac, and Windows): <https://repology.org/project/httpie/versions>.

Find downstream details including steps to configure the environment, building/installing/testing the new version, in tables below.

Legend:

- :heavy_check_mark: Official maintainer.
- :white_check_mark: Unofficial, but trusted, maintainer.

### Linux

|       Status       | Distribution                               |
| :----------------: | ------------------------------------------ |
| :heavy_check_mark: | [Alpine](linux/alpine/README.md)           |
| :white_check_mark: | [Arch Linux](linux/archlinux/README.md)    |
| :white_check_mark: | [CentOS, RHEL](linux/centos/README.md)     |
| :white_check_mark: | [Debian GNU/Linux](linux/debian/README.md) |
| :white_check_mark: | [Fedora](linux/fedora/README.md)           |
| :heavy_check_mark: | [Gentoo](linux/gentoo/README.md)           |
| :white_check_mark: | Manjaro                                    |
| :heavy_check_mark: | [Snapcraft](linux/snapcraft/README.md)     |
| :heavy_check_mark: | [Spack](linux/spack/README.md)             |
| :heavy_check_mark: | [Void Linux](linux/voidlinux/README.md)    |

<!--
TODO
|   :construction:   | [AOSC](linux-aosc.md)                   |
|   :construction:   | [Funtoo](linux-funtoo.md) (1.0.2)       |
|   :construction:   | [LiGurOS](linux-liguros.md)             |
|   :construction:   | [Mageia](linux-mageia.md) (2.3.0)       |
|   :construction:   | [nixpkgs](linux-nixpkgs.md) (2.4.0)     |
|   :construction:   | [PLD Linux](linux-pld.md) (0.7.2)       |
|   :construction:   | [Slackware](linux-slackware.md) (1.0.3) |
|   :construction:   | [SlitTaZ](linux-slitaz.md) (2.0.0)      |
|   :construction:   | [Solus](linux-solus.md) (2.4.0)         |
-->

### Mac

|       Status       | Tool                                           |
| :----------------: | ---------------------------------------------- |
| :heavy_check_mark: | :construction: [Homebrew](mac/brew/README.md)  |
| :heavy_check_mark: | :construction: [MacPorts](mac/ports/README.md) |

### Windows

|       Status       | Tool                                                      |
| :----------------: | --------------------------------------------------------- |
| :heavy_check_mark: | :construction: [Chocolatey](windows/chocolatey/README.md) |
