# 📂 Linux File & Permission Management Practice

## 📌 Objective
Practice file creation, reading files, understanding permissions, and modifying file permissions in Linux.

---

# 🧩 Task 1: Create Files

## 🔹 Create Empty File

```bash
touch devops.txt
```

## 🔹 Create File with Content

```bash
echo "This is DevOps practice notes." > notes.txt
```

OR

```bash
cat > notes.txt
```

## 🔹 Create Script File

```bash
vim script.sh
```

Add content inside vim:

```bash
echo "Hello DevOps"
```

Save and exit.

## ✅ Verify Files

```bash
ls -l
```

✔ Files created successfully.

---

# 📖 Task 2: Read Files

## 🔹 Read notes.txt

```bash
cat notes.txt
```

## 🔹 View script.sh in Read-Only Mode

```bash
vim -R script.sh
```

## 🔹 First 5 Lines of /etc/passwd

```bash
head -5 /etc/passwd
```

## 🔹 Last 5 Lines of /etc/passwd

```bash
tail -5 /etc/passwd
```

✔ Successfully viewed file contents.

---

# 🔐 Task 3: Understand Permissions

Permission Format:

```
rwxrwxrwx
```

- First 3 → Owner
- Next 3 → Group
- Last 3 → Others

Values:
- r = 4
- w = 2
- x = 1

## 🔹 Check File Permissions

```bash
ls -l devops.txt notes.txt script.sh
```

### Example Output:

```
-rw-r--r-- devops.txt
-rw-r--r-- notes.txt
-rw-r--r-- script.sh
```

### Explanation:

- Owner → Read & Write
- Group → Read only
- Others → Read only
- No execute permission yet

---

# 🛠 Task 4: Modify Permissions

## 🔹 Make script.sh Executable

```bash
chmod +x script.sh
```

Run script:

```bash
./script.sh
```

✔ Output:
```
Hello DevOps
```

---

## 🔹 Make devops.txt Read-Only

```bash
chmod 444 devops.txt
```

✔ Now no one can write to it.

---

## 🔹 Set notes.txt to 640

```bash
chmod 640 notes.txt
```

Meaning:
- Owner → Read & Write
- Group → Read only
- Others → No permission

---

## 🔹 Create Directory project/ with 755

```bash
mkdir project
chmod 755 project
```

Meaning:
- Owner → rwx
- Group → r-x
- Others → r-x

## ✅ Verify After Changes

```bash
ls -l
```

---

# 🧪 Task 5: Test Permissions

## 🔹 Try Writing to Read-Only File

```bash
echo "Test" >> devops.txt
```

❌ Error:
```
Permission denied
```

---

## 🔹 Try Executing File Without Execute Permission

If execute permission removed:

```bash
./script.sh
```

❌ Error:
```
Permission denied
```

---

# 🧠 What I Learned

- How to create files in Linux
- How to read files using cat, head, tail
- How Linux permissions work (rwx)
- How to change permissions using chmod
- How to test and verify permission errors

---

# 🎯 Conclusion

Successfully completed Linux file and permission management tasks including:

- File creation
- Reading system files
- Understanding permission structure
- Modifying file permissions
- Testing access restrictions

This improved my Linux fundamentals for DevOps and system administration.

---

## 👨‍💻 Author

Kamlesh Rathod  
DevOps Learner
