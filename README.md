# Dockerfiles

This repository manages files for build and run with Docker.

## Build Docker

### Refer to each folder.

Refer to each folder.

###

If you receive following error message, you need to remove docker image cache.

```shell-session
#6 0.902 E: You don't have enough free space in /var/cache/apt/archives/.
```

Execute this command to check many cache. (for zsh in macOS terminal)

```bash
docker images | grep none | cut -b 50-64 | tr '\n' ' '
```

Execute this command to remove "none" cache. (for zsh in macOS terminal)

```bash
docker rmi `docker images | grep none | cut -b 50-64 | tr '\n' ' '`
```

If you remove many image cache, cho-kimochee !!

## Test with Docker

### Execute in the windows machine while the machine being booted by docker.

```dosbatch
docker ps
docker cp <container ID>:/usr/app/testtest.md .
```
