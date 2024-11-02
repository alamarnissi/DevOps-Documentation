
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
> `-t` Give a tag to your image
> `-f, --file` Specify the path to the docker file

Run container

```sh
# run container from an image
docker run --name [container-name] [image-name]:[image-version]/[tag]

# run container and expose it to host server
docker run --name [container-name] -p [host-port]:[container-port] [image-name]:[Image_version]/[tag]

# run container with a volume
docker run --name [container-name] -v /path/on/host:[container-directory] [image-name]:[Image_version]/[tag]
```

> **OPTIONS:** \
> `--name` Give a name to your new container \
> `-d` Run container detached (in background) \
> `-p` Map ports between host and container `docker run --name my-app-container -p 5000:5000 my-app-image:latest` \
> `-v` Mount a directory from your host system into the container `docker run -v ${PWD}/scripts:/code/scripts myimage:latest`

Show images

```sh
docker images
```

remove image

```sh
docker rmi [image-id]
```

Show running containers

```sh
docker ps
```

Show all containers (running and stopped)

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

Remove container

```sh
docker rm [container-id]
```

Interact with a container

```sh
docker exec -it [container-name] bash
```

## 2. Docker Images

**Docker Image:** This is like a "blueprint" or template for your application, containing everything it needs to run, including the code, dependencies, libraries, and system tools. Think of it as a snapshot that can be used to create running instances.

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

**Container:** A container is a running instance of a Docker image. When you "run" an image, Docker creates a container, which is an isolated environment where your application lives and operates independently from other processes on your system. You can start, stop, and delete containers without affecting the image.

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

## 5. Docker Volumes and Storage

**Volume/Storage:** Volumes provide a way to store data separately from the container's lifecycle. Since containers are meant to be lightweight and ephemeral (they can be stopped and removed without affecting the image), volumes allow data to persist across restarts or even after the container is deleted.

### List All Volumes

Display all Docker volumes.

```sh
docker volume ls
```

### Create a Docker Volume

Create a new volume to persist data.

```sh
docker volume create [volume-name]
```

### Mount a Volume to a Container

Attach a volume to a container to persist data across restarts.

```sh
docker run -v [volume-name]:/path/in/container [image-name]
```

- **Example:** `docker run -v my-volume:/data app-image`

### Remove a Docker Volume

Delete a volume by name.

```sh
docker volume rm [volume-name]
```

### Remove All Unused Volumes

Clear all volumes not currently used by containers.

```sh
docker volume prune
```

## 6. Docker Networking

**Docker network:** is a way for Docker containers to communicate with each other and with external systems. Networks allow containers to share information, send data back and forth, and be isolated from each other as needed. Docker provides different types of networks to control how containers interact.
- For example, a bridge network is for internal container-to-container communication, and a host network is for sharing the host's network directly.

### List All Networks

Show all Docker networks.

```sh
docker network ls
```

### Create a New Network

Create a custom network.

```sh
docker network create [network-name]
```

- **Example:** `docker network create my-network`

### Connect a Container to a Network

Add a container to an existing network.

```sh
docker network connect [network-name] [container-id]
```

### Disconnect a Container From a Network

Remove a container from a network.

```sh
docker network disconnect [network-name] [container-id]
```

### Remove a Network

Delete an unused network

```sh
docker network rm [network-name]
```

## 7. Docker Logs and Monitoring

### View Container Logs

Check logs for a container.

```sh
docker logs [container-id]
```

> **OPTIONS:** \
> `-f` Follow log output (live).

- **Example:** `docker logs -f my-container`

### Monitor Container Resource Usage

Display real-time resource usage of running containers.

```sh
docker stats
```

- **Example:** `docker stats my-container`

### Inspect a Container or Image

Display detailed information on a container or image.

```sh
docker inspect [container-id or image-id]
```

## 8. Docker Cleanup and System Management

### Remove All Unused Data

Clear out unused data (dangling images, stopped containers, etc.).

```sh
docker system prune
```

> **OPTIONS:** \
> `-a` Remove all unused images not just dangling ones

- **Example:** `docker system prune -a`

### Show Docker Disk Usage

Check the space used by Docker images, containers, volumes, and networks.

```sh
docker system df
```

## 9. Docker-Compose

**Docker Compose:** is a tool that allows you to define and run multiple Docker containers together using a single configuration file, called docker-compose.yml. With Docker Compose, you can easily manage multi-container applications by specifying all services, networks, and volumes they need in one place, making it simple to start, stop, and manage complex applications

### Start Services with Docker Compose

Run multiple containers defined in a `docker-compose.yml` file.

```sh
docker-compose up
```

> **OPTIONS/** \
> `-d` Run containers in detached mode (in background)

- **Example:** `docker-compose up -d`

### Stop Services with Docker Compose

Stop services started by Docker Compose.

```sh
docker-compose down
```

### List Running Services with Docker Compose

View running services defined in the `docker-compose.yml` file.

```sh
docker-compose ps
```