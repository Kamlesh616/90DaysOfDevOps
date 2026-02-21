# 🐚 Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## 🎯 Objective
Level up shell scripting skills by learning:
- `for` and `while` loops
- Command-line arguments (`$1`, `$#`, `$@`, `$0`)
- Installing packages via script
- Basic error handling

---

# ✅ Task 1 – For Loop

## 📄 File: `for_loop.sh`

```bash
#!/bin/bash

for fruit in Apple Banana Mango Orange Grapes
do
    echo "Fruit: $fruit"
done
```

### ▶ Run

```bash
chmod +x for_loop.sh
./for_loop.sh
```

---

## 📄 File: `count.sh`

```bash
#!/bin/bash

for i in {1..10}
do
    echo $i
done
```

---

# ✅ Task 2 – While Loop

## 📄 File: `countdown.sh`

```bash
#!/bin/bash

echo "Enter a number:"
read num

while [ $num -ge 0 ]
do
    echo $num
    num=$((num - 1))
done

echo "Done!"
```

---

# ✅ Task 3 – Command-Line Arguments

## 📄 File: `greet.sh`

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./greet.sh <name>"
else
    echo "Hello, $1!"
fi
```

### ▶ Run

```bash
./greet.sh Kamlesh
```

---

## 📄 File: `args_demo.sh`

```bash
#!/bin/bash

echo "Script name: $0"
echo "Total arguments: $#"
echo "All arguments: $@"
```

### ▶ Example Run

```bash
./args_demo.sh DevOps Linux Docker
```

---

# ✅ Task 4 – Install Packages via Script

## 📄 File: `install_packages.sh`

```bash
#!/bin/bash

# Check if script is run as root
if [ "$EUID" -ne 0 ]; then
    echo "Run as root"
    exit 1
fi

packages=(nginx curl wget)

for pkg in "${packages[@]}"
do
    if dpkg -s "$pkg" &> /dev/null; then
        echo "$pkg is already installed. Skipping."
    else
        echo "Installing $pkg..."
        apt update -y
        apt install -y "$pkg"
        echo "$pkg installed successfully."
    fi
done
```

### ▶ Run as Root

```bash
sudo -i
chmod +x install_packages.sh
./install_packages.sh
```

---

# ✅ Task 5 – Error Handling

## 📄 File: `safe_script.sh`

```bash
#!/bin/bash

set -e

mkdir /tmp/devops-test || echo "Directory already exists"

cd /tmp/devops-test || echo "Failed to enter directory"

touch test-file.txt || echo "Failed to create file"

echo "Script completed."
```

---

# 🧠 What I Learned

- `for` loops iterate over lists or ranges.
- `while` loops run until a condition becomes false.
- `$1`, `$#`, `$@`, `$0` help handle arguments.
- Scripts can automate package installation.
- `set -e` exits on error.
- `$EUID` helps verify root user.
- `||` handles command failure gracefully.

---

✅ Completed Day 17 – Shell Scripting (Loops, Arguments & Error Handling)
