# 🐚 Day 16 – Shell Scripting Basics

## 🎯 Objective
Start learning shell scripting fundamentals:
- Shebang (`#!/bin/bash`)
- Variables
- `echo`, `read`
- Basic `if-else` conditions

---

# ✅ Task 1 – Your First Script

## 📄 File: `hello.sh`

```bash
#!/bin/bash

echo "Hello, DevOps!"
```

### 🔹 Make Executable & Run

```bash
chmod +x hello.sh
./hello.sh
```

### 🔹 Output

```
Hello, DevOps!
```

### 🔹 What If Shebang Is Removed?

- Script may still run using default shell.
- But it may not use **bash specifically**.
- Some bash-specific features may fail.
- Shebang tells the system **which interpreter to use**.

---

# ✅ Task 2 – Variables

## 📄 File: `variables.sh`

```bash
#!/bin/bash

NAME="Kamlesh"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```

### 🔹 Run

```bash
chmod +x variables.sh
./variables.sh
```

### 🔹 Output

```
Hello, I am Kamlesh and I am a DevOps Engineer
```

---

## 🔹 Single Quotes vs Double Quotes

```bash
echo 'Hello $NAME'
echo "Hello $NAME"
```

### Output

```
Hello $NAME
Hello Kamlesh
```

### Difference:

- **Single quotes (' ')** → No variable expansion  
- **Double quotes (" ")** → Variables are expanded  

---

# ✅ Task 3 – User Input with read

## 📄 File: `greet.sh`

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Enter your favourite tool:"
read tool

echo "Hello $name, your favourite tool is $tool"
```

### 🔹 Run

```bash
chmod +x greet.sh
./greet.sh
```

---

# ✅ Task 4 – If-Else Conditions

---

## 📄 File: `check_number.sh`

```bash
#!/bin/bash

echo "Enter a number:"
read num

if [ "$num" -gt 0 ]; then
    echo "The number is Positive"
elif [ "$num" -lt 0 ]; then
    echo "The number is Negative"
else
    echo "The number is Zero"
fi
```

---

## 📄 File: `file_check.sh`

```bash
#!/bin/bash

echo "Enter filename:"
read filename

if [ -f "$filename" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

---

# ✅ Task 5 – Combine It All

## 📄 File: `server_check.sh`

```bash
#!/bin/bash

SERVICE="nginx"

echo "Do you want to check the status of $SERVICE? (y/n)"
read choice

if [ "$choice" = "y" ]; then
    status=$(systemctl is-active $SERVICE)

    if [ "$status" = "active" ]; then
        echo "$SERVICE is running."
    else
        echo "$SERVICE is not running."
    fi
else
    echo "Skipped."
fi
```

### 🔹 Run

```bash
chmod +x server_check.sh
./server_check.sh
```

---

# 🧠 What I Learned

- Shebang defines which shell executes the script.
- Variables store reusable data.
- `read` takes user input.
- `if-elif-else` controls decision making.
- `-f` checks file existence.
- Shell scripting helps automate DevOps tasks.

---

✅ Completed Day 16 – Shell Scripting Basics
```
