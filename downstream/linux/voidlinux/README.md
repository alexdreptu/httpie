# Void Linux

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/voidlinux/template>
- Downstream: <https://github.com/void-linux/void-packages/blob/master/srcpkgs/httpie/template>

## Release process

Open a pull request to update the downstream file ([example](https://github.com/void-linux/void-packages/pull/32905)).

- The commit message must be `httpie: update to XXX.`.

### Test

Launch the docker image:

```bash
docker pull voidlinux/voidlinux
docker run -it --rm voidlinux/voidlinux
```

From inside the container:

```bash
# Sync and upgrade once, assume error comes from xbps update
xbps-install -Syu
# Install tools
xbps-install -y git xtools file util-linux binutils bsdtar coreutils

# Clone
git clone --depth=1 git://github.com/void-linux/void-packages.git void-packages-src
cd void-packages-src

# Retrieve the patch
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/voidlinux/template \
    -o srcpkgs/httpie/template

# Check the package
xlint srcpkgs/httpie/template

# Link / to /masterdir
ln -s / masterdir

# Enable ethereal chroot-style
export XBPS_ALLOW_CHROOT_BREAKOUT=yes
./xbps-src binary-bootstrap
./xbps-src chroot

# Build the package
cd void-packages
export SOURCE_DATE_EPOCH=0
./xbps-src pkg httpie

# Install the package
xbps-install --repository=hostdir/binpkgs httpie

# And finally test it!
http --version
https --version
```

## Try locally

Launch the docker image:

```bash
docker pull voidlinux/voidlinux
docker run -it --rm voidlinux/voidlinux
```

From inside the container:

```bash
# Install
xbps-install -Syu
xbps-install -y httpie

# Enjoy!
http --version
https --version
```
