# 🔒 File Permissions & Ownership

In DevOps, securing configuration files and scripts is crucial. Linux manages this using **Read (r)**, **Write (w)**, and **Execute (x)** permissions for **User (u)**, **Group (g)**, and **Others (o)**.

## 👥 Ownership Management
| Command | Description | Example |
| :--- | :--- | :--- |
| `chmod` | Change file/directory access permissions | `chmod +x script.sh` *(make executable)* |
| `chown` | Change file/directory owner and group | `sudo chown nginx:nginx index.html` |
| `chgrp` | Change group ownership | `chgrp developers app.log` |

## 💡 Quick Permission Reference
* **Absolute (Numeric) Mode:**
  * `7` = Read + Write + Execute ($4 + 2 + 1$)
  * `6` = Read + Write ($4 + 2$)
  * `4` = Read Only ($4$)
* **Common DevOps Patterns:**
  * `chmod 755 script.sh` -> Owner can do everything; group/others can read and execute.
  * `chmod 600 id_rsa` -> Private SSH key: Only the owner can read/write (required by SSH).
