# Install ArchLinux on a MacBook 2007

Mainly a series of tips and links to the place where I found the solution.  
This notes are from July 2016, the older they are, the more likely is that you can find some better (more up-to-date) document on internet.

For multiple reason I've decided to install linux on my white MacBook that I bought Fall 2007, a nice machine that served me very well.  
Archlinux is a distribution requiring some intermediate knowledge, especially when you're booting it on an older machine. 

The starting point is the [beginners' guide](https://wiki.archlinux.org/index.php/Beginners'_guide).  I've used even a couple of videos from, very well done and helpful:
    - [Installing Arch Linux in 15 minutes](https://www.youtube.com/watch?v=_fBIeKQSiAc&index=2&list=LLhMFJVtFdG_BvpgBZw4fbTQ)
    - [Installing Arch Linux in 15 Minutes Desktop](https://www.youtube.com/watch?v=1HVGs_ErRL8&index=1&list=LLhMFJVtFdG_BvpgBZw4fbTQ)

I've reported here some of the solution that I found to overcome some of the roadblocks I had to overcome.

Note that (Archlinux has a guide that covers some Mac specific issues](https://wiki.archlinux.org/index.php/MacBook)

## First point, booting the live ISO
My MacBook is using UEFI as bootloader however, even if the CPU is 64bit, the UEFI BIOS is 32bit, so I had to build a custom boot disk (on a USBStick) following this instructions:

[UBUNTU (OR OTHER LINUX) ON THE ASUS TRANSFORMER BOOK T100](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/) 
[LATEST STEPS TO INSTALL UBUNTU ON THE ASUS T100TA](http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/)

The key point was to create a bootable USBStick from the standard archlinux install CD and add a 32bit version of the EFI bootloader, [from here](https://github.com/jfwells/linux-asus-t100ta/tree/master/boot).

## Partitioning and configuring the boot
Following the video, we need to make a change to support the UEFI bootloader for our MacBook. In this case it is important to create the boot partition using the FAT32 filesystem and then I've used the `efibootmgr` utility; in my case:
    
    efibootmgr -d /dev/sda -p 1 -c -L "Arch Linux" -l /vmlinuz-linux -u "root=/dev/sda2 rw initrd=/initramfs-linux.img"

More info available on the [Archlinux EFI guide](https://wiki.archlinux.org/index.php/EFISTUB#Booting_EFISTUB)

## WiFi card
My MacBook is using a Broadcom BCM4321 WiFi card, don't know why but the module in the default kernel does not recognize it.  [But seems to be a common issue](https://bbs.archlinux.org/viewtopic.php?id=198246)    
In this case the issue is installing the b43-firmware package that can be find in the [AUR archive](https://aur.archlinux.org/packages/b43-firmware/), to do this, I've taken some informations on interned on [how to install an AUR package](https://bbs.archlinux.org/viewtopic.php?id=93793).  
At the end is really:

- Download the package:

    curl https://aur.archlinux.org/cgit/aur.git/snapshot/b43-firmware.tar.gz -O

- unpack it

    tar xzvf b43-firmware.tar.gz

- build the package

    cd b43-firmware
    makepkg -s

- install it

    sudo pacman -U /path/to/pkg.tar.xz
    
- configure the network

    sudo wifi-menu

## Other issues that I still have to investigate

    - The trackpad is detected and seems to work, but the mouse position is sending points only for the lower half of the screen. This is not usable at this moment and I'm using a USB Mouse.
    - Bluetooth HW is not detected
    - WiFi is not connected automatically even when the network is known 