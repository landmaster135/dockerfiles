# Test

## Build Docker

### DockerイメージをBuildする

```dosbatch
docker build -t my-rust-app .
```

### Dockerイメージを起動する

```dosbatch
docker run -it --rm --name my-running-rust-app my-rust-app
```

## Test with Docker

### Execute in the machine via docker image.

```shell
npm run <script>
```

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
