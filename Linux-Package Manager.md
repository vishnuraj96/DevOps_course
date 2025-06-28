
# Install and Manage Packages

## APT (Advanced Package Tool)

APT is used for installing, upgrading, and removing packages.

### Update package list:
```bash
sudo apt update
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.1.png)

### Upgrade all packages:
```bash
sudo apt upgrade
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.2.png)

### Install a package:
```bash
sudo apt install nmap
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.3.png)

### Remove a package:
```bash
sudo apt remove nmap
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.4.png)

---

## dpkg

### List all packages in the system:
```bash
dpkg -l
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.5.png)

### To list the files installed by a package:
```bash
dpkg -L ufw
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/464fce224d8734ae0bbf05dd2a8192c8260079d5/image/6.6.png)

### Installing a .deb file:
```bash
sudo dpkg -i zip_3.0-4_amd64.deb
```

### Uninstalling packages:
```bash
sudo dpkg -r zip
```
