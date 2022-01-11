# Test

## Build Docker

```dosbatch
# DockerイメージをBuildする
docker build -t my-python-app .
# Dockerイメージを起動する
docker run -it --rm --name my-running-app my-python-app
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

```dosbatch
docker ps
docker cp <container ID>:/usr/app/testtest.md .
```
