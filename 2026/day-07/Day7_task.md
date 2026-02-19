# 🐧 Linux Fundamentals – DevOps Practice

## 📌 Objective
This project is created to practice basic Linux commands and understand important Linux directories for DevOps.

---

# 📂 Linux File System Hierarchy

## 1️⃣ / (Root Directory)
- This is the starting point of Linux.
- All files and folders come under this directory.

---

## 2️⃣ /home
- Stores normal users' home directories.
- Example:
  /home/kamlesh

---

## 3️⃣ /root
- Home directory of root (admin) user.
- Only system administrator can access.

---

## 4️⃣ /etc
- Stores configuration files.
- Example:
  - SSH config
  - Network config
  - Service settings

---

## 5️⃣ /var/log
- Stores log files.
- Used for troubleshooting and debugging.
- Very important for DevOps.

Example:
  /var/log/syslog
  /var/log/auth.log

---

## 6️⃣ /tmp
- Stores temporary files.
- Automatically cleaned by system.

---

# 📦 Important Binary Directories

## 7️⃣ /bin
- Contains essential system commands.
- Example:
  ls
  cp
  mv
  rm

---

## 8️⃣ /usr/bin
- Contains user command binaries.
- Most applications are stored here.

---

# ⚡ Process Management Practice

## 🔎 List Running Processes

```bash
ps aux | head -5
```

- Shows currently running processes
- Displays PID, CPU usage, user

---

## 🛠 Check SSH Service

```bash
ps aux | grep ssh
```

or

```bash
systemctl status ssh
```

- Shows if SSH service is running
- Displays service status

---

# 🧠 What I Learned
- Linux directory structure
- Process monitoring
- Service checking
- Log file importance
- Basic troubleshooting

---

# 🚀 Why This is Important for DevOps
Linux is the base of:
- Cloud
- CI/CD
- Docker
- Kubernetes
- Server Management

Strong Linux basics = Strong DevOps foundation.

---

## 👨‍💻 Author
Kamlesh Rathod  
DevOps Learner
