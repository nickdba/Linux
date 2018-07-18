Oracle Linux 

## Network configuration

```bash
cd /etc/sysconfig/network-scripts
nano ifcfg-enp0s8
```

Change the configuration to suit your needs and delete the comments

```bash
ONBOOT=yes
IPADDR=192.168.60.110    # This is the ip address
GATEWAY=192.168.60.1	 # The gateway is ususaly the router
DNS1=8.8.8.8        	 # Google dns servers (8.8.8.4) 
```

Set the host name and link it to the ip adress
nano /etc/hostname
nano /etc/hosts            # host


## Run Levels

Some comands and their descriptions

```bash
sudo systemctl get-default
sudo systemctl set-default runlevel3.target   # runlevel3.target - no gui; runlevel5.target - with gui
systemctl start gdm							  # to start gnome gui
```








