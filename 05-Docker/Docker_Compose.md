# 🐳 Docker Compose

Docker Compose allows you to run multiple containers using a single YAML file.

Instead of typing many `docker run` commands, you describe everything inside a `docker-compose.yml` (or `compose.yml`) file.

---

# Why Docker Compose?

Imagine a web application with:

- Frontend
- Backend
- Database

Without Compose:

```bash
docker run frontend
docker run backend
docker run mysql
```

With Compose:

```bash
docker compose up
```

Everything starts automatically.

---

# Basic Structure

```yaml
services:
  web:
    image: nginx

  database:
    image: mysql
```

---

# Example

```yaml
services:
  frontend:
    image: nginx
    ports:
      - "3000:80"

  backend:
    image: node:20
    ports:
      - "5000:5000"

  database:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123
```

---

# Start Services

```bash
docker compose up
```

Background mode

```bash
docker compose up -d
```

---

# Stop Services

```bash
docker compose down
```

---

# View Running Services

```bash
docker compose ps
```

---

# View Logs

```bash
docker compose logs
```

Follow logs

```bash
docker compose logs -f
```

---

# Rebuild Images

```bash
docker compose build
```

---

# Restart Services

```bash
docker compose restart
```

---

# Stop Services

```bash
docker compose stop
```

---

# Start Existing Services

```bash
docker compose start
```

---

# Pull Latest Images

```bash
docker compose pull
```

---

# Build and Start

```bash
docker compose up --build
```

---

# Execute Commands

```bash
docker compose exec backend bash
```

---

# Remove Everything

```bash
docker compose down -v
```

Also removes volumes created by Compose.

---

# Common Commands

| Command | Purpose |
|----------|---------|
| docker compose up | Start services |
| docker compose up -d | Detached mode |
| docker compose down | Stop services |
| docker compose ps | Running services |
| docker compose logs | View logs |
| docker compose restart | Restart |
| docker compose build | Build images |
| docker compose exec service bash | Open terminal |

---

# Memory Trick

```
Docker Run
↓

One Container

Docker Compose
↓

Many Containers
```
