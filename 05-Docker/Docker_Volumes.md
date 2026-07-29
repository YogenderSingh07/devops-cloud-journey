# 📁 Docker Volumes

Docker Volumes provide persistent storage for containers.

Without volumes, any data created inside a container is lost when the container is removed.

---

# Why Do We Need Volumes?

Suppose you run a MySQL container.

```bash
docker run mysql
```

The database stores its files inside the container.

If the container is deleted:

```bash
docker rm mysql-container
```

Everything is lost.

Volumes solve this problem by storing data outside the container.

```
Container
│
├── Application
├── OS Libraries
└── Data
      │
      ▼
Docker Volume
```

Even if the container is deleted, the volume still exists.

---

# List Volumes

```bash
docker volume ls
```

---

# Create a Volume

```bash
docker volume create my-volume
```

Example

```bash
docker volume create mysql-data
```

---

# Inspect a Volume

```bash
docker volume inspect my-volume
```

---

# Mount a Volume

```bash
docker run -d \
-v my-volume:/app/data \
nginx
```

Meaning

```
my-volume
     │
     ▼
/app/data (inside container)
```

---

# Bind Mount vs Volume

## Bind Mount

```bash
docker run -v C:\Projects:/app nginx
```

Uses a folder on your computer.

---

## Named Volume

```bash
docker run -v my-volume:/app nginx
```

Managed completely by Docker.

---

# Anonymous Volume

```bash
docker run -v /app/data nginx
```

Docker automatically creates a random volume.

---

# Remove a Volume

```bash
docker volume rm my-volume
```

---

# Remove Unused Volumes

```bash
docker volume prune
```

---

# Volume Workflow

```
Create Volume
      │
      ▼
Attach to Container
      │
      ▼
Store Data
      │
      ▼
Delete Container
      │
      ▼
Data Still Exists
```

---

# Common Commands

| Command | Purpose |
|----------|---------|
| docker volume ls | List volumes |
| docker volume create my-volume | Create volume |
| docker volume inspect my-volume | View details |
| docker volume rm my-volume | Delete volume |
| docker volume prune | Delete unused volumes |
| docker run -v my-volume:/app nginx | Attach volume |

---

# Memory Trick

```
Container = Temporary

Volume = Permanent
```
