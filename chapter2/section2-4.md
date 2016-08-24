# Chapter 2, Section 4: System Information

Sometimes you will need to check the kernel version of the current system you are on which can be obtained using uname:

```
[root@ie composecode]# uname
Linux
[root@ie composecode]# uname -a
Linux rhel7.composecode.com 3.10.0-327.28.3.el7.x86_64 #1 SMP Fri Aug 12 13:21:05 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux
[root@ie composecode]#
```

You might also want to check the version of RHEL which is currently being used, you can do this by using the cat command on /etc/redhat-release:

```
[root@ie composecode]# cat /etc/redhat-release
Red Hat Enterprise Linux Server release 7.2 (Maipo)
```

The cat command is short for concatenate and can be used to combine text files together. The uanme command can also be used to obtain other hardware information such as operating systen name, processor type and the release date/time of the kernel which is currently being used.

RHEL7 now has a new command line tool for modifying the system's hostname known as hostnamectl. The example below shows how to print the system's hostname, the second command will set the system's hostname:

```
[root@ie /]# hostnamectl
   Static hostname: rhel7.composecode.com
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 1522f06ee6324d07bf5d06f00d61471c
           Boot ID: ae26c728fe0141c68dfd164c3b3bc33e
    Virtualization: kvm
  Operating System: Employee SKU
       CPE OS Name: cpe:/o:redhat:enterprise_linux:7.2:GA:server
            Kernel: Linux 3.10.0-327.28.3.el7.x86_64
      Architecture: x86-64
[root@ie /]# hostname set-hostname rhel7.composecode.com

```

At some point you will probably want or need to change the system's date and time. This is usually the case if you're moving machines from country to country or working on severs in several geographic regions:

```
[root@ie /]# timedatectl
      Local time: Tue 2016-08-23 17:57:02 BST
  Universal time: Tue 2016-08-23 16:57:02 UTC
        RTC time: Tue 2016-08-23 16:57:02
       Time zone: Europe/London (BST, +0100)
     NTP enabled: n/a
NTP synchronized: no
 RTC in local TZ: no
      DST active: yes
 Last DST change: DST began at
                  Sun 2016-03-27 00:59:59 GMT
                  Sun 2016-03-27 02:00:00 BST
 Next DST change: DST ends (the clock jumps one hour backwards) at
                  Sun 2016-10-30 01:59:59 BST
                  Sun 2016-10-30 01:00:00 GMT
```

You can set the set the time using the same command with the set-time option:

```
[root@ie /]# timedatectl set-time 2015-08-23
[root@ie /]# timedatectl set-time 19:06
[root@ie /]# date
Sun 23 Aug 19:06:02 BST 2015
```

You can also use it to change the timezone:
```
[root@ie /]# timedatectl list-timezones
Africa/Abidjan
Africa/Accra
Africa/Addis_Ababa
Africa/Algiers
Africa/Asmara
Africa/Bamako
Africa/Bangui
Africa/Banjul
Africa/Bissau
Africa/Blantyre
Africa/Brazzaville
Africa/Bujumbura
...
[root@ie /]# timedatectl set-timezone Africa/Accra
```

To display the path of a command, use the which command. For example, we can display the path of the timedatectl command:

```
[root@ie /]# which timedatectl
/bin/timedatectl
```

The command lspci will display information about all connected PCI devices, you can also use lsusb and lscpu to list usb devices and processors. You can also use -v to make the output

```
[root@uk /]# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 44
Model name:            Intel(R) Xeon(R) CPU           E5620  @ 2.40GHz
Stepping:              2
CPU MHz:               2399.972
BogoMIPS:              4799.94
Hypervisor vendor:     KVM
Virtualization type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              12288K
NUMA node0 CPU(s):     0
```
