# 📘 Day 11 – Linux Ownership & Group Management


## 🎯 Objective
To practice Linux file ownership, group management, and permission control using chown, chgrp, and recursive operations.

---

## ✅ Task 1: Understanding Ownership

### Command
```bash
ls -l
```

### Format
```
-rw-r--r-- 1 owner group size date filename
```

### Difference Between Owner and Group

- Owner → The user who created or owns the file.
- Group → A collection of users who share access permissions.
- Owner has primary control.
- Group allows shared access.

---

## ✅ Task 2: Basic chown Operations

### Create File
```bash
touch devops-file.txt
```

### Check Owner
```bash
ls -l devops-file.txt
```

### Change Owner
```bash
sudo chown tokyo devops-file.txt
sudo chown berlin devops-file.txt
```

### Verify
```bash
ls -l devops-file.txt
```

---

## ✅ Task 3: Basic chgrp Operations

### Create File
```bash
touch team-notes.txt
```

### Create Group
```bash
sudo groupadd heist-team
```

### Change Group
```bash
sudo chgrp heist-team team-notes.txt
```

### Verify
```bash
ls -l team-notes.txt
```

---

## ✅ Task 4: Change Owner & Group Together

### Create File
```bash
touch project-config.yaml
```

### Change Owner and Group
```bash
sudo chown professor:heist-team project-config.yaml
```

### Create Directory
```bash
mkdir app-logs
```

### Change Directory Ownership
```bash
sudo chown berlin:heist-team app-logs
```

---

## ✅ Task 5: Recursive Ownership Change

### Create Structure
```bash
mkdir -p heist-project/vault
mkdir -p heist-project/plans
touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf
```

### Create Group
```bash
sudo groupadd planners
```

### Change Ownership Recursively
```bash
sudo chown -R professor:planners heist-project/
```

### Verify
```bash
ls -lR heist-project/
```

---

## ✅ Task 6: Practice Challenge

### Create Users
```bash
sudo useradd tokyo
sudo useradd berlin
sudo useradd nairobi
```

### Create Groups
```bash
sudo groupadd vault-team
sudo groupadd tech-team
```

### Create Directory & Files
```bash
mkdir bank-heist
touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt
```

### Set Different Ownership
```bash
sudo chown tokyo:vault-team bank-heist/access-codes.txt
sudo chown berlin:tech-team bank-heist/blueprints.pdf
sudo chown nairobi:vault-team bank-heist/escape-plan.txt
```

### Verify
```bash
ls -l bank-heist/
```

---

## 📚 What I Learned

- Linux file ownership structure
- Difference between user and group
- How to use chown and chgrp
- Recursive ownership changes
- Practical user & group management

---

**Status: ✅ Day 11 Completed Successfully**
