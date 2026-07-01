# 🚀 Nginx Runbook

Nginx (pronounced *Engine-X*) is a high-performance web server, reverse proxy, load balancer, and API gateway.

---

# Service Management

| Command | Purpose | DevOps Context |
|----------|----------|----------------|
| `sudo systemctl start nginx` | Start service | Start after deployment |
| `sudo systemctl stop nginx` | Stop service | Maintenance window |
| `sudo systemctl restart nginx` | Restart service | Apply configuration changes |
| `sudo systemctl reload nginx` | Reload configuration without downtime | Preferred in production |
| `sudo systemctl status nginx` | Check current status | First troubleshooting step |
| `sudo systemctl enable nginx` | Start automatically at boot | Production servers |
| `sudo systemctl disable nginx` | Disable auto-start | Testing environments |

---

# Configuration Validation

Always validate configuration before restarting.

```bash
sudo nginx -t
```

Expected output:

```text
syntax is ok
test is successful
```

Never restart production without passing this test.

---

# Viewing Logs

### Access Log

```bash
sudo tail -f /var/log/nginx/access.log
```

Shows:

- Client requests
- HTTP methods
- Status codes
- Response size

---

### Error Log

```bash
sudo tail -f /var/log/nginx/error.log
```

Useful for:

- Configuration errors
- Permission problems
- Backend failures
- SSL issues

---

# Configuration Files

Main configuration:

```text
/etc/nginx/nginx.conf
```

Site configurations:

```text
/etc/nginx/sites-available/
```

Enabled sites:

```text
/etc/nginx/sites-enabled/
```

---

# Default Website Location (WSL)

The default webpage is stored at

```text
/var/www/html/
```

Example:

```text
/var/www/html/index.nginx-debian.html
```

Replace or edit this file to display your own webpage.

Example:

```bash
sudo nano /var/www/html/index.nginx-debian.html
```

---

# Accessing Nginx Locally (WSL)

Start the server

```bash
sudo systemctl start nginx
```

Open your browser:

```
http://localhost
```

or

```
http://127.0.0.1
```

If Nginx is listening on port 80, the default welcome page should appear.

---

# Checking Which Port Nginx Uses

```bash
sudo ss -tulpn | grep nginx
```

or

```bash
sudo netstat -tulpn | grep nginx
```

Expected:

```
:80
```

---

# Port Conflict

Apache and Nginx both use:

```
Port 80
```

Only one service can bind to the port at a time.

If Apache is already running:

```bash
sudo systemctl stop apache2
```

Then start Nginx.

---

# Troubleshooting

## Service won't start

Check:

```bash
sudo systemctl status nginx
```

Then

```bash
sudo journalctl -u nginx
```

---

## Configuration error

```bash
sudo nginx -t
```

---

## Port already in use

```bash
sudo lsof -i :80
```

Find which process owns port 80.

---

# Production Best Practices

✅ Validate configuration before restart

```bash
sudo nginx -t
```

✅ Prefer

```bash
reload
```

instead of

```bash
restart
```

to avoid downtime.

✅ Monitor

- access.log
- error.log

during deployments.

---
