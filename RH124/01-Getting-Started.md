---
title: 01. Getting Started
description: 
published: true
date: 2020-07-19T05:02:37.339Z
tags: 
editor: markdown
---

# PRIMEROS PASOS CON RED HAT ENTERPRISE LINUX

## Primeros pasos con Red Hat Enterprise Linux
https://access.redhat.com/products/red-hat-enterprise-linux#getstarted

## El enfoque de código abierto
https://opensource.com/open-source-way

# ENLACES OFICIALES DE CURSOS Y EXÁMENES

--------------
CURSOS
--------------
  RH124: https://www.redhat.com/en/services/training/rh124-red-hat-system-administration-i

  RH134: https://www.redhat.com/en/services/training/rh134-red-hat-system-administration-ii	

  RH294: https://www.redhat.com/en/services/training/rh294-red-hat-system-administration-iii-linux-automation

  RH318: https://www.redhat.com/en/services/training/rh318-red-hat-virtualization

-------------------
EXÁMENES
-------------------
  EX200 (RHCSA): https://www.redhat.com/en/services/training/ex200-red-hat-certified-system-administrator-rhcsa-exam

  EX294 (RHCE): https://www.redhat.com/en/services/training/ex294-red-hat-certified-engineer-rhce-exam-red-hat-enterprise-linux-8

  EX318 (RHC Specialist in Virtualization): https://www.redhat.com/en/services/training/ex318-red-hat-certified-specialist-virtualization-exam
  

### System-wide Default Language Settings
```
localectl(1)
vconsole.conf(5)

localectl
localectl set-locale LANG=fr_FR.urt8
/etc/locale.conf
```

### Language Packs
```
locale(7), localectl(1), locale.conf(5), vconsole.conf(5), unicode(7), and utf-8(7) man pages

yum list langpacks-*
yum install langpacks-fr
yum repoquery --whatsupplements langpack-fr
```

### What is Open Source Software?

>  Is software with source code that anyone can use, study, modify, and share
> They grant the user the right to run the program and also to view, modify, compile, and redistribute the source royalty-free to others

### Types of Open Source Licenses

+ Copyleft licenses that are designed to encourage keeping code open source
	+ GNU General Public License (GPL)
	+ Lesser GNU Public License (LGPL)
+ Permissive licenses that are designed to maximize code reusability.
	+ MIT/X11 license
	+ Simplified BSD
	+ Apache Software License 2.0


### Who Develops Open Source Software?

> Open source development today is overwhelmingly
professional.

### Who is Red Hat?

> Red Hat's mission is to be the catalyst in communities of customers, contributors, and partners creating better technology the open source way

### What is a Linux distribution?
> Distributions generally have many common characteristics:
>
> Distributions consist of a Linux kernel and supporting user space programs.
>
> Distributions can be small and single-purpose or include thousands of open source programs.
>
> Distributions must provide a means of installing and updating the distribution and its components.
>
> The provider of the distribution must support that software, and ideally, be participating directly in the community developing that software.


### Development of Red Hat Enterprise Linux

> Red Hat develops and integrates open source software into RHEL through a multistage process:
>
> Red Hat participates ... Upstream Porjects
>
> Red Hat sponsors and integrates ... Community Platforms
>
> Red Hat stabilizes ... support products platdorms, and solutions
>






