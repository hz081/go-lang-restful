# Go application starter kit

This is a starter kit for a Go application. It uses a Makefile to drive the build (the
universal API to software projects) and a Dockerfile to build a docker image.

## Customizing it

To use this, simply copy these files and make the following changes:

Makefile:

   - change `BIN` to your binary name
   - rename `cmd/myapp` to `cmd/$BIN`
   - change `PKG` to the Go import path of this repo
   - change `REGISTRY` to the Docker registry you want to use
   - maybe change `SRC_DIRS` if you use some other layout
   - choose a strategy for `VERSION` values - git tags or manual

Dockerfile.in:

   - change the `MAINTAINER` to you
   - maybe change or remove the `USER` if you need

## Building

Run `make` or `make build` to compile your app.  This will use a Docker image
to build your app, with the current directory volume-mounted into place.  This
will store incremental state for the fastest possible build.

Run `make container` to build the container image.  It will calculate the image
tag based on the most recent git tag, and whether the repo is "dirty" since
that tag (see `make version`).

Run `make push` to push the container image to `REGISTRY`.

Run `make clean` to clean up.