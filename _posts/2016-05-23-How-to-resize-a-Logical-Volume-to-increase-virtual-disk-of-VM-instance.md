---
layout: post
comments: true
title: How to increase the storage of a Virtual Machine by resizing Logical Volume
---

Increasing the partition/storage of a linux Virtual-Machine instance is done in three steps.

### Resize the Virtual Disk

Power off the virtual machine and then, increase the virtual disk/storage size from the virtual machine settings. By increasing storage space here, the OS is not going to use/detect this. For that we have resize the partition using Disk partition manager (Gparted here).

### Get Gparted and resize the partition.

For gparted we can either use Gparted.iso or any of ubuntu live CD. I'm using a bootable USB stick with Ubuntu live CD iso.

> For choosing/changing the boot order/device for virtual instance, We have to increase the boot delay in Options -> Boot options -> Power on Boot Delay.
> This will allow us to see the boot screen for the specified no. of milliseconds.

In Gparetd first resize the extended partition, then resize the LVM.

### Resize the LVM Volume.

For resizing the LVM, first resize the Physical Volume.

```sh
$ sudo pvs

PV         VG              Fmt  Attr PSize   PFree
  /dev/sda5  ubuntuServer-vg lvm2 a--  99.76g 9.16g

$ sudo pvresize /dev/sda5

Physical volume "/dev/sda5" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized

```

Next extend the Logical volume to the full size of PV(Physical Volume).

```sh
$ sudo lvdisplay

  --- Logical volume ---
  LV Path                /dev/PA-server-vg/root
  LV Name                root
  VG Name                PA-server-vg
  LV UUID                fwuhJl-mvBY-xDgv-ihmF-CCDH-U2kX-EZ7tMV
  LV Write Access        read/write
  LV Creation host, time PA-server, 2014-10-17 19:31:06 +0530
  LV Status              available
  # open                 1
  LV Size                31.76 GiB
  Current LE             8130
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Path                /dev/PA-server-vg/swap_1
  LV Name                swap_1
  VG Name                PA-server-vg
  LV UUID                Xqk8xg-mVYW-zgpc-FYPz-MSpd-0bIr-Kqgnxq
  LV Write Access        read/write
  LV Creation host, time PA-server, 2014-10-17 19:31:06 +0530
  LV Status              available
  # open                 0
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
```

Take the LV Path of the volume to be extended(root, here /dev/PA-server-vg/root
), now we can resize it to the available 100% using `lvextend`.

```sh
$ lvextend -l+100%FREE /dev/PA-server-vg/root
```
Now the last step is to extend the file-system on the volume.

```sh
$ resize2fs /dev/PA-server-vg/root
```

Now check the with `df -h`, we have resized the disk/storage of the VM.
