# Linux Partitioning and Persistence

## 1. Create a New Partition with ext3 Filesystem

- **Identify an available disk:**
  ```bash
  fdisk -l
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/1a60b80f809e192d6c008094cd3112a505d797eb/image/Picture1.png)
  
- **Create a new partition:**
  ```bash
  fdisk /dev/sda
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture2.png)
 
  Press “n” (to add a new partition) and give partition number, first and last sector. New partition will create with partition size.
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture3.png)

- **Format the new partition with the ext3 filesystem:**
  ```bash
  mkfs.ext3 /dev/sda4
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture4.png)
 
## 2. Mount the Partition to `/mnt/mypartition`

- **Create the mount point directory:**
  ```bash
  mkdir -p /mnt/mypartition
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture5.png)
 
- **Mount the partition to /mnt/mypartition**
  ```bash
  mount /dev/sda4 /mnt/mypartition
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture6.png)

## 3. Create a File with a Fake Address

- **Within /mnt/mypartition, create a file named address**
  ```bash
  cd /mnt/mypartition
  vim address
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture7.png)

- **Write a fake address into the address file**

  In Vim:
  - Press `i` to enter insert mode and type the address.
  - Press `Esc`, then type `:wq` to save and exit.

  To verify:
  ```bash
  cat address
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture8.png)

## 4. Ensure Persistence After Reboot

- **Edit the /etc/fstab file to add an entry for the new partition**
  ```bash
  vim /etc/fstab
  ```

  Add a line in this format:
  ```
  /dev/sda4  /mnt/mypartition  ext3  defaults  0  0
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture9.png)

- **Reboot the system and verify that:**

The partition is mounted automatically.
The address file still exists in /mnt/mypartition**
  ```bash
  mount -a
  ls /mnt/mypartition/
  reboot
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture10.png)

  After reboot:
  ```bash
  cat /mnt/mypartition/address
  ```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/4e6190be59cc9ebac4c8e5eb0248dc4a950a32fd/image/Picture11.png)

