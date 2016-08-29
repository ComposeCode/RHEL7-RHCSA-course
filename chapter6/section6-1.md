# Chapter 6, Section 1: Virtualization

- Explain what virtualization is, explain KVM, QEMU, libvirt.
- Explain benefits of virtulalization.
- Add virtualization diagram
- Explain kickstart

# Checking Virtualization support
- Example of using lscpu for establishing virtualization support  + grep vmx/svm on /proc/cpuinfo
- Installing virtualization yum groups
- Explain the virtual routing virbr0 (NAT, etc)
- Explain storage pool and storage volume
- Explain virtualization management tool

# Using Virtual Machine manager
- Using virtual machine manager/virsh/virt-manager, using virt-install

root@ie networks]# cat default.xml
<network>
  <name>default</name>
  <bridge name="virbr0"/>
  <forward/>
  <ip address="192.168.122.1" netmask="255.255.255.0">
    <dhcp>
      <range start="192.168.122.2" end="192.168.122.254"/>
    </dhcp>
  </ip>
</network>
[root@ie networks]# pwd
/usr/share/libvirt/networks
[root@ie networks]# ls
default.xml

- Exmaples of creating virtual networks, storage pools

# Configuring FTP Server as yum repo
- yum install -y vsftpd
- local_root=...
- firewall-cmd --add-service=ftp --permanent ; firewall-cmd --reload
- /var/ftp/pub/...
- configuring yum file

# Creating a bridge
- example of creating bridge
- brctl to show bridges (brctl show br0)

# installing vm with GUI (virt manager) or through kickstart installation method
- How to setup kickstart via anacoda-ks.cfg
- add url line, url --url="ftp://ip/pub/rhel7/..."
- system-config-kickstart tool can be used
- ksvalidator example

# wget utility
- wget examples 
