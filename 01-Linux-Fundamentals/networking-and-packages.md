# 🌐 Networking, Troubleshooting & Package Management

In DevOps, software installations and network troubleshooting are daily tasks. This module covers system updates, port inspections, and connectivity diagnostics.

## 📦 Package Management (Ubuntu/Debian Focus)
| Command | Description | Example |
| :--- | :--- | :--- |
| `sudo apt update` | Refresh the local package index with latest repositories | `sudo apt update` |
| `sudo apt upgrade` | Upgrade all installed packages to their newest versions | `sudo apt upgrade -y` |
| `sudo apt install` | Install a software package from the repository | `sudo apt install curl ufw git -y` |
| `sudo apt remove` | Remove an installed software package | `sudo apt remove apache2` |

## 🔍 Network Diagnostics & Connectivity
| Command | Description | Example |
| :--- | :--- | :--- |
| `ping` | Send ICMP ECHO_REQUEST to network hosts to check latency | `ping -c 4 8.8.8.8` |
| `curl` | Transfer data from or to a server (excellent for API testing) | `curl -I https://nginx.org` *(Fetches headers)* |
| `wget` | Non-interactive network downloader | `wget https://wordpress.org/latest.tar.gz` |
| `ss` / `netstat` | Investigate sockets and ports to see what is listening | `ss -tulpn` *(Shows active listening ports)* |
| `dig` / `nslookup` | Query DNS name servers for domain resolutions | `dig example.com A` |

## 🔀 I/O Redirection & Streams
| Operator | Description | Example |
| :--- | :--- | :--- |
| `\|` (Pipe) | Sends the output of command A as the input to command B | `ss -tulpn \| grep 80` *(Finds what is on port 80)* |
| `>` | Redirects output to a file (overwrites existing content) | `echo "Port 8080" > ports.conf` |
| `>>` | Redirects output to a file (appends to the end of the file) | `echo "Done!" >> deployment.log` |
