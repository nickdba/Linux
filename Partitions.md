# Partitions

To show all disk usage.

```bash
df -h
```

To show disks and partitions

```bash
~> fdisk -l
# or
~> parted -l
# or
~> lsblk
```

To work on a disk; Do Not pass the partition (/dev/sda1) but rather the disk.
Showing an example using fdisk and parted.

```bash
~> fdisk /dev/sda  
# or
~> parted /dev/sda
```

To format a partition to ext4 format

```bash
~> mkfs.ext4 <partition>
```

To show uuid of all partitions

```bash
~> blkid
```
