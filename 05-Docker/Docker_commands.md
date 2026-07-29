# 🐳 Docker Commands Cheat Sheet

A quick reference for the Docker commands you'll use most often.

---

# 1. Check Docker Installation

```bash
docker --version
```

Displays the installed Docker version.

---

# 2. View Docker Information

```bash
docker info
```

Shows Docker system information.

---

# 3. Download an Image

```bash
docker pull <image-name>
```

Example:

```bash
docker pull nginx
```

Downloads an image from Docker Hub.

---

# 4. List Images

```bash
docker images
```

Displays all downloaded Docker images.

---

# 5. Build an Image

```bash
docker build -t <image-name> .
```

Example:

```bash
docker build -t my-app .
```

Builds an image from the Dockerfile in the current directory.

---

# 6. Run a Container

```bash
docker run <image-name>
```

Example:

```bash
docker run nginx
```

Creates and starts a container.

---

# 7. Run a Container in Detached Mode

```bash
docker run -d <image-name>
```

Example:

```bash
docker run -d nginx
```

Runs the container in the background.

---

# 8. Assign a Name to a Container

```bash
docker run --name <container-name> <image-name>
```

Example:

```bash
docker run --name web nginx
```

---

# 9. Map Ports

```bash
docker run -p <host-port>:<container-port> <image-name>
```

Example:

```bash
docker run -p 8080:80 nginx
```

- Host Port → Port on your computer.
- Container Port → Port inside the container.

Access:

```
http://localhost:8080
```

---

# 10. Run in Interactive Mode

```bash
docker run -it ubuntu
```

Starts an interactive terminal.

---

# 11. List Running Containers

```bash
docker ps
```

---

# 12. List All Containers

```bash
docker ps -a
```

Shows both running and stopped containers.

---

# 13. Stop a Container

```bash
docker stop <container-id/container-name>
```

Example:

```bash
docker stop web
```

---

# 14. Start a Container

```bash
docker start <container-name>
```

---

# 15. Restart a Container

```bash
docker restart <container-name>
```

---

# 16. Pause a Container

```bash
docker pause <container-name>
```

Temporarily freezes the container.

---

# 17. Resume a Paused Container

```bash
docker unpause <container-name>
```

---

# 18. Remove a Container

```bash
docker rm <container-name>
```

The container must be stopped first.

Force removal:

```bash
docker rm -f <container-name>
```

---

# 19. Remove an Image

```bash
docker rmi <image-name>
```

---

# 20. Remove All Stopped Containers

```bash
docker container prune
```

---

# 21. Remove Unused Images

```bash
docker image prune
```

Remove all unused images:

```bash
docker image prune -a
```

---

# 22. Remove Everything Unused

```bash
docker system prune
```

Remove everything including unused images:

```bash
docker system prune -a
```

---

# 23. View Container Logs

```bash
docker logs <container-name>
```

Follow logs in real time:

```bash
docker logs -f <container-name>
```

---

# 24. Execute Commands Inside a Running Container

```bash
docker exec -it <container-name> bash
```

Example:

```bash
docker exec -it web bash
```

If Bash isn't installed:

```bash
docker exec -it web sh
```

---

# 25. View Running Processes

```bash
docker top <container-name>
```

---

# 26. Monitor Resource Usage

```bash
docker stats
```

Displays live CPU, memory, and network usage.

---

# 27. Inspect a Container

```bash
docker inspect <container-name>
```

Shows detailed JSON information.

---

# 28. View Port Mapping

```bash
docker port <container-name>
```

---

# 29. Copy Files

From Host → Container

```bash
docker cp file.txt web:/app
```

From Container → Host

```bash
docker cp web:/app/file.txt .
```

---

# 30. Rename a Container

```bash
docker rename old-name new-name
```

---

# 31. Tag an Image

```bash
docker tag my-app my-app:v1
```

---

# 32. Push an Image to Docker Hub

Login:

```bash
docker login
```

Push:

```bash
docker push username/my-app:latest
```

---

# 33. Search Docker Hub

```bash
docker search nginx
```

---

# 34. Save an Image

```bash
docker save -o image.tar my-app
```

---

# 35. Load an Image

```bash
docker load -i image.tar
```

---

# 36. View Docker Networks

```bash
docker network ls
```

---

# 37. Create a Network

```bash
docker network create my-network
```

---

# 38. Run a Container on a Custom Network

```bash
docker run --network my-network nginx
```

---

# 39. List Docker Volumes

```bash
docker volume ls
```

---

# 40. Create a Volume

```bash
docker volume create my-volume
```

---

# 41. Mount a Volume

```bash
docker run -v my-volume:/data nginx
```

---

# 42. Display Docker Disk Usage

```bash
docker system df
```

---

# 43. Stop All Running Containers

```bash
docker stop $(docker ps -q)
```

---

# 44. Remove All Containers

```bash
docker rm $(docker ps -aq)
```

---

# 45. Remove All Images

```bash
docker rmi $(docker images -q)
```

---

# Docker Command Structure

```text
docker <command> <subcommand> [options]
```

Example:

```bash
docker run -d -p 8080:80 --name web nginx
```

Breakdown:

- `docker` → Docker CLI
- `run` → Create and start a container
- `-d` → Detached mode
- `-p 8080:80` → Port mapping
- `--name web` → Container name
- `nginx` → Image

---

# Most Frequently Used Commands

| Command | Purpose |
|----------|---------|
| `docker images` | List images |
| `docker ps` | Running containers |
| `docker ps -a` | All containers |
| `docker build -t app .` | Build image |
| `docker run -d -p 8080:80 app` | Run container |
| `docker stop <container>` | Stop container |
| `docker start <container>` | Start container |
| `docker restart <container>` | Restart container |
| `docker logs <container>` | View logs |
| `docker exec -it <container> bash` | Open terminal |
| `docker rm <container>` | Delete container |
| `docker rmi <image>` | Delete image |
| `docker system prune -a` | Clean unused Docker resources |

---

## Quick Memory Trick

**B → I → C**

- **Build** → `docker build`
- **Image** → `docker images`
- **Container** → `docker run`

Think of it as:

```
Dockerfile
     ↓
docker build
     ↓
Image
     ↓
docker run
     ↓
Container
```
