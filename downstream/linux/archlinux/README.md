# Arch Linux

Note: Sending patches downstream does not seem easy. I failed to find where is located the package file on <https://gitlab.archlinux.org>. So we are relying on the last maintainer and it works pretty well so far.

## Downstream details

Maintainer: daurnimator <daurnimator@archlinux.org>

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/archlinux/APKBUILD>
- Downstream: <https://github.com/archlinux/svntogit-community/blob/packages/httpie/trunk/PKGBUILD>

## Release process

Check <https://archlinux.org/packages/community/any/httpie/> and if the version is outdated, simply [report it](https://archlinux.org/packages/community/any/httpie/flag/).

## Try locally

Launch the docker image:

```bash
docker pull archlinux
docker run -it --rm archlinux
```

From inside the container:

```bash
# Install
pacman -Sy --noconfirm httpie

# Enjoy!
http --version
https --version
```
