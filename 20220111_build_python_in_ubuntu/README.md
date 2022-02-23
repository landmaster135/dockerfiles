# Test

## Build Docker

DockerイメージをBuildする

```dosbatch
docker build -t my-cloudsdk-container .
```

Dockerイメージを起動する

```dosbatch
docker run -it --rm --name my-running-container my-cloudsdk-container
```

両方まとめて実行する

```dosbatch
docker build -t my-cloudsdk-container . && docker run -it --rm --name my-running-container my-cloudsdk-container
```

## Check version of python and pip.
```shell
python3 -V
```

```shell
pip -V
```

## Check package list.
```shell
pip list
```

## Test with Docker

### Execute in the machine via docker image.

```shell
python <script>
```

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
