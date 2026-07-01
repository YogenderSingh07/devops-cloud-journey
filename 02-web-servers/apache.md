# 🛠 Apache HTTP Server Runbook

Apache HTTP Server (`apache2`) is one of the world's most widely used web servers.

It supports static websites, PHP applications, virtual hosts, SSL, reverse proxying, and more.

---

# Service Management

| Command | Purpose | DevOps Context |
|----------|----------|----------------|
| `sudo systemctl start apache2` | Start Apache | Initial deployment |
| `sudo systemctl stop apache2` | Stop Apache | Maintenance |
| `sudo systemctl restart apache2` | Restart service | Apply configuration changes |
| `sudo systemctl reload apache2` | Reload configuration | Zero-downtime configuration updates |
| `sudo systemctl status apache2` | Check service status | First troubleshooting step |
| `sudo systemctl enable apache2` | Auto-start at boot | Production servers |
| `sudo systemctl disable apache2` | Disable auto-start | Testing environments |

---

# Configuration Validation

Always validate configuration before restarting.

```bash
sudo apachectl configtest
```

Expected output:

```text
Syntax OK
```

Never restart production when configuration validation fails.

---

# Viewing Logs

### Access Log

```bash
sudo tail -f /var/log/apache2/access.log
```

Shows:

- Incoming requests
- HTTP methods
- Status codes

---

### Error Log

```bash
sudo tail -f /var/log/apache2/error.log
```

Useful for:

- Startup failures
- Module issues
- PHP errors
- SSL errors

---

# Configuration Files

Main configuration:

```text
/etc/apache2/apache2.conf
```

Virtual Hosts:

```text
/etc/apache2/sites-available/
```

Enabled sites:

```text
/etc/apache2/sites-enabled/
```

---

# Default Website Location (WSL)

Default document root:

```text
/var/www/html/
```

Example file:

```text
/var/www/html/index.html
```

Replace it with your own webpage.

Example:

```bash
sudo nano /var/www/html/index.html
```

---

# Accessing Apache Locally (WSL)

Start Apache

```bash
sudo systemctl start apache2
```

Visit

```
http://localhost
```

or

```
http://127.0.0.1
```

The Apache default page should load.

---

# Checking Apache Port

```bash
sudo ss -tulpn | grep apache2
```

or

```bash
sudo netstat -tulpn | grep apache2
```

Expected:

```
:80
```

---

# Port Conflict with Nginx

Apache and Nginx both use:

```
Port 80
```

If Nginx is already running:

```bash
sudo systemctl stop nginx
```

Then start Apache.

---

# Troubleshooting

## Apache won't start

```bash
sudo systemctl status apache2
```

Then

```bash
sudo journalctl -u apache2
```

---

## Configuration issue

```bash
sudo apachectl configtest
```

---

## Port already in use

```bash
sudo lsof -i :80
```

---

# Production Best Practices

✅ Validate configuration before restart

```bash
sudo apachectl configtest
```

✅ Prefer

```bash
reload
```

instead of

```bash
restart
```

whenever possible.

✅ Monitor

- access.log
- error.log

during deployments.

---
