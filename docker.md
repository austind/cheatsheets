# Docker Cheat Sheet

All images and containers may be referenced by their name, or a unique substring of their SHA256 hash.

### Run an image as a container

```sh
docker run <image-name-or-id>
```

### Expose port from container to local system

Exposes port 80 from the image to port 3000 on localhost.

```sh
docker run -p 3000:80 <image-name-or-id>
```

### Nuke everything

```sh
docker system prune -a
```

### List running containers

```sh
docker ps
```

### Remove unused images

```sh
docker image prune
```

### Remove stopped containers

```sh
docker container prune
```

### Remove container when stopped

```sh
docker run --rm <image-name-or-id>
```

### Copy files into a container

Copy all files from local src/ folder to /app folder on container named boring_vaughan.

```sh
docker cp src/. boring_vaughan:/app
```

### Volumes & Bind Mounts

#### Volumes

Persistent storage that Docker manages, i.e., the user can't view or modify the contents.

##### Anonymous Volumes

* Deleted when container is deleted, if container was created with `--rm` flag
* Can't persist data across containers

Added to `Dockerfile`:

```dockerfile
VOLUME [ "/path/inside/container/to/persist" ]
```

Declared at container run time:

```sh
docker run -v /path/inside/container/to/persist myimage:tag
```

##### Named Volumes

* Persists across container deletion

```sh
docker run -v volumename:/path/inside/container/to/persist myimage:tag
```

Containers run with the same `volumename` value will have access to the same data.

#### Bind Mounts

Persistent data that the user can access and modify.

Persists the current working directory into the container's `/app` directory:

```sh
docker run -v $(cmd):/app myimage:tag
```

NOTE: Bind mounts must be an absolute path (relative paths won't work).