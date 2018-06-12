# Setting up a network file system (NFS)

This tutorial will include 2 parts, the server and the client.
If focuses on NFS version 3.

## Server configuration

On the server, open the terminal and install `nfs-kernel-server` module and `rpcbind`.
The `rpcbind` utility converts RPC program numbers into universal addresses.

```bash
sudo apt-get update
sudo apt-get install nfs-kernel-server
sudo apt-get install rpcbind
```

Configure your shares by editing `/etc/exports`.

```bash
sudo cp /etc/exports /etc/exports.original
sudo nano /etc/exports
```

Here's a line from my old configuration:

```bash
/mnt/mybook300G         192.169.0.*(rw,sync,no_root_squash,no_subtree_check)
```

Check the file after modifications

```bash
sudo exportfs -ra
```

Start the `nfs` and `rpcbind` services

```bash
sudo service rpcbind start
sudo systemctl start nfs-kernel-server.service


```

That is all for the server configuration.

### Client Configuration

```bash
sudo apt install nfs-common
```

Fist we create a directory and we want to mount content to.
And we will change the ownership and permissions on the folder.

```bash
sudo mkdir mybook300G
sudo chwon nicky:nicky mybook300G
sudo chmod 770 mybook300G
```

Test connection by mounting the share. The ip address is the ip of the server.
Check all mount with `df` command.
Un-mount using `umount` command.

```bash
sudo mount -o uid=nicky,gid=nicky 192.169.0.12:/mnt/mybook300G /media/mybook300G
sudo df -Th
sudo umount /media/mybook300G
```

Modify `/etc/fstab` to make the mount permanent

```bash
sudo cp fstab fstab.original
sudo nano fstab
```

Add the following at the end of `fstab`.

```bash
# External Drives
# MyBook300G over the nfs network
192.169.0.12:/mnt/mybook300G  /media/mybook300G  nfs  auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800,user  0 2
```

First we specify the server ip and mount point and mount type will be `nfs`.
Option `nolock` is desirable as if the share is not found at the boot time it will just continue.
Option `user` will allow the share to be mounted as the user rather than root.

Mount all the content of `fstab` without rebooting and check mounts.

```bash
sudo mount -a
sudo df -Th
```
