# SyncThing

## Installation Debian/Ubuntu/Mint

Add release key
```
curl -s https://syncthing.net/release-key.txt | sudo apt-key add -
```

Add the "stable" channel to your APT sources:
```
echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list
```

Update and install syncthing:
```
sudo apt-get update
sudo apt-get install syncthing
```

## Configure for remote access

Change configuration address

```
cd ~/.config/syncthing/
cp config.xml config.xml.old
nano config.xml
``` 
 
## NFS Sharing

 https://askubuntu.com/questions/7117/which-to-use-nfs-or-samba