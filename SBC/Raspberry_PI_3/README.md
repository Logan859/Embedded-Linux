# Raspberry Pi Resouces

* [Raspberry Pi Bare Metal](https://github.com/fordp2002/ArmCopro/wiki/Raspberry-Pi-Bare-Metal) & [related link](https://microeletroniki.wordpress.com/)
* [ChibiOS/RT on the Raspberry Pi](https://www.stevebate.net/chibios-rpi/GettingStarted.html)
* [Raspberry Pi ARM based bare metal examples](https://github.com/dwelch67/raspberrypi)
* [Bare metal Raspberry Pi 3 tutorials](https://github.com/bztsrc/raspi3-tutorial)
* [Open Projects: Raspberry, Beaglebone BSP](https://devel.rtems.org/wiki/Developer/OpenProjects)
* [A Real-Time Operating System on the Raspberry Pi](http://www.pebblebay.com/raspberry-pi-embedded/)
* [A port of FreeRTOS to the raspberry pi](https://github.com/jameswalmsley/RaspberryPi-FreeRTOS)
* [FreeRTOS Sucessfully Ported](https://www.raspberrypi.org/forums/viewtopic.php?f=72&t=22423)
* [Exploring AArch64 assembler - Raspberry](https://thinkingeek.com/2016/10/08/exploring-aarch64-assembler-chapter1/)
* [A bootloader for the Raspberry Pi using the ethernet device](https://github.com/Nvreformat/Etherboot)
* [Bare Metal Raspberry Pi](https://taylorpetrick.com/blog/post/bare-metal-pi-setup)
* [Bare Metal Programming in C](http://www.valvers.com/open-software/raspberry-pi/step01-bare-metal-programming-in-cpt1/)
* [Baking Pi – Operating Systems Development](https://www.cl.cam.ac.uk/projects/raspberrypi/tutorials/os/)
* [Search for 'Raspberry' topic on Github](https://github.com/topics/raspberry-pi-3?l=c)
* [elinux: Raspberry Pi Programming](https://elinux.org/Raspberry_Pi_Programming) or [elinux: RPi Hub](https://elinux.org/RPi_Hub)
* [Stanford CS104e - An Experimental Course on Operating Systems](https://web.stanford.edu/class/cs140e/)
* [Computer Systems](http://cs107e.github.io/)
* [Build a Debian-based ARM64 system for Raspberry Pi 3](https://github.com/UMRnInside/RPi-arm64)
* [Learning operating system development using Linux kernel and Raspberry Pi](https://github.com/s-matyukevich/raspberry-pi-os)
* [A port of FreeRTOS to the raspberry pi 2B. With USB+Ethernet+TCP/IP.](https://github.com/Forty-Tw0/RaspberryPi-FreeRTOS)
* [64-bit Tiano Core UEFI for the Raspberry Pi 3](https://github.com/andreiw/RaspberryPiPkg)
* [CXCORE-RaspberryPi3-ubuntu-18.04-aarch64](https://github.com/chainsx/ubuntu64-rpi#cxcore-raspberrypi3-ubuntu-1804-aarch64--)
* [Sample source: Baremetal source code for Raspberry](https://github.com/LdB-ECM/Raspberry-Pi)
* [Sample source: NarcOS - A bare metal ultralight kernel for Raspberry Pi 3](https://github.com/forkachild/NarcOS)
* [Sample source: FreeRTOS v9.0.0 port for Raspberry Pi 1](https://github.com/leodido99/RaspberryPi1-FreeRTOSv9.0.0)
* [Sample source: A bare-metal experiments with the RaspberryPi](https://github.com/majorviraj/my-os)
* [「BareMetalで遊ぶ Raspberry Pi」のプログラムです。](https://github.com/jitomesky/RPi_Micon_C85book)
* [UEFI for RaspberryPi2 and RaspberryPi3 based on Linaro EDK2](https://github.com/ms-iot/RPi-UEFI)
* [ARM-episodes](https://github.com/invictus1306/ARM-episodes) & [ARM exploitation for IoT](https://quequero.org/2017/07/arm-exploitation-iot-episode-1/)
* [ARM shellcode and exploit development - BSidesMunich 2018](https://github.com/invictus1306/Workshop-BSidesMunich2018)
* [64 bit Bare Metal Programming on RPI-3](https://archive.fosdem.org/2017/schedule/event/programming_rpi3/attachments/slides/1475/export/events/attachments/programming_rpi3/slides/1475/bare_metal_rpi3.pdf)
* [Raspberry Pi 3 Bare Metal](https://adamransom.github.io/posts/raspberry-pi-bare-metal-part-1.html)
* [Assembly code for Raspberry Pi](https://github.com/Alkesst/RPIAssembly)
* [A public Baremetal Raspberry Pi code](https://github.com/LdB-ECM/Raspberry-Pi)
* [Raspberry-Pi Bare Metal Tutorial](https://github.com/BrianSidebotham/arm-tutorial-rpi)
* [uCOS-II on Raspberry Pi](https://github.com/fmlab/ucos_RaspberryPi)
* [Porting uCOSII to the raspberry pi A+/B+/2B](https://github.com/mopplayer/uCOSII_RPi)
* [Bare-metal examples](https://github.com/mrvn/RaspberryPi-baremetal)
* [Bare-metal lab](https://github.com/tzuCarlos/RaspberryPi)
* [Exploring Raspberry Pi: Interfacing to the Real World with Embedded Linux {book}](https://www.wiley.com/en-us/Exploring+Raspberry+Pi%3A+Interfacing+to+the+Real+World+with+Embedded+Linux-p-9781119188681)
* [Exploring Raspberry Pi: Interfacing to the Real World with Embedded Linux {website}](http://exploringrpi.com/)


# Raspberry Pi 3 Setup
The steps I took get my Raspberry Pi 3 up and running.

## Upgrade Jessie
Run the following commands to [upgrade Jessie to Pixel](https://www.raspberrypi.org/blog/introducing-pixel/), which includes Chromium with hardware video support:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install -y rpi-chromium-mods
sudo apt-get install -y python-sense-emu python3-sense-emu
sudo apt-get install -y python-sense-emu-doc realvnc-vnc-viewer
```

## Change Password
Run the following command, then enter the current password and a new password twice to confirm:
```
passwd
```

## Setup SSH
Launch the Raspbery Config:
```
sudo raspi-config
```

Go to `9 Advanced Options` then `A4 SSH` and choose `<Enable>`.

Open the `/etc/ssh/sshd_config` file and add the following:
```
PermitRootLogin no
ClientAliveInterval 30
ClientAliveCountMax 5
```

Then restart the SSH service:
```
sudo service ssh restart
```

## Disable Automatic Desktop Login
Run the configuration command:
```
sudo raspi-config
```

Go to `3 Boot Options` then `B3 Desktop` and choose `<Ok>`.

## Setup Display
Ensure the display works nicely over HDMI:
```
sudo nano /etc/boot.txt
```

Add the following lines to the bottom of the file:
```
hdmi_group=1
hdmi_mode=16
hdmi_ignore_cec_init=1
hdmi_ignore_cec=1
hdmi_drive=2
gpu_mem=128
```

In order to disable HDMI CEC you also need to drop a config file on the recovery partition:
```
sudo su
mount /dev/mmcblk0p1 /mnt
echo hdmi_ignore_cec_init=1 >> /mnt/config.txt
umount /mnt
exit
```

Now reboot the system:
```
sudo reboot
````

## Install Kodi
Update repositories and install Kodi packages:
```
sudo apt-get update
sudo apt-get install kodi
```

Create a Kodi shortcut on the desktop that boots in standalone mode (avoids blackscreen on exit):
```
touch ~/Desktop/kodi-standalone.desktop
nano ~/Desktop/kodi-standalone.desktop
```

Add the following contents to the file:
```
[Desktop Entry]
Version=1.0
Name=Kodi
GenericName=Media Center
Comment=Manage and view your media
Exec=kodi-standalone
Icon=kodi
Terminal=false
Type=Application
Categories=AudioVideo;Video;Player;TV;
```

## Install FAT32, ExFAT and NTFS File System Support
Install the following packages:
```
sudo apt-get install exfat-fuse exfat-utils ntfs-3g
```

## Mount NAS
Ensure the CFIS packages are installed:
```
sudo apt-get install cifs-utils
```

Create a credentials file for the username and password:
```
touch ~/.smbcredentials
nano ~/.smbcredentials
```

Add the following contents, replacing the username and password:
```
username=username
password=password
```

Change the permissions of the credentials file:
```
chmod 600 ~/.smbcredentials
```

Make a directory to mount the NAS to:
```
sudo mkdir /media/NAS
```

Test you can mount the NAS manually:
```
sudo mount -t cifs //192.168.0.x/NAS /media/NAS -o credentials=~/.smbcredentials,vers=1.0
```

Any mounting problems can be found by checking the logs:
```
tail -f  /var/log/kern.log
```

You can find out your users UID and GID with these commands:
```
id -u username
id -g username
```

Alternatively you can just use your username and group instead.

Now update the `/etc/fstab` file to auto mount the NAS as **read-only**:
```
//192.168.0.x/NAS /media/NAS cifs credentials=/home/username/.smbcredentials,_netdev,x-systemd.automount,iocharset=utf8,sec=ntlm,ro 0 0
```

Or for full **read and write** add this to the `/etc/fstab` instead:
```
//192.168.0.x/NAS /media/NAS cifs credentials=/home/username/.smbcredentials,_netdev,x-systemd.automount,iocharset=utf8,sec=ntlm,rw 0 0
```

_Note: Update the lines above with your own NAS IP address, mount directory, username, UID and GID accordingly. For devices running older versions of Samba you may need to add `,vers=1.0` after `ro` or `rw` above._

Now run this to mount the NAS:
```
sudo mount -a
```

Create a handy symlink to the NAS on the desktop:
```
sudo ln -s /media/NAS ~/Desktop/NAS
```

## Mount USB Drive
Find the UUID of the USB drive:
```
sudo blkid
ls -l /dev/disk/by-uuid/
```

The output should look something like the following. Note the _UUID_ value:
```
/dev/sda1: LABEL="USB DRIVE" UUID="1234-5678" TYPE="exfat" PARTUUID="ffffffff-01"
```

Make a directory to mount the USB drive to:
```
sudo mkdir /media/USB-Drive
```

Test mounting the drive manually to make sure it works:
```
sudo mount -t exfat -o uid=pi,gid=pi UUID=1234-5678 /media/USB-Drive
```

Now add the following to the `/etc/fstab` to auto mount the USB drive:
```
UUID=1234-5678 /media/USB-Drive exfat defaults,nofail,uid=1000,gid=1000,dmask=000,fmask=111 0 0
```

_Note: Update the line above with your own UUID, mount directory, file system, UID and GID accordingly._

Now run this to mount the USB drive:
```
sudo mount -a
```

Create a handy symlink to the USB drive on the desktop:
```
sudo ln -s /media/USB-Drive ~/Desktop/USB-Drive
```

To repair an exFAT drive on Windows run the following command:
```
chkdsk.exe /F Z:
```

_Note: Replace Z: with the relevant drive letter._

## Create EXT4 Drive

You can format a partition as EXT4:
```
mkfs.ext4 /path/to/mount -L YourLabel
```

You can also change the drive label afterwards:
```
e2label /path/to/mount YourLabel
```

And you can easily mount it in the `/etc/fstab` as follows:
```
UUID=1234-5678 /media/USB-Drive ext4 defaults,auto 0 0
```

## Backup NAS to USB Drive
First, create a directory to store the backup logs in:
```
mkdir ~/Backups
```

Then create an rsync ignore file, this will exclude unneccesary Windows and macOS files from being backed up:
```
touch ~/Backups/rsync_excludes.txt
```

And add the following contents:
```
$RECYCLE.BIN
$Recycle.Bin
._*
.AppleDB
.AppleDesktop
.AppleDouble
.com.apple.timemachine.supported
.dbfseventsd
.DocumentRevisions-V100*
.DS_Store
.fseventsd
.PKInstallSandboxManager
.Spotlight*
.SymAV*
.symSchedScanLockxz
.TemporaryItems
.Trash*
.vol
.VolumeIcon.icns
Desktop DB
Desktop DF
hiberfil.sys
lost+found
Network Trash Folder
pagefile.sys
Recycled
RECYCLER
System Volume Information
Temporary Items
Thumbs.d
```

Do a dry run (the `-n` flag) to ensure the correct files are being backed up:
```
rsync -rtvun --exclude-from="$HOME/Backups/rsync_excludes.txt" /media/NAS/ /media/USB-Drive/
```

Next, create a script to handle the backups:
```
touch Backups/backup.sh
```

With the following contents:
```
#!/bin/bash

BACKUP_DIR="$HOME/Backups"
BACKUP_LOG="$BACKUP_DIR/nas_backups_`date +'%Y-%m-%d'`.txt"
BACKUP_EXCLUDES="$BACKUP_DIR/rsync_excludes.txt"
BACKUP_LOG_DAYS=7

/usr/bin/rsync -rtvu --log-file="$BACKUP_LOG" --exclude-from="$BACKUP_EXCLUDES" --delete-after /media/NAS/ /media/USB-Drive/
find $BACKUP_DIR/nas_backups_*.txt -mtime +$BACKUP_LOG_DAYS -exec rm {} \;
```

Once you're happy it works you can add it to your user's crontab:
```
crontab -e
```

Add the following contents to it to run it every night at 1am:
```
SHELL=/bin/bash

0 1 * * * $HOME/Backups/backup.sh
```

You can add the `--exclude` option to exclude a specific pattern of files or directories, and the `--delete-after` option to ensure files deleted from the target are also removed from the destination.

You can see the last backup log by viewing the file contents:
```
cat ~/Logs/nas_backups_YYYY-MM-DD.txt
```

You can see what environment variables are available in the cron environment by adding the following to your crontab (you'll need to add whatver `* * * * *` you want):
```
env >> $HOME/Backups/cron_env.txt
```

You can also ensure any macOS hidden "dotfiles" are deleted by create a `dotfiles.sh` script:

```
touch dotfiles.sh
chmod +x dotfiles.sh
```

And then adding the following contents to it:
```
find /media/NAS -not -path "*ExcludeDirectory*" -iname ".*" -type f -exec rm -rf {} \;
```

_Note: The filesystem must be writeable for this to work._

You can also add this to the crontab:
```
0 1 * * * $HOME/Backups/dotfiles.sh
```

## Setup Steam Controller
The following instructions should allow you to use the Steam Controller wirelessly.

Download and install the Steam Controller Python drivers:
```
cd ~/
git clone https://github.com/ynsta/steamcontroller.git
cd steamcontroller
sudo pip install libusb1
sudo python3.4 setup.py install
```

Now create the file rules file:
```
sudo touch /lib/udev/rules.d/99-steam-controller-perms.rules
sudo nano /lib/udev/rules.d/99-steam-controller-perms.rules
```

Then add the following to it:
```
# This rule is needed for basic functionality of the controller in
# Steam and keyboard/mouse emulation
SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", MODE="0666"

# This rule is necessary for gamepad emulation; make sure you
# replace 'pgriffais' with the username of the user that runs Steam
KERNEL=="uinput", MODE="0660", GROUP="group", OPTIONS+="static_node=uinput"
```

_Note: Replace `group` with the group of user (e.g. `pi`)._

Now reload udev:
```
sudo udevadm control --reload
```

Start the driver and your controller should work:
```
sc-desktop.py start
```

To start the driver automatically at the desktop create the file:
```
touch ~/.config/autostart/Steam-Controller.desktop
nano ~/.config/autostart/Steam-Controller.desktop
```

Add the following contents to the file:
```
[Desktop Entry]
Exec=sc-desktop.py start
```

You can also install an on-screen keyboard:
```
sudo apt-get install florence
```

And then create a shortcut to it on the desktop:
```
touch ~/Desktop/keyboard.desktop
```

Then add the following contents to the file:
```
[Desktop Entry]
Name=Keyboard
Exec=florence
Terminal=false
Type=Application
Icon=florence
```

## Install Steam Link
```
sudo apt update
sudo apt install steamlink
```

## Install Docker
```
curl -fsSL https://get.docker.com | sh
```

## Install Pi Hole
```
curl -sSL https://install.pi-hole.net | bash
```

### Install DNS over HTTPS

Follow Pi Hole's official instructions: [https://docs.pi-hole.net/guides/dns-over-https/](https://docs.pi-hole.net/guides/dns-over-https/)

## Install Useful Packages
```
sudo apt-get install tree screen tmux
```

## Notes
You can see the icons available for desktop shortcuts in `/usr/share/pixmaps/`

## Links
- https://www.raspberrypi.org/documentation/configuration/config-txt.md
- http://raspberrypi.stackexchange.com/questions/6682/stopping-rasppi-raspbmc-from-auto-changing-source-on-tv
- https://www.raspberrypi.org/forums/viewtopic.php?t=100811
- https://mtantawy.com/quick-tip-how-to-update-to-latest-kodi-16-jarvis-on-raspberry-pi/
- https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=150438
- https://launchpad.net/ubuntu/trusty/+package/firefox
- http://raspberrypi.stackexchange.com/questions/27179/automatic-mounting-of-nas-drive-fails
- http://www.htpcguides.com/properly-mount-usb-storage-raspberry-pi/
- http://www.miqu.me/blog/2015/01/14/tip-exfat-hdd-with-raspberry-pi/
- https://github.com/ynsta/steamcontroller
- http://askubuntu.com/questions/686214/how-do-i-get-a-steam-controller-working
- https://www.raspberrypi.org/forums/viewtopic.php?t=18968
- http://www.techrepublic.com/article/five-tips-for-getting-the-most-out-of-a-raspberry-pi-3-as-a-pc/
- http://raspberrypi.stackexchange.com/questions/44384/how-to-get-chromium-on-raspberry-3/44690
- https://www.raspberrypi.org/blog/introducing-pixel/
- http://alanwsmith.com/rsync-exclude-list-for-mac-osx
- https://kuttler.eu/en/post/sshfs-transport-endpoint-not-connecte/
- http://www.omaroid.com/fstab-permission-masks-explained/
- http://askubuntu.com/questions/429848/dmask-and-fmask-mount-options
- http://askubuntu.com/questions/609003/mount-exfat-warning
- http://blog.marcelotmelo.com/linux/ubuntu/rsync-to-an-exfat-partition/
- http://stackoverflow.com/questions/2135478/how-to-simulate-the-environment-cron-executes-a-script-with
- https://kwilson.io/blog/format-a-linux-disk-as-ext4-from-the-command-line/
- http://anonexp.blogspot.co.uk/2013/04/ext4-mount-options-for-ext4-file-system.html
- https://unix.stackexchange.com/questions/114485/fdisk-l-shows-ext3-file-system-as-hpfs-ntfs
- https://gordonlesti.com/mount-ext4-usb-flash-drive-to-raspberry-pi/
- https://github.com/moby/moby/pull/24815
- https://www.jaredwolff.com/raspberry-pi-setting-your-locale/
- https://help.ubuntu.com/community/MountWindowsSharesPermanently
- https://serverfault.com/questions/367934/how-do-i-pass-credential-file-to-mount-cifs
- https://www.jeffgeerling.com/blog/2017/mount-raspberry-pi-sd-card-on-mac-read-only-osxfuse-and-ext4fuse