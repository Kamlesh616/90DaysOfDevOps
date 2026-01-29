# Linux Fundamentals Practice Note

## Goal
Practice basic Linux commands by checking processes, inspecting one service, and performing a small troubleshooting flow.

---

## Target Service
Service chosen: ssh  
Reason: SSH is a common and important Linux service.

---

## Process Checks

### 1. List Running Processes
Command:
ps aux | head -5

Observation:
Shows currently running processes. System processes are running normally.

---

### 2. Find SSH Process
Command:
pgrep -a ssh

Observation:
SSH process is running and its PID is visible.

---

## Service Checks

### 3. Check SSH Service Status
Command:
systemctl status ssh

Observation:
SSH service is active and running.

---

### 4. List Running Services
Command:
systemctl list-units --type=service --state=running | head

Observation:
Multiple system services are running, including SSH.

---

## Log Checks

### 5. View SSH Logs
Command:
journalctl -u ssh -n 20

Observation:
No recent error messages found in SSH logs.

---

### 6. View Authentication Logs
Command:
tail -n 20 /var/log/auth.log

Observation:
Successful SSH login entries are present.

---

## Mini Troubleshooting Steps (If SSH Stops Working)

1. Check if SSH process exists  
   Command: pgrep ssh

2. Check SSH service status  
   Command: systemctl status ssh

3. Start SSH service if stopped  
   Command: sudo systemctl start ssh

4. Check logs for errors  
   Command: journalctl -u ssh

---

## Summary
This practice covers:
- Checking running processes
- Inspecting a systemd service
- Reading service logs
- Performing basic troubleshooting steps

