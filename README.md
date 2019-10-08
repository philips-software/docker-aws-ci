[![Build Status](https://action-badges.now.sh/philips-software/docker-aws-ci/workflows/build/badge.svg)](https://github.com/philips-software/docker-aws-ci/actions)
[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)

# Docker images

This repo will contain docker images for AWS related CI tasks

Installed tools:
- aws cli
- kubectl
- git
- zip
- curl
- jq

Current versions available:
```
.
├── python-alpine
│   └── Dockerfile
```
## Usage

Images can be found on [https://hub.docker.com/r/philipssoftware/node/](https://hub.docker.com/r/philipssoftware/docker-aws-ci/).

```
docker run philipssoftware/aws-ci:lts aws --version
docker run philipssoftware/aws-ci:lts kubectl --version
```

## Content

The images obviously contain aws cli, but also two other files:
- `REPO`
- `TAGS`

### REPO

This file has a url to the REPO with specific commit-sha of the build.
Example: 

```
$ docker run philipssoftware/node:12 cat REPO
https://github.com/philips-software/aws-ci/tree/facb2271e5a563e5d6f65ca3f475cefac37b8b6c
```

### TAGS

This contains all the similar tags at the point of creation. 

```
$ docker run philipssoftware/aws-ci:<TAK> cat TAGS
```

You can use this to pin down a version of the container from an existing development build for production.


## Why

> Why do we have our own docker image definitions?

We often need some tools in a container for checking some things. F.e. [jq](https://stedolan.github.io/jq/), [aws-cli](https://aws.amazon.com/cli/) and [curl](https://curl.haxx.se/).
We can install this every time we need a container, but having this baked into a container seems a better approach.

That's why we want our own docker file definitions.

## Issues

- If you have an issue: report it on the [issue tracker](https://github.com/philips-software/aws-ci/issues)

## Author

- Niek Palm <niek.palm@philips.com>

## License

License is MIT. See [LICENSE file](LICENSE.md)

## Philips Forest

This module is part of the Philips Forest.

```
                                                     ___                   _
                                                    / __\__  _ __ ___  ___| |_
                                                   / _\/ _ \| '__/ _ \/ __| __|
                                                  / / | (_) | | |  __/\__ \ |_
                                                  \/   \___/|_|  \___||___/\__|  

                                                                 Infrastructure
```

Talk to the forestkeepers in the `docker-images`-channel on Slack.

[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)
