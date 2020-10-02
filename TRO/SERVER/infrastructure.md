---
title: Infrastructure
description: 
published: true
date: 2020-10-02T18:52:11.537Z
tags: 
editor: markdown
dateCreated: 2020-09-30T22:53:48.754Z
---

# Infrastructure
····


## Ovirt / RHEV

### Update and Upgrade

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

## Proxmox


