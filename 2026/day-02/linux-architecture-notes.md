Here's a single, well-structured **Linux Architecture, Processes, and systemd** note that combines everything into one document and is ideal for a DevOps beginner.

# Linux Architecture, Processes, and systemd

## 1. Linux Architecture Overview

Linux follows a layered architecture where each layer has a specific responsibility.

```text
+----------------------------------+
| User Applications                |
| (Docker, Nginx, Python, Firefox) |
+----------------------------------+
| Shell (Bash, Zsh)                |
+----------------------------------+
| System Libraries                 |
| (glibc, libc, etc.)              |
+----------------------------------+
| Linux Kernel                     |
+----------------------------------+
| Hardware                         |
| (CPU, RAM, Disk, Network)        |
+----------------------------------+
```

### Hardware

The physical components of a computer system.

Examples:

* CPU
* RAM
* SSD/HDD
* Network Interface Card (NIC)
* Keyboard and Mouse

---

### Kernel

The kernel is the heart of Linux and runs in privileged mode.

Responsibilities:

* Process Management
* Memory Management
* Device Management
* File System Management
* Network Management
* Security and Permissions

Examples:

* Allocates CPU time to processes
* Manages RAM usage
* Controls disks and network interfaces

---

### System Libraries

System libraries provide functions that applications use to interact with the kernel.

Examples:

* glibc
* libc

Applications use libraries which internally make system calls to communicate with the kernel.

---

### Shell

The shell is a command interpreter that acts as an interface between the user and the operating system.

Popular Shells:

* Bash
* Zsh
* Fish

Example:

```bash
ls -l
```

Flow:

```text
User
 ↓
Shell
 ↓
Kernel
 ↓
Hardware
```

---

### User Space

User space contains all applications and utilities used by users.

Examples:

* Docker
* Nginx
* Vim
* Python
* Firefox

Applications cannot directly access hardware. They communicate with the kernel using **System Calls**.

---

## User Space vs Kernel Space

### User Space

* Applications run here.
* Limited privileges.
* Cannot directly access hardware.
* Safer because application failures usually do not crash the system.

### Kernel Space

* Linux Kernel runs here.
* Full access to hardware and system resources.
* Handles CPU, memory, networking, and storage operations.

Communication between User Space and Kernel Space happens through **System Calls**.

```text
Application
     ↓
System Call
     ↓
Kernel
     ↓
Hardware
```

---

## Linux Architecture Flow Example

Command:

```bash
cat file.txt
```

Execution Flow:

```text
User
 ↓
Shell (Bash)
 ↓
System Libraries
 ↓
System Call
 ↓
Kernel
 ↓
Disk (Hardware)
 ↓
Kernel
 ↓
Shell
 ↓
Output on Screen
```

---

## 2. Boot Process Overview

Understanding booting helps in troubleshooting server startup issues.

1. BIOS/UEFI starts.
2. Bootloader (GRUB) loads.
3. Linux Kernel loads into memory.
4. Kernel initializes hardware.
5. Kernel starts PID 1 (systemd).
6. systemd starts services and reaches the target state.

Example services started during boot:

* SSH
* Networking
* Docker
* Nginx

---

## 3. Processes in Linux

### What is a Process?

A process is a running instance of a program.

Example:

```bash
firefox
```

Launching Firefox creates one or more processes.

Each process has:

* PID (Process ID)
* PPID (Parent Process ID)
* State
* Memory usage
* CPU usage

---

### Parent and Child Processes

Every process is created by another process.

Example:

```text
bash
 └── python app.py
```

Here:

* Bash = Parent
* Python = Child

View process hierarchy:

```bash
pstree
```

---

### Process Creation

Linux primarily uses:

#### fork()

Creates a copy of the parent process.

#### exec()

Loads a new program into the process.

Example:

```text
Shell
  ↓ fork()
Child Process
  ↓ exec()
Runs command
```

---

## 4. Process States

### Running (R)

Currently executing on the CPU.

### Sleeping (S)

Waiting for an event.

Examples:

* Waiting for keyboard input
* Waiting for network response

### Uninterruptible Sleep (D)

Waiting for hardware operations.

Example:

* Disk I/O

### Stopped (T)

Paused by user or signal.

Example:

```bash
Ctrl + Z
```

### Zombie (Z)

Process has completed execution but the parent process has not collected its exit status.

Characteristics:

* Uses almost no memory
* Indicates poor process cleanup

View zombie processes:

```bash
ps aux | grep Z
```

---

## 5. Process Scheduling

The Linux Scheduler decides:

* Which process runs
* For how long
* On which CPU core

Goals:

* Fair CPU allocation
* Maximum performance
* System responsiveness

Useful command:

```bash
top
```

Shows:

* CPU usage
* Memory usage
* Running processes

---

## 6. Understanding PID 1

PID 1 is the first userspace process started by the kernel.

On modern Linux systems:

```bash
systemd
```

usually runs as PID 1.

Check:

```bash
ps -p 1
```

Output:

```text
PID  COMMAND
1    systemd
```

If PID 1 fails, the system becomes unstable because all services depend on it.

---

## 7. What is systemd?

systemd is the initialization system and service manager used by most modern Linux distributions.

Responsibilities:

* Start services
* Stop services
* Restart services
* Monitor services
* Manage boot process
* Manage dependencies
* Collect logs

Why it matters:

* Automatically restarts failed services
* Speeds up system boot
* Simplifies service management
* Centralizes logging

---

## 8. systemd Units

Everything in systemd is represented by a unit.

### Service Units

Examples:

```text
nginx.service
docker.service
ssh.service
```

### Target Units

Group multiple services together.

Example:

```text
multi-user.target
```

### Timer Units

Used like cron jobs.

Example:

```text
backup.timer
```

---

## 9. Essential systemd Commands

Check service status:

```bash
systemctl status nginx
```

Start service:

```bash
systemctl start nginx
```

Stop service:

```bash
systemctl stop nginx
```

Restart service:

```bash
systemctl restart nginx
```

Enable service at boot:

```bash
systemctl enable nginx
```

Disable service:

```bash
systemctl disable nginx
```

List active services:

```bash
systemctl list-units --type=service
```

---

## 10. Logs and journald

systemd includes a logging service called **journald**.

View all logs:

```bash
journalctl
```

View service logs:

```bash
journalctl -u nginx
```

View recent errors:

```bash
journalctl -xe
```

Follow logs in real time:

```bash
journalctl -f
```

This is one of the most important troubleshooting tools for DevOps engineers.

---

## 11. Five Linux Commands Used Daily

```bash
ps aux
```

View running processes.

```bash
top
```

Monitor CPU and memory usage.

```bash
systemctl
```

Manage services.

```bash
journalctl
```

View logs.

```bash
kill <PID>
```

Terminate processes.

---

## 12. Additional Useful Commands

```bash
uname -a
```

Display kernel information.

```bash
free -h
```

Show memory usage.

```bash
df -h
```

Show disk usage.

```bash
uptime
```

Display system uptime and load.

```bash
pstree
```

Display process hierarchy.

---

## 13. Why DevOps Engineers Must Learn This

Understanding Linux architecture, processes, and systemd helps you:

* Troubleshoot crashed services
* Analyze CPU and memory issues
* Investigate application failures
* Understand the Linux boot process
* Debug system startup issues
* Read and analyze logs efficiently
* Manage production servers confidently

Most cloud servers, containers, Docker hosts, and Kubernetes worker nodes run Linux, making these concepts fundamental for every DevOps engineer.

### DevOps Mental Model

```text
Hardware
   ↓
Kernel
   ↓
systemd (PID 1)
   ↓
Services (Docker, Nginx, SSH)
   ↓
Applications
```

Understanding this flow makes Linux troubleshooting significantly easier and forms the foundation of DevOps, Cloud Computing, Docker, and Kubernetes.

This version is comprehensive enough for learning, revision, interview preparation, and future troubleshooting as you progress in your DevOps journey.
