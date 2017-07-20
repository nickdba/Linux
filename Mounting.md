# Mounting an external device

This is a short example how to manually mount a hard-drive.

## Prerequisite 
Most of the desktop distributions these days will automatically mount a drive.
However if tou have a network share and you want a permanent mount this is the way to go. All the commands are done in the terminal.

First we will check all devices the plugged in.
```
sudo parted -l
```
Identify the disk you will be mounted.
It usually looks something like `/dev/sda1`

If the file is ntfs format make sure you have the ntfs-3g packet
```
sudo apt-get update
sudo apt-get install ntfs-3g
```

We all need to create one directory for the mount. In this example
we will call the directory mydisk.
```
sudo mkdir /mnt/mydisk
```

## Mounting the disk
In our example the drive is /dev/sdd2.
You can mount the disk with the following command
```
mount /dev/sdd2
```

## Making mount permanent
To accomplish a permanent mount you can modify /etc/fstab file.
```
sudo cp /etc/fstab /etc/fstab.old
sudo nano /etc/fstab    
```
And add the following line 
```
/dev/sdd2   /mnt/mydisk  ntfs    defaults        1       1
```
To save `CTRL+X` -> `Y` -> `Enter`

sudo mount -t ntfs -o uid=pi,gid=pi /dev/sdd2 /mnt/mydisk 



```
df -h
``` 

Option -h means human readable.





