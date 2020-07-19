---
title: 02. Accessing the Command Line
description: 
published: true
date: 2020-07-19T08:12:44.175Z
tags: 
editor: markdown
---

# Header
Your content here


> Linux command line is provided by a program called the shell
>
> Prompt is a string that ends with a `$` when a regular user starts `[user@host ~]$` and `[root@host ~]#` when shell is running as the superuser
>

### Commands entered at the shell prompt have three basic parts

+	command
+	options ... flags
+ arguments ... targets

### Logging in to a Local Computer
>
> In Red Hat Enterprise Linux 8, if the graphical environment is available, the login screen will run on the first virtual console, called tty1. Five additional text login prompts are available on virtual consoles two through six. `Ctrl+Alt and a function key (F2 through F6)`
>
> In Red Hat Enterprise Linux 6 and 7 initial graphical environment replaces the login screen on the first virtual console instead of starting on a new virtual console.
>	In Red Hat Enterprise Linux 8, if you log in using the graphical login screen, your graphical environment will start on the first
virtual console that is not currently being used by a login session.
>
> a headless server might have a login prompt provided by its serial console, running on a serial port which is connected to a networked console server for remote access to the serial console.


### Logging in over the Network

> Secure Shell (SSH) provide by OpenSSH as a program get a shell prompt on a remote system.
>
> ssh command encrypts the connection to secure the communication
>
> ssh best practictice include public key authentication `[user@host ~]$ ssh -i mylab.pem remoteuser@remotehost` the private key must have 600 permission, to achive that use chmod 600 mylab.pem
> 
> Each time you connect to a remote host with ssh, the remote host sends ssh its host key to authenticate itself and to help set up encrypted communication. The ssh-agent use ~/.ssh/known_hosts








