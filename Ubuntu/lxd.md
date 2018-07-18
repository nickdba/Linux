# LXD containers useful commands

To show containers

```bash
lxc list
lxc info <container_name>
```

To start/stop containers

```bash
lxc start <container_name>
lxc stop <container_name>
```

To get container's console

```bash
lxc exec <container_name> bash
```

To share a folder with a container

 ```bash
 lxc config set <container_name> security.privileged true
 lxc config device add <container_name> <share_name> disk source=<share_path> path=<lxd_share_path>
 ```

## Working with images

To list images and display information about image i1

```bash
lxc image list
lxc image show i1
```

To publish to an image and export to a tar.gz

 ```bash
lxc publish -f c1 --alias i1
lxc image export i1 .
 ```

 To import an image from tar.gz and them create a container from the image

 ```bash
lxc image import file.tar.gz --alias i1
lxc init i1 c1 -s st1
 ```

## Working with storage

To list disks and display information about storage st1

```bash
lxc storage list
lxc storage show st1
lxc storage volume list st1
```