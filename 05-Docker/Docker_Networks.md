# 🌐 Docker Networks

Docker Networks allow containers to communicate with each other.

Instead of using IP addresses, containers can communicate using their names.

---

# Why Networks?

Imagine two containers:

```
Frontend
      │
      ▼
Backend
      │
      ▼
Database
```

All three need to communicate.

Docker Networks make this possible.

---

# List Networks

```bash
docker network ls
```

Typical output

```
bridge
host
none
```

---

# Default Networks

## Bridge

Default network for containers.

Containers on the same bridge network can communicate.

---

## Host

Shares the host machine's network.

No network isolation.

---

## None

Container has no networking.

---

# Create a Network

```bash
docker network create my-network
```

---

# Run Container on Network

```bash
docker run -d \
--network my-network \
--name web \
nginx
```

---

Another container

```bash
docker run -d \
--network my-network \
--name api \
node
```

Now the containers can communicate.

Example:

```
http://api:5000
```

No IP address required.

---

# Inspect a Network

```bash
docker network inspect my-network
```

---

# Connect an Existing Container

```bash
docker network connect my-network container-name
```

---

# Disconnect a Container

```bash
docker network disconnect my-network container-name
```

---

# Remove a Network

```bash
docker network rm my-network
```

---

# Network Workflow

```
Create Network
      │
      ▼
Attach Containers
      │
      ▼
Containers Communicate
```

---

# Types of Networks

| Network | Purpose |
|----------|---------|
| bridge | Default container communication |
| host | Uses host's network |
| none | No networking |
| overlay | Multi-host communication (Docker Swarm) |
| macvlan | Container gets its own MAC/IP |

---

# Common Commands

| Command | Purpose |
|----------|---------|
| docker network ls | List networks |
| docker network create my-network | Create network |
| docker network inspect my-network | View details |
| docker network connect | Connect container |
| docker network disconnect | Disconnect container |
| docker network rm my-network | Remove network |

---

# Memory Trick

```
Volume
↓

Stores Data

Network
↓

Connects Containers

Compose
↓

Manages Multiple Containers
```

---

# Complete Docker Flow

```
Dockerfile
      │
      ▼
docker build
      │
      ▼
Image
      │
      ▼
docker compose up
      │
      ▼
Containers
      │
      ├──────────────┐
      ▼              ▼
Volumes         Networks
(Store Data)   (Communication)
```
