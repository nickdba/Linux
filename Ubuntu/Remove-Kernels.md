# Remove Kernels

Check your active kernel and make sure you are not removing that.

```bash
~> uname -r
```

These are the normal commands to remove old kernels from your sistem but sometimes they don't work.

```bash
~> apt --purge autoremove
~> purge-old-kernels --keep 3 -qy
```

Identify all kernes from your system and remove them manually.

```bash
~> sudo -i
~> dpkg --list | egrep -i --color 'linux-'      # Identify all 'linux-' installed packages (E.g. 4.15.0-23)
~> dpkg --list | grep 4.15.0-23                 # Make sure you get all 4.15.0-23 packages
~> apt --purge remove linux-image-4.15.0-23-generic linux-modules-4.15.0-23-generic linux-modules-extra-4.15.0-23-generic   # Remove all found packages
~> dpkg --list | grep 4.15.0-23                 # Double check everything is removed
```
