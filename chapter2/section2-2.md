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

Another common command is mkdir, known as make directory which can be used to create a directory for files. See the example below on how to use it:

```
$ mkdir test-directory
$ ls
README.md	SUMMARY.md	chapter1	chapter2	rhel7_rhcsa.md	test-directory
```

Some machines have several active users running different commands at once. Sometimes it is useful to find out which session we are currently using. The tty command is useful for that purpose:

```
$ tty
/dev/ttys003
```

We can also check who is logged into the system and which of those users we are:

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
