# Alpine

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/alpine/APKBUILD>
- Downstream: <https://gitlab.alpinelinux.org/alpine/aports/-/blob/master/community/httpie/APKBUILD>

## Release process

Open a pull request to update the downstream file ([example](https://gitlab.alpinelinux.org/alpine/aports/-/merge_requests/25075)).

- The `pkgrel` value must be set to `0`.
- The commit message must be `community/httpie: upgrade to XXX`.

### Development

Launch the docker image:

```bash
docker pull alpine
docker run -it --rm alpine
```

From inside the container:

```bash
# Install tools
apk add alpine-sdk sudo

# Add a user (password required)
adduser me
addgroup me abuild
echo "me    ALL=(ALL) ALL" >> /etc/sudoers

# Switch user
su - me

# Create a private key (not used but required)
abuild-keygen -a -i

# Clone
git clone --depth=1 https://gitlab.alpinelinux.org/alpine/aports.git
cd aports/community/httpie

# Retrieve the patch
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/alpine/APKBUILD \
    -o APKBUILD

# Build the package
abuild -r

# Install the package
sudo apk add --repository ~/packages/community httpie

# And test it!
http --version
https --version
```

## Try locally

Launch the docker image:

```bash
docker pull alpine
docker run -it --rm alpine
```

From inside the container:

```bash
# Install
apk add httpie

# Enjoy!
http --version
https --version
```
