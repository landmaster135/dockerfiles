# Test

## Build and Run Docker

DockerイメージをBuildする

```dosbatch
docker build -t my-pythonll-image .
```

Dockerコンテナを起動する

```dosbatch
docker run -it --rm --name my-pythonll-container my-pythonll-image
```

両方まとめて実行する

```dosbatch
docker build -t my-pythonll-image . && docker run -it --rm --name my-pythonll-container my-pythonll-image
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

execute function

```shell
python3 ./src/landmasterlibrary/image_editor.py test_data_dir
```

test execution

***

```shell
pytest test/test_text_replacer.py
```

```shell
pytest test/test_generaltool.py
```

***

check test coverage

```shell
pytest --cov --cov-branch -v test/test_text_replacer.py
```

***

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
