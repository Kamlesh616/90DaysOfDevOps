# 📊 Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator

## 🎯 Objective
Create a production-style Bash script that:
- Analyzes server log files
- Counts errors
- Detects critical events
- Generates a structured daily report
- Optionally archives processed logs

---

# ✅ Script: `log_analyzer.sh`

```bash
#!/bin/bash
set -euo pipefail

# ----------------------------
# Input Validation
# ----------------------------

if [ $# -ne 1 ]; then
    echo "Usage: $0 <log_file_path>"
    exit 1
fi

LOG_FILE="$1"

if [ ! -f "$LOG_FILE" ]; then
    echo "Error: File does not exist."
    exit 1
fi

# ----------------------------
# Variables
# ----------------------------

DATE=$(date +%Y-%m-%d)
REPORT_FILE="log_report_${DATE}.txt"
TOTAL_LINES=$(wc -l < "$LOG_FILE")
ERROR_COUNT=$(grep -Ei -c "ERROR|Failed" "$LOG_FILE" || true)

# ----------------------------
# Console Output
# ----------------------------

echo "Analyzing log file: $LOG_FILE"
echo "Total lines: $TOTAL_LINES"
echo "Total errors (ERROR/Failed): $ERROR_COUNT"

echo ""
echo "--- Critical Events ---"
grep -n "CRITICAL" "$LOG_FILE" || echo "No critical events found."

echo ""
echo "--- Top 5 Error Messages ---"
grep "ERROR" "$LOG_FILE" | \
awk '{$1=$2=$3=""; print $0}' | \
sed 's/^ *//' | \
sort | uniq -c | sort -rn | head -5 || echo "No ERROR entries found."

# ----------------------------
# Generate Report
# ----------------------------

{
    echo "========================================="
    echo "Log Analysis Report"
    echo "========================================="
    echo "Date of Analysis: $DATE"
    echo "Log File: $LOG_FILE"
    echo "Total Lines Processed: $TOTAL_LINES"
    echo "Total ERROR/Failed Count: $ERROR_COUNT"
    echo ""

    echo "----- Top 5 Error Messages -----"
    grep "ERROR" "$LOG_FILE" | \
    awk '{$1=$2=$3=""; print $0}' | \
    sed 's/^ *//' | \
    sort | uniq -c | sort -rn | head -5 || echo "No ERROR entries found."
    echo ""

    echo "----- Critical Events -----"
    grep -n "CRITICAL" "$LOG_FILE" || echo "No critical events found."
    echo ""

} > "$REPORT_FILE"

echo ""
echo "Report generated: $REPORT_FILE"

# ----------------------------
# Optional: Archive Log File
# ----------------------------

ARCHIVE_DIR="archive"

mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"

echo "Log file moved to $ARCHIVE_DIR/"
```

---

# 📝 Generated Report Example

Example filename:

```
log_report_2026-02-20.txt
```

Contents include:

- Date of analysis  
- Log file name  
- Total lines processed  
- Total error count  
- Top 5 error messages  
- Critical events with line numbers  

---

# 📄 Documentation: `day-20-solution.md`

```markdown
# Day 20 – Log Analyzer Solution

## Approach

1. Used strict mode: `set -euo pipefail`
2. Validated input arguments and file existence.
3. Counted total lines using:
   wc -l
4. Counted errors using:
   grep -Ei "ERROR|Failed"
5. Extracted CRITICAL events with line numbers using:
   grep -n
6. Found top 5 ERROR messages using:
   grep | awk | sort | uniq -c | sort -rn | head -5
7. Generated a structured report file:
   log_report_<date>.txt
8. Archived processed logs into an archive/ directory.

## Key Concepts Used

- Command-line arguments ($# , $1)
- Error handling
- Pipes and text processing
- Sorting and counting occurrences
- File redirection
- Strict mode safety
- Directory management (mkdir -p)
- File movement (mv)

## Real-World Value

This script simulates production log monitoring:
- Helps detect frequent failures
- Identifies critical system issues
- Automates daily reporting
- Prevents reprocessing of old logs

## Improvements for Future

- Add email notification
- Add colorized console output
- Add support for multiple log files
- Convert report to HTML format
```

---

# 🧠 What I Learned

- Log analysis is core to DevOps & System Administration.
- Text processing tools (`grep`, `awk`, `sort`, `uniq`) are extremely powerful.
- Strict mode prevents silent failures.
- Automation improves monitoring reliability.
- Structured reports help in daily operational reviews.

---

✅ Completed Day 20 – Log Analyzer & Report Generator
