# Raspberry PI setup

Setting up a Raspberry PI (macOS)

## Topics

Flashing OS, Boot Configuration, WIFI, SSH, Updates, Upgrades, Space Cleanup,
VNC Server (RealVNC), Vim, USB Access, Docker, NodeJS, Hostname, Password,
Network Connection over USB, Audio

## Formatting SD card

```bash
diskutil list
```

Find partition with with `external`, `physical` properties on the list.

```bash
sudo diskutil eraseDisk FAT32 BACKUP MBRFormat /dev/disk2
Password:
Started erase on disk2
Unmounting disk
Creating the partition map
Waiting for partitions to activate
Formatting disk2s1 as MS-DOS (FAT32) with name BACKUP
512 bytes per physical sector
/dev/rdisk2s1: 31085888 sectors in 1942868 FAT32 clusters (8192 bytes/cluster)
bps=512 spc=16 res=32 nft=2 mid=0xf8 spt=32 hds=255 hid=2 drv=0x80 bsec=31116286 bspf=15179 rdcl=2 infs=1 bkbs=6
Mounting disk
Finished erase on disk2
```

## Flashing OS

[https://etcher.io/](https://etcher.io/)

## Modify boot configuration

```bash
 cd /Volumes/boot
➜  boot
touch wpa_supplicant.conf
vim wpa_supplicant.conf
```

### WiFi

#### Content of `wpa_supplicant.conf`

```text
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
update_config=1
country=IT
ap_scan=1

network={
    ssid="YOURSSID"
    psk="YOURPASSWORD"
    scan_ssid=1
}
```
If you need to configure more than one SSID you can add networks information setting a priority:

```text
network={
    ssid="SchoolNetworkSSID"
    psk="passwordSchool"
    id_str="school"
}

network={
    ssid="HomeNetworkSSID"
    psk="passwordHome"
    id_str="home"
}
```

Reference: [Setting WiFi up via the command line](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)

#### Disable WiFi on boot

On device with built-in WiFi add a line `dtoverlay=pi3-disable-wifi` to boot
configuration:

```bash
cd /Volumes/boot
sudo vim config.txt
```

Ref.: [https://git.io/vFje3](https://git.io/vFje3)

### Bluetooth

#### Disable Bluetooth on boot

On device with built-in Bluetooth add a line `dtoverlay=pi3-disable-bt` to boot
configuration:

```bash
cd /Volumes/boot
sudo vim config.txt
```

Ref.: [dtoverlay=pi3-disable-bt](dtoverlay=pi3-disable-bt)

### Enable SSH

```bash
touch ssh
```

## Connecting

### Verify WIFI

```bash
ping -c 3 raspberrypi.local
PING raspberrypi.local (192.168.1.20): 56 data bytes
64 bytes from 192.168.1.20: icmp_seq=0 ttl=64 time=12.041 ms
64 bytes from 192.168.1.20: icmp_seq=1 ttl=64 time=19.085 ms
64 bytes from 192.168.1.20: icmp_seq=2 ttl=64 time=11.659 ms

--- raspberrypi.local ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 11.659/14.262/19.085/3.414 ms
```

### Connect via SSH

```bash
ssh pi@raspberrypi.local
```

Default password: **raspberry**

You could eventually update your SSH fingerprints:

```bash
ssh-keygen -R raspberrypi.local
ssh pi@raspberrypi.local
```

### Connect to RaspberryPI over SSH without password

On the raspberrypi create the folder `~/.ssh`

    mkdir ~/.ssh

Then generate a new key pair to use with the Pi:

mkdir ~/.ssh

    ssh-keygen -t ed25519
    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/home/tj/.ssh/id_ed25519):
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /home/tj/.ssh/id_ed25519.
    Your public key has been saved in /home/tj/.ssh/id_ed25519.pub.
    The key fingerprint is:
    67:5d:f7:fa:5f:4c:1d:fb:cb:f8:2f:11:7a:4f:9e:15 tj@bsdnow.tv
    The key's randomart image is:
    +--[ED25519  256--+
    |                 |
    |                 |
    |              ...|
    |           . ..E=|
    |        S o .. o=|
    |         o  . o++|
    |             ..=*|
    |              +o=|
    |             ..=*|
    +-----------------+

Now, copy the public key on the RaspberryPi

    scp ~/.ssh/id_ed25519.pub username@serverip:.ssh/authorized_keys

You can disable password authentication in sshd_config by changing the "PasswordAuthentication yes" line to "PasswordAuthentication no" after doing this step. Be sure to restart the daemon for changes to take effect. At this point you should be able to SSH into the server without entering your password. It's using the key pair we just generated for authentication now.

To connect to your RaspberryPi using this newly generated key you can use ssh's `-i` parameter:

    ssh -i ~/.ssh/id_ed25519 pi@raspberrypi.local

* [Reference](https://www.bsdnow.tv/tutorials/ssh-tmux)
* [Reference](https://www.cyberciti.biz/faq/force-ssh-client-to-use-given-private-key-identity-file/)

### Update/Upgrade setup

* Update

```bash
sudo apt-get update
```

* Then Upgrade

```bash
sudo apt-get dist-upgrade
```

* [Optional] Cleanup

```bash
sudo apt-get clean
```

### Fixing locale

```bash
sudo locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales
```

Toggled en_US.UTF-8 UTF-8 in the configuration process with SPACE. Then ENTER on the en_US.UTF-8 option within the next screen.

```bash
sudo vi /etc/environment
```

Added these two lines to said file:

```bash
LANGUAGE="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
```

```bash
sudo reboot now
```

Login again:

```bash
locale
```

Everything with locales seems fixed when logging in with users or runninglocale again now.

## Vim

### Install Vim

```bash
sudo apt-get install vim
```

### Syntax Highlighting in Vim

```txt
" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
"syntax on
```

```bash
sudo vim /etc/vim/vimrc
```

and removes quotes before `syntax on`.

### Plugin Manager for Vim

The [vim-plug](https://github.com/junegunn/vim-plug) is used here.

#### Installation

```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Now configure `Vim` configuration file to support plugins with `vim-plug`:

```.virmrc
" Star of plugin section
" Specify a directory for plugins
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')
" Make sure you use single quotes

" Initialize plugin system
call plug#end()
" end of plugin section
```

Example setup:

```.vimrc
" Star of plugin section
" Specify a directory for plugins
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')
" Make sure you use single quotes

Plug 'scrooloose/syntastic'

Plug 'tpope/vim-fugitive'

Plug 'pangloss/vim-javascript'

Plug 'scrooloose/nerdtree'

Plug 'tpope/vim-surround'

Plug 'bling/vim-airline'

Plug 'flazz/vim-colorschemes'

" Initialize plugin system
call plug#end()
" end of plugin section
```

For details see:
[`vim-plug` installation](https://github.com/junegunn/vim-plug#installation)

## Enable USB access

* Edit `config.txt`:

```bash
cd /boot/
sudo vim config.txt
```

Add a line on the end:

```text
dtoverlay=dwc2
```

* Creaty empty `ssh` file if not yet created in `/boot/` directory:

```bash
touch ssh
```

* Edit `cmdline.txt`:

```bash
sudo vim cmdline.txt
```

Add a config item `modules-load=dwc2,g_ether` after `rootwait`:

```text
rootwait modules-load=dwc2,g_ether
```

The content of `cmdline.txt` after modification:

```text
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=4cc82cbf-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait modules-load=dwc2,g_ether quiet splash plymouth.ignore-serial-consoles
```

## Docker support

### Docker Installation

Docker support is now official with Raspbian Jessie:

```bash
SUPPORT_MAP="
...
armv6l-raspbian-jessie
...
```

```bash
curl -sSL https://get.docker.com | sh
```

Verify installation:

```bash
sudo docker run hello-world
```

### Removing elevated requirement

```bash
sudo usermod pi -aG docker
logout
```

(and start your terminal session again, e.g. using SSH)

### Example Dockerfile built and run on device

Here is an example of using custom built Docker image to use Blinkt pHAT:

```Dockerfile
FROM resin/rpi-raspbian:jessie

# dependencies
RUN apt-get update -qy
RUN apt-get install -qy python3
RUN apt-get install -qy python3-pip
RUN apt-get install -qy python3-rpi.gpio
# Cancel out any Entrypoint already set in the base image.
ENTRYPOINT []

# Blinkt
RUN apt-get install -qy python3-blinkt

# app code dependecies

RUN pip3 install request

WORKDIR /root/

# COPY library  library
# WORKDIR /root/library
# RUN python3 setup.py install
# RUN pip3 install request

WORKDIR /root/
COPY examples   examples
WORKDIR /root/examples/
# install app specific  requirements (can be cached already)
RUN pip3 install -r requirements.txt
# code
CMD ["python3", "cheerlights.py"]
```

## Node Support

This will install latest version (https://github.com/sdesalas/node-pi-zero):

```bash
wget -O - https://raw.githubusercontent.com/sdesalas/node-pi-zero/master/install-node-v.last.sh | bash
```

This will produce:

```bash
wget -O - https://raw.githubusercontent.com/sdesalas/node-pi-zero/master/install-node-v.last.sh | bash
--2017-11-25 18:05:45--  https://raw.githubusercontent.com/sdesalas/node-pi-zero/master/install-node-v.last.sh
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.112.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.112.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1703 (1.7K) [text/plain]
Saving to: ‘STDOUT’

-                                       100%[===============================================================================>]   1.66K  --.-KB/s   in 0.001s

2017-11-25 18:05:46 (1.26 MB/s) - written to stdout [1703/1703]

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   99k  100   99k    0     0  75234      0  0:00:01  0:00:01 --:--:-- 75282
--2017-11-25 18:05:48--  https://nodejs.org/dist/v9.2.0/node-v9.2.0-linux-armv6l.tar.gz
Resolving nodejs.org (nodejs.org)... 104.20.23.46, 104.20.22.46, 2400:cb00:2048:1::6814:172e, ...
Connecting to nodejs.org (nodejs.org)|104.20.23.46|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16896011 (16M) [application/gzip]
Saving to: ‘node-v9.2.0-linux-armv6l.tar.gz’

node-v9.2.0-linux-armv6l.tar.gz         100%[===============================================================================>]  16.11M   878KB/s   in 27s

2017-11-25 18:06:16 (619 KB/s) - ‘node-v9.2.0-linux-armv6l.tar.gz’ saved [16896011/16896011]
```

```bash
$ node --version
v9.2.0
```

### Yarn support

The generic installation script works without a problem. See
[Yarn Installation](https://yarnpkg.com/en/docs/install#alternatives-tab):

```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
```

```bash
yarn --version
1.3.2
```

## Hostname Change

Edit configuraction file:

### To change Hostname and Password I simply use `raspi-config`
```bash
sudo raspi-config
```

### Was
```bash
sudo vim /etc/hostname
```

```bash
sudo /etc/init.d/hostname.sh
sudo reboot
```

## Password Change

> This is a security risk - please login as the 'pi' user and type 'passwd' to
> set a new password.

```bash
passwd
```

## Network Connection Over USB

On your Mac OS go to `>System Preferences > Sharing`, select correction
interface in `Share your connection from` dropdown. Then select `To Computer
Using` > `RNDIS/Ethernet Gadget` and finally enable `Internet Sharing` service.

Verify connection from your Raspberry PI:

```bash
ping -c 3 google.com
```

## Audio

### Setup

* Write down your plugged device card and device number:

```bash
arecord -l
```

* Write down your plugged device card and device number:

```bash
aplay -l
```

* create and edit configuration in `/home/pi`:

```bash
touch /home/pi/.asoundrc
sudo vim /home/pi/.asoundrc
```

* add default configuration for sound interface based on previous steps results.
  Example for Sound Blaster Audio card:

```text
pcm.!default {
  type asym
  capture.pcm "mic"
  playback.pcm "speaker"
}
pcm.mic {
  type plug
  slave {
    pcm "hw:1,0"
  }
}
pcm.speaker {
  type plug
  slave {
    pcm "hw:1,0"
  }
}
```

Verify setup by running `speaker-test`:

```bash
speaker-test -t wav
```

## MongoDB

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mongodb-server
```

To allow connection from other machine
[bind to local network address](https://docs.mongodb.com/manual/reference/configuration-options/):

```bash
sudo vim /etc/mongodb.conf
```

```txt
bind_ip = 127.0.0.1,192.168.1.13
```

## Services Status Check

If you installed any component as a service and you are interested to check
their current status:

```bash
sudo service {SERVICE_NAME} status
```

or list all services statuses:

```bash
sudo service --status-all
```

Here it lists `MongoDB` service as not running:

```bash
 [ + ]  kmod
 [ + ]  lightdm
 [ - ]  mongodb
 [ - ]  motd
 [ - ]  mountall-bootclean.sh
 [ - ]  mountall.sh
```

## Increase Swap File Size

Sometimes when compiling from the source it is usefull to increase swap file
size for the duration of the build:

```bash
sudo vim /etc/dphys-swapfile
```

Change from defualt `CONF_SWAPSIZE=100` to `CONF_SWAPSIZE=2048`

Restart swap file service:

```bash
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
...
free -m
             total       used       free     shared    buffers     cached
Mem:           434        284        149          4         20        173
-/+ buffers/cache:         90        343
Swap:         2047          0       2047
```

## Update Python version

Ref.:
[Installing Python 3.6 on Raspbian](https://gist.github.com/dschep/24aa61672a2092246eaca2824400d37f)

## Install TMUX

[tmux wiki](https://github.com/tmux/tmux/wiki) When using SSH you could detach
current session to background using `tmux`:

[tmux cheatsheet](https://gist.github.com/MohamedAlaa/2961058)

To install tmux

    sudo apt-get install tmux

#### Automate ssh and tmux

I'm currently using this function

    function pissh(){
      /usr/bin/ssh -i ~/.ssh/id_ed25519 -t $@ "tmux attach || tmux new";
    }

[Reference](https://stackoverflow.com/a/27614878/118862)

## Backup SD Card

First of all you have to identify the right disk; where is your sdcard. For this you can use:

```bash
diskutil list
```

supposing that your sdcard is connected to `/dev/disk2` you can use the command:

```bash
sudo dd if=/dev/disk2 of=~/Desktop/backup.img
```

where `/dev/disk2` is a name of a mounted sd card, `~/Desktop/backup.img` is a
location of the backup file to be created. After the backup image has been
created use Etcher to flush it to new sd card.

Your image at this point is going to have the exact size of the sdcard. You can use [PiShrink](https://github.com/Drewsif/PiShrink) to reduce it's size so that, when you copy the image on a new sdcard, the image automatically resize itself to the correct size.

PIShrink requires linux because it uses some utilities only available there. To use it on macOS you can use docker and [Dan Sullivan's version of PiShrinks](https://github.com/deepeeess/PiShrink).

```bash
docker-compose run pishrink /pishrink/pishrink.sh /pishrink/someimage.img
```

**NOTE:** You may need to change the image owner from `root` to your own before you are able to use pPisShrinks using the `chown` command.

## Connect/Mount USB memory sticks

### Step 1 – Plug In The Device

The first step is to plug in your USB stick. If you are using a mouse and keyboard you will need a decent USB hub at this point. (e.g. the PiHub by Pimoroni).

### Step 2 – Identify The Devices Unique ID

In order to find the unique reference (UUID) for your drive run the following command in the terminal :

    ls -l /dev/disk/by-uuid/

### Step 3 – Create a Mount Point

A mount point is a directory that will point to the contents of your flash drive. Create a suitable folder :

    sudo mkdir /media/usb

I’m using `usb` but you can give it whatever name you like. Keep it short as it saves typing later on. Now we need to make sure the Pi user owns this folder :

    sudo chown -R pi:pi /media/usb

You will only need to do this step once.

### Step 4 – Manually Mount The Drive

To manually mount the drive use the following command :

    sudo mount /dev/sda1 /media/usb -o uid=pi,gid=pi

This will mount the drive so that the ordinary Pi user can write to it. Omitting the `-o uid=pi,gid=pi` would mean you could only write to it using `sudo`.

Now you can read, write and delete files using `/media/usb` as a destination or source without needing to use sudo.

### Step 5 – Un-mounting The Drive

You don’t need to manually un-mount if you shutdown your Pi but if you need to remove the drive at any other time you should un-mount it first. Only the user that mounted the drive can un-mount it.

    umount /media/usb

If you used the fstab file to auto-mount it you will need to use :

    sudo umount /media/usb

If you are paying attention you will notice the command is `umount` NOT `unmount`!

### Step 6 – Auto Mount

When you restart your Pi your mounts will be lost and you will need to repeat Step 4. If you want your USB drive to be mounted when the system starts you can edit the fstab file :

    sudo vim /etc/fstab

Then add the following line at the end :

    UUID=18A9-9943 /media/usb vfat auto,nofail,noatime,users,rw,uid=pi,gid=pi 0 0

The `nofail` option allows the boot process to proceed if the drive is not plugged in. The `noatime` option stops the file access time being updated every time a file is read from the USB stick. This helps improve performance.

Make sure you set the correct UUID.

Now reboot :

    sudo reboot

Your USB drive should be auto-mounted and available as `/media/usb`.

### An Extra Note About File Systems

In the examples above I specified `vfat` as the file system of the device as it was formatted as FAT32. If you need to change the file system replace references of `vfat` with `ntfs-3g`, `ext3` or `ext4`.

If you are using NTFS you will also need to install the following package :

    sudo apt-get install ntfs-3g

[How To Mount A USB Flash Disk On The Raspberry Pi](https://www.raspberrypi-spy.co.uk/2014/05/how-to-mount-a-usb-flash-disk-on-the-raspberry-pi/)

## Author

[Originally from @peterblazejewicz](https://github.com/peterblazejewicz/raspberry-pi-setup)
Updates from Pietro F. Maggi
