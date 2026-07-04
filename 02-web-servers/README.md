# 🌐 Module 02 — Web Servers

Web servers are responsible for serving web content to clients over HTTP/HTTPS.

In modern DevOps environments, **Nginx** and **Apache HTTP Server** are the two most commonly deployed web servers.

---

## 📂 Module Contents

| File | Description |
|------|-------------|
| `nginx.md` | Nginx installation, management commands, configuration, logs, default files |
| `apache.md` | Apache HTTP Server management, configuration, logs, default files |

---

## Learning Objectives

After completing this module you should be able to:

- Install Apache and Nginx
- Manage services using `systemctl`
- Validate configuration before deployment
- Troubleshoot startup failures
- Locate configuration files
- Read production logs
- Understand default document roots
- Handle port conflicts between Apache and Nginx
- Access locally hosted websites inside WSL

---

## Production Note

Both Apache and Nginx are capable of serving static websites, acting as reverse proxies, and terminating SSL connections.

In production:

- **Nginx** is commonly used for high-performance reverse proxying and load balancing.
- **Apache** is widely used for dynamic web hosting, especially with PHP applications.

Many production environments even use **both together**, with Nginx acting as the frontend proxy and Apache serving backend requests.

---

🪟 *Next Phase: [03-Networking/](../03-Networking/) -> Moving on from Web servers to Understanding networking fundamentals (devices,protocols,models).*

