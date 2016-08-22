# Chapter 2, Section 1: SSH (Secure Shell)

RHEL Systems can be accessed in multiple ways, the most common way is through the use of secure shell. Secure Shell is a cryptographic network protocol which can be used to work remotely on Linux and other Unix systems. SSH provides a secure channel over an unsecured network through a client-server architecture. More information around the Secure Shell protocol can be found on Wikipedia (https://en.wikipedia.org/wiki/Secure_Shell).

Most distributions of Windows do not come with an SSH client, so a free tool like PuTTY must be downloaded (http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html). For newer versions of Windows, such as Windows 10, Microsoft provide a Linux Bash Shell which can be installed which should provide an SSH client out of the box (https://msdn.microsoft.com/en-us/commandline/wsl/about).

Most Unix systems including RHEL and OSX machines will come with an SSH client which can usually be accessed through the terminal. On OSX, the Terminal should be available from the Applications menu under utilities. On other Unix distributions, the terminal will be found in various different places depending on which desktop environment you have installed (Gnome, KDE, XFCE etc). Once your terminal is open, type man ssh to read the SSH manual page.

You can SSH to a machine based on hostname or ip address, the following example shows an attempt to make an SSH connection to the host with ip 192.168.1.114:

```
$ ssh 192.168.1.114
The authenticity of host '192.168.1.114 (192.168.1.114)' can't be established.
ECDSA key fingerprint is SHA256:yNPABygzPkJCSLEdd5hh5lbqO+zb0Qq1hp1j3VW4Ths.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.114' (ECDSA) to the list of known hosts.
composecode@192.168.1.114's password:
```

You will be promoted to accept the finger print of hosts public key which usually gets put into a file in the user's home directory. On CentOS/RHEL it would most likely be (/root/.ssh/known_hosts or /home/composecode/.ssh/known_hosts). On OSX, this will most likely be /Users/composecode/.ssh/known_hosts. The fingerprint is usually based on the file /etc/ssh/ssh_host_ecdsa_key.pub on the machine you're trying to connect to.

If you wish to log in as different user, you can do this in two different ways:

```
$ ssh root@192.168.1.114
$ ssh -l kittens@192.168.1.114
```

If you wish to run graphical tools like gnome-calculator, you can do so by using the -X option as shown below:

```
$ ssh -X 192.168.1.114
```
