# Fedora

## Downstream details

- Maintainer: Miro Hrončok <miro@hroncok.cz>
- Release monitoring: <https://release-monitoring.org/project/1337/>
- User feedbacks: <https://bodhi.fedoraproject.org/updates/?packages=httpie>

Added the [.packit.yaml](https://github.com/httpie/httpie/blob/master/.packit.yaml) local file.
It allows us to have real-time Fedora checks on pull requests and new releases.

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/linux/fedora/httpie.spec>
- Downstream: <https://src.fedoraproject.org/rpms/httpie/blob/rawhide/f/httpie.spec>

## Release process

There is nothing to do on our side: `Packit` will see the new release and open a pull request [there](https://src.fedoraproject.org/rpms/httpie). Then, a Fedora maintainer will review it and merge.

## Try locally

Launch the docker image:

```bash
docker pull fedora
docker run -it --rm fedora
```

From inside the container:

```bash
# Install
dnf install -y httpie

# Enjoy!
http --version
https --version
```

## Q/A with Miro

Q: What would the command to install the latest stable version look like?

A: Assuming the latest stable version is already propagated to Fedora:

```bash
# Note that yum is an alias to dnf.
$ sudo dnf install httpie
```

Q: Will dnf/yum upgrade then update to the latest?

A: Yes, assuming the same as above.

Q: Are new versions backported automatically?

A: No. The process is:

1. A new HTTPie release is created on Github.
2. A pull request for Fedora `rawhide` (the development version of Fedora, currently Fedora 35) is created.
3. A Fedora packager (usually Miro) sanity checks the pull request and merges, builds. HTTPie is updated in `rawhide` within 24 hours (sometimes more, for unrelated issues).
4. A Fedora packager decides whether the upgrade is suitable for stable Fedora releases (currently 34, 33), if so, merges the changes there.
5. (if the above is yes) The new version of HTTPie lands in `updates-testing` repo where it waits for user feedback and lands within ~1 week for broad availability.
