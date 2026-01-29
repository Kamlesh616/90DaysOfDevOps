# Linux File Read/Write Practice Note

## Goal
Practice basic file read and write operations using simple Linux commands.

---

## Task Overview
In this practice, we will:
- Create a text file
- Write text into the file
- Append new lines
- Read the file using different commands

---

## File Used
File name: notes.txt

---

## Step 1: Create and Write to File

### Write first lines using >
Command:
echo "This is my first note." > notes.txt

Command:
echo "Linux file handling practice." >> notes.txt

Command:
echo "Learning basic commands step by step." >> notes.txt

Observation:
File notes.txt is created and contains 3 lines.

---

## Step 2: Append More Lines

### Append new lines using >>
Command:
echo "Reading and writing files is important." >> notes.txt

Command:
echo "This file is created for practice." >> notes.txt

Observation:
New lines are added without removing old content.

---

## Step 3: Read Full File

### Read entire file using cat
Command:
cat notes.txt

Observation:
All lines in notes.txt are displayed.

---

## Step 4: Read Part of File

### Read first lines using head
Command:
head notes.txt

Observation:
Shows the first few lines of the file.

### Read last lines using tail
Command:
tail notes.txt

Observation:
Shows the last few lines of the file.

---

## Step 5: Write and Display Using tee

### Write and display at the same time
Command:
echo "This line is added using tee command." | tee -a notes.txt

Observation:
Line is displayed on screen and appended to the file.

---

## Summary
- File created using redirection
- Text written and appended using > and >>
- File read using cat, head, and tail
- tee used to write and display output together

This is a simple and repeatable file read/write practice in Linux.
