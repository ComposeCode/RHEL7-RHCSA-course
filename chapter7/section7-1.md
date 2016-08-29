# Chapter 7 Section 1: Linux boot process

- Explain RHEL7 boot process and replacing init/upstart with systemd
- Explain each phase: Firmware phase > grub phase > kernel phase (ramdisk) > initialization phase
- Explain system startup 0

# Kernel version and file structure
- using uname and determining version
- upgrading kernel

[root@ie ~]# cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.10.0-327.28.3.el7.x86_64 root=/dev/mapper/vg00-root ro rd.lvm.lv=vg00/swap crashkernel=auto rd.lvm.lv=vg00/usr rd.lvm.lv=vg00/root rhgb quiet LANG=en_GB.UTF-8
[root@ie ~]# cat /proc/version
Linux version 3.10.0-327.28.3.el7.x86_64 (mockbuild@x86-037.build.eng.bos.redhat.com) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-4) (GCC) ) #1 SMP Fri Aug 12 13:21:05 EDT 2016

# Kernel modules
- lsmod, modprobe, cat /proc/modules
- modinfo, depmod

# Grub
- Give introduction to grub
- modifying grub at boot time for password reset, other issues (grub2-mkconfig /boot/grub2/grub.cfg and /boot/efi/EFI/redhat/grub.cfg)
- grub2-set-default 1

# Resetting root password example
- chroot /sysroot
- mount -o remount,rw /
- passwd
- touch /.autorelabel
- exit
- reboot

# fstab
chroot /sysroot
mount -o remount,rw /
modify fstab
touch ./autorelabel
exit
reboot

# System D Units
- example of pstree (pstree -p and pstree -u)
- example of pkg-config (display systemdsystem unit directory and userconf directory)
- make note of special units created and destroyed at run time in /etc/rc.d/init.d
- describe some  unit types
- systemd-analyze
- systemd-analyze blame (work out how long processes took to start)

# Control groups
- explain and give examples of control groups (cgroups)
- systemd-cgls, systemctl-cgtop
- systemctl show -p BlockIOWeight -p CPUShares atd
- systemctl set-property atd BlockIOWeight=200 CPUShares=256

# Systemctl command
- explain systemctl commands and give examples
- systemctl get-default
- systemctl set-default graphical.target
- systemctl set-default multi-user.target
- systemctl halt (shutdown to halt state)
- systemctl poweroff (shutdown system)
- systemctl reboot (reboot the system)
- systemctl hybrid-sleep (put machine in sleep.)


# Shutdown command
- examples of shutdown shutdown -P 20 etc

# System logging
- starting and enabling rsyslog service
- rsyslog conf examples
- rsyslogd -N 1 (to check for errors)

# Logrotate
- explain log rotate and cron job, log rotation config
- custom log rules example

# Boot log file
- explain /var/log/boot.log

# Journalctl
- explain the journal and Journalctl
- show examples of using journactl (journalctl -f, journalctl -o verobose, journalctl -b etc)
