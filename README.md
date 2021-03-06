# Zig

[![CircleCI](https://circleci.com/gh/Eloitor/docker-zig.svg?style=svg)](https://circleci.com/gh/Eloitor/docker-zig)

A docker image for [Zig](https://ziglang.org) with the c libraries X11 and Xft.
This image is based upon Alpine Linux 3.12.

See https://github.com/euantorano/docker-zig the original version of this image without the libraries.

## Using this image

### Building an executable

```
docker run -v $PWD:/app eloitor/zig:0.7.0 build-exe hello.zig -lc -lX11 -lXft
```

The commands for the extra libraries (`-lc -lX11 -lXft` are optional.

If you don't need the libraries, you can also run  the image `euantorano/zig`.
## Available tags

There are two variants of tags provided by this repository - release tags such as `0.7.0`, and `master` branch builds such as `master-28018703`.

The most recent `master-X` build is always tagged as simply `master` as well as having a tag including the Git hash for the release.

The most recent stable release is always tagged as `latest`.

## Building the Docker image(s)

A simple Python script (`build.py`) is included that scrapes the [Zig Releases web page](https://ziglang.org/download/) in order to get available releases. It then builds an image for every release, including the current master release and pushes them to Docker Hub.

This script uses [`pipenv`](https://pipenv.readthedocs.io/en/latest/) and can be ran as follows: `pipenv run python build.py --version-path ./last_version --master-path ./last_master`.
