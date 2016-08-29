# Chapter 11 Section 1: SELinux and Firewall configuration

- Explain firewall and difference between iptables and firewalld, with diagram
- enabling and stopping the firewall, disabling the service
- Examples of adding service, adding individual ports (firewalld and iptables)
- Give examples of reload/restarting the firewall service
- Examples of removing/disabling ports
- List the possible firewall-cmd commands (list-ports, list-interfaces)


## Explain SELinux

- Explain SELinux
- id command + examples (id -Z)
- disabling/enabling selinux, temporary, checking log
- yum install setools-console package for seinfo
- semanage login -l command (view mappings)
- ps -eZ for processes (list selinux contents for processes)
- ll -Z /etc/passwd (selinux contents for files)
- explain selinux contexts on ports, setting contexts on ports (semanage ports -l)
- explain and give example of using getsebool + setsebool (semanage boolean -l to list usage of bools)
- explain and give examples of chcon, restorecon, matchpathcon
- explain and give examples of status, modifying user contexts
- changing the selinux content on a file example (semanage fcontent -a -s user_u -t public_content_t /root/file1), -a add fcontext with specifed user and type
- example of changing selinux content on root home and verifying change
- example of adding and removing ports from selinux (semanage port -a -t port_type -p tcp 8010, semanage port -d  -ty http_port_t -p tcp 8010)
- example of copying files with preserved selinux context (cp --preserve=context /root/xxx /root/) ...

## Analyzing SELinux Alerts
- yum install setroubleshoot-server for the sealert command 
