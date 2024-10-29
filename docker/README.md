
# Docker Basics

Search a docker image in hub.docker.com

```sh
docker search [image-name]
```

Download a docker image from hub.docker.com

```sh
docker image pull [image-name]:[image-version]/[image-tag]
```

Build new docker image

```sh
docker build -t [image-label] .   # the dot . means the currect folder, you can chage it by the path/to/dockerfile
```

> **OPTIONS:** \
> `-f, --file` Specify a docker file name (default is 'Dockerfile')

Run container

```sh
docker run --name [container-name] [image-name]:[image-version]/[tag]
```

> **OPTIONS:** \
> `-d` Run container detached (in background)

Expose your application to host server

```sh
docker run --name [container-name] -p [host-port]:[container-port] [image-name]:[Image_version]/[tag]
```

> **Example:** `docker run --name my-app-container -p 5000:5000 my-app-image:latest`

Show images

```sh
docker images
```

remove image

```sh
docker rmi [image-id]
```


Show active containers

```sh
docker ps
```

Show all containers

```sh
docker ps -a
```

Start a stopped container

```sh
docker start [container-id]
```

Stop container

```sh
docker stop [container-id]
```

Stop container immediatly

```sh
docker stop -t 0 [container-id]
```

Remove container

```sh
docker rm [container-id]
```

Interact with a container

```sh
docker exec -it [container-name] bash
```