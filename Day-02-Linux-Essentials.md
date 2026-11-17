# 🐧 Linux Essentials – Complete Notes

\<p align="center">
&#x20; 🌟 \<b>My Linux Learning Journey\</b> 🌟
\</p>

Welcome to my Linux Essentials notes! 💻

These notes cover the basic Linux concepts and commands that are useful for beginners and DevOps learners.

## 📚 Table of Contents

1. 📁 Files and Directories
2. 🗂️ Linux Filesystem Hierarchy
3. 🔍 Finding and Viewing Files
4. 👤 Users and Groups
5. 🔐 File Ownership
6. 🛡️ Linux Permissions
7. ⚙️ chmod Command
8. 👥 chown and chgrp
9. 🔑 sudo and Root User
10. 🔄 Linux Processes
11. 📊 Process Inspection
12. 🚀 Foreground and Background Processes
13. 🛑 Process Signals
14. 🔧 Services and Daemons
15. ⚡ systemd and systemctl
16. 📝 systemd Unit Files
17. 📋 Logs with journalctl
18. 🎯 DevOps Linux Roadmap

---

## 📁 1. Files and Directories

### What is a File?

A file is used to store information such as text, images, videos and code.

### What is a Directory?

A directory is a folder used to store files and other directories.

### Important Commands

| Command | Description              |
| ------- | ------------------------ |
| `pwd`   | Shows current location   |
| `ls`    | Lists files and folders  |
| `cd`    | Changes directory        |
| `mkdir` | Creates a directory      |
| `touch` | Creates an empty file    |
| `cp`    | Copies files             |
| `mv`    | Moves or renames files   |
| `rm`    | Removes files            |
| `cat`   | Displays file content    |
| `less`  | Views files page by page |
| `head`  | Shows the first lines    |
| `tail`  | Shows the last lines     |

### 💡 Example

```bash
mkdir myfolder
cd myfolder
touch notes.txt
ls
```

---

## 🗂️ 2. Linux Filesystem Hierarchy

Linux starts with one main directory called `/` (root).

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/home`   | Normal users' home directories |
| `/root`   | Home directory of root user    |
| `/etc`    | Configuration files            |
| `/var`    | Changing data and logs         |
| `/tmp`    | Temporary files                |
| `/opt`    | Optional applications          |
| `/usr`    | Programs and libraries         |
| `/proc`   | Information about processes    |
| `/dev`    | Device files                   |

### 🧠 Remember

- `/etc` = Configuration
- `/var` = Changing data
- `/tmp` = Temporary files

---

## 🔍 3. Finding and Viewing Files

### Important Commands

```bash
find /var/log -name "*.log"
which java
cat application.log
less application.log
head application.log
tail application.log
tail -f application.log
```

💡 `tail -f` helps you watch new log entries live.

---

## 👤 4. Users and Groups

Linux is a multi-user operating system.

Different users can work on the same server.

### Commands

```bash
whoami
id
groups
```

- `whoami` – Shows the current username.
- `id` – Shows user and group IDs.
- `groups` – Shows the groups of the current user.

---

## 🔐 5. File Ownership

Every file has an owner and a group.

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 aditya developers 2048 app.conf
```

- `aditya` = Owner
- `developers` = Group

---

## 🛡️ 6. Linux Permissions

Linux has three basic permissions:

| Permission | Meaning |
| ---------- | ------- |
| `r`        | Read    |
| `w`        | Write   |
| `x`        | Execute |

Permissions are assigned to:

- 👤 User
- 👥 Group
- 🌍 Others

Example:

```text
rwxr-xr--
```

- User = `rwx`
- Group = `r-x`
- Others = `r--`

### 📂 Directory Permissions

- `r` = List directory contents
- `w` = Create or delete entries
- `x` = Enter or access the directory

---

## ⚙️ 7. chmod Command

The `chmod` command changes file permissions.

### Numeric Values

| Number | Permission |
| ------ | ---------- |
| 7      | `rwx`      |
| 6      | `rw-`      |
| 5      | `r-x`      |
| 4      | `r--`      |

Remember:

- Read = 4
- Write = 2
- Execute = 1

### Examples

```bash
chmod 755 deploy.sh
chmod 600 secret.key
chmod +x deploy.sh
```

---

## 👥 8. chown and chgrp

These commands change file ownership and group ownership.

```bash
sudo chown ubuntu:developers app.jar
sudo chgrp developers app.jar
```

- `chown` = Change owner.
- `chgrp` = Change group.

---

## 🔑 9. sudo and Root User

Linux has normal users and a special administrator account called `root`.

- Normal user = Limited permissions.
- Root user = Almost unrestricted access.

Use `sudo` to run commands with administrative privileges.

```bash
sudo systemctl restart nginx
```

---

## 🔄 10. Linux Processes

A program is a file stored on disk.

When we run that program, Linux creates a process.

- Program = Stored executable file.
- Process = Running instance of a program.
- PID = Process ID.

---

## 📊 11. Process Inspection

Useful commands:

```bash
ps
ps aux
top
htop
ps aux | grep java
```

Important details:

- PID = Process ID
- USER = Process owner
- CPU = CPU usage
- MEM = Memory usage
- COMMAND = Running command

---

## 🚀 12. Foreground and Background Processes

### Foreground Process

Runs directly in the terminal.

```bash
java -jar app.jar
```

### Background Process

Runs in the background.

```bash
java -jar app.jar &
```

Other commands:

```bash
jobs
fg
bg
```

---

## 🛑 13. Process Signals

The `kill` command sends a signal to a process.

```bash
kill 1234
kill -9 1234
```

- `SIGTERM` = Requests graceful termination.
- `SIGKILL` = Forces immediate termination.

💡 Avoid using `kill -9` unnecessarily.

---

## 🔧 14. Services and Daemons

A service is a program designed to run continuously or in the background.

Examples:

- Nginx
- MySQL
- Docker
- SSH
- Jenkins

Services are also called **daemons**.

---

## ⚡ 15. systemd and systemctl

`systemd` manages system services.

### Important Commands

```bash
systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl enable nginx
sudo systemctl disable nginx
```

### ⭐ Important Difference

- `start` = Starts the service now.
- `enable` = Configures the service to start automatically during boot.

---

## 📝 16. systemd Unit Files

A service configuration file can be created at:

```text
/etc/systemd/system/myapp.service
```

Example:

```ini
[Unit]
Description=My Spring Boot Application

[Service]
User=ubuntu
ExecStart=/usr/bin/java -jar /opt/myapp/app.jar
Restart=always

[Install]
WantedBy=multi-user.target
```

Important options:

- `User` = Which user runs the process?
- `ExecStart` = Which command starts the application?
- `Restart` = Should it restart after failure?
- `WantedBy` = When should it participate in startup?

---

## 📋 17. Logs with journalctl

Logs help us understand why a service failed.

### Commands

```bash
journalctl -u nginx
journalctl -u nginx -f
journalctl -u myapp -f
```

💡 `-f` helps watch logs live.

---

## 🎯 18. Complete DevOps Linux Roadmap

After learning these topics, you should be able to:

1. Connect to a Linux server using SSH.
2. Navigate the filesystem.
3. Find configuration and application files.
4. Check file permissions.
5. Change ownership and permissions.
6. Identify running processes.
7. Stop problematic processes.
8. Start and restart services.
9. Check application logs.

## 🚀 What's Next?

After building your Linux foundation, you can move towards:

- 🐳 Docker
- 🔧 Jenkins
- ☁️ AWS
- ☸️ Kubernetes
- 🔄 CI/CD

---

<p align="center">
  🌟 <b>Keep Learning | Keep Practicing | Keep Growing</b> 🌟
</p>

<p align="center">
  <b>Happy Learning! 🐧💻</b>
</p>
