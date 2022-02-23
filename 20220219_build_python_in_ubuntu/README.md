# Test

## Build and Run Docker

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
python3 app.py
```

```shell
python3 test/test_helpers.py
```

```shell
coverage run test/test_helpers.py
```

```shell
coverage report -m test/test_helpers.py
```

```shell
coverage html -d coverage_html
```

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
