# Setting up a network file system (NFS)

This tutorial will include 2 parts the server part and the client parts

## Server configuration

From the terminal on the server nsf server application.

```
sudo apt-get update
sudo apt-get install nfs-kernel-server
```

Configure your shares by editing /etc/exports. 

```bash
sudo nano /etc/exports
```

Here's a line from my live version that shares my music:

```bash
/mnt/seagate5T          192.168.0.*(rw,sync,no_root_squash)
/mnt/mybook1T           192.168.0.*(rw,sync,no_root_squash)
/mnt/mybook300G         192.168.0.*(rw,sync,no_root_squash)
```

Restart the nfs service

```bash
sudo service rpcbind start
sudo systemctl start nfs-kernel-server.service
```

### Client Configuration

```bash
sudo apt install nfs-common
```

fist we create a directory and we 

test connection 

```
sudo mount 192.168.0.36:/mnt/seagate5T /media/seagate5T
```

```
sudo cp fstab fstab.original
sudo nano fstab
```


 https://askubuntu.com/questions/7117/which-to-use-nfs-or-samba