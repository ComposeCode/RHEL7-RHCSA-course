# Chapter 7 Section 12: Configuring the Network Configuration

- example of setting hostname with hostname and hostnamectl
- example of uname -n, cat /etc/hostname, nmcli general hostname ...

- ipv4 address with example commands: ip addr
- explain ifconfig deprecation, explain subnetting, subnet mask, protocols (cat /etc/protocols)
- briefly explain udp/tcp protocols
- example of ip neighbor (arp)
- explain interface naming, explain interface configuration file, location, examples

# Interface administration commands
- network manager tools/service give examples of: ifdown/ifup/ip/nmcli/nmtui
- Explain the different directives in the eth0
- Example of adding a nic and configuring it (using text files and nmcli)
- Using ping to verify connectivity (dont forget firewall rules)

# Configuring NTP
- installing ntp system-config-date packages
- changing ntp config, enabling service, starting service, testing service with ntpq -p

# OpenLDAP
- Explain OpenLDAP Client, explain trees, protocol, format etc.
- installing openldap openldap-clients nss-pam-ldapd sssd authconfig
- configuring and setting up LDAP Client with authconfig-tui
- using getend group groupname to verify group creation 
