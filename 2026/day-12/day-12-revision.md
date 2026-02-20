# Day 12 – Breather & Revision (Days 01–11)

## Goal
Take a one-day pause to consolidate everything from Days 01–11 so I don’t forget the fundamentals I just built.

---

## Mindset & Plan (Day 01 Revisit)

- Original Goal: Build strong Linux fundamentals.
- Progress: More confident with files, permissions, services, and users.
- Updates to Plan:
  - Practice chmod numeric values daily.
  - Improve log reading with journalctl.
  - Increase troubleshooting speed.

---

## Processes & Services Review

### Commands Re-run

```bash
ps aux
systemctl status ssh
journalctl -u ssh
```
## File Skills Practice

- echo "revision practice" >> notes.txt
- chmod 755 notes.txt
- ls -l notes.txt
- cp notes.txt notes_backup.txt
- mkdir revision_dir

## Cheat Sheet Refresh – Top 5 Commands
```
1) ls -l

2) ps aux

3) systemctl status <service>

4) journalctl -xe

5) df -h
```

## User & Group Practice

```
sudo useradd practiceuser
id practiceuser
sudo chown practiceuser:practiceuser notes.txt
ls -l notes.txt
```

