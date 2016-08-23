# Chapter 2, Section 2: Common Linux Commands

Most Unix systems usually share the same subnet of commands which can be used across different distributions. For example, the ls command (list directory contents) is available on OSX, Ubuntu and Scientific Linux.

```
$ ls
README.md	SUMMARY.md	chapter1	chapter2	rhel7_rhcsa.md
```

Unix commands can be simple or complicated. Most commands have several available options or parameters available which allow the user to modify the output or functionality of the command. For example, the ls command has several different options available:

```
$ ls -S # sort files by size
$ ls -a # include directories beginning with .
$ ls -e # ACL associated with the files, if present, as printed

These  can also be combined:

ls -Sae # does all of the previous options in one command.
```

Another common command is cd which allows the user to change the current working directory. Another command known as pwd allows the user to print the current working directory. The examples below demonstrate how to use these commands:

```
$ pwd
/Users/composecode/Desktop/Source/RHEL7-RHCSA-course-helper
  ...

$ cd /etc
$ ls
  afpovertcp.cfg				fstab.hd				nanorc					profile
  aliases					ftpd.conf				networks				profile~orig
  aliases.db				ftpd.conf.default			newsyslog.conf				protocols
  apache2					ftpusers				newsyslog.d				racoon
  asl					gettytab				nfs.conf				rc.common
  ...

$ cd  # running cd without a directory will take you to the users home directory
```

The pwd command shows the current working directory (in this case, the books source directory) and the cd command shows how we can move into the /etc/ directory and list the files inside it. Another common command is mkdir, known as make directory which can be used to create a directory for files. See the example below on how to use it:

```
$ mkdir test-directory
$ ls
README.md	SUMMARY.md	chapter1	chapter2	rhel7_rhcsa.md	test-directory
```

The output shows the test-directory directory has been created and can be seen in the output. Some machines have several active users running different commands at once. Sometimes it is useful to find out which session we are currently using. The tty command is useful for that purpose:

```
$ tty
/dev/ttys003
```

The output shows which terminal session we are currently using. We can also check who is logged into the system and which of those users we are:

```
$ who
console  Aug 18 10:04
ttys000  Aug 18 10:04
ttys001  Aug 21 01:17
ttys002  Aug 21 01:22
ttys003  Aug 21 01:32

$ who am i
ttys003  Aug 21 01:32
```

As you can see from the output, there are several active terminal sessions on the machine, but the commands are being run from session ttys003. Another very useful command is called w known was what. The what command displays information similar to the who command but it also tells the length of time the user has been idle for, along with CPU utilization and current activity:

```
$ w
 22:36:50 up 2 days,  2:10,  2 users,  load average: 0.04, 0.22, 0.28
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     tty1                      Sat20   34:01m  0.84s  0.84s -bash
root     pts/0    192.168.1.100    Sun21    2.00s  0.03s  0.02s -bash
```

Another very useful command is called uptime, which displays how long a system has been up for, how many users are currently logged in and the average load on the system:

```
$ uptime
22:46:00 up 2 days,  2:19,  2 users,  load average: 0.00, 0.06, 0.18
```

The whoami command is used to show the user executing the command, note the output is slightly different to the who am i command:

```
[root@ie ssh]# whoami
root
[root@ie ssh]# who am i
root     pts/0        2016-08-21 21:30 (192.168.1.100)
```

When logged into a system you can change to another user using the su command. Unix systems typically have a super user account known as root which is usually used for system administration. The principle of least privilege recommends that most users and applications run under an ordinary account to perform their work, as a superuser account is capable of unrestricted, potentially adverse, system-wise changes. For example, a user may log into a system as the user composecode, but may use the su (substitute user) command to change to another use account such as root:

```
$ su root
Password:
[root@ie /]#
```

As you can see, you will be prompted to put in root's password to su to that user. The logname can be used to find the original user which has logged in, even if they have changed their user account using su:

```
[root@ie ~]# logname
composecode
```

The id command can be used to display a user's UID (user identifier), GID (group ID), username, groupname and all secondary groups the user is a member of and finally, the selinux content:

```
[root@ie ~]# id
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

A user may be a member of many different groups. It is common for a user to be a member of the wheel group which grants a user the ability to perform superuser commands in a similar fashion to the root user (https://en.wikipedia.org/wiki/Wheel_(Unix_term)). The groups command can be used to display the list of groups a user belongs to:

```
[composecode@ie ~]$ groups
composecode wheel
```

Another very useful command is known as clear, which can be used to clear the terminal session:

```
[root@ie /]# clear
```
