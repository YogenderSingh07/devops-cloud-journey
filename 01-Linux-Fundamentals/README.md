# 🐧 Linux Fundamentals & System Administration

Mastering the Linux operating system is the absolute baseline for any DevOps and Cloud Engineer. This directory contains my comprehensive documentation, cheat sheets, and practical lab notes on system administration, networking, and security.

---

## 🗺️ Learning Path Modules

To keep things organized and highly scannable, I have divided my Linux notes into distinct operational pillars:

### 📁 [1. File & Directory Management](./file-management.md)
*Core navigation, creating/deleting assets, and text processing/searching.*
* **Key Focus:** Fast navigation (`cd`, `pwd`), dynamic lookups (`find`, `grep`), and live log streaming (`tail -f`).

### 🔒 [2. Permissions & Ownership](./permissions-and-ownership.md)
*Securing configuration files, managing system users, and establishing access controls.*
* **Key Focus:** Numerical mode permissions (`755`, `600`), ownership assignment (`chown`), and securing critical DevOps assets like private SSH keys.

### ⚙️ [3. Process Management & Monitoring](./process-management.md)
*Resource monitoring, process lifecycle control, and real-time system performance analysis.*
* **Key Focus:** Tracking CPU/RAM usage (`top`, `htop`, `free`), disk allocation checks (`df -h`), and managing background processes (`&`, `bg`, `fg`).

### 🌐 [4. Networking, Troubleshooting & Packages](./networking-and-packages.md)
*DNS lookups, tracking listening ports, network streaming, and automated package distribution.*
* **Key Focus:** Port identification (`ss -tulpn`), API testing (`curl`), and stream pipeline manipulation (`|`, `>`).

---

## 🛠️ Hands-On Labs Completed

### Lab 1: Secure Remote Access (SSH Setup)
- Generated cryptographic SSH key pairs locally using `ssh-keygen -t ed25519`.
- Transferred public keys to target instances to configure passwordless, secure login.
- Modified `/etc/ssh/sshd_config` to strictly enforce key-based authentication.

### Lab 2: Network Port & Target Connectivity Verification
- Verified active daemon binding by piping socket stats to grep: `ss -tulpn | grep 80`.
- Inspected remote server responses and response headers over standard protocols using `curl -I`.

---

## ⚡ Essential Commands Cheat Sheet (Daily Drivers)

| Objective | Command | Real-World DevOps Context |
| :--- | :--- | :--- |
| **Check Active Daemons** | `ps aux \| grep nginx` | Verifying if a web server process is actively handling traffic. |
| **Audit Listening Ports** | `ss -tulpn` | Checking if your app or container bound properly to its port. |
| **Live Log Tailing** | `tail -f /var/log/syslog` | Monitoring system errors live during deployment failures. |
| **Fix Key Permissions** | `chmod 600 ~/.ssh/id_rsa` | Restricting private SSH key access so the client doesn't reject it. |
| **Storage Audit** | `df -h` | Diagnosing out-of-disk-space issues on application servers. |

---

🪟 *Next Phase: [02-web-servers/](../02-web-servers/) -> Moving from local system administration to managing live web servers (Nginx & Apache).*
