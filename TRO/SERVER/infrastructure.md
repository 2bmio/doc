---
title: Infrastructure
description: 
published: true
date: 2020-10-12T17:46:28.572Z
tags: 
editor: markdown
dateCreated: 2020-09-30T22:53:48.754Z
---

# Infrastructure
····


## Ovirt / RHEV


### Automate virtual machine deployment with Ansible: Design


```
pip install ansible Jinja2 ovirt-engine-sdk-python --user
```


### Update/Upgrade

```
engine-upgrade-check
hosted-engine --vm-status
yum update ovirt\*setup\*
```

### VNC consoles are returning "Something went wrong, connection is closed" while doing a minor update

> In my case this issue was related whit the **CA Certificate** that you need to add on your browser before upload .iso files or use the novpn service. You can get this certificate from the main site https://engine-instance.ltd/ovirt-engine/ under the **Download column**.
> 
> And If you want to available the service, use this code on your engine instance:
> 
> engine-setup --otopi-environment="OVESETUP_CONFIG/websocketProxyConfig=bool:True"
> 
> ref: https://www.ovirt.org/develop/release-management/features/virt/novnc-console.html
> 
{.is-success}


### VM stuck in "Migrating to" or "Shutting down"


Install the query package engine

```
    yum install engine-db-query
```

Get the id of the VM where xxx  → name of machine

```
    engine-db-query --statement "select vm_guid status from vm_static where vm_name='xxx';"
```

Forece turn off the machine where yyy → vm_guid

```
engine-db-query --statement "update vm_dynamic SET status=0 where vm_guid='yyy';"
```




---
---
---




## Proxmox

### Guide to GPU Passthrough on VMs
https://www.reddit.com/r/homelab/comments/b5xpua/the_ultimate_beginners_guide_to_gpu_passthrough/

```
echo "options vfio-pci ids=10de:128b,10de:0e0f disable_vga=1"> /etc/modprobe.d/vfio.conf

cd /sys/bus/pci/devices/0000:02:00.0/
echo 1 > rom
cat rom > /usr/share/kvm/AsusGeForceGT710B.2048.bin
echo 0 > rom
```
```
# vim /etc/pve/qemu-server/XXX.conf
hostpci0: 02:00,pcie=1,/usr/share/kvm/AsusGeForceGT710B.2048.bin
```


---
---
---





