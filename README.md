# Ubuntu Base Images

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/bced2d477fd8443b80ff528d1c0bc2d1)](https://app.codacy.com/gh/buluma/ubuntu?utm_source=github.com&utm_medium=referral&utm_content=buluma/ubuntu&utm_campaign=Badge_Grade_Settings)
[![14.04, trusty](https://github.com/buluma/ubuntu/actions/workflows/build-14.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-14.04.yml) [![16.04, xenial](https://github.com/buluma/ubuntu/actions/workflows/build-16.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-16.04.yml) [![18.04, bionic](https://github.com/buluma/ubuntu/actions/workflows/build-18.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-18.04.yml) [![20.04, focal](https://github.com/buluma/ubuntu/actions/workflows/build-20.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-20.04.yml) [![22.04, jammy](https://github.com/buluma/ubuntu/actions/workflows/build-22.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-22.04.yml) [![23.04, lunar](https://github.com/buluma/ubuntu/actions/workflows/build-23.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-23.04.yml) [![SL Scan](https://github.com/buluma/ubuntu/actions/workflows/shiftleft-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/shiftleft-analysis.yml) [![Codacy Security Scan](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml) [![Codacy Security Scan](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml)

## Quick reference

-	**Maintained by**:  
	[Buluma (Shadow Walker)](https://github.com/buluma/ubuntu)

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://dockr.ly/slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

## Supported tags and respective `Dockerfile` links

-	[`14.04`, `trusty-20191217`, `trusty`](https://github.com/buluma/ubuntu/blob/main/ubuntu1404/Dockerfile)
-	[`16.04`, `xenial-20210804`, `xenial`](https://github.com/buluma/ubuntu/blob/main/ubuntu1604/Dockerfile)
-	[`18.04`, `bionic-20210930`, `bionic`](https://github.com/buluma/ubuntu/blob/main/ubuntu1804/Dockerfile)
-	[`20.04`, `focal-20211006`, `focal`, `latest`](https://github.com/buluma/ubuntu/blob/main/ubuntu2004/Dockerfile)
-	[`21.04`, `hirsute-20211107`, `hirsute`](https://github.com/buluma/ubuntu/blob/main/ubuntu2104/Dockerfile)
-	[`21.10`, `impish-20211102`, `impish`, `rolling`](https://github.com/buluma/ubuntu/blob/main/ubuntu2110/Dockerfile)
-	[`22.04`, `jammy-20211122`, `jammy`](https://github.com/buluma/ubuntu/blob/main/ubuntu2204/Dockerfile)
-	[`23.04`, `lunar-20230314`, `lunar`, `latest`](https://github.com/buluma/ubuntu/blob/main/ubuntu2304/Dockerfile)

## Quick reference (cont.)

-	**Where to file issues**:  
	[the cloud-images bug tracker](https://github.com/buluma/ubuntu/issues) (include the `docker` tag)

-	**Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
	[`amd64`](https://hub.docker.com/r/amd64/ubuntu/), [`arm32v7`](https://hub.docker.com/r/arm32v7/ubuntu/), [`arm64v8`](https://hub.docker.com/r/arm64v8/ubuntu/), [`i386`](https://hub.docker.com/r/i386/ubuntu/), [`ppc64le`](https://hub.docker.com/r/ppc64le/ubuntu/), [`riscv64`](https://hub.docker.com/r/riscv64/ubuntu/), [`s390x`](https://hub.docker.com/r/s390x/ubuntu/)

-	**Published image artifact details**:  
	[repo-info repo's `repos/ubuntu/` directory](https://github.com/docker-library/repo-info/blob/master/repos/ubuntu) ([history](https://github.com/docker-library/repo-info/commits/master/repos/ubuntu))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images repo's `library/ubuntu` file](https://github.com/buluma/ubuntu) ([history](https://github.com/buluma/ubuntu/commits/main))

-	**Source of this description**:  
	[docs repo's `ubuntu/` directory](https://github.com/buluma/ubuntu/blob/main/README.md) ([history](https://github.com/buluma/ubuntu/commits/main/README.md))

## What is Ubuntu?

Ubuntu is a Debian-based Linux operating system that runs from the desktop to the cloud, to all your internet connected things. It is the world's most popular operating system across public clouds and OpenStack clouds. It is the number one platform for containers; from Docker to Kubernetes to LXD, Ubuntu can run your containers at scale. Fast, secure and simple, Ubuntu powers millions of PCs worldwide.



opment of Ubuntu is led by Canonical Ltd. Canonical generates revenue through the sale of technical support and other services related to Ubuntu. The Ubuntu project is publicly committed to the principles of open-source software development; people are encouraged to use free software, study how it works, improve upon it, and distribute it.

> [wikipedia.org/wiki/Ubuntu](https://en.wikipedia.org/wiki/Ubuntu)

![logo](https://raw.githubusercontent.com/docker-library/docs/01c12653951b2fe592c1f93a13b4e289ada0e3a1/ubuntu/logo.png)

## What's in this image?

This image is built from official rootfs tarballs provided by Canonical (specifically, https://partner-images.canonical.com/oci/ for Bionic and later and https://partner-images.canonical.com/core/ for older releases).

The `ubuntu:latest` tag points to the "latest LTS", since that's the version recommended for general use. The `ubuntu:rolling` tag points to the latest release (regardless of LTS status).

Along a similar vein, the `ubuntu:devel` tag is an alias for whichever release the "devel" suite on the mirrors currently points to, as determined by the following one-liner: `wget -qO- http://archive.ubuntu.com/ubuntu/dists/devel/Release | awk -F ': ' '$1 == "Codename" { print $2; exit }'`

## Locales

Given that it is a minimal install of Ubuntu, this image only includes the `C`, `C.UTF-8`, and `POSIX` locales by default. For most uses requiring a UTF-8 locale, `C.UTF-8` is likely sufficient (`-e LANG=C.UTF-8` or `ENV LANG C.UTF-8`).

For uses where that is not sufficient, other locales can be installed/generated via the `locales` package. [PostgreSQL has a good example of doing so](https://github.com/docker-library/postgres/blob/69bc540ecfffecce72d49fa7e4a46680350037f9/9.6/Dockerfile#L21-L24), copied below:

```dockerfile
RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
	&& localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.utf8
```

## How is the rootfs built?

The [tarballs published by Canonical](https://partner-images.canonical.com/oci/) are built from scripts that live in [the livecd-rootfs project](https://code.launchpad.net/~ubuntu-core-dev/livecd-rootfs/+git/livecd-rootfs/+ref/ubuntu/master), especially `live-build/auto/build`.
