# Debian-12-iso-scan-support

Providing additional functionality for diskless booting & installation of Debian GNU/Linux via GNU GRUB. It is possible booting official Debian Installation (live) media diskless via GNU GRUB, but it is not possible installing the system via Debian Installer. This repository provides config and image files for this installation scenario.
This solution was triggered by this bug report https://github.com/Mexit/MultiOS-USB/issues/77 and adopted to MultiOS-USB as a 'one-click-solution', but is usable with any grub2 loopback setup. All files used for the initrd "iso-scan-12.15.0.gz" are provided by Debian Project (Debian 12 "bookworm" see: [here](https://github.com/Rockets31/Debian-12-iso-scan-support/blob/main/docs/README_inst)).

# Features
- Filesystems: exfat, ext4
- Scan for devices & ISO files ('iso-scan')
- Provide full debian boot menu
- Supported ISOs: debian-12.15.0-amd64-DVD-1.iso, debian-12.15.0-amd64-netinst.iso, debian-live-12.15.0-amd64-cinnamon.iso, debian-live-12.15.0-amd64-gnome.iso, debian-live-12.15.0-amd64-kde.iso, debian-live-12.15.0-amd64-lxde.iso, debian-live-12.15.0-amd64-lxqt.iso, debian-live-12.15.0-amd64-mate.iso, debian-live-12.15.0-amd64-standard.iso, debian-live-12.15.0-amd64-xfce.iso.

# Usage
Load provided 'iso-scan-12.15.0.gz' along with the main 'initrd.gz' of the installation media via grub loopback module. This adds necessary functionality for installing Debian 12.5 via debian installer. If you are using 'https://github.com/Mexit/MultiOS-USB', it is just a few steps:

0. Use MultiOS-USB partition on 'exfat' or 'ext4' filesystem.
1. Copy your Debian-12.15.0-iso files to 'ISOs' directory.
2. Copy 'iso-scan-12.15.0.gz' file to MultiOS-USB partition, so it is next to 'ISOs' & 'MultiOS-USB' directory.
3. Create a directory for 'grub.cfg' files e.g.: '/MultiOS-USB/config_priv/debian-iso-scan'
4. Copy 'debian-12.15.0-amd64_d-i.cfg' and 'debian-12.15.0-amd64-live_d-i.cfg' there.
5. Reboot into 'MultiOS-USB' and start e.g. 'debian-12.15.0-amd64-DVD-1.iso [config_priv]' entry.
6. The installer will scan for devices & iso files and you have to select it.
