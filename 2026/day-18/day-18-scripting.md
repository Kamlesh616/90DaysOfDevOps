# 🐚 Day 18 – Shell Scripting: Functions & Intermediate Concepts

## 🎯 Objective
Write cleaner and safer shell scripts using:
- Functions
- Return values
- Local variables
- Strict mode (`set -euo pipefail`)
- Real-world scripting patterns

---

# ✅ Task 1 – Basic Functions

## 📄 File: `functions.sh`

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    sum=$(( $1 + $2 ))
    echo "Sum: $sum"
}

# Calling functions
greet "Kamlesh"
add 10 20
```

### ▶ Run

```bash
chmod +x functions.sh
./functions.sh
```

---

# ✅ Task 2 – Functions with System Checks

## 📄 File: `disk_check.sh`

```bash
#!/bin/bash

check_disk() {
    echo "Disk Usage:"
    df -h /
}

check_memory() {
    echo "Memory Usage:"
    free -h
}

main() {
    check_disk
    echo "----------------------"
    check_memory
}

main
```

---

# ✅ Task 3 – Strict Mode (`set -euo pipefail`)

## 📄 File: `strict_demo.sh`

```bash
#!/bin/bash
set -euo pipefail

echo "Strict mode enabled"

# Undefined variable (set -u)
echo "Value of VAR is: $VAR"

# Failing command (set -e)
ls /nonexistent-directory

# Pipe failure (set -o pipefail)
cat missingfile.txt | grep "test"
```

---

## 📌 What Each Flag Does

- `set -e` → Exit immediately if any command fails.
- `set -u` → Exit if using an undefined variable.
- `set -o pipefail` → If any command in a pipeline fails, the whole pipeline fails.

Without strict mode:
- Script may continue silently even after errors.

With strict mode:
- Script stops immediately, preventing hidden failures.

---

# ✅ Task 4 – Local Variables

## 📄 File: `local_demo.sh`

```bash
#!/bin/bash

use_local() {
    local message="Inside Function"
    echo "$message"
}

use_global() {
    message="Global Variable"
}

use_local
echo "Outside after local: ${message:-Not Defined}"

use_global
echo "Outside after global: $message"
```

### 🔎 Explanation

- `local` variables exist only inside the function.
- Global variables are accessible everywhere.

---

# ✅ Task 5 – System Info Reporter Script

## 📄 File: `system_info.sh`

```bash
#!/bin/bash
set -euo pipefail

print_header() {
    echo "================================="
    echo "$1"
    echo "================================="
}

print_hostname_os() {
    print_header "System Information"
    echo "Hostname: $(hostname)"
    echo "OS: $(uname -a)"
}

print_uptime() {
    print_header "Uptime"
    uptime
}

print_disk_usage() {
    print_header "Top 5 Disk Usage"
    df -h | head -n 6
}

print_memory_usage() {
    print_header "Memory Usage"
    free -h
}

print_top_processes() {
    print_header "Top 5 CPU Processes"
    ps -eo pid,comm,%cpu --sort=-%cpu | head -n 6
}

main() {
    print_hostname_os
    print_uptime
    print_disk_usage
    print_memory_usage
    print_top_processes
}

main
```

### ▶ Run

```bash
chmod +x system_info.sh
./system_info.sh
```

---

# 🧠 What I Learned

- Functions make scripts reusable and clean.
- Arguments inside functions use `$1`, `$2`, etc.
- `local` prevents variable leakage.
- `set -euo pipefail` makes scripts safer.
- `$?` returns last command’s exit code.
- Real-world scripts use structured functions and a `main()` entry point.

---

✅ Completed Day 18 – Shell Scripting: Functions & Intermediate Concepts
