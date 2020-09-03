# Static Ip with Netplan

Make sure and confirm that network interface is not managed by cloud-init.

```bash
~> sudo -i
~> cat /etc/cloud/cloud.cfg.d/subiquity-disable-cloudinit-networking.cfg
   - network: {config: disabled}
```

Check the current configuration and modfy the file from DHCP4 to a static address.

```bash
~> ip address
~> vi /etc/netplan/00-installer-config.yaml
```

```bash
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp0s3:
      dhcp4: true
  version: 2

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp0s3:
      addresses: [192.168.0.3/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [4.2.2.2, 8.8.8.8]
  version: 2  
```

Apply the netplan configuration and reboot. Lastly check the configuration again.

```bash
~> netplan apply
~> ip address
~> reboot
~> ip address
```
