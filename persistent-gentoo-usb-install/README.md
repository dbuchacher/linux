This assumes you ahve downloaded a stage3 package from the gentoo website

```shell
su
```


```shell
# optional: find what your usb drive is called
fdisk -l
```

```shell
fdisk /dev/sda
```

```
g
n
enter
enter
+512M
***if it asks to remove signature: y
n
enter
enter
+2048M
*** if it ask to remove signature: y
n
enter
enter
enter
*** if it ask to remove signature: y
t
1
1
t
2
11
p
```

should look simular to
```
Command (m for help): p
Disk /dev/sda: 14.53 GiB, 15597568000 bytes, 30464000 sectors
Disk model: Ultra
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A5CE9399-8C0E-774D-8303-8BB722051554

Device       Start      End  Sectors  Size Type
/dev/sda1     2048  1050623  1048576  512M EFI System
/dev/sda2  1050624  5244927  4194304    2G Microsoft basic data
/dev/sda3  5244928 30463966 25219039   12G Linux filesystem

Filesystem/RAID signature on partition 1 will be wiped.
Filesystem/RAID signature on partition 2 will be wiped.
Filesystem/RAID signature on partition 3 will be wiped.

Command (m for help):
```

w to write changes
```
w
```

```
mkfs.vfat -F 32 /dev/sda1
mkfs.vfat -F 32 /dev/sda2
mkfs.ext4 /dev/sda3
```

This assumes you have downloaded a stage3 package from the gentoo website
```
mkdir /mnt/gentoo
mount /dev/sda3 /mnt/gentoo
# This assumes you have downloaded a stage3 package from the gentoo website
tar xpvf stage3-*.tar.xz --xattrs-include='*.*' --numeric-owner



