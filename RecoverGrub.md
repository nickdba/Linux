# Recover Grub

This tutorial will focus on recovering Grub using a live usb stick.

Prepare an linux installation stick preferably with the same distribution and version  
you currently have installed.

Boot from the stick. If it is allows you to try on use that and open a terminal.  
If not while you are in the installation process, press Ctrl+Alt+l(F1-F6) to open a new session.

Once in switch to root and check partitions for the linux installation.

```bash
~> sudo -i       # To become root
~> fdisk -l      # To list partitions and find out the linux installation one
                 # Search for the one with /boot /env /proc /root
```

After identifying the partition mount the following directories. Where sdd2 is the partition that you founded.

```bash
~> mount /dev/sdd2 /mnt
~> mount --bind /dev /mnt/dev
~> mount --bind /dev/pts /mnt/dev/pts
~> mount --bind /proc /mnt/proc
~> mount --bind /sys /mnt/sys
```

Next is time to chroot in the new system and install grub.  
Notice that we use the disk here not the partition.

```bash
~> chroot /mnt
~> grub-install /dev/sdd
~> grub-install --recheck /dev/sdd
update-grub
```

Exit chroot and reboot.

```bash
~> exit
~> reboot
```

After reboot press Esc key few time, you should see the grub now.
