---
title: home
description: 
published: true
date: 2020-06-25T20:46:00.245Z
tags: 
editor: markdown
---

# home
Your content here





### Anki Recommended Settings

```
New Cards
    Steps in minutes    15 1440 8640
    Order               random
    New Cards/day       50
    Graduating interval 15
    Easy intervals      60
Reviews
    Maximum reviews/day 9999
    Maximum interval    90
Lapses
    Steps               20
    New interval        70%
    Minimum interval    2
    Leech action        Tag Only
```



### Extending a Linux file system after resizing a volume

#### Extending a partition (if needed)

```
bot@dev-1:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  120G  0 disk
├─sda1   8:1    0    1M  0 part
└─sda2   8:2    0   70G  0 part /

bot@dev-1:~$ sudo growpart /dev/sda 2
  CHANGED: partition=2 start=4096 old: size=146794496 end=146798592 new: size=251654111 end=251658207

bot@dev-1:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  120G  0 disk
├─sda1   8:1    0    1M  0 part
└─sda2   8:2    0  120G  0 part /
```

#### Extending the file system

```
bot@dev-1:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        69G   12G   54G  18% /

bot@dev-1:~$ sudo resize2fs /dev/sda2
resize2fs 1.45.5 (07-Jan-2020)
  Filesystem at /dev/sda2 is mounted on /; on-line resizing required
  old_desc_blocks = 9, new_desc_blocks = 15
  The filesystem on /dev/sda2 is now 31456763 (4k) blocks long.

bot@dev-1:~$ df -h
/dev/sda2       118G   12G  101G  11% /
```



# VSCode 
VScodium are now using open-vsx.org as extension gallery.
```
# to back swtich the extension gallery

sudo vim /usr/share/vscodium-bin/resources/app/product.json

"extensionsGallery": {
    "serviceUrl": "https://marketplace.visualstudio.com/_apis/public/gallery",
    "itemUrl": "https://marketplace.visualstudio.com/items"
}

```