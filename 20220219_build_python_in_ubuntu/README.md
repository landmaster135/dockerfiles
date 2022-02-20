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