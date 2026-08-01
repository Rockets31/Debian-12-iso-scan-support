# Debian-12-iso-scan-support

Providing additional functionality for diskless booting & installation of Debian Bookworm via GNU GRUB. It is possible booting official Debian Installation (live) media diskless via GNU GRUB, but it is not possible installing the system via Debian Installer. This repository provides config and image files for this installation scenario.
This solution was triggered by this bug report https://github.com/Mexit/MultiOS-USB/issues/77 and adopted to MultiOS-USB as a 'one-click-solution', but is usable with any grub2 loopback setup. All files used for the initrd "iso-scan-12.15.0.gz" are provided by Debian Project (Debian 12 "bookworm" see: [here](https://github.com/Rockets31/Debian-12-iso-scan-support/blob/main/docs/README_inst)).

# Features
- Filesystems: exfat, ext4
- Scan for devices & ISO files ('iso-scan')
- Provide full Debian 12 boot menu
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

#Screenshots
<img width="1040" height="500" alt="bookworm_debian-installer_main-menu_0" src="https://github.com/user-attachments/assets/15a729e4-a4ca-406d-98ad-98e220cc074d" />
<img width="1040" height="500" alt="bookworm_ask_device_0" src="https://github.com/user-attachments/assets/58f5a038-67ab-477e-8643-6f38cc32eab7" />
<img width="1040" height="500" alt="bookworm_ask_which_iso_0" src="https://github.com/user-attachments/assets/e89d2db0-8f86-4aa7-a8a4-c057b46b1329" />
<img width="1040" height="600" alt="bookworm_debian-installer_dark-contrast_0" src="https://github.com/user-attachments/assets/ddb07f7c-0215-4804-ac0f-e365ae6f716f" />
<img width="1080" height="800" alt="bookworm-dark_keyboard" src="https://github.com/user-attachments/assets/6b96b2ec-8e37-424d-9320-1ada9c2c02de" />

