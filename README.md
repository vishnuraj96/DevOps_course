# 🐧 Linux Partitioning and Persistence

This guide walks you through creating a new partition in Linux using `fdisk`, formatting it with the `ext3` filesystem, mounting it, and ensuring it remains persistent after reboot.

---

Linux Partitioning and Persistence
Create a New Partition with ext3 Filesystem
Identify an available disk
fdisk -l
 

Create a new partition
fdisk /dev/sda


Press “n” (to add a new partition) and give partition number, first and last sector. New partition will create with partition size.


Format the new partition with the ext3 filesystem
mkfs.ext3 /dev/sda4


Mount the Partition to /mnt/mypartition
Create the mount point directory
mkdir -p /mnt/mypartition


Mount the partition to /mnt/mypartition
mount /dev/sda4 /mnt/mypartition


Create a File with a Fake Address
Within /mnt/mypartition, create a file named address
cd /mnt/mypartition
vim address

Write a fake address into the address file 
Change to insert mode press ”i” and type the address and to write the address press “esc” key and “:wq” to save the address
cat address(ti view the address)

Ensure Persistence After Reboot
Edit the /etc/fstab file to add an entry for the new partition
vim /etc/fstab
after that add     . Write and quit the file

 Reboot the system and verify that:
The partition is mounted automatically
Mount -a
The address file still exists in /mnt/mypartition
ls /mnt/mypartition/
cat /mnt/mypartition/address

 After reboot the partition is still exists


