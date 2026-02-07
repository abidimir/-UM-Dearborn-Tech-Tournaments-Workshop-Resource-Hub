# Docker Cheatsheet

A quick reference for Docker commands and concepts.

---

## Core Concepts

| Term | What it means |
|------|---------------|
| **Image** | A blueprint/template for a container. Read-only. Built from a Dockerfile. |
| **Container** | A running instance of an image. You can have many containers from one image. |
| **Dockerfile** | A text file with instructions to build an image. |
| **Docker Hub** | Public registry for Docker images (like GitHub for containers). |
| **Volume** | Persistent storage that survives container restarts. |
| **Docker Compose** | Tool for defining multi-container applications in a YAML file. |

### Mental Model

```
Dockerfile  →  Image  →  Container(s)
(recipe)       (cake)    (slices being eaten)
```

---

## Working with Images

```bash
# List images on your machine
docker images

# Pull an image from Docker Hub
docker pull python:3.11

# Build an image from a Dockerfile in current directory
docker build -t my-app .

# Build with a specific Dockerfile
docker build -f Dockerfile.dev -t my-app:dev .

# Remove an image
docker rmi image-name

# Remove all unused images
docker image prune
```

### Image Naming Convention

```
repository:tag

# Examples:
python:3.11           # Python version 3.11
python:3.11-slim      # Smaller Python image
my-app:latest         # Your app, latest version
my-app:v1.0.0         # Your app, specific version
```

If you don't specify a tag, Docker assumes `:latest`.

---

## Working with Containers

```bash
# Run a container from an image
docker run python:3.11

# Run interactively with terminal access (-it)
docker run -it python:3.11 bash

# Run in background (detached mode)
docker run -d my-app

# Run with a name
docker run --name my-container my-app

# Run with port mapping (host:container)
docker run -p 8000:8000 my-app

# Run with environment variables
docker run -e DATABASE_URL=postgres://... my-app

# Run with a volume mount (host:container)
docker run -v $(pwd):/app my-app

# List running containers
docker ps

# List ALL containers (including stopped)
docker ps -a

# Stop a running container
docker stop container-name

# Start a stopped container
docker start container-name

# Remove a container
docker rm container-name

# Remove a running container (force)
docker rm -f container-name

# Remove all stopped containers
docker container prune
```

---

## Inspecting & Debugging

```bash
# View container logs
docker logs container-name

# Follow logs in real-time
docker logs -f container-name

# Execute a command in a running container
docker exec container-name ls /app

# Open a shell in a running container
docker exec -it container-name bash

# View container details
docker inspect container-name

# View resource usage
docker stats
```

---

## Dockerfile Basics

A Dockerfile contains instructions to build an image. Each instruction creates a layer.

```dockerfile
# Start from a base image
FROM python:3.11-slim

# Set the working directory inside the container
WORKDIR /app

# Copy requirements first (for better caching)
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application
COPY . .

# Expose a port (documentation, doesn't actually publish)
EXPOSE 8000

# Command to run when container starts
CMD ["python", "app.py"]
```

### Common Dockerfile Instructions

| Instruction | Purpose |
|-------------|---------|
| `FROM` | Base image to start from |
| `WORKDIR` | Set working directory |
| `COPY` | Copy files from host to image |
| `RUN` | Execute commands during build |
| `ENV` | Set environment variables |
| `EXPOSE` | Document which port the app uses |
| `CMD` | Default command when container runs |
| `ENTRYPOINT` | Configure container as executable |

---

## Docker Compose

Docker Compose lets you define multi-container applications in a single file.

### Example docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    environment:
      - DEBUG=true
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

### Docker Compose Commands

```bash
# Start all services (in background)
docker compose up -d

# Start and rebuild images
docker compose up -d --build

# View logs
docker compose logs

# Follow logs
docker compose logs -f

# Stop all services
docker compose stop

# Stop and remove containers, networks
docker compose down

# Stop and remove everything including volumes
docker compose down -v

# List running services
docker compose ps

# Execute command in a service
docker compose exec web bash
```

---

## Volumes

Volumes persist data beyond container lifecycle.

```bash
# Create a named volume
docker volume create my-data

# List volumes
docker volume ls

# Run container with named volume
docker run -v my-data:/app/data my-app

# Run container with bind mount (current directory)
docker run -v $(pwd):/app my-app

# Remove a volume
docker volume rm my-data

# Remove all unused volumes
docker volume prune
```

---

## Cleanup Commands

Docker can use a lot of disk space. Clean up regularly:

```bash
# Remove all stopped containers
docker container prune

# Remove all unused images
docker image prune

# Remove all unused volumes
docker volume prune

# Remove everything unused (containers, images, networks, volumes)
docker system prune -a --volumes

# See disk usage
docker system df
```

---

## Common Patterns

### Development Workflow

```bash
# Build the image
docker build -t my-app .

# Run with live code reload (mount source code)
docker run -p 8000:8000 -v $(pwd):/app my-app

# Or use Docker Compose (recommended for development)
docker compose up
```

### Quick Testing

```bash
# Run Python interactively
docker run -it python:3.11

# Run a one-off command
docker run python:3.11 python -c "print('Hello!')"

# Run bash in any image
docker run -it ubuntu bash
```

---

## Quick Reference Table

| Command | What it does |
|---------|--------------|
| `docker build -t name .` | Build image from Dockerfile |
| `docker run image` | Run a container |
| `docker run -it image bash` | Run interactively |
| `docker run -p 8000:8000 image` | Run with port mapping |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker stop name` | Stop a container |
| `docker logs name` | View container logs |
| `docker exec -it name bash` | Shell into container |
| `docker compose up -d` | Start compose services |
| `docker compose down` | Stop compose services |

---

## Tips

- **Use specific image tags** — `python:3.11` not `python:latest` for reproducibility
- **Use slim/alpine images** — Smaller images = faster builds and deploys
- **Order Dockerfile for caching** — Put things that change less often at the top
- **Don't run as root** — Add a non-root user for production images
- **Use .dockerignore** — Exclude unnecessary files from the build context
- **Clean up regularly** — `docker system prune` is your friend