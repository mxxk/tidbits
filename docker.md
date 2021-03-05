# Docker Tidbits

## Inspect Docker VM Contents on Docker for Mac

With [Docker Machine](https://docs.docker.com/machine/) it was possible to SSH into the VM (`docker-machine ssh`) and inspect Docker volume contents, etc. This is still possible on the more modern [Docker for Mac](https://docs.docker.com/docker-for-mac/install/), albeit in a roundabout way:

```
docker run -it --privileged --pid=host ubuntu nsenter -t 1 -m -u -n -i sh
```

Source: https://gist.github.com/BretFisher/5e1a0c7bcca4c735e716abf62afad389

## Build Unminimized Ubuntu Docker Image w/ Timezone & Locale

```Dockerfile
FROM ubuntu:latest
SHELL ["bash", "-c"]
RUN ln -fs /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y locales OTHER_DEPENDENCIES
RUN yes | unminimize
ARG LOCALE_UTF8=en_US.UTF-8
RUN locale-gen "${LOCALE_UTF8}"
ENV LC_ALL=${LOCALE_UTF8}
```

## Simple Long-Running Docker Container

The Docker Compose configuration below can be spun up with `docker-compose up` and quickly gracefully terminate on Ctrl-C or equivalent.

```yml
version: '3'
services:
  main:
    image: ubuntu:latest
    tty: true
    command:
      - bash
```
