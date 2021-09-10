# Snapcraft

## Files

Local: <https://github.com/httpie/httpie/blob/master/snapcraft.yaml>

## Release process

Trigger a new [build](https://snapcraft.io/httpie/builds), then [promote it](https://snapcraft.io/httpie/releases). If more management is needed: [revisions supervision](https://dashboard.snapcraft.io/snaps/httpie/revisions/).

### Development

Launch the docker image:

```bash
docker pull ubuntu/latest
docker run -it --rm ubuntu/latest
```

From inside the container:

```bash
# Clone
git clone --depth=1 https://github.com/httpie/httpie.git
cd httpie

# Build
export SNAPCRAFT_BUILD_ENVIRONMENT_CPU=8
export SNAPCRAFT_BUILD_ENVIRONMENT_MEMORY=16G
snapcraft --debug

# Install
sudo snap install --dangerous httpie_XXX_amd64.snap

# Test
httpie.http --version
httpie.https --version
# Auto-aliases cannot be tested when installing a snap outside the store.
# http --version
# https --version

# Remove
sudo snap remove httpie
```

## Try locally

Launch the docker image:

```bash
docker pull ubuntu/latest
docker run -it --rm ubuntu/latest
```

From inside the container:

```bash
# Install
sudo snap install --edge httpie

# Enjoy!
http --version
https --version
```
