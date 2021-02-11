# Docker Tidbits

## Inspect Docker VM Contents on Docker for Mac

With [Docker Machine](https://docs.docker.com/machine/) it was possible to SSH into the VM (`docker-machine ssh`) and inspect Docker volume contents, etc. This is still possible on the more modern [Docker for Mac](https://docs.docker.com/docker-for-mac/install/), albeit in a roundabout way:

```
docker run -it --privileged --pid=host ubuntu nsenter -t 1 -m -u -n -i sh
```

Source: https://gist.github.com/BretFisher/5e1a0c7bcca4c735e716abf62afad389
