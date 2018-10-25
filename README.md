# Releaser
[![GoDoc](https://godoc.org/github.com/DecipherNow/releaser?status.svg)](https://godoc.org/github.com/DecipherNow/releaser)
[![Go Report Card](https://goreportcard.com/badge/github.com/DecipherNow/releaser)](https://goreportcard.com/report/github.com/DecipherNow/releaser)

Implement the decipher release process.  The two sub-commands available here are `github` and `docker`, to help with two main release processes.

### Github
The github functionality is a simple wrapper around a github SDK to create
releases, tag commits, and upload release assets.  

### Docker
The docker functionality is a simple wrapper around a docker SDK to take a
source image, tag it with major, major.minor, and major.minor.patch tags, and then to push up to dockerhub.

## Usage
### Help
Help packes are available for both the Docker and Github processes:

#### Docker Image Tag/Push
```bash
>>$ ./releaser help docker
NAME:
   releaser docker - Do the docker job

USAGE:
   releaser docker [command options] [arguments...]

OPTIONS:
   --symver value    Symantic Version of the release to prepare
   --image value     Source Docker image to release
   --username value  Username for cmd operations
   --password value  Password for cmd operations
   --suffix value    String to be appended to the final docker tag. e.g. -alpine, -centos

```

#### Github Release

```bash
justin@mal:~/go/src/github.com/deciphernow/releaser$ ./releaser help github
NAME:
   releaser github - Do the github release

USAGE:
   releaser github [command options] [arguments...]

OPTIONS:
   --symver value        Symantic Version of the release to prepare
   --token value         Access token for github releases
   --organization value  Organization for github releases
   --username value      Username for cmd operations
   --password value      Password for cmd operations
   --asset value         File[s] to be uploaded to the github release
```

### Symver tagging/push docker images
`releaser docker --symver v1.3.4 --image deciphernow/gm-proxy:latest --username $DOCKER_USER --password $DOCKER_PASS`

### Create release and upload an asset for the release
`releaser github --symver 3.4.5 --token $GITHUB_TOKEN --organization deciphernow --asset ./binary-asset`

## Build
1. `dep ensure -v`
2. `go build`