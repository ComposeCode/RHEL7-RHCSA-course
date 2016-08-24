# Chapter 2, Section 5: Compression and Archiving Tools

## Compression

Compression tools can be used to compress files in order to save space which in turn makes them faster to transfer. These are used frequently for all kinds of files, including software, configuration files, images and music.

Red Hat Enterprise Linux has many available compression tools, such as bzip2 (bunzip2) and gzip (gunzip). The example below shows you how to create an archive using gzip:

```
[root@uk ~]# gzip /etc/resolv.conf /etc/hosts
[root@uk ~]# cd /etc/
[root@uk etc]# ls | grep .gz
hosts.gz
resolv.conf.gz
```

First we compress the resolv.conf and hosts files in /etc/ are compressed into individual gzip archives. We then verify they have been compressed in the /etc/ directory. To uncompress the files, we run the command:

```
[root@uk ~]# gunzip /etc/hosts.gz
[root@uk ~]# gunzip /etc/resolv.conf.gz
```

The bzip2 command does exactly the same thing, below is an example of using bzip2:

```
[root@uk ~]# bzip2 /etc/resolv.conf /etc/hosts
[root@uk ~]# cd /etc/
[root@uk etc]# ls | grep .gz
hosts.gz
resolv.conf.gz
```

Here is how we uncompress the files using bzip2:

```
[root@uk ~]# bunzip2 /etc/hosts.gz
[root@uk ~]# bunzip2 /etc/resolv.conf.gz
```

## Tar

There are several archiving tools available on RHEL, the most common being tar (also known as tarball). Archive tools can be used to combine several files into one single file to make storage and distribution of files easier. They can also preserve file attributes, ownership, group ownership and timestamp. Tar has several command line options, it is important that you know how to create and extract archives.

The following example creates an archive and then extracts it:

```
[root@uk ~]# tar -cvf /root/etc.tar /etc/ # Create Tar
[root@uk ~]# tar -xvf /root/etc.tar       # Extract Tar
```

Note that the -c option creates an archive, the -x option is used to extract an archive and the -f option is used to specify the tarball to be used or created. The -v option is used to give verbose output. There are many other options which can be viewed in the tar man pages entry.

The most important option is probably -j which adds bzip2 compression to the archive automatically, instead of having to do both the compression and archiving operations individually. The alternative is the -z option which uses gzip compression instead. The -t option can be used to list the files within the tarball.  

## Star

The star command (known as standard tar) adds extra functionality to the regular tar command. It supports SELinux contexts and extended file attributes which are not covered by standard tar. The utility is not installed by default so you will have to install the package first if you intend to use it. The syntax is mostly identical to using tar:

```
[root@uk ~]# star cvf /root/etc.tar -xattr -H=exustar /etc/
[root@uk ~]# star tvf /root/etc.tar
```

The first example creates a tar of /etc/ and preserves the SELinux file contexts in the root home directory. The second extracts the archive in the /root/ home directory. 
