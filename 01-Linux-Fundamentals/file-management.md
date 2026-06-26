# 📁 Linux File & Directory Management

## 📍 Navigation & Discovery
| Command | Description | Example |
| :--- | :--- | :--- |
| `pwd` | Print Working Directory (shows exactly where you are) | `pwd` |
| `ls` | List directory contents | `ls -la` *(shows hidden files & details)* |
| `cd` | Change directory | `cd /var/www/html` |
| `cd ..` | Move up one directory level | `cd ..` |

## 🛠️ Creation & Deletion
| Command | Description | Example |
| :--- | :--- | :--- |
| `mkdir` | Create a new directory | `mkdir -p project/src` *(creates parents)* |
| `touch` | Create an empty file or update timestamp | `touch index.html` |
| `rm` | Remove files or directories | `rm -rf old-files/` *(force recursive)* |
| `cp` | Copy files or directories | `cp config.conf config.conf.bak` |
| `mv` | Move or rename files/directories | `mv script.sh /usr/local/bin/` |

## 🔍 Viewing & Searching
| Command | Description | Example |
| :--- | :--- | :--- |
| `cat` | Concatenate and display file content | `cat /etc/nginx/nginx.conf` |
| `less` | View file content page-by-page (better for large files) | `less /var/log/nginx/error.log` |
| `head` | View the first N lines of a file | `head -n 15 app.log` |
| `tail` | View the last N lines of a file | `tail -f app.log` *(follows live updates)* |
| `grep` | Search for a specific pattern inside files | `grep "404" access.log` |
| `find` | Search for files in a directory hierarchy | `find . -name "*.sh"` |
