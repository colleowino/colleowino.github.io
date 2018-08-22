---
layout:     post
title:      "my slow ubuntu [unresolved]"
date:       2018-08-22 12:27:00 am
tags: hacks tools
categories: ubuntu
author:     "colleowino"
header-img: /img/ubuntu.jpg

---
My ubuntu os has suddenly become slow and I wanted it make it faster. I figured it would be caused by some of these updates. I usually update my computer whenever there is an update available. How about I downgrade my kernel version maybe that would be the answer. 

```shell
% uname -r
4.15.0-30-generic
```
The next step was to figure out how to downgrade it.Then I read somewhere that the best way to go about it is to remove the current version and then it will fall back to the previous version. Big mistake. 
```shell
 sudo apt-get remove linux-image-4.13.0-45-generic linux-headers-4.13.0-45-generic
```
At some point it adviced me that updating that removing the current kernel was unsafe and it was better to abort the mission. I gave in and abandoned what it. Unfortunately I removed the other and reboot my system. Now when I boot up it doesn't load the network, sound and brightness drivers.
Upon further googling, I decided to download the packages on another computer and install them manually
```
sudo dpkg -i *.deb 
```
This appeared to be working but it still forced me to restart when the drivers fail to load on startup and then it picks them up at when I don't use grub menu to select the os.

Now am just looking for a way to make the grub updates [permanent](https://ubuntuforums.org/showthread.php?t=2200335)

already tried ``sudo update-grub`` it would update grub but the same menu would show up when at boot. 
```
% sudo update-grub                                                                                   
[sudo] password for cliff:
Generating grub configuration file ...  
Found linux image: /boot/vmlinuz-4.17.0-041700-generic
Found initrd image: /boot/initrd.img-4.17.0-041700-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found linux image: /boot/vmlinuz-4.15.0-23-generic
Found initrd image: /boot/initrd.img-4.15.0-23-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 16.04.4 LTS (16.04) on /dev/sda8
Adding boot menu entry for EFI firmware configuration
done
````
Time to add something else ```sudo grub-install /dev/sda`` and that still didn't work out
```
% sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, httpsblocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```
Read up on grub and turns out [grub 2](https://opensource.com/article/17/3/introduction-grub2-configuration-linux) needs to be installed in the boot partition, checked out which partiton I was using through ``disks``  and gave it another go.

At that point I just booted up my other ubuntu partition and run update-grub. I reasoned that it could be under the control of that grub config. Lo and behold. It detected the pop os partition and on reboot it even showed the other kernel versions I had installed. Now it was time to go back to the hunt for what was actually causing the slow boot times.
``` 
sudo systemctl disable NetworkManager-wait-online.service
````
That didn't seem to help things and I resorted to the critical chain, looking for the service that's causing me the most pain and dealing with them one by one.
```
% systemd-analyze critical-chain                     
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @49.851s
└─multi-user.target @49.851s
  └─postfix.service @32.079s +1ms
    └─postfix@-.service @29.654s +2.424s
      └─network-online.target @29.653s
        └─network.target @29.652s
          └─NetworkManager.service @24.415s +5.236s
            └─dbus.service @24.095s
              └─basic.target @24.094s
                └─sockets.target @24.094s
                  └─uuidd.socket @24.094s
                    └─sysinit.target @23.999s
                      └─systemd-timesyncd.service @23.654s +345ms
                        └─systemd-tmpfiles-setup.service @23.236s +388ms
                          └─systemd-journal-flush.service @3.701s +19.533s
                            └─systemd-remount-fs.service @3.241s +427ms
                              └─systemd-journald.socket @3.150s
                                └─system.slice @3.150s
                                  └─-.slice @3.149s
```
Instead of disabling journal [flashing](https://forum.antergos.com/topic/6151/disabling-systemd-journal-flush-service/2) its better to set to clean after a few days. 
disabled a few others
```
% sudo systemctl disable lvm2-monitor.service  
[sudo] password for cliff: 
Removed /etc/systemd/system/sysinit.target.wants/lvm2-monitor.service.
```
Went as far as adjusting the networkManager-wait-online settings
[link](https://askubuntu.com/questions/615006/ubuntu-15-04-network-manager-causing-slow-boot)

Now its still slow but blame is pointing to a different reason 
```
% systemd-analyze blame              
         25.186s apt-daily.service
         22.682s plymouth-quit-wait.service
         19.750s systemd-journal-flush.service
         13.272s dev-sda5.device
         13.201s lvm2-activation-early.service
```
To disable it ``sudo systemctl edit apt-daily.timer`` and add time [options](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297) to it
```
[Timer]
OnBootSec=15min
OnUnitActiveSec=1d
AccuracySec=1h
RandomizedDelaySec=30min
```
Its getting incredibly frustrating and I have decided to fight a different battle. I will re-install everything in the hopes that I will be careful about the boot times and try to notice if it get's any slower in future runs. Then triage the exact cause as soon as possible. 

-----

