# OCI Images

[![Build images](https://github.com/pgils/oci-images/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/pgils/oci-images/actions/workflows/build.yml)

Various OCI images.

## Images

### [`debian-slim`][debian-slim]

Slim Debian image based on [`debian:<suite>-slim`][debian].

[debian-slim]: debian-slim/Containerfile
[debian]: https://hub.docker.com/_/debian

### [`debian-build`][debian-build]

Generic build image based on [`buildpack-deps`][buildpack],

Additional packages included:

- Bitbake
- Debian package development tools
- LLVM-clang
- Golang compiler
- UPX
- rclone

[debian-build]: debian-build/Containerfile
[buildpack]: https://hub.docker.com/_/buildpack-deps

#### Usage

##### Docker

```cli
> docker run -ti --rm -v $(pwd):/work ghcr.io/pgils/debian-build:bookworm
```

The `uid` and `gid` of the `builder` user in the container are automatically updated to match the ownership of the `/work` directory by the `entrypoint` script.

##### Podman

```cli
> podman run -ti --rm -v $(pwd):/work --entrypoint bash ghcr.io/pgils/debian-build:bookworm
```

Override the entrypoint to prevent unnecessary user switching since `root` will already be mapped to the unprivileged user on the host.
