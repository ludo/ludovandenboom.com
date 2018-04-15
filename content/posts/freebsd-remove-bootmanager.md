+++
title = "FreeBSD: Remove Bootmanager"
authors = ["ludo"]
description = ""
tags = []
date = "2009-02-21T10:00:00"
+++

While installing FreeBSD 7.1 I accidentally chose to install the [FreeBSD Boot Manager](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html#BOOTMGR "FreeBSD Handbook: Install a Boot Manager"), where I should have chosen to install a standard MBR. Although not that big a deal I still wanted to remove the boot manager from the system. While searching the internet I stumbled upon a lot of resources telling me to use `boot0cfg` to remove the boot manager. Unfortunately this command failed with the error `boot0cfg: /boot/mbr: unknown or incompatible boot code`. The solution to this problem is to use `fdisk` instead of `boot0cfg` like so:

```
# fdisk −B −b /boot/mbr ad0
```