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
DNS1=192.168.60.1        # The DNS is the same as the gateway (router ip) 
GATEWAY=192.168.60.1
```

## Run Levels

```bash
sudo systemctl get-default
sudo systemctl set-default runlevel3.target   # this is starts the system without a gui
```

to start gnome

systemctl start gdm


