# Spack

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/spack/package.py>
- Downstream: <https://github.com/spack/spack/blob/develop/var/spack/repos/builtin/packages/httpie/package.py>

## Release process

Open a pull request to update the downstream file ([example](https://github.com/spack/spack/pull/25888)).

- The commit message must be `httpie: add vXXX`.

### Development

Launch the docker image:

```bash
docker pull spack/centos7
docker run -it --rm spack/centos7
```

From inside the container:

```bash
# Clone
git clone --depth=1 https://github.com/spack/spack.git
cd spack

# Retrieve the patch
curl https://raw.githubusercontent.com/httpie/httpie/master/downstream/linux/spack/package.py \
    -o var/spack/repos/builtin/packages/httpie/package.py

# Check the package
spack spec httpie

# Check available versions (it should show the new version)
spack versions httpie

# Install the package
spack install httpie@XXX
spack load httpie

# And test it!
http --version
https --version
```

## Try locally

Launch the docker image:

```bash
docker pull spack/centos7
docker run -it --rm spack/centos7
```

From inside the container:

```bash
# Install
spack install httpie
spack load httpie

# Enjoy!
http --version
https --version
```
