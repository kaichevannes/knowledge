# Linux Core Concepts

## Kernel

The kernel manages memory, processes, drivers, and security. It separates memory into a kernel space which manages hardware and a user space which contains applications that make calls to the kernel space such as: open(), close(), readdir().

When the kernel detects a new hardware device it sends a uevent to the user space device manager daemon udev — this creates a new device under /dev/dynamicname.

## Working With Hardware

- `dmesg` is used to show messages from the ring buffer which contains logs from hardware devices.
- `udevadm` is a utility for querying udev.
- `lspci` lists PCI (Peripheral Component Interconnect) devices like ethernet cards, video cards, wifi adapters that attach to ethernet slots.
- `lsblk` shows the disk blocks and partitions. Disk means the whole physical space, partition is the split out usable space within the disk.
- `lscpu` provides information on your CPU: architecture, cores (sockets), threads, model.
- `lsmem` provides information about memory.
- `free -m` shows memory usage.
- `lshw` provides information on the hardware of the entire machine.

## Boot

1. BIOS POST
"Power On Self Test" — hardware is working.

2. Boot Loader (e.g. GRUB2)
BIOS loads the boot code from the boot device, located in the first sector of the hard disk. In linux this is located in the /boot filesystem. Loads selected kernel into memory.

3. Kernel Initialization
Decompress kernel and start executing. Initialize hardware, memory management. Looks for INIT process to run, setting up user space and processes for user environment.

4. INIT Process (systemd)
INIT function then calls systemd daemon, responsible for mounting file systems, managing system services. `ls -l /sbin/init` shows the INIT process used.

## Runlevels

Sets the mode of operation. `runlevel` shows the mode. 3 (multiuser.target) means command line interface, 5 (graphical.target) means graphical. systemd will run services based on the runlevel. We can set the runlevel with `systemctl set-default multi-user.target`.

## File Types

Every object in Linux is a type of file:

1. Regular File
2. Directory
3. Special Files
    3.1 Character Files — devices under /dev/foo allowing the OS to communicate to IO devices serially (mouse/keyboard)
    3.2 Block Files — block devices like harddisks & RAM
    3.3 Links — hard links share data, soft links (symlinks) are pointers to another file.
    3.4 Socket Files — Enables commuication between two files
    3.5 Named Pipes — Allows data to flow from one process to another

`file` command shows the file type. `ls -l` will also show the file type in the first letter of the output.

## Filesystem Hierarchy

- /bin — binaries for external commands like mv, mkdir, date.
- /boot — boot device (e.g. GRUB2) and kernel.
- /dev — special block and character device files for devices like disks and peripherals.
- /etc — stores most configuration files.
- /home — user home directory.
- /lib — (and /lib64) contains shared libraries imported into programs.
- /media — where mounted devices show up like external USB drives `df` shows details about mounted file systems.
- /mnt — temporarily mount external file systems.
- /opt — third party programs.
- /tmp — temporary files.
- /usr — used to contain user home directories but now user applications and data such as Firefox.
- /var — system data like logs.
