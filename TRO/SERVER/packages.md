---
title: Packages
description: 
published: true
date: 2020-10-12T18:04:59.977Z
tags: 
editor: markdown
dateCreated: 2020-10-12T18:04:59.977Z
---

# pfSense
Your content here


# Named/Bind9

> values on this example:
> domain: example.com
> network: 192.168.1.0

Commands: `named-checkconf` for check named status

+ edit: /etc/named.conf
```
vim /etc/named.conf

allow-query { localhost; 192.168.1.0/24; };
include "/etc/named/named.conf.local";
```

+ create: /etc/named/named.conf.local
```
vim /etc/named/named.conf.local

zone "example.com" {
        type master;
        file "/etc/named/example.com.hosts";
        };
zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/named/192.168.1.rev";
        };
```

+ create: /etc/named/example.com.hosts
```
vim /etc/named/example.com.hosts

$ttl 38400
example.com.     IN      SOA     iop. admin.example.com. (
                        1602359933
                        10800
                        3600
                        604800
                        38400 )
example.com.     IN      NS      iop.
host-01.example.com.       IN      A       192.168.1.1
host-02.example.com.       IN      A       192.168.1.2
host-03.example.com.       IN      A       192.168.1.3
```

+ create: /etc/named/192.168.1.rev
```
vim /etc/named/192.168.1.rev

$ttl 38400
1.168.192.in-addr.arpa. IN      SOA     iop. admin.example.com. (
                        1602359968
                        10800
                        3600
                        604800
                        38400 )
1.168.192.in-addr.arpa. IN      NS      iop.
1.1.168.192.in-addr.arpa.     IN      PTR     host-01.example.com.
2.1.168.192.in-addr.arpa.     IN      PTR     host-02.example.com.
3.1.168.192.in-addr.arpa.     IN      PTR     host-03.example.com.
```



