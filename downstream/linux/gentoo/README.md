# Gentoo

## Downstream details

- Release monitoring: <https://packages.gentoo.org/packages/net-misc/httpie>

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/gentoo/>
- Downstream: <https://github.com/gentoo/gentoo/tree/master/net-misc/httpie/>

## Release process

Open a pull request to create `httpie-XXX.ebuild` and update `Manifest`.

- Here is how to calculate the size and checksum (replace `2.5.0` with the correct version):

  ```bash
  # Download
  $ wget https://github.com/httpie/httpie/archive/2.5.0.tar.gz

  # Size
  $ stat --printf="%s\n" 2.5.0.tar.gz
  1105177

  # Checksum
  $ openssl dgst -blake2b512 2.5.0.tar.gz
  BLAKE2b512(2.5.0.tar.gz)= 6e16868c81522d4e6d2fc0a4e093c190f18ced720b35217930865ae3f8e168193cc33dfecc13c5d310f52647d6e79d17b247f56e56e8586d633a2d9502be66a7
  ```

- The commit message must be `net-misc/httpie: version bump to XXX`.

### Development

Launch the docker image:

```bash
docker pull gentoo/stage3
docker run -it --rm gentoo/stage3
```

From inside the container:

```bash
# Install tools
emerge --sync
emerge pkgcheck repoman

# Go to the package location
cd /var/db/repos/gentoo/net-misc/httpie

# Retrieve patches (only files that were modified since the last release)
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/gentoo/httpie-XXX.ebuild \
  -o httpie-XXX.ebuild
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/gentoo/Manifest \
  -o Manifest
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/gentoo/metadata.xml \
  -o metadata.xml

# Basic checks
repoman manifest
repoman full -d -x
pkgcheck scan

# Build and install the package
emerge --with-test-deps httpie-XXX.ebuild

# Run the tests suite
ebuild httpie-XXX.ebuild clean test

# And test it!
http --version
https --version
```

## Try locally

Launch the docker image:

```bash
docker pull gentoo/stage3
docker run -it --rm gentoo/stage3
```

From inside the container:

```bash
# Intall
emerge --sync
emerge httpie

# Enjoy!
http --version
https --version
```
