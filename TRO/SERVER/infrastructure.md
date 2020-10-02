---
title: Infrastructure
description: 
published: true
date: 2020-10-02T17:03:01.295Z
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

### Something went wrong, connection is closed

```
```


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


