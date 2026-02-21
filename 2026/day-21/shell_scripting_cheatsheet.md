
# 🐚 Shell Scripting Cheat Sheet – DevOps Quick Reference

---

# 📌 Quick Reference Table

| Topic | Key Syntax | Example |
|-------|------------|----------|
| Variable | `VAR="value"` | `NAME="DevOps"` |
| Argument | `$1, $2` | `./script.sh arg1` |
| If | `if [ condition ]; then` | `if [ -f file ]; then` |
| For loop | `for i in list; do` | `for i in 1 2 3; do` |
| Function | `name() { ... }` | `greet() { echo "Hi"; }` |
| Grep | `grep pattern file` | `grep -i "error" log.txt` |
| Awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| Sed | `sed 's/old/new/g' file` | `sed -i 's/foo/bar/g' config.txt` |

---

# ✅ Task 1 – Basics

## Shebang
```bash
#!/bin/bash
```
Tells system which interpreter to use.

## Run Script
```bash
chmod +x script.sh
./script.sh
bash script.sh
```

## Comments
```bash
# Single line comment
echo "Hello" # Inline comment
```

## Variables
```bash
NAME="Kamlesh"
echo $NAME
echo "$NAME"
echo '$NAME'
```
- `$VAR` → value  
- `"$VAR"` → preserves spaces  
- `'$VAR'` → literal string  

## Read Input
```bash
read -p "Enter name: " NAME
```

## Command-line Arguments
```bash
$0  # script name
$1  # first argument
$#  # number of arguments
$@  # all arguments
$?  # last exit status
```

---

# ✅ Task 2 – Operators & Conditionals

## String Comparisons
```bash
[ "$a" = "$b" ]
[ "$a" != "$b" ]
[ -z "$a" ]  # empty
[ -n "$a" ]  # not empty
```

## Integer Comparisons
```bash
[ "$a" -eq 5 ]
[ "$a" -ne 5 ]
[ "$a" -lt 5 ]
[ "$a" -gt 5 ]
[ "$a" -le 5 ]
[ "$a" -ge 5 ]
```

## File Tests
```bash
[ -f file ]  # regular file
[ -d dir ]   # directory
[ -e file ]  # exists
[ -r file ]  # readable
[ -w file ]  # writable
[ -x file ]  # executable
[ -s file ]  # not empty
```

## If / Elif / Else
```bash
if [ condition ]; then
    echo "True"
elif [ other ]; then
    echo "Else If"
else
    echo "False"
fi
```

## Logical Operators
```bash
command && echo "Success"
command || echo "Fail"
[ ! -f file ]
```

## Case Statement
```bash
case $1 in
    start) echo "Starting";;
    stop) echo "Stopping";;
    *) echo "Unknown";;
esac
```

---

# ✅ Task 3 – Loops

## For Loop (List)
```bash
for i in 1 2 3; do
    echo $i
done
```

## For Loop (C-style)
```bash
for ((i=1;i<=5;i++)); do
    echo $i
done
```

## While Loop
```bash
while [ $i -lt 5 ]; do
    ((i++))
done
```

## Until Loop
```bash
until [ $i -eq 5 ]; do
    ((i++))
done
```

## Break & Continue
```bash
break
continue
```

## Loop Over Files
```bash
for file in *.log; do
    echo $file
done
```

## Loop Over Command Output
```bash
while read line; do
    echo $line
done < file.txt
```

---

# ✅ Task 4 – Functions

## Define Function
```bash
greet() {
    echo "Hello $1"
}
```

## Call Function
```bash
greet "DevOps"
```

## Return Value
```bash
add() {
    echo $(( $1 + $2 ))
}
result=$(add 2 3)
```

## Return vs Echo
```bash
return 1   # exit code
echo "5"   # actual output
```

## Local Variables
```bash
myfunc() {
    local VAR="inside"
}
```

---

# ✅ Task 5 – Text Processing Commands

## grep
```bash
grep "error" file
grep -i "error" file
grep -r "error" .
grep -c "error" file
grep -n "error" file
grep -v "info" file
grep -E "error|fail" file
```

## awk
```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
awk 'BEGIN{print "Start"} {print $1} END{print "End"}' file
```

## sed
```bash
sed 's/old/new/g' file
sed -i 's/foo/bar/g' file
sed '2d' file
```

## cut
```bash
cut -d: -f1 /etc/passwd
```

## sort
```bash
sort file
sort -n file
sort -r file
sort -u file
```

## uniq
```bash
uniq file
uniq -c file
```

## tr
```bash
tr 'a-z' 'A-Z'
tr -d '\r'
```

## wc
```bash
wc -l file
wc -w file
wc -c file
```

## head / tail
```bash
head -n 10 file
tail -n 10 file
tail -f logfile.log
```

---

# ✅ Task 6 – Useful One-Liners

## Delete files older than 7 days
```bash
find /path -type f -mtime +7 -delete
```

## Count lines in all .log files
```bash
wc -l *.log
```

## Replace string across files
```bash
sed -i 's/old/new/g' *.conf
```

## Check if service running
```bash
systemctl is-active nginx
```

## Disk usage alert
```bash
df -h | awk '$5+0 > 80 {print "High usage:", $0}'
```

## Tail and filter errors
```bash
tail -f app.log | grep --line-buffered "ERROR"
```

---

# ✅ Task 7 – Error Handling & Debugging

## Exit Codes
```bash
exit 0
exit 1
echo $?
```

## set -e
Exit immediately if a command fails.

```bash
set -e
```

## set -u
Error on undefined variables.

```bash
set -u
```

## set -o pipefail
Fail if any command in pipe fails.

```bash
set -o pipefail
```

## set -x (Debug Mode)
```bash
set -x
```

## Trap
```bash
cleanup() {
    echo "Cleaning up..."
}
trap cleanup EXIT
```

---

# 🚀 Final Notes

- Always use `set -euo pipefail` in production scripts.
- Quote variables: `"$VAR"`
- Validate inputs.
- Use functions for reusable logic.
- Log outputs for debugging.
- Keep scripts readable and modular.

---

✅ Personal DevOps Shell Scripting Cheat Sheet – Ready for Real-World Use
