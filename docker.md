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