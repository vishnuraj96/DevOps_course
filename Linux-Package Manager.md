
# Install and Manage Packages

## APT (Advanced Package Tool)

APT is used for installing, upgrading, and removing packages.

### Update package list:
```bash
sudo apt update
```
![image alt](https://github.com/vishnuraj96/DevOps_course/blob/1a60b80f809e192d6c008094cd3112a505d797eb/image/6.1.png)

### Upgrade all packages:
```bash
sudo apt upgrade
```

### Install a package:
```bash
sudo apt install nmap
```

### Remove a package:
```bash
sudo apt remove nmap
```

---

## dpkg

### List all packages in the system:
```bash
dpkg -l
```

### To list the files installed by a package:
```bash
dpkg -L ufw
```

### Installing a .deb file:
```bash
sudo dpkg -i zip_3.0-4_amd64.deb
```

### Uninstalling packages:
```bash
sudo dpkg -r zip
```
