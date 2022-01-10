# Test

## Build Docker

```dosbatch
# DockerイメージをBuildする
docker build -t my-nodejs-app .
# Dockerイメージを起動する
docker run -it --rm --name my-running-app my-nodejs-app
```

## Test with Docker

### Execute in the machine via docker image.

```shell
npm run <script>
```

### Execute in the windows machine while the machine being booted by docker.

```dosbatch
docker ps
docker cp <container ID>:/usr/app/testtest.md .
```
