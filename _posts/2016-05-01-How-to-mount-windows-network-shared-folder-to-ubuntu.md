---
layout: post
comments: true
title: How to mount windows network shared folder to ubuntu.
---

For mounting windows shares in ubuntu using [cifs-utils](https://wiki.samba.org/index.php/LinuxCIFS_utils).
Install cifs utils `sudo apt-get install cifs-utils`.

for mounting use this command:

```sh

$ sudo mount -t cifs //<windows-ip>/<path-to-shared-folder>/ /path/to/ubunut-mount-point/ -o username=<username>,password=<password>,uid=1000,gid=1000

eg:
$ sudo mount -t cifs //192.168.1.202/sample/ /mnt/shared/ -o username=bob,password=123456,uid=1000,gid=1000

```
