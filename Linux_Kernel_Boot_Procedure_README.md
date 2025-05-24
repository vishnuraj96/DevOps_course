
# 🐧 Linux, Kernel, and Boot Procedure

## 🌍 What is Linux?
Linux is a popular open-source OS created by Linus Torvalds in 1991. It is widely used for its:

- Free and open nature
- Strong security
- Stability
- Customizability
- Hardware compatibility
- Supportive community

---

## 🔧 Basic Linux Commands

### Navigation
- `ls`, `cd`, `pwd`

### File Management
- `cp`, `mv`, `rm`

### System Info
- `free`, `df`, `top`

### Networking
- `netstat`, `ifconfig`, `ping`

---

## 🧠 Kernel

The kernel bridges hardware and software, operating in:

- **Kernel Space**: For system-level operations.
- **User Space**: For user applications.

### Key Functions:
1. Resource management
2. Process scheduling
3. Memory management
4. Device management
5. Access control
6. Interprocess communication (IPC)
7. Security

### Types of Kernels:
- **Monolithic**: All in one space; fast but less safe.
- **Microkernel**: Only essentials in kernel space.
- **Hybrid**: Mix of both (e.g., Windows, macOS).
- **Nano Kernel**: Minimalist kernel.
- **Exo Kernel**: Maximum control in user space.

---

## 📦 Kernel Modules

Kernel modules are dynamic pieces of code that extend kernel capabilities.

### Benefits:
- Load/unload at runtime
- Adapt to hardware changes
- Easier maintenance
- Optimize resource use

---

## 🖥 Booting Process

1. **POST (Power-On Self-Test)**
   - Hardware check (CPU, RAM, I/O)

2. **MBR (Master Boot Record)**
   - Loads the bootloader

3. **Boot Loader**
   - Loads the kernel into RAM
   - Initializes the operating system
