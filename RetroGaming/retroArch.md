# RetroArch

Install RetroArch, the standalone service, and some assets for the themes using `yay` as some are in the AUR and some in the Pacman repository.

```bash
yay -S --needed retroarch retroarch-assets-xmb retroarch-assets-ozone retroarch-standalone-service
```

Install all the libretro emulators you see fit.

```bash
yay libretro
```

All the cores are installed in `/usr/lib/libretro`, but they will not appear in RetroArch's GUI until you add them in the configuration.  
When you first run RetroArch, it will create the user configuration file `~/.config/retroarch/retroarch.cfg`.  
Modify this file to include the global config:

```bash
#include "/etc/retroarch.cfg"
```

RetroArch's cores look for BIOS files at the location set with the `system_directory` option in `retroarch.cfg`.  
Most of the cores require the files directly in this directory; some may need a subdirectory with a specific name.

Install controller support.

```bash
yay -S --needed game-devices-udev
```

You can use the interface to download the Xbox controller profile for your user:

Main Menu -> Online Updater -> Update Controller Profile

You can launch a game from the command line to test that things are working:

```bash
retroarch --libretro /path/to/some_core_libretro.so /path/to/rom
```

References:  
- [Arch Linux Wiki - RetroArch](https://wiki.archlinux.org/title/RetroArch)  
- [EndeavourOS Discovery - Gaming](https://discovery.endeavouros.com/gaming/steam-lutris-wine/2022/01/)  
- [Libretro Docs - BIOS](https://docs.libretro.com/library/bios/)