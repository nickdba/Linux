# Mounting an external device

This is an example how to manually mount a hard-drive.
Our example user is called pi, the default user in `Raspbian`, debian based distribution for raspberry pi devices. 

## Prerequisite 
Most of the desktop distributions these days will automatically mount a drive.
However, if you have a raspberry pi or any other device that will use a lite version of linux, this is the way to go. All the commands are done in the terminal as the gui might not be available

First we will check all devices the plugged in.

```bash
sudo parted -l
or 
sudo sfdisk -l
```

Identify the disk you will be mounted.
It usually looks something like `/dev/sda1`

If the file is `ntfs` format make sure you have `ntfs-3g` packet installed.

```bash
sudo apt-get update
sudo apt-get install ntfs-3g
```

Create the mount-point directory. In this example the directory is named `mydisk`. 
Change the owner and give full access for himself and his group.

```bash
sudo mkdir /mnt/mydisk
sudo chown pi:pi /mnt/mydisk
sudo chmod 770 /mnt/mydisk
```

## Mounting the disk
In our example the drive is /dev/sda1.
Mount the disk with the following command

```bash
mount -t ntfs -o -o uid=pi,gid=pi /dev/sda1 /mnt/mydisk 
```

## Making mount permanent
To accomplish a permanent mount you need modify `/etc/fstab` file.
First we will get the UUID for the disk.

```bash
sudo blkid
```

Search for a like looking something like 

```bash
/dev/sda1: LABEL="My Book" UUID="AA9D-F0BC" TYPE="vfat" PARTUUID="44fdfe06-01"
```

Copy UUID

```bash
sudo cp /etc/fstab /etc/fstab.old
sudo nano /etc/fstab    
```

And add the following lines 

```bash
# mydisk mount
UUID=AA9D-F0BC   /mnt/mydisk  ntfs    defaults,uid=pi,gid=pi        0       2
```

To save `CTRL+X` -> `Y` -> `Enter`

Check the mount.

```bash
sudo mount -a
sudo df -Th
``` 
