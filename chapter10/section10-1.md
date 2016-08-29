# Chapter 10 Section 1: File Systems and Swap

- Explain what file systems are
- Explain different types of file systems with a table
- Explain disk-based vs network-based bs memory based

# XFS File System
- Explain the xfs file system

# EXT File Systems
- Explain the extended file systems

# VFAT File System
- Explain vFAT File System

# File System Administration Commands
- Give examples of dumpe2fs, e2fsck, e2label
- Give Examples of mke2fs/mkfs.xfs etc
- Give examples of resize2fs, tune2fs
- Give examples of xfs_info, xfs_repair, xfs_admin
- Give examples of df, du, blkid, findmnt, mount, umount, fuser

# The mount command
- Explain and give examples of mount with numerous options: async, acl, atime, auto, defaults, remount, (rw) etc.

# Determining a filesystem UUID

- Give examples and explain:
- xfs_admin -u /dev/sda1
- blkid /dev/sda1
- grep boot /etc/fstab

# Labelling a file system
- Give examples and explain:
- xfs_admin -l /dev/sda1
- umount file system first (umount /boot for example)
- xfs_admin -L bootfs /dev/sda1 (bootfs will be the new label)
- mount /boot

# Automatically mounting a file systen at boot time (editing fstab)
- give examples, explain how it can break the system

# File System Usage
- Explain what df and du show, how they can be monitored

# Examples of creating mounting, unmounting partitions and file systems (ext, xfs, vfat)

- VFAT through parted (mklabel msdos, mkpart fat32)

# Repairing damaged EXT and XFS File Systems
- EXT: umount file system, run e2fsck to determine logical voume device file, dumpe2fs to get backedup superblocks, fsck on superblocks to repair the primary superblock, Remount file system

- XFS: unmount file system, run xfs_repair on /dev/vg_name/lv_name, remount file system

# Mounting remote file systems (nfs, CIFS, iSCSI, etc)
- Example of mounting nfs: yum install nfs-utils
- mkdir /nfsmountpoint
```
- fstab entry for nfs: 192.168.1.1:/nfsmountpoint /nfsmountpoint nfs _netdev 0 0
```
- mount the file system mount -t nfs 192.168.0.1:/nfsmount /nfsmount
- etc...


- Example of mounting CIFS File System:
- Install yum -y install samba-client cifs-utils
- log onto share with smbclient: //192.168.0.110/someshare -U user
- make mountpooint mkdir /someshare
- mount the share: mount //192.168.0.1/someshare /someshare -o username=user
- check through df and mount to check it has been mounted
- modify the share to set the credentials /etc/samba/someshare:
```
/etc/samba/someshare
username: user
password: password
```

- set root ownership on config file
chown /etc/samba/share and chroot 0400 /etc/samba/share

- create a file on the samba share and check it has worked
- unmount file system, reboot, check it is still mounted

## autofs

- explain benefits of autofs
- example of using autofs
- yum install autofs
- explain master map file

## Using AUTOFS To Mount NFS Share with a Direct Map
- explain direct map
- example of using a direct map:
- yum install autofs nfs-utils
- mkdir /autodir (create the mount point autodir if it does not already exist)
- edit the /etc/auto.master file and add the entry if it does not exist: /- /etc/auto.direct
- create an /etc/auto.direct file and add the mount point: /autodir server1.example.com:/nfsrhcsa
- systemctl enable autofs, systemctl start autofs, check the mounts and status of the service.

## Using AutoFS with an Indirect Map
- explain indirect map examplel with autofs
- install autofs as per usual...
- make sure mountpoint is available /autodir
- Edit the /etc/auto.master and ensure that the following indriect map entry is defined: /misc /etc/auto.misc
- Edit the /etc/auto.misc file and add: autodir server1.example.com:/somenfs
- check mounts etc, enable services as per usual


## Automounting User Home Directories
-   indirect map in /etc/auto.home (* -nfs4,rw &:/home/&)
-   etc the /etc/auto.master to use the new map file /home /etc/auto.home
-   restart autofs service


## Swap
- Determining free swap space with free -h example
- cat /proc/meminfo (alternative)
- Example for creating swap on regular partition: mkswap /dev/sda1
- Example for creating swap on lvm partition: mkswap /dev/vg10/swapvol
- Turn the swap on afterwares: swapon /dev/sda1
- Use vmstat to work out the free virtual memory
- Add swap partition to fstab !!!

- Example of removing swap space
- Swapoff, remove partitions

## Access Control Lists (ACLS)
- Explain ACLs and give examples of ACL commands: chacl, getfacl, setfacl
- Explain ACL Rule syntax and structure.
- Explain setfacl commands (removing acl etc)
- Explain the role of the mask value on the ACL
- Examples of setting, deleting, determining acls
- Explain user/group/mask/other
- Remember to set default to acl on fstab and remount file system: (mount -o remount,acl /home)
