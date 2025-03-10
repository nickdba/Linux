# RetroArch

Install the retroarch, stand alone service and some assets for the themes using yay as some are in aur and some in the pacman repo.

```bash
yay -S --needed retroarch retroarch-assets-xmb retroarch-assets-ozone retroarch-standalone-service
```

Install all the libretro emulators you see fit.

```bash
yay libretro
```

All the cores are intalled in `/usr/lib/libretro` but they will not appear in the RetroArch's GUI until you add them in the configuration.  
When you first run RetroArch it will create the user configuration file `~/.config/retroarch/retroarch.cfg`.  
Modify this in order to include the global config. 


```bash
#include "/etc/retroarch.cfg"
```

Retroarchs cores are looking for BIOS files at the location set with the `system_directory` option in `retroarch.cfg`.  
Most of the cores require the files directly in this directory, some may need a subdirectory with a specific name.

Install controller support.

```bash
yay -S --needed game-devices-udev
```

You can use the interface to download xbox controller profile for your user.

Main Menu -> Online Updater -> Update controller profile

You can launch a game from the command line to test that things are working.

```bash
retroarch --libretro /path/to/some_core_libretro.so /path/to/rom
```

References:  
https://wiki.archlinux.org/title/RetroArch  
https://discovery.endeavouros.com/gaming/steam-lutris-wine/2022/01/  
https://docs.libretro.com/library/bios/