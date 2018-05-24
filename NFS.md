# Setting up a network file system (NFS) on debian systems

This tutorial will include 2 parts the server part and the client parts

## Server configuration

From the terminal on the server run the following commands to install necessary programs.
Make sure you are root first by running `su` command.

```
apt update
apt install nfs-kernel-server rpcbind
systemctl enable nfs-kernel-server
systemctl enable rpcbind
```

Configure your shares by editing /etc/exports. 

```bash
nano /etc/exports
```

Here's a line from my live version that shares my music:

```bash
/mnt/seagate5T          192.168.0.*(rw,sync,no_root_squash)
/mnt/mybook1T           192.168.0.*(rw,sync,no_root_squash)
/mnt/mybook300G         192.168.0.*(rw,sync,no_root_squash)
```

## Restart the nfs services

In case you need to restart the service run the following as root.

```bash
systemctl restart rpcbind
systemctl restart nfs-kernel-server.service
```

## Client Configuration

For the terminal on the client computer, become root by running `su` command.

```bash
apt install nfs-common
```

Fist we create a directory and we want to mount content to.

```bash
mkdir mybook300G
```

test connection 

```
mount 192.168.0.36:/mnt/seagate5T /media/seagate5T
```

```
cd /etc
cp fstab fstab.original
nano fstab
```

```
# External Drives
# MyBook300G over the nfs network
192.168.0.36:/mnt/mybook300G    /media/mybook300G	nfs     auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800,user  0       2
```

mount the system automatically using fstab file

```
mount -a
```

 https://askubuntu.com/questions/7117/which-to-use-nfs-or-samba