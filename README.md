# Ubuntu Base Images

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/bced2d477fd8443b80ff528d1c0bc2d1)](https://app.codacy.com/gh/buluma/ubuntu?utm_source=github.com&utm_medium=referral&utm_content=buluma/ubuntu&utm_campaign=Badge_Grade_Settings)
[![20.04, focal](https://github.com/buluma/ubuntu/actions/workflows/build-20.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-20.04.yml) [![22.04, jammy](https://github.com/buluma/ubuntu/actions/workflows/build-22.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-22.04.yml) [![23.04, lunar](https://github.com/buluma/ubuntu/actions/workflows/build-23.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-23.04.yml) [![24.04, noble](https://github.com/buluma/ubuntu/actions/workflows/build-24.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-24.04.yml) [![25.04, plucky](https://github.com/buluma/ubuntu/actions/workflows/build-25.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-25.04.yml) [![25.10, questing](https://github.com/buluma/ubuntu/actions/workflows/build-25.10.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-25.10.yml) [![26.04, resolute](https://github.com/buluma/ubuntu/actions/workflows/build-26.04.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/build-26.04.yml) [![SL Scan](https://github.com/buluma/ubuntu/actions/workflows/shiftleft-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/shiftleft-analysis.yml) [![Codacy Security Scan](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml) [![Codacy Security Scan](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml/badge.svg?branch=main)](https://github.com/buluma/ubuntu/actions/workflows/codacy-analysis.yml)

## About

This repository contains Docker images for multiple Ubuntu versions, maintained by Michael Buluma (Buluma). These images are designed to provide consistent, reliable Ubuntu base images for containerized applications and development environments.

The images follow the official Ubuntu Docker image patterns but include additional configurations to support systemd and Ansible usage within containers, making them particularly useful for testing and development scenarios.

## Key Features

- Multiple Ubuntu versions supported (14.04 through 26.04)
- Systemd-enabled containers for full service management
- Ansible-ready environment (with optional Ansible installation)
- Multi-architecture support (amd64, arm64, ppc64le, s390x, etc.)
- Regular automated builds and security updates
- Optimized for containerized environments while maintaining compatibility with traditional Ubuntu packages

## Supported tags and respective `Dockerfile` links

### Currently Supported LTS Versions
-	[`20.04`, `focal`, `focal-20220612`, `latest`](https://github.com/buluma/ubuntu/blob/main/ubuntu2004/Dockerfile) *(EOL: May 2025)*
-	[`22.04`, `jammy-20251013`, `jammy`](https://github.com/buluma/ubuntu/blob/main/ubuntu2204/Dockerfile) *(EOL: June 2027)*
-	[`24.04`, `noble-20251013`, `noble`, `latest`](https://github.com/buluma/ubuntu/blob/main/ubuntu2404/Dockerfile) *(EOL: May 2029)*

### Currently Supported Non-LTS Versions
-	[`23.04`, `lunar`, `lunar-20230314`, `devel`](https://github.com/buluma/ubuntu/blob/main/ubuntu2304/Dockerfile) *(EOL: January 2024)*
-	[`25.04`, `plucky-20251001`, `plucky`](https://github.com/buluma/ubuntu/blob/main/ubuntu2504/Dockerfile) *(EOL: January 2026)*

### Deprecated/EOL LTS Versions
-	[`14.04`, `trusty`, `trusty-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu1404/Dockerfile) *(EOL: April 2019)*
-	[`16.04`, `xenial`, `xenial-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu1604/Dockerfile) *(EOL: April 2021)*
-	[`18.04`, `bionic`, `bionic-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu1804/Dockerfile) *(EOL: May 2023)*

### Deprecated/EOL Non-LTS Versions
-	[`21.04`, `hirsute`, `hirsute-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu2104/Dockerfile) *(EOL: January 2022)*
-	[`21.10`, `impish`, `impish-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu2110/Dockerfile) *(EOL: July 2022)*
-	[`22.10`, `kinetic`, `kinetic-20220612`](https://github.com/buluma/ubuntu/blob/main/ubuntu2210/Dockerfile) *(EOL: July 2023)*

### Rolling/Development Versions
-	[`25.10`, `questing-20251217`, `questing`, `rolling`](https://github.com/buluma/ubuntu/blob/main/ubuntu2510/Dockerfile) *(EOL: July 2026)*
-	[`26.04`, `resolute-20251208`, `resolute`, `devel`](https://github.com/buluma/ubuntu/blob/main/ubuntu2604/Dockerfile) *(Development)*

## Building and Running

### Building Images

To build a specific Ubuntu version:

```bash
cd ubuntu2004  # or any version directory
docker build -t ubuntu:20.04 .
```

### Running Containers

The images are designed to run with privileged access for systemd support:

```bash
# Run with systemd support
docker run --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro -it ubuntu:20.04

# Run with Ansible support
docker run --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro -it ubuntu:20.04 /lib/systemd/systemd
```

## Development Conventions

### Dockerfile Patterns

Each Dockerfile follows a consistent pattern:
1. Base image from official Ubuntu
2. Install essential packages including systemd components
3. Configure initctl faker for older Ubuntu versions
4. Set up volumes for systemd functionality
5. Define entrypoint and health checks

### Systemd Support

The images are configured to support systemd services by:
- Mounting `/sys/fs/cgroup` as a volume
- Using systemd as the init process (`/lib/systemd/systemd` or `/sbin/init`)
- Disabling problematic services like getty that consume CPU in containerized environments

### Ansible Integration

Many images include Ansible support (often commented out by default) with:
- Python package installations
- Inventory configuration
- Service management capabilities

## Maintainer

- **Michael Buluma** (Buluma)
- GitHub: https://github.com/buluma/ubuntu
