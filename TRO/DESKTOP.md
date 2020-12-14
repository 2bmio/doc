---
title: Desktop
description: 
published: true
date: 2020-12-14T06:52:21.398Z
tags: 
editor: markdown
dateCreated: 2020-09-30T22:08:35.997Z
---

# tiling
windoww manager


# floating
windoww manager


## Gnome

###  VSCode is opened instead of system path

```
vim ~/.config/mimeapps.lis

[Default Applications]
inode/directory = org.gnome.Nautilus.desktop
```


## Brightness

```
xrandr -q
xrandr -q | grep ' connected' | head -n 1 | cut -d ' ' -f1

# 0.7 refers the 70% 
xrandr --output HDMI-1 --brightness 0.7
# to back on 100% use 1 
xrandr --output HDMI-1 --brightness 1.0
```

