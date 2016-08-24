# Chapter 2, Section 3: Simple User History

The last command can be used to report the recent history of successful logins attempts on a system. It shows their username, ip address and the time they logged in:

```
[composecode@ie ~]$ last
composecode pts/0        192.168.1.100    Tue Aug 23 14:59   still logged in   
root     pts/0        192.168.1.100    Sun Aug 21 21:30 - 14:59 (1+17:28)   
root     pts/0        192.168.1.100    Sun Aug 21 21:24 - 21:29  (00:04)    
root     tty1                          Sat Aug 20 20:27   still logged in   
reboot   system boot  3.10.0-327.28.3. Sat Aug 20 20:26 - 15:52 (2+19:26)   
root     tty1                          Sat Aug 20 12:59 - 20:26  (07:26)    
reboot   system boot  3.10.0-229.el7.x Sat Aug 20 12:58 - 15:52 (3+02:54)   

wtmp begins Sat Aug 20 12:58:19 2016
```

You can also use the last command to find out the last time a specific command was run, such as reboot:

```
$ last reboot
reboot   system boot  3.10.0-327.28.3. Sat Aug 20 20:26 - 16:16 (2+19:50)   
reboot   system boot  3.10.0-229.el7.x Sat Aug 20 12:58 - 16:16 (3+03:18)   

wtmp begins Sat Aug 20 12:58:19 2016
```

Another command can be used to check the recent history of bad login attempts:

```
[root@ie /]# lastb
calvinha ssh:notty    192.168.1.100    Sun Aug 21 21:24 - 21:24  (00:00)    
calvinha ssh:notty    192.168.1.100    Sun Aug 21 21:13 - 21:13  (00:00)    
root     tty1                          Sat Aug 20 12:59 - 12:59  (00:00)    

btmp begins Sat Aug 20 12:59:30 2016
```

The command lastlog can be used to display the last login time for all users. Note that some user accounts are functional accounts used for various system services such as apache.

```
[root@ie /]# lastlog
Username         Port     From             Latest
root             pts/0                     Tue Aug 23 16:18:03 +0100 2016
bin                                        **Never logged in**
daemon                                     **Never logged in**
adm                                        **Never logged in**
lp                                         **Never logged in**
sync                                       **Never logged in**
shutdown                                   **Never logged in**
halt                                       **Never logged in**
mail                                       **Never logged in**
operator                                   **Never logged in**
games                                      **Never logged in**
ftp                                        **Never logged in**
nobody                                     **Never logged in**
avahi-autoipd                              **Never logged in**
dbus                                       **Never logged in**
polkitd                                    **Never logged in**
tss                                        **Never logged in**
postfix                                    **Never logged in**
sshd                                       **Never logged in**
composecode        pts/0    192.168.1.100    Tue Aug 23 14:59:47 +0100 2016
systemd-bus-proxy                           **Never logged in**
systemd-network                            **Never logged in**
saslauth                                   **Never logged in**
qpidd                                      **Never logged in**
postgres                                   **Never logged in**
qdrouterd                                  **Never logged in**
squid                                      **Never logged in**
apache                                     **Never logged in**
mongodb                                    **Never logged in**
unbound                                    **Never logged in**
tomcat                                     **Never logged in**
foreman-proxy                              **Never logged in**
puppet                                     **Never logged in**
```

Finally, the history command can be used to display the recent commands executed by the current user:

```
[root@ie composecode]# history
    1  subscription-manager register
    2  subscription-manager attach --auto
    3  yum update -y
    4  subscription-manager repos --disable=*
    5  subscription-manager repos --enable=rhel-7-server-rpms
    6  yum update -y
    7  reboot
    9  ssh 192.168.1.111
   10  ssh 192.168.1.1
   12  yum install nslookup
   14  yum install nslookup -y
   15  yum install bind-utils -y
   ...
[root@ie composecode]#
```
