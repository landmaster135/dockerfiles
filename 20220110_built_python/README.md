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

## Run a single Python script
```dosbatch
docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp python:3 python your-daemon-or-script.py
```

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
