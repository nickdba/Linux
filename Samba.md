# How to install samba and share folders to windows network


```bash
sudo apt-get update
sudo apt-get install samba

sudo smbpasswd -a <user_name>
```

```bash
cd /etc/samba/
sudo co smb.conf smb.conf.original
sudo nano smb.conf
testparm
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

https://forums.linuxmint.com/viewtopic.php?f=157&t=185410#p960482