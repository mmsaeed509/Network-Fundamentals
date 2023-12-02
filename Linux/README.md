# Linux or GNU/LINUX

You can learn Linux form [Here](https://linuxjourney.com/)

### install VBox Additional Modules

```Bash
cd /media/$USER/VBox_GAs_version

sudo bash VBoxLinuxAdditions.run
```
version
___

### Main Differences between distros

- Release Type:

  - Rolling: also known as rolling update or continuous delivery, is a concept in software development of frequently delivering updates to applications.
  - Fixed (Stable/Point Release): follow a particular release schedule, where they bundle updates to the kernel and the core operating system services and deliver them to the users as a new release.

- Package Manager

  - is an app that help you to install/update/remove packages, tools etc...
  - like: 
    - APT: For Debian/Debian-Based Distro (Ubuntu, Debian, ParrotOS, and Kali Linux)
    - DNF & YUM: For RedHat/RedHat-Based Distro (RHEL/CentOS 8, Fedora)
    - Pacman: For Arch/Arch-Based Distro (Arch, GarudaLinux, Exodia OS, and BlackArch Linux)
    - Zypper: For OpenSUSE
    - Portage: For Gentoo
    - XBPS (X Binary Package System): Void Linux Distro
    - PPM (Puppy package manager): Puppy Linux

___

### TUI Apps 

Text-based user interface or terminal user interface

```Bash
pacman -Sg Exodia-TUI-Apps
```
___

### Linux Permissions
Linux Permissions control access to files and directories. There are three types of permissions: **read (r)**, **write (w)**, and **execute (x)**. These permissions apply to three entities: **owner**, **group**, and **others**.

## Permission Types

- **Read (r):** Allows viewing the content of a file or the list of files in a directory.
- **Write (w):** Enables modification of a file's content or the ability to create, delete, and rename files in a directory.
- **Execute (x):** Permits the execution of a file (for scripts and binaries) or access to a directory.

## Permission Entities

- **Owner:** The user who owns the file or directory.
- **Group:** A collection of users with similar permissions.
- **Others:** Everyone else who doesn't fall into the owner or group category.

## Symbolic Representation

Permissions are represented using a combination of letters:

- `r` for read
- `w` for write
- `x` for execute

### Example

```bash
-rw-r--r-- 1 user group 1024 Dec 1 12:00 myfile.txt
```

In this example, the owner has read and write permissions, the group has read-only permissions, and others have read-only permissions.

```bash
drwxr-xr-x o0xwolf o0xwolf 252 B  Fri Nov 24 18:01:46 2023 GitHub
.rw-r--r-- o0xwolf o0xwolf 625 B  Wed Nov 15 08:35:12 2023 pkgs.txt
```

## Numeric Representation

Permissions can also be represented numerically:

- `4` for read
- `2` for write
- `1` for execute

Each entity's permissions are assigned a value, and the sum represents the overall permission value.

### Example

```bash
chmod 644 myfile.txt
```

In this example, the owner has read and write (4+2) permissions, and the group and others have read-only (4) permissions.

___

### Linux Filesystem Hierarchy

The Linux Filesystem Hierarchy Standard (FHS) defines the organization and layout of files and directories in a Linux system.

![FHS](./imgs/FHS.png)

#### FHS:

- Root Directory (/)
  - The top-level directory that contains all other directories and files.
  - Represented by a single forward slash (`/`).

- `/bin`
  - Essential binary files and commands required for system boot and repair.

- `/boot`
  - Boot Loader files and the Linux kernel.
  - Configuration files for the Boot Loader.

- `/dev`
  - Device files representing hardware devices.
  - Examples include disk drives, terminals, and printers.

`/etc`
  - System-wide configuration files and scripts.
  - Contains configuration files for various services and applications.

- `/home`
  - Home directories for regular users.
  - Each user has a subdirectory here with their personal files.

- `/lib` and `/lib64`
  - Essential shared libraries required by system binaries and commands.

- `/media`
  - Mount points for removable media such as USB drives and CDs.

- `/mnt`
  - Temporary mount point for mounting filesystems.

- `/opt`
  - Optional software packages installed by the system administrator.

- `/proc`
  - Virtual filesystem containing information about system processes and kernel parameters.

- `/root`
  - Home directory for the root user (system administrator).

- `/sbin`
  - System binaries essential for system maintenance and recovery.

- `/srv`
  - Data for services provided by the system.

- `/tmp`
  - Temporary files used by applications and the system.

- `/usr`
  - Secondary hierarchy for user data and program files.
  - Typically read-only after the system is booted.

- `/var`
  - Variable files such as logs, databases, and spool files.
  - Content that may change during normal system operation.

This hierarchy provides a standardized structure for organizing files and directories in a Linux system, facilitating consistent and predictable system administration.

> `./` -> refer to current directory
> `../` -> refer to parent directory

___

### Linux Mounting and Unmounting

Mounting in Linux refers to associating a filesystem with a directory, making its contents accessible to the system. Unmounting is the process of detaching a filesystem from its mount point.

#### Mounting

- **Command:** The `mount` command is used to mount a filesystem.
  ```bash
  mount /dev/sdb1 /mnt/usb
  ```
This command mounts the filesystem on `/dev/sdb1` to the directory `/mnt/usb`.

- **Mount Point:**
  - A directory where the contents of the mounted filesystem become accessible.
  - Common mount points include `/mnt` or `/media`.

- **Filesystems:**
  - Filesystems can be local (e.g., ext4) or network-based (e.g., NFS).

- **AutoMounting:**
  - Some systems automatically mount certain filesystems upon startup or device connection.

#### Unmounting

- **Command:** The `umount` command is used to unmount a filesystem.
  ```bash
  umount /mnt/usb
  ```
  This command unmounts the filesystem mounted on `/mnt/usb`.

- **Precautions:**
  - Before physically removing a device or making changes, unmount to ensure data integrity.

- **Forced Unmount:**
  - In some cases, when a filesystem is in use, the `umount` command may not work. The `umount -l` option can force an unmount.

- **Network Mounts:**
  - For network-based mounts, the `umount` command is still used, but the filesystem might be remote (e.g., NFS).

Mounting and unmounting are essential tasks in managing Linux filesystems, allowing for organized access to various storage devices and network resources.

___

### Linux Kernel Modules (Drivers)

Linux kernel modules are pieces of code that can be loaded and unloaded into the Linux kernel at runtime. They extend the functionality of the kernel by providing support for specific hardware, file systems, or functionalities.

## Key Points

- **Dynamic Extension:**
  - Kernel modules can be dynamically loaded and unloaded without rebooting the system.
  - This allows for efficient use of system resources and the ability to add or remove functionalities as needed.

- **Functionality:**
  - Modules often serve as drivers for hardware devices, enabling the kernel to communicate with and control various peripherals.
  - Examples include graphics card drivers, network drivers, and file system drivers.

- **Kernel Module Commands:**
  - `insmod`: Used to insert (load) a kernel module into the running kernel.
    ```bash
    insmod my_module.ko
    ```
  - `rmmod`: Used to remove (unload) a loaded kernel module.
    ```bash
    rmmod my_module
    ```

- **Dependency Resolution:**
  - Modules can depend on other modules. The kernel automatically resolves and loads dependent modules when a module is loaded.

- **Listing Modules:**
  - The `lsmod` command lists currently loaded modules.
    ```bash
    lsmod
    ```

- **Configuration Files:**
  - Configuration files for modules are often found in the `/etc/modprobe.d/` directory.
  - They can be used to set module options and configurations.

- **Kernel Module Source Code:**
  - Kernel modules are typically written in C.
  - Kernel headers and build tools are required for compiling modules.

- **Security Considerations:**
  - Loading and unloading modules require appropriate permissions.
  - Kernel modules have the potential to impact system stability and security.

Kernel modules are a powerful mechanism in Linux, allowing for flexibility in managing and extending the functionality of the kernel, particularly in supporting a wide range of hardware and software components.

___

### Everything is a File

In Unix-like operating systems, the philosophy "Everything is a file" means that virtually everything, regardless of its nature, can be treated as a file or a file-like object. This concept simplifies the design and interaction within the system.

## Key Points

- **Uniform Interface:**
  - In Unix, devices, directories, processes, and network sockets are represented as files.
  - This uniformity allows a consistent interface for working with diverse system components.

- **File Descriptors:**
  - Processes interact with files through file descriptors.
  - Standard input (`stdin`), standard output (`stdout`), and standard error (`stderr`) are examples of file descriptors.

- **Device Files:**
  - Hardware devices, such as disk drives and printers, are accessed through device files in the `/dev` directory.

- **Directories:**
  - Directories are special files that contain lists of other files and directories.
  - The hierarchical filesystem structure is navigated using file-like operations.

- **Processes:**
  - Information about processes is represented as files in the `/proc` directory.
  - For example, `/proc/<pid>/status` contains status information for a process with a specific PID.

- **Network Sockets:**
  - Network communication is abstracted as files, allowing processes to read from and write to network sockets as if they were regular files.

- **Consistency and Simplicity:**
  - Treating diverse entities as files simplifies the system design and provides a consistent way to interact with different components.

- **Programming Paradigm:**
  - This concept influences the Unix programming paradigm, encouraging a modular and flexible approach.

The "Everything is a file" philosophy enhances the simplicity, consistency, and versatility of Unix-like systems, promoting a unified approach to handling various system resources.

___

### Linux Symbolic Links (Symlinks)

Symbolic links, or symlinks, in Linux are special files that act as pointers or references to another file or directory. They provide a flexible and efficient way to create references across the filesystem.
> Like shortcuts in Windows OS

## Key Points

- **Creation:**
  - Symlinks are created using the `ln` command with the `-s` option.
    ```bash
    ln -s /path/to/target /path/to/symlink
    ```

- **File Types:**
  - Unlike hard links, symlinks are distinct files with their own inode and data block.
  - They can reference files, directories, or even non-existent paths.

- **Relative and Absolute Paths:**
  - Symlinks can use either relative or absolute paths.
  - Relative paths are specified in relation to the symlink's location, while absolute paths provide the full path.

- **Target Changes:**
  - If the target of a symlink is moved or renamed, the symlink still points to the correct location.
  - If the target is deleted, the symlink becomes a "dangling symlink."

- **Permissions and Ownership:**
  - Symlinks have their own permissions and ownership information.
  - Permissions on the symlink determine who can read or follow the link.

- **Use Cases:**
  - Common use cases include simplifying directory structures, linking shared libraries, and creating shortcuts.

- **Distinguishing Symlinks:**
  - The `ls` command displays symlinks with an arrow (`->`) indicating the linked path.
    ```bash
    ls -l /path/to/symlink
    ```

- **Caution:**
  - Deleting a symlink doesn't affect the target, but deleting the target removes the symlink's purpose.

Symbolic links are powerful tools for creating flexible and dynamic relationships between files and directories, providing a convenient way to organize and access information within the Linux filesystem.
