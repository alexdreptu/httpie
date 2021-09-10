# CentOS

## Downstream details

- Maintainer: Mikel Olasagasti <mikel@olasagasti.info>
- Release monitoring: <https://release-monitoring.org/project/1337/>

## Files

Same as [Fedora](../fedora/README.md).

## Release process

Same as [Fedora](../fedora/README.md).

## Try locally

Launch the docker image:

```bash
docker pull centos
docker run -it --rm centos
```

From inside the container:

```bash
# Install
yum install -y epel-release
yum install -y httpie

# Enjoy!
http --version
https --version
```

## Q/A with Mikel

Q: What should we do to help seeing a new version on CentOS?

A: When a new release is published Miro and I get notified by [release-monitoring](https://release-monitoring.org/project/1337/), that fills a BugZilla ticket reporting a new version being available.

The system also tries to create a simple patch to update the spec file, but in the case of CentOS it needs some manual revision. For example for 2.5.0 `defuxedxml` dep is required. Maybe with CentOS-9 and some new macros that are available now in Fedora it can be automated same way. But even the bump can be automated, maintainers should check for license changes, new binaries/docs/ and so on.
