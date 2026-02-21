# 🛠️ Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## 🎯 Objective
Apply real-world scripting skills:
- Log rotation
- Automated backups
- Cron scheduling
- Error handling
- Maintenance automation

---

# ✅ Task 1 – Log Rotation Script

## 📄 File: `log_rotate.sh`

```bash
#!/bin/bash
set -euo pipefail

LOG_DIR="${1:-}"

if [ -z "$LOG_DIR" ]; then
    echo "Usage: $0 <log_directory>"
    exit 1
fi

if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist."
    exit 1
fi

compressed_count=0
deleted_count=0

# Compress .log files older than 7 days
while IFS= read -r file; do
    gzip "$file"
    ((compressed_count++))
done < <(find "$LOG_DIR" -type f -name "*.log" -mtime +7)

# Delete .gz files older than 30 days
while IFS= read -r file; do
    rm -f "$file"
    ((deleted_count++))
done < <(find "$LOG_DIR" -type f -name "*.gz" -mtime +30)

echo "Compressed files: $compressed_count"
echo "Deleted files: $deleted_count"
```

---

# ✅ Task 2 – Server Backup Script

## 📄 File: `backup.sh`

```bash
#!/bin/bash
set -euo pipefail

SOURCE="${1:-}"
DEST="${2:-}"

if [ -z "$SOURCE" ] || [ -z "$DEST" ]; then
    echo "Usage: $0 <source_directory> <backup_destination>"
    exit 1
fi

if [ ! -d "$SOURCE" ]; then
    echo "Error: Source directory does not exist."
    exit 1
fi

mkdir -p "$DEST"

TIMESTAMP=$(date +%Y-%m-%d)
ARCHIVE="$DEST/backup-$TIMESTAMP.tar.gz"

tar -czf "$ARCHIVE" -C "$(dirname "$SOURCE")" "$(basename "$SOURCE")"

if [ -f "$ARCHIVE" ]; then
    echo "Backup created: $ARCHIVE"
    echo "Size: $(du -h "$ARCHIVE" | cut -f1)"
else
    echo "Backup failed!"
    exit 1
fi

# Delete backups older than 14 days
find "$DEST" -type f -name "backup-*.tar.gz" -mtime +14 -delete
```

---

# ✅ Task 3 – Crontab

## 🔍 Check Current Cron Jobs

```bash
crontab -l
```

---

## ⏰ Cron Syntax

```
* * * * *  command
│ │ │ │ │
│ │ │ │ └── Day of week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## 📝 Required Cron Entries

### Run log_rotate.sh every day at 2 AM

```bash
0 2 * * * /path/to/log_rotate.sh /var/log/myapp >> /var/log/log_rotate.log 2>&1
```

### Run backup.sh every Sunday at 3 AM

```bash
0 3 * * 0 /path/to/backup.sh /source/dir /backup/dir >> /var/log/backup.log 2>&1
```

### Run health_check.sh every 5 minutes

```bash
*/5 * * * * /path/to/health_check.sh >> /var/log/health.log 2>&1
```

---

# ✅ Task 4 – Combined Scheduled Maintenance Script

## 📄 File: `maintenance.sh`

```bash
#!/bin/bash
set -euo pipefail

LOG_FILE="/var/log/maintenance.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') : $1" >> "$LOG_FILE"
}

run_log_rotation() {
    log "Starting log rotation..."
    /path/to/log_rotate.sh /var/log/myapp >> "$LOG_FILE" 2>&1
    log "Log rotation completed."
}

run_backup() {
    log "Starting backup..."
    /path/to/backup.sh /source/dir /backup/dir >> "$LOG_FILE" 2>&1
    log "Backup completed."
}

main() {
    log "===== Maintenance Started ====="
    run_log_rotation
    run_backup
    log "===== Maintenance Finished ====="
}

main
```

---

## ⏰ Cron Entry to Run Maintenance Daily at 1 AM

```bash
0 1 * * * /path/to/maintenance.sh
```

---

# 🧠 What I Learned

- Automating log rotation prevents disk space issues.
- Automated backups protect server data.
- `tar` + `gzip` are essential for server administration.
- `find` with `-mtime` helps manage old files.
- Cron enables full automation.
- Logging with timestamps improves debugging.
- Strict mode (`set -euo pipefail`) prevents silent failures.

---

✅ Completed Day 19 – Log Rotation, Backup & Crontab Project
