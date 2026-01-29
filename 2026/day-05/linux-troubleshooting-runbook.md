# Linux Troubleshooting Runbook

## Target Service / Process
Service: ssh  
Purpose: Inspect system health and troubleshoot a running service using basic Linux commands.

---

## Environment Basics

### System Information
Command:
uname -a  
Observation: Linux kernel is running normally on a 64-bit system.

### OS Information
Command:
cat /etc/os-release  
Observation: System is running Ubuntu 22.04 LTS.

---

## Filesystem Sanity

### Create Test Directory
Command:
mkdir /tmp/runbook-demo  
Observation: Filesystem is writable.

### Copy and Verify File
Command:
cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo  
Observation: File creation and permissions are working correctly.

---

## Snapshot: CPU & Memory

### Memory Usage
Command:
free -h  
Observation: Sufficient free memory available, no memory pressure.

### SSH Process Resource Usage
Command:
pgrep ssh  
ps -o pid,pcpu,pmem,comm -p <PID>  
Observation: SSH process is using very low CPU and memory.

---

## Snapshot: Disk & IO

### Disk Space Usage
Command:
df -h  
Observation: Disk usage is within safe limits.

### Log Directory Size
Command:
du -sh /var/log  
Observation: Logs are not consuming excessive disk space.

---

## Snapshot: Network

### Listening Ports
Command:
ss -tulpn | grep ssh  
Observation: SSH is listening on port 22.

### Local Network Check
Command:
curl -I localhost  
Observation: Local network stack is responding.

---

## Logs Reviewed

### SSH Service Logs
Command:
journalctl -u ssh -n 50  
Observation: No recent errors found in SSH logs.

### Authentication Logs
Command:
tail -n 50 /var/log/auth.log  
Observation: Successful SSH login entries observed.

---

## Quick Findings
System health is normal.  
SSH service is running and responsive.  
No CPU, memory, disk, or network issues detected.  
Logs show no critical errors.

---

## If This Worsens (Next Steps)

1. Restart SSH service safely  
   Command: sudo systemctl restart ssh

2. Increase SSH log verbosity  
   Action: Set LogLevel VERBOSE in /etc/ssh/sshd_config

3. Monitor real-time system usage  
   Command: top
