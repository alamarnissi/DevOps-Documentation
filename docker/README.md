
# Docker Basics

## 1. Day-to-Day Work

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

## 2. Docker Images

### Search for a Docker Image

Search for images in Docker Hub.

```sh
docker search [image-name]
```

### Download a Docker Image

Pull an image from Docker Hub.

```sh
docker pull [image-name]:[tag]
```

- **Example:** `docker pull ubuntu:latest`

### Build a New Docker Image

Build an image from a Dockerfile in the current directory (using .) or specify a path to the Dockerfile.

```sh
docker build -t [image-label] .
```

> **OPTIONS:** \
> `-t` Specify a tag (label) for the image. \
> `-f` Specify a custom Dockerfile (`-f path/to/dockerfile`).

- **Example:** `docker build -t my-app:1.0 .`


### List All Docker Images

Display all available images on your local machine.

```sh
docker images
```

## 3. Docker Containers 

### Run a Docker Container

Start a container from an image.

```sh
docker run --name [container-name] [image-name]:[tag]
```

> **OPTIONS:** \
> `-d` Run container in detached mode (background). \
> `-p` Map ports between host and container (`-p [host-port]:[container-port]`). 

- **Example:** `docker run -d --name my-nginx -p 8080:80 nginx:latest`

### Run an Interactive Container

Start a container interactively (useful for debugging).

```sh
docker run -it [image-name] bash
```

- **Example:** `docker run -it ubuntu bash`

### List Running Containers

Show all running containers.

```sh
docker ps
```

### List All Containers (Running and Stopped)

Show all containers, including those that have been stopped.

```sh
docker ps -a
```

### Stop a Running Container

Stop a container.

```sh
docker stop [container-id]
```

### Stop a Container Immediately

Force-stop a container.

```sh
docker stop -t 0 [container-id]
```

### Start a Stopped Container

Restart a stopped container.

```sh
docker start [container-id]
```

### Remove a Container

Delete a stopped container.

```sh
docker rm [container-id]
```

- **Example:** `docker rm my-container`

### Remove All Stopped Containers

Remove all containers that are not running.

```sh
docker container prune
```

## 4. Docker Container Lifecycle

### Pause a Container

Pause all processes in a container.

```sh
docker pause [container-id]
```

### Unpause a Container

Resume a paused container.

```sh
docker unpause [container-id]
```

### Restart a Container

Restart a container (stops and starts it again).

```sh
docker restart [container-id]
```

### Attach to a Running Container

Attach to a running container’s console.

```sh
docker attach [container-id]
```

### Interact with a Running Container

Run a command inside an active container (e.g., access shell).

```sh
docker exec -it [container-name] bash
```

- **Example:** `docker exec -it my-container bash`