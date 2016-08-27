# Chapter 3, Section 1: RHEL Directory Structure, Filesystems and Partitions

Red Hat Linux follows the File System Hierarchy Standard (FHS - https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for file system organization. This standard defines the directory structure and directory contents in unix-like operating systems and is maintained by the Linux Foundation.  There are two primary types of file system: disk-based which is used as a long term store and memory based which is stores runtime data respectively.

Files themselves can either be static or dynamic. Files can be reference either using absolute paths or relative paths based on where they are stored or being accessed from.

- disk based vs memory based, static/dynamic files, relative or absolute paths.
- Explain file types in more detail
- tree command, file system layout diagram
- explain file command
- explain filesystems vs partitions vs directories
- explain default layout, recommendations
- explain lvm/vg/vgs

There are many different file systems available in Linux. The most common used by RHEL7 is typically XFS, EXT4 or BTRFS. The default RHEL7 installation uses XFS. In accordance with the FHS standard, there are usually two directories created during a default RHEL7 installation: /boot and /. Usually these are put on separate partitions. You can also put other directories, such as /var, /usr and /tmp on other partitions each with their own individual filesystems.

## The Root File System (/)

The root file system (/) is the top level file system in the FHS and contains many other top level directories such as /media and /dev. If you're on a Unix system you can move to the root of the file system by typing cd /, if you then type ls, you will see the list of directories in the root file system which are described below.

Some key directories are:

* /etc - This directory is used to store system configuration files. For example, there are configuration files for your network interfaces, DNS and NTP servers in this directory, along with configuration files for many other services and processes.  
* /root - This is the root user's home directory
* /media - this directory is used by the system to automatically mount removable media (USB Sticks, CD/DVD, etc)
* /mnt -  This directory can be used to mount removable media such as USB Sticks, USB Hard-drives or ISOs.


## The Boot File System (/boot)

Most systems will have the boot directory on a separate partition with its own File System. The recommended minimum size is 500mb and it may be extended to store additional versions of the kernel (if the kernel is upgraded the version changes and previous versions can be kept if issues are found with the new kernel).

## The var File System (/var)

The variable (known as /var) directory is usually put on a separate partition with its own filesystem just like boot. This filesystem frequently changes while the system is operational. It's usally used for holding log files, lock files, spool files and even web pages. All kinds of dynamic data is stored in this file system.

Some notable directories inside /var are:

* /var/log - This directory includes log files, such as messages
* /var/spool - This directory holds queued items: printer jobs, cron jobs, emails, etc.
* /var/tmp - Large temporary files
* /var/www/html - If apache is installed (httpd), webpages default to this directory.

## The usr File System (/usr)

The unix system resources file system contains general files related to the system and is usually mounted as read-only. Some of the software installed on the system is installed there.

Some notable directories inside /usr are:

* /usr/lib - contains shared libraries used by many different commands and programs from /usr/bin, /usr/sbin, the linux kernel and other programs.
* /usr/bin - contains binaries for commands
* /usr/sbin - contains binaries for commands required for system administration and system startup.
* /usr/local - this directory serves as a system administrator repository, storing tools/software from the web, custom software or products written in-house.
* /usr/include - contains C header files
* /usr/src - contains source code
* /usr/share - this directory contains man pages and other documentation, configuration files etc.

## The opt File System (/opt)

The optional file system holds additional software installed on the system. Some companies use /opt for internal or third party tooling like monitoring and auditing software. Opt can also be put on a separate partition or created as an LVM just like /var or /usr. Usually each new piece of software has its own directory created inside /opt.

## The home File System (/home)

The home file system stores user home directories for users apart from root (the root home directory is usually /root). User accounts on a unix system can be given a home directory. For example, if you are creating user accounts with useradd, you can specify the directory by adding the -d option to that command (useradd -d /home/composecode composecode). The home directories should be used to save personal files and each home directory is owned by the user to which the directory is assigned to, access to these directories is not possible for other users by default.

## The devices File System (/dev)

The dev (devices) file system contains device nodes for physical and virtual devices. For example, if you plug in a hard-drive to your machine or cd-rom drive, it should appear in here as a device. The device nodes are created and deleted by the udevd service as devices are removed or added to the system. The device nodes are used by the kernel to communicate with each of the respective devices.

There are two types of device files: raw device files (https://en.wikipedia.org/wiki/Raw_device) and block device files. The Linux Kernel accesses devices using either or both types of device files. Block devices (hard-drives, optical drives, etc) are
accessed in a parallel fashion, with data exchanged in blocks (parallel). Raw devices (printers, keyboards, mice, etc) are accessed in a serially, with streams of bits transferred during kernel and device communication.

This is a virtual file system and it is not usually put onto a separate file system or LV.

## The Proc File System (/proc)

The proc (process) file system is used to maintain information about the state of the kernel. The directory includes details on the system's CPU, memory, disks, partitioning, file systems, networking and processes running on the system.

The file system contains thousands of zero length files which are pointers to data structures maintained by the kernel in system memory. The kernel automatically manages this file system and it should not be tampered with unless absolutely required.

The content of proc are populated at boot time and are updated during run-time by the system. When the system is shut down, the contents of proc are destroyed. There are some useful files in this directory, such as meminfo and cpuinfo, For example:

```
cat /proc/cpuinfo # will give you information about your processor
```

Some other system utilities use this file system for monitoring or to report on system performance, such as top, ps or vmstat. This is a virtual file system and it is not usually put onto a separate file system or LV.

## The System File System (/sys)

The system file system (known as /sys) contains information about hotplug hardware and is maintained in the /sys file system. The information in this file system is automatically maintained and it acts as a reference for loading kernel modules and creating device nodes in the /dev/ file system. This is a virtual file system and it is not usually put onto a separate file system or LV.

## The temporary File System (/tmp)

The temporary file system is used for storing temporary files and data. It is sometimes used by automated installers for third party or in-house tooling. The contents of the temp file system are deleted automatically when the system is turned off or rebooted.


## Symbolic Links (known as Symlinks)

Symbolic links are used to create 'short-cuts' to another file or directory. For example, you may have a file which is generated by Process A in directory /tmp/ but want Process B to access that file in /home/composecode/, you could create a symbolic link (known as a symlink) to that file in /home/composecode which can be used to edit the file. If you run the ll command on a symbolically linked file or directory, the output will show that it is both a link (denoted by the letter l at the start of the output) and that an arrow points to the original file/directory the link is pointing to. You can also use the file command to verify if a file is a symlink or otherwise.

## Device Files

For each piece of hardware in your Linux machine there is a special device file used by the kernel to communicate with that hardware. As mentioned previously, these can either be raw or block device files. If you go into the /dev file system and run the ll command, you will notice that some files are denoted with a 'c' character and some are denoted with a 'b'. The files with 'b' are block device files, where as the device files with 'c' are character/raw device files. Also as previously mentioned, the file command can be used to work out if a file is block or character/raw device file.
