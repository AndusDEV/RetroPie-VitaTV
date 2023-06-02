# RetroPie VitaTV
This will help you turn a modded Vita into a VitaTV

# Requirements:
_( You don't need to install them yourself now. The guide will walk you through step-by-step :) )_
## Required:
 - [Vita UDCD UVC](https://github.com/xerpi/vita-udcd-uvc) by xerpi - Allows streaming the PS Vita through a USB cable.
 - [ds4vita](https://github.com/xerpi/ds4vita) by xerpi - Allows using DualShock 4 through Bluetooth with Vita. _(Probably needed)_
## Optional:
 - [MiniVitaTV](https://github.com/TheOfficialFloW/MiniVitaTV) by TheFloW - Tricks Vita into thinking that it's actually a VitaTV. You can play local multiplayer games but it's buggy and unsupported.

# Instructions:
## Vita Setup:
On the Vita you just need to install some plugins and restart the console.
You can do it in 2 ways:
### AutoPlugin II (Or apps similar to this):
 1. Search and install udcd-uvc, ds4vita, and MiniVitaTV
 2. Reboot the console, and you're done here.
### Manually:
#### 1. udcd-uvc:
  - Download udcd_uvc.skprx from [here](https://github.com/xerpi/vita-udcd-uvc/releases)
  - Copy that file onto your Vita's SD Card to: `ur0:tai`
#### 2. ds4vita:
  - Download ds4vita.skprx from [here](https://github.com/xerpi/ds4vita/releases)
  - Copy it to the same folder as previously
#### 3. MiniVitaTV _(optionally)_:
  - Download ds3.skprx and minivitatv.skprx from [here](https://github.com/TheOfficialFloW/MiniVitaTV/releases)
  - _(I'm not sure if you can use ds4vita and ds3 together, I had problems with my DS4 when using both)_
  - Copy both files to the same folder as previously
#### 4. Installing:
  - Open your taiHEN config file (probably `ur0:tai/config.txt`) using app like [VitaShell](https://github.com/TheOfficialFloW/VitaShell):
    - Add udcd_uvc under `*KERNEL` section with a line like this: `ur0:tai/udcd_uvc.skprx`
    - Add ds4vita under `*KERNEL` section with a line like this: `ur0:tai/ds4vita.skprx`
    - _(Optionally)_ Add minivitatv and ds3 under `*KERNEL` section with a line like this:
    ```
    ur0:tai/minivitatv.skprx
    ur0:tai/ds3.skprx
    ```
  - Reboot your console and it should work as intended!
## RetroPie Setup:
 - [Connect to your RetroPie through SSH](https://retropie.org.uk/docs/SSH/)
 - Install mpv using `sudo apt-get install mpv`
 - Go to one of the rom directories _(I went to `/home/pi/RetroPie/roms/ports`)_
 - Create a new file using `nano Vita.sh` _(You can name the file whatever you want, but it needs to end with `.sh`)_
 - Paste this content in it:
    ```
    #!/bin/bash
    mpv av://v4l2:/dev/video0 --profile=low-latency --untimed --fs
    exit
    ```
  - Save using `ctrl+x`
  - Exit the SSH session.
  - Restart EmulationStation or the whole system.
## Usage:
  - Connect Vita to your Raspberry Pi using an USB cable.
  - Find and run the script you've just made _(`Vita.sh`, should show as `Vita`)_
  - You should now see your Vita screen!
  - If you want to exit it use `Q` on a keyboard connected to your Pi.
# You're done!
Congratulations, if everything went as it should you now have a VitaTV!
