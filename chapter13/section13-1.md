# Chapter 13,  Section 1: SSH And TCP Wrappers

- Explain SSH, versions, algorithms, encryption techniques etc.
- explain openSSH packages (what they do etc), explain the different commands

## SSHD + SSH Configuration
- Explain the configuration options for sshd
- explain the configuration options for the ssh client and keys location

## Generating an SSH Key
- Setup ssh key based authentication between two hosts
- Generate ssh key with ssh-keygen
- Use ssh-copy-id -i to move key from 1 machine to another.
- Tail /var/log/secure to check the key authentication has worked

##  TCP Wrappers
- Explain what they are, the package which uses them, syntax
- Give examples of using them (hosts.allow and hosts.deny)
