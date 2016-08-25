# Chapter 3, Section 1: RHEL Directory Structure, Filesystems and Partitions

Red Hat Linux follows the File System Hierarchy Standard (FHS - https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for file system organization. This standard defines the directory structure and directory contents in unix-like operating systems and is maintained by the Linux Foundation.  There are two primary types of file system: disk-based which is used as a long term store and memory based which is stores runtime data respectively.

Files themselves can either be static or dynamic. Files can be reference either using absolute paths or relative paths based on where they are stored or being accessed from.

- disk based vs memory based, static/dynamic files, relative or absolute paths.
- tree command, file system layout diagram
- explain filesystems vs partitions vs directories
- explain default layout, recommendations

There are many different file systems available in Linux. The most common used by RHEL7 is typically XFS, EXT4 or BTRFS. The default RHEL7 installation uses XFS. In accordance with the FHS standard, there are usually two directories created during a default RHEL7 installation: /boot and /. Usually these are put on separate partitions. You can also put other directories, such as /var, /usr and /tmp on other partitions each with their own individual filesystems.

## The Root File System (/)

The root file system (/) is the top level file system in the FHS and contains many other top level directories such as /media and /dev. Some key directories are:

/etc - This directory is used to store system configuration files. For example, there are configuration files for your network interfaces, DNS and NTP servers in this directory, along with configuration files for many other services and processes.  

/root - This is the root user's home directory

/media - This directory can be used to mount removable media such as USB Sticks, USB Hard-drives or ISOs

/mnt -
