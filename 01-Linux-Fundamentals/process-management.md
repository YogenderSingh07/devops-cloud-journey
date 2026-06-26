# ⚙️ Linux Process Management & Monitoring

How to monitor system resources, view running services, and safely terminate processes.

## 📊 System Monitoring
| Command | Description | Example |
| :--- | :--- | :--- |
| `top` | Dynamic, real-time view of running processes | `top` |
| `htop` | Interactive, colorized process viewer (highly recommended) | `htop` |
| `ps` | Snapshot of current active processes | `ps aux` *(displays all user processes)* |
| `df` | Report file system disk space usage | `df -h` *(human-readable format)* |
| `free` | Display amount of free and used memory (RAM) | `free -m` *(in Megabytes)* |

## 🛑 Process Control
| Command | Description | Example |
| :--- | :--- | :--- |
| `kill` | Terminate a process by its Process ID (PID) | `kill 1234` |
| `kill -9` | Forcefully kill a stubborn process | `kill -9 1234` |
| `killall` | Kill processes by name | `killall nginx` |
| `bg` | Send a process to the background | `bg %1` |
| `fg` | Bring a background process to the foreground | `fg %1` |
| `&` | Run a command in the background immediately | `python3 app.py &` |
