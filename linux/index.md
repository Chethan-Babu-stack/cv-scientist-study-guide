# Essential Linux Commands for Interviews (Updated)

This guide covers the most important Linux commands commonly asked about in technical interviews—particularly useful for data engineers, ML/AI engineers, and system developers.

---

## 1. 📁 File & Directory Management

| Command | Description |
|--------|-------------|
| `ls -l` | List directory contents in long format (shows permissions, owner, size, date) |
| `cd <dir>` | Change to directory `<dir>` |
| `pwd` | Print the current working directory |
| `mkdir <dir>` | Create a new directory |
| `rm <file>` | Delete file |
| `rm -r <dir>` | Delete directory recursively |
| `cp <src> <dest>` | Copy file or directory |
| `mv <src> <dest>` | Move or rename file or directory |
| `touch <file>` | Create a new, empty file |

---

## 2. 📄 File Viewing & Editing

| Command | Description |
|--------|-------------|
| `cat <file>` | View file contents |
| `less <file>` | View large files with paging |
| `head -n 10 <file>` | View first 10 lines |
| `tail -n 10 <file>` | View last 10 lines |
| `tail -f <file>` | Live view of log files |
| `grep "pattern" <file>` | Search for a pattern inside a file |
| `nano <file>` | Easy-to-use text editor |
| `vim <file>` | Advanced text editor (modal-based) |

---

## 3. 🔐 Permissions & Ownership

| Command | Description |
|--------|-------------|
| `ls -l` | Shows file permissions |
| `chmod +x <file>` | Make file executable |
| `chmod 755 <file>` | Set read-write-execute for owner, read-execute for others |
| `chown user:group <file>` | Change ownership of file to `user` and group to `group` |

---

## 4. 📊 Disk & File System Usage

| Command | Description |
|--------|-------------|
| `df -h` | Show mounted file systems, their sizes, usage, and mount points. Human-readable format (`-h`).<br>**Useful for checking available disk space.** |
| `du -sh <dir>` | Show total size of a directory. `-s` for summary, `-h` for human-readable.<br>**Useful for checking how much space a folder is using.** |
| `du -h --max-depth=1` | Show size of each subfolder (depth 1) in the current directory |

---

## 5. 🧠 Process & Resource Monitoring

| Command | Description |
|--------|-------------|
| `top` | Display dynamic real-time view of system processes |
| `htop` | Enhanced `top` (needs to be installed) |
| `ps aux` | View all running processes |
| `kill <pid>` | Terminate process by PID |
| `kill -9 <pid>` | Force kill process |
| `free -h` | Display memory usage (RAM + Swap) |
| `uptime` | Show system uptime and load average |

---

## 6. 🌐 Networking

| Command | Description |
|--------|-------------|
| `ping <host>` | Test connection to a host |
| `curl <url>` | Fetch data from a URL |
| `wget <url>` | Download a file from the web |
| `ip a` | Show network interfaces and IP addresses |
| `netstat -tuln` | Show open ports and listening services |

---

## 7. 🔁 File Sync & Transfer

### 🔄 `rsync` — Efficient File Synchronization
| Command | Description |
|--------|-------------|
| `rsync -avh <src> <dest>` | Archive mode, verbose, human-readable |
| `rsync -avz <src> <user@host>:<dest>` | Sync files to remote host via SSH |
| `rsync --progress <src> <dest>` | Show progress while syncing |
| `rsync -a --delete <src> <dest>` | Sync and delete files in dest that are not in source |

### ☁️ `rclone` — Cloud Storage Sync
| Command | Description |
|--------|-------------|
| `rclone config` | Setup remote cloud storage |
| `rclone ls remote:` | List files in remote |
| `rclone copy <src> remote:<dest>` | Copy from local to cloud |
| `rclone sync <src> remote:<dest>` | Sync directory to remote (delete extra files) |
| `rclone check <local> <remote>` | Compare local vs remote files |
| `rclone mount remote:path /mnt/remote` | Mount remote cloud drive as local FS (advanced) |

---

## 8. 🖥️ Using `screen` — Background Terminal Sessions

| Command | Description |
|--------|-------------|
| `screen` | Start a new screen session |
| `screen -S <name>` | Start a named session |
| `screen -ls` | List running screen sessions |
| `screen -r <name>` | Reattach to a session |
| `Ctrl+A` then `D` | Detach from session |
| `exit` | Exit screen session cleanly |
| `screen -L` | Start with logging enabled |
| `screen -Logfile output.log` | Log output to a specific file |

---

## 9. 📦 Package Management

### Ubuntu/Debian
| Command | Description |
|--------|-------------|
| `sudo apt update` | Update package list |
| `sudo apt upgrade` | Upgrade installed packages |
| `sudo apt install <package>` | Install a package |
| `sudo apt remove <package>` | Uninstall a package |

---

## 10. 👤 User Management

| Command | Description |
|--------|-------------|
| `whoami` | Show current user |
| `adduser <name>` | Add new user |
| `passwd` | Change user password |
| `su - <user>` | Switch to user |
| `id` | Show current UID, GID and groups |

---

