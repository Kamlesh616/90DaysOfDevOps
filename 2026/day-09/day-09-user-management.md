# 👥 Linux User & Group Management Practice

## 📌 Objective
Practice Linux user management, group management, permissions, and shared directories.

---

# 🧩 Task 1: Create Users

## 👤 Users Created:
- tokyo
- berlin
- professor

## 🔹 Create Users with Home Directory

```bash
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
```

## 🔹 Set Passwords

```bash
sudo passwd tokyo
sudo passwd berlin
sudo passwd professor
```

## ✅ Verification

Check users:

```bash
cat /etc/passwd
```

Check home directories:

```bash
ls /home
```

✔ Users successfully created.

---

# 👥 Task 2: Create Groups

## 🛠 Groups Created:
- developers
- admins

## 🔹 Create Groups

```bash
sudo groupadd developers
sudo groupadd admins
```

## ✅ Verification

```bash
cat /etc/group
```

✔ Groups successfully created.

---

# 🔄 Task 3: Assign Users to Groups

## 🔹 Assign tokyo → developers

```bash
sudo usermod -aG developers tokyo
```

## 🔹 Assign berlin → developers + admins

```bash
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
```

## 🔹 Assign professor → admins

```bash
sudo usermod -aG admins professor
```

## ✅ Verify Group Membership

```bash
groups tokyo
groups berlin
groups professor
```

✔ Users assigned to correct groups.

---

# 📁 Task 4: Shared Directory

## 🔹 Create Directory

```bash
sudo mkdir -p /opt/dev-project
```

## 🔹 Set Group Owner

```bash
sudo chown :developers /opt/dev-project
```

## 🔹 Set Permissions (775)

```bash
sudo chmod 775 /opt/dev-project
```

## 🔹 Verify Permissions

```bash
ls -ld /opt/dev-project
```

Expected permission:

```
drwxrwxr-x
```

## 🔹 Test File Creation

Switch user:

```bash
su - tokyo
touch /opt/dev-project/test1.txt
```

```bash
su - berlin
touch /opt/dev-project/test2.txt
```

✔ Files created successfully.

---

# 🏢 Task 5: Team Workspace

## 🔹 Create User

```bash
sudo useradd -m nairobi
sudo passwd nairobi
```

## 🔹 Create Group

```bash
sudo groupadd project-team
```

## 🔹 Add Users to Group

```bash
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

## 🔹 Create Workspace Directory

```bash
sudo mkdir -p /opt/team-workspace
```

## 🔹 Set Group & Permissions

```bash
sudo chown :project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
```

## 🔹 Test as nairobi

```bash
su - nairobi
touch /opt/team-workspace/teamfile.txt
```

✔ File created successfully.

---

# 🧠 What I Learned

- How to create users in Linux
- How to create and manage groups
- How to assign users to multiple groups
- How to set directory ownership
- How to configure permissions (775)
- How shared directories work in Linux

---

# 🎯 Conclusion

Successfully completed Linux user and group management tasks including:

- User creation
- Group creation
- Group assignment
- Shared directory configuration
- Permission management
- Team workspace setup

This practice improved my Linux administration skills for DevOps.

---

## 👨‍💻 Author

Kamlesh Rathod  
DevOps Learner
