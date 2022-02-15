# Test

## Build Docker

```dosbatch
# DockerイメージをBuildする
docker build -t my-python-env .
# Dockerイメージを起動する
docker run -it --rm --name my-running-app my-python-env
```

## Run a single Python script
```dosbatch
docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp python:3 python your-daemon-or-script.py
```

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
