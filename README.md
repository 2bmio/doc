---
title: Wellcome!
description: wellcome page!
published: true
date: 2020-12-17T09:43:19.587Z
tags: 
editor: markdown
dateCreated: 2020-06-04T21:54:00.081Z
---

# wellcome!
never end story>

# ·····
https://speech-to-text-demo.ng.bluemix.net/

# ·····
VIRT-SYSPREP: RESETTING VIRTUAL MACHINE SETTINGS

https://libguestfs.org/virt-sysprep.1.html

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-guest_virtual_machine_disk_access_with_offline_tools-using_virt_sysprep

# ·····

https://free-snippets.com/2020/09/07/installing-rhvh-on-uefi-hardware-using-pxe-boot-2-3/

# ·····

https://vnugget.com/

# ·····

https://www.techbeatly.com/2018/06/setup-your-vim-editor-for-ansible-playbook.html

# ·····

https://vim.fandom.com/wiki/Moving_around

# ·····

https://learnvimscriptthehardway.stevelosh.com/

# ·····

https://thoughtbot.com/blog/how-to-edit-an-existing-vim-macro

# ·····


https://medium.com/@schtoeffel/you-don-t-need-more-than-one-cursor-in-vim-2c44117d51db

# ·····


https://github.com/mingrammer/diagrams


# ·····

https://github.com/glutanimate/review-heatmap#installation


# ·····


https://github.com/Huion-Linux/DIGImend-kernel-drivers-for-Huion/issues/4



# ·····


https://gist.github.com/Deevad/51820854ffd5ea5cd883


# ·····

https://pritunl.com/

# ·····

https://youtu.be/WAjy6K3kUC0?t=7145

# ·····

https://fedoramagazine.org/getting-started-with-fedora-coreos/


# ·····

1. First contact
cat /etc/*-release
uname -a
hostnamectl
uptime
2. Is anyone else on board?
who
who -Hu
grep sh$ /etc/passwd
3. Physical or virtual machine
dmidecode -s system-manufacturer
dmidecode -s system-product-name
lshw -c system | grep product | head -1
cat /sys/class/dmi/id/product_name
cat /sys/class/dmi/id/sys_vendor
4. Hardware
lscpu or cat /proc/cpuinfo
lsmem or cat /proc/meminfo
ifconfig -a
ethtool ##devname##
lshw
lspci
dmidecode
5. Installed software
rpm -qa
rpm -qa | grep ##pkgname##
rpm -qi ##pkgname##
yum repolist
yum repoinfo
yum install ##pkgname##
ls -l /etc/yum.repos.d/
6. Running processes and services
pstree -pa 1
ps -ef
ps auxf
systemctl
7. Network connections
netstat -tulpn
netstat -anp
lsof -i
ss
iptables -L -n
cat /etc/resolv.conf
8. Kernel
uname -r
cat /proc/cmdline
lsmod
modinfo ##module##
sysctl -a
cat /boot/grub2/grub.cfg
9. Logs
dmesg
tail -f /var/log/messages
journalctl

# ·····

