# Linux Partitioning and Persistence

## 1. Create a New Partition with ext3 Filesystem

- **Identify an available disk:**
  ```bash
  fdisk -l
  ```

- **Create a new partition:**
  ```bash
  fdisk /dev/sda
  ```

  Press `n` (to add a new partition), provide partition number, first and last sector.

- **Format the new partition with the ext3 filesystem:**
  ```bash
  mkfs.ext3 /dev/sda4
  ```

## 2. Mount the Partition to `/mnt/mypartition`

- **Create the mount point directory:**
  ```bash
  mkdir -p /mnt/mypartition
  ```

- **Mount the partition:**
  ```bash
  mount /dev/sda4 /mnt/mypartition
  ```

## 3. Create a File with a Fake Address

- **Navigate to the mount point and create a file named `address`:**
  ```bash
  cd /mnt/mypartition
  vim address
  ```

- **Write a fake address into the file:**

  In Vim:
  - Press `i` to enter insert mode and type the address.
  - Press `Esc`, then type `:wq` to save and exit.

  To verify:
  ```bash
  cat address
  ```

## 4. Ensure Persistence After Reboot

- **Edit the `/etc/fstab` file:**
  ```bash
  vim /etc/fstab
  ```

  Add a line in this format:
  ```
  /dev/sda4  /mnt/mypartition  ext3  defaults  0  2
  ```

- **Reboot and verify:**
  ```bash
  reboot
  ```

  After reboot:
  ```bash
  mount -a
  ls /mnt/mypartition/
  cat /mnt/mypartition/address
  ```

---

## 📷 Including the Image on GitHub

If your original PDF had an image you'd like to include, make sure to upload it to your GitHub repo and reference it like this:

```markdown
![Partition Setup](images/partition_screenshot.png)
```

Replace `images/partition_screenshot.png` with the correct relative path to your image file.

---

> ✅ After reboot, the partition should still exist, be mounted, and contain the `address` file.
