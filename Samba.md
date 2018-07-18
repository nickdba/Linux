# Samba configuration on Ubuntu/Linux Mint and Win 10

## Setting up Linux server

Install and configure samba.
Open a terminal session and run the installation and user creation.
Replace <variables> appropriately.

```bash
sudo su
apt update
apt install samba
smbpasswd -a <user_name>
mkdir <samba_share_folder>
chown -R <user_name>:<user_name> <samba_share_folder>
chmod -R 775 <samba_share_folder>
```

Then we will modify samba configuration file, but first we will backup the original just in case.

```bash
cd /etc/samba/
cp smb.conf smb.conf.original
nano smb.conf
```

At the end of the file

```bash
[<share_name>]
path = <samba_share_folder>
valid users = <user_name>
read only = no
```

Test parameters and restart the smbd service

```bash
testparm
systemctl restart smbd
systemclt enable smbd
```

## Accessing the files from another Linux machine

From the console

```bash
smbclient //<samba_server_ip>/<share_folder> -U <user_name>
ls
```

Using Nemo file and folder default organizer for Linux Mint, type in the address:

```bash
smb://<samba_server_ip>
``` 

Then type in the user credentials and add the folder to bookmarks.

## Accessing the files from Windows 10

In the explorer

```bash
\\<samba_server_ip>
```

Then type in the user credentials and add the folder to bookmarks.

## Accessing Windows 10 shares from Linux Mint 

First you should know both machines IPs. And one machine can ping each other.

Windows : command prompt - ipconfig
Linux : terminal - ifconfig
ping < ip_adress >

Then we will create a share on windows.

1. Choose a folder that you want to share. 
2. Right click on it and choose properties
3. On the Sharing tab click on Advanced Sharing...
4. Share the folder and set permissions
5. Apply
6. On the Sharing tab click on Network and sharing center link from Password Protection area.
7. Turn on discovery network
8. Turn on file and printer sharing

On the firewall add the Linux ip for both incoming and outgoing as trusted.
This is an important step and can be fiddly, depending on the firewall you are using.

We need to modify the samba configuration file, but first we will backup the original file just in case.

Install and configure samba.
Open a terminal session and run the installation and user creation.


If host cannot be resolved verify the firewall rules on both machine and make sure both machine can ping each other.

## Accessing Linux Mint shares from Windows 10

Add/modify the following lines to the following file.
Remove anything else from the file.
Replace all < variables > appropriately. 

```bash
Configuration:
[global]
netbios name = <Server_Name>
server string = <Server_Description>
workgroup = WORKGROUP
hosts allow =
;socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
remote announce =
remote browse sync =
client min protocol = SMB2
client max protocol = SMB3

[<Share_name>]
path = /mnt/Music
comment = No comment
browsable = yes
read only = no
valid users =
writable = yes
public = yes
create mask = 0755
directory mask = 0755
force user = root
force create mode = 0755
force directory mode = 0755
hosts allow =
```

Control x to save file and enter to confirm the overwriting.
Next we will test the configuration and restart the service.

```bash
testparm -s
sudo service nmbd restart
sudo service smbd restart
```

Using Bojour discovery service setup. 

```bash
sudo service avahi-daemon start
cd /etc/avahi/services/
sudo cp samba.service samba.service.original
sudo nano /etc/avahi/services/samba.service
```

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>

Write the following in your explorer
smb://192.168.0.36/seagate5t

## More info on:

https://forums.linuxmint.com/viewtopic.php?f=157&t=185410#p960482

https://www.computerhope.com/issues/ch001636.htm

https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/

https://ubuntuforums.org/showthread.php?t=288534