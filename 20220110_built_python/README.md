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
