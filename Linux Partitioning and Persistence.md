
# 🐧 Linux Partitioning and Persistence

This guide walks you through creating a new partition in Linux using `fdisk`, formatting it with the `ext3` filesystem, mounting it, and ensuring it remains persistent after reboot.

---

## 📋 Prerequisites

- Root or sudo access
- A Linux machine with available disk space
- Familiarity with the command line

---

## 🛠️ Steps

### 1. Identify an Available Disk

```bash
fdisk -l
```

### 2. Create a New Partition

```bash
fdisk /dev/sda
```

- Press `n` to add a new partition.
- Specify partition number, first and last sector.
- Save and exit.

### 3. Format the Partition with ext3

```bash
mkfs.ext3 /dev/sda4
```

> Replace `/dev/sda4` with your actual partition.

### 4. Mount the Partition

```bash
mkdir -p /mnt/mypartition
mount /dev/sda4 /mnt/mypartition
```

### 5. Create a File with a Fake Address

```bash
cd /mnt/mypartition
vim address
```

- Press `i` to enter insert mode, type the fake address.
- Press `Esc` and then type `:wq` to save and exit.

View the contents:

```bash
cat address
```

### 6. Ensure Persistence After Reboot

Edit `/etc/fstab`:

```bash
vim /etc/fstab
```

Add the following line:

```
/dev/sda4    /mnt/mypartition    ext3    defaults    0    2
```

Save and exit.

### 7. Verify After Reboot

```bash
reboot
```

After reboot, verify:

```bash
mount -a
ls /mnt/mypartition/
cat /mnt/mypartition/address
```

✅ Your partition should be auto-mounted and the address file should exist.

---

## ⚠️ Notes

- Replace `/dev/sda4` with your partition name.
- Be careful when using `fdisk` to avoid data loss.
