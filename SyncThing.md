# SyncThing

## Installation Debian/Ubuntu/Mint

Add release key

```bash
curl -s https://syncthing.net/release-key.txt | sudo apt-key add -
```

Add the "stable" channel to your APT sources:

```bash
echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list
```

Update and install syncthing:

```bash
sudo apt-get update
sudo apt-get install syncthing
```

## Configure for remote access

Change configuration address

```bash
cd ~/.config/syncthing/
cp config.xml config.xml.old
nano config.xml
```
