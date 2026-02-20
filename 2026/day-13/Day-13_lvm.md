# 📦 Day 13 – Linux Volume Management (LVM)

## 🎯 Objective
Learn and practice Linux LVM to create, manage, extend, and mount logical volumes dynamically.

---

## 🔐 Step 0: Switch to Root User

```bash
sudo -i
# OR
sudo su
```

---

## 💽 Optional: Create a Virtual Disk (If No Spare Disk Available)

```bash
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024
losetup -fP /tmp/disk1.img
losetup -a
```

### Sample Output

```bash
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied

/dev/loop0: [2065]: (/tmp/disk1.img)
```

---

# 🧪 Challenge Tasks

---

## ✅ Task 1: Check Current Storage

### Commands

```bash
lsblk
pvs
vgs
lvs
df -h
```

### Sample Output

```bash
lsblk

NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    0   20G  0 disk
├─sda1        8:1    0    1G  0 part /boot
└─sda2        8:2    0   19G  0 part /
loop0         7:0    0    1G  0 loop

pvs
PV         VG   Fmt  Attr PSize PFree

vgs
VG   #PV #LV #SN Attr   VSize VFree

lvs
LV   VG   Attr       LSize

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        19G  5.0G   13G  28% /
```

---

## ✅ Task 2: Create Physical Volume

### Commands

```bash
pvcreate /dev/loop0
pvs
```

### Sample Output

```bash
Physical volume "/dev/loop0" successfully created.

pvs
PV           VG   Fmt  Attr PSize PFree
/dev/loop0        lvm2 ---  1.00g 1.00g
```

---

## ✅ Task 3: Create Volume Group

### Commands

```bash
vgcreate devops-vg /dev/loop0
vgs
```

### Sample Output

```bash
Volume group "devops-vg" successfully created

vgs
VG         #PV #LV #SN Attr   VSize VFree
devops-vg    1   0   0 wz--n- 1.00g 1.00g
```

---

## ✅ Task 4: Create Logical Volume

### Commands

```bash
lvcreate -L 500M -n app-data devops-vg
lvs
```

### Sample Output

```bash
Logical volume "app-data" created.

lvs
LV        VG         Attr       LSize
app-data  devops-vg  -wi-a----- 500.00m
```

---

## ✅ Task 5: Format and Mount the Logical Volume

### Commands

```bash
mkfs.ext4 /dev/devops-vg/app-data
mkdir -p /mnt/app-data
mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data
```

### Sample Output

```bash
mke2fs 1.46.5
Creating filesystem with 512000 1k blocks...

df -h /mnt/app-data
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/devops--vg-app--data   493M  1.2M  456M   1% /mnt/app-data
```

---

## ✅ Task 6: Extend the Logical Volume

### Commands

```bash
lvextend -L +200M /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
```

### Sample Output

```bash
Size of logical volume devops-vg/app-data changed from 500.00 MiB to 700.00 MiB.

resize2fs 1.46.5
Filesystem resized successfully.

df -h /mnt/app-data
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/devops--vg-app--data   690M  1.5M  650M   1% /mnt/app-data
```

---

## 🧠 LVM Architecture Flow

```
Disk (/dev/loop0)
      ↓
Physical Volume (PV)
      ↓
Volume Group (devops-vg)
      ↓
Logical Volume (app-data)
      ↓
Filesystem (ext4)
      ↓
Mount Point (/mnt/app-data)
```

---

## 🚀 What I Learned

- LVM provides flexible disk management.
- Storage can be extended without deleting data.
- Logical volumes can be resized dynamically.
- Structure follows: Disk → PV → VG → LV → Filesystem → Mount.

---

✅ Successfully created, mounted, and extended an LVM logical volume.
