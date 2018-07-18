# SyncThing

## Installation Debian/Ubuntu/Mint

Add release key
<<<<<<< HEAD
```
=======

```bash
>>>>>>> 1c314bfa235dec8d5ad0b0cf4d7a9247074b3cf1
curl -s https://syncthing.net/release-key.txt | sudo apt-key add -
```

Add the "stable" channel to your APT sources:
<<<<<<< HEAD
```
=======

```bash
>>>>>>> 1c314bfa235dec8d5ad0b0cf4d7a9247074b3cf1
echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list
```

Update and install syncthing:
<<<<<<< HEAD
```
=======

```bash
>>>>>>> 1c314bfa235dec8d5ad0b0cf4d7a9247074b3cf1
sudo apt-get update
sudo apt-get install syncthing
```

## Configure for remote access

Change configuration address

<<<<<<< HEAD
```
cd ~/.config/syncthing/
cp config.xml config.xml.old
nano config.xml
``` 
=======
```bash
cd ~/.config/syncthing/
cp config.xml config.xml.old
nano config.xml
```
>>>>>>> 1c314bfa235dec8d5ad0b0cf4d7a9247074b3cf1
