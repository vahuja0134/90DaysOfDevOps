# Linux Commands Cheat Sheet for DevOps

## 1. Navigation & File System

| Command                 | Purpose                     |
| ----------------------- | --------------------------- |
| `pwd`                   | Show current directory      |
| `ls -la`                | List files with permissions |
| `cd <dir>`              | Change directory            |
| `mkdir <dir>`           | Create directory            |
| `touch file.txt`        | Create file                 |
| `cp src dest`           | Copy files                  |
| `mv src dest`           | Move or rename files        |
| `rm -rf <dir>`          | Remove files/directories    |
| `find / -name file.txt` | Find files                  |
| `locate file.txt`       | Quickly locate files        |
| `tree`                  | Show directory structure    |

---

## 2. File Content & Text Processing

| Command                      | Purpose           |
| ---------------------------- | ----------------- |
| `cat file.txt`               | Display file      |
| `less file.txt`              | Read large file   |
| `head -10 file.txt`          | First 10 lines    |
| `tail -10 file.txt`          | Last 10 lines     |
| `tail -f app.log`            | Follow logs live  |
| `grep "error" app.log`       | Search text       |
| `sort file.txt`              | Sort data         |
| `uniq file.txt`              | Remove duplicates |
| `cut -d: -f1 file.txt`       | Extract fields    |
| `awk '{print $1}' file.txt`  | Process columns   |
| `sed 's/old/new/g' file.txt` | Replace text      |
| `wc -l file.txt`             | Count lines       |

---

## 3. Process Management

| Command       | Purpose                     |
| ------------- | --------------------------- |
| `ps aux`      | Show processes              |
| `ps -ef`      | Full process details        |
| `top`         | Real-time process monitor   |
| `htop`        | Interactive process monitor |
| `pstree`      | Process hierarchy           |
| `pgrep nginx` | Find process by name        |
| `kill PID`    | Stop process                |
| `kill -9 PID` | Force stop process          |
| `jobs`        | Show background jobs        |
| `bg`          | Run job in background       |
| `fg`          | Bring job to foreground     |

---

## 4. Service Management (systemd)

| Command                               | Purpose              |
| ------------------------------------- | -------------------- |
| `systemctl status nginx`              | Service status       |
| `systemctl start nginx`               | Start service        |
| `systemctl stop nginx`                | Stop service         |
| `systemctl restart nginx`             | Restart service      |
| `systemctl reload nginx`              | Reload configuration |
| `systemctl enable nginx`              | Start at boot        |
| `systemctl disable nginx`             | Disable at boot      |
| `systemctl list-units --type=service` | Running services     |
| `systemctl --failed`                  | Failed services      |
| `systemctl list-unit-files`           | Installed services   |

---

## 5. Logs & Troubleshooting

| Command                     | Purpose            |
| --------------------------- | ------------------ |
| `journalctl`                | View system logs   |
| `journalctl -xe`            | Recent errors      |
| `journalctl -u docker`      | Service logs       |
| `journalctl -f`             | Live logs          |
| `dmesg`                     | Kernel messages    |
| `tail -f /var/log/syslog`   | Follow system log  |
| `tail -f /var/log/messages` | View system events |

---

## 6. Memory Monitoring

| Command             | Purpose                |
| ------------------- | ---------------------- |
| `free -h`           | Memory usage           |
| `vmstat`            | Memory and CPU stats   |
| `top`               | Live memory monitoring |
| `cat /proc/meminfo` | Detailed memory info   |

---

## 7. CPU Monitoring

| Command  | Purpose                    |
| -------- | -------------------------- |
| `top`    | CPU usage                  |
| `htop`   | Interactive CPU monitoring |
| `lscpu`  | CPU information            |
| `uptime` | Load averages              |
| `mpstat` | CPU statistics             |

---

## 8. Disk Management

| Command    | Purpose             |
| ---------- | ------------------- |
| `df -h`    | Filesystem usage    |
| `du -sh *` | Directory sizes     |
| `lsblk`    | Block devices       |
| `fdisk -l` | Disk partitions     |
| `mount`    | Mounted filesystems |
| `umount`   | Unmount filesystem  |

---

## 9. Networking

| Command                   | Purpose             |
| ------------------------- | ------------------- |
| `ip addr`                 | Show IP addresses   |
| `ip route`                | Show routing table  |
| `ping google.com`         | Connectivity test   |
| `curl https://google.com` | HTTP request        |
| `wget URL`                | Download files      |
| `dig google.com`          | DNS lookup          |
| `nslookup google.com`     | DNS resolution      |
| `traceroute google.com`   | Network path        |
| `ss -tulnp`               | Open ports          |
| `netstat -tulnp`          | Network connections |
| `hostname -I`             | Local IP address    |

---

## 10. User & Permission Management

| Command                | Purpose             |
| ---------------------- | ------------------- |
| `whoami`               | Current user        |
| `id`                   | User and group IDs  |
| `groups`               | User groups         |
| `useradd`              | Create user         |
| `passwd`               | Change password     |
| `chmod 755 file`       | Change permissions  |
| `chown user:user file` | Change ownership    |
| `umask`                | Default permissions |

---

## 11. Package Management

### Ubuntu/Debian

| Command             | Purpose              |
| ------------------- | -------------------- |
| `apt update`        | Update package index |
| `apt upgrade`       | Upgrade packages     |
| `apt install nginx` | Install package      |
| `apt remove nginx`  | Remove package       |

### RHEL/CentOS

| Command             | Purpose         |
| ------------------- | --------------- |
| `yum install nginx` | Install package |
| `yum update`        | Update packages |
| `dnf install nginx` | Install package |

---

## 12. Archive & Compression

| Command                    | Purpose         |
| -------------------------- | --------------- |
| `tar -cvf archive.tar dir` | Create archive  |
| `tar -xvf archive.tar`     | Extract archive |
| `gzip file`                | Compress file   |
| `gunzip file.gz`           | Decompress file |
| `zip -r archive.zip dir`   | Create zip      |
| `unzip archive.zip`        | Extract zip     |

---

## 13. SSH & Remote Access

| Command                   | Purpose            |
| ------------------------- | ------------------ |
| `ssh user@host`           | Connect to server  |
| `scp file user@host:/tmp` | Copy file remotely |
| `ssh-keygen`              | Generate SSH key   |
| `ssh-copy-id user@host`   | Copy SSH key       |

---

## 14. System Information

| Command       | Purpose               |
| ------------- | --------------------- |
| `uname -a`    | Kernel information    |
| `hostnamectl` | OS and host details   |
| `uptime`      | Uptime and load       |
| `date`        | Current date/time     |
| `env`         | Environment variables |
| `history`     | Command history       |

---

## 15. Useful /proc Commands

| Command              | Purpose        |
| -------------------- | -------------- |
| `cat /proc/cpuinfo`  | CPU details    |
| `cat /proc/meminfo`  | Memory details |
| `cat /proc/1/status` | PID 1 details  |
| `cat /proc/version`  | Kernel version |

---

# Most Important DevOps Troubleshooting Commands

```bash
ps aux
top
htop
systemctl status <service>
journalctl -u <service>
tail -f logfile
df -h
free -h
ip addr
ss -tulnp
curl URL
ping host
dig domain
find /
grep
```

# Troubleshooting Flow

## Service Down

```bash
systemctl status nginx
journalctl -u nginx
```

## High CPU

```bash
top
ps aux --sort=-%cpu
```

## High Memory

```bash
free -h
ps aux --sort=-%mem
```

## Disk Full

```bash
df -h
du -sh *
```

## Network Issue

```bash
ip addr
ping google.com
curl https://google.com
```

## DNS Issue

```bash
dig google.com
nslookup google.com
```
