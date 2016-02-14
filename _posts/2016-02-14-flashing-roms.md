---
layout:     post
title:      "I flashed a custom rom and I liked it"
date:       2016-02-14 02:15:00
tags: android flashing rom flash-tool 
categories: tools
author:     "colleowino"
excerpt: Well, android one dropped in Kenya and I not being the one to be left out got myself one. After experiencing a couple of issues mainly to do with the "doze" feature I decided to go back to the stock rom. Here is how it went down.

---
Its valentines day and its almost 3 am and am out here flashing roms. This is the life I was given. I don't think I chose this life, it chose me. I do this for the love of the game more than anything. So I code late at night for reasons I find hard to articulate. Frankly I bought an infinix and immediately after upgrading the os to marshmallow thinks got weird. The doze feature became my main source of pain. Pressing the wake button taught me a think or two about patience.

I had to wait 5 second on average to get the screen to light up and the worst part is that it doesn't matter whether the phone was idle of if you were making a call. Imagine waiting some seconds just to hang up and no matter who you call. If you want to end the call, you end it right there and then. I guess with time people would expect me cursing to signal the end of the call but before things got there I decided to act. 

So I searched online on the best way to flash back to stock android and I found a nice article on xda-developers and I knew my problems were about to end. You know how it goes, I downloaded the rom but this guy didn't post a link to the flash tool. So I had to look for it somewhere else. Okay, Its not so bad. found it a half an hour later and all seemed good but nah. Installing VCOM drivers was a pain and eventually it failed to work on windows.

I spent two weeks downloading different versions of the same flashing tool and It still wasn't working. I finally gave up on windows and went on with my life until yesterday when I decided to try if I could flash it using ubuntu. I knew there was linux version so I downloaded it and tried flashing it but nothing worked. So I hit the interwebs again and boom I found a really nice article that walked me through the installation process and I could even do <code> dmesg | grep usb </code> and see my phone detected :D

So I was sure that my phone was getting detected but when I clicked flash it still wasn't working. At this point I was almost giving up and then went to Youtube. That's when I noticed I was doing it wrong from the start. Maybe it could have even worked on windows. Looking at the output from flash tool. It showed that it was waiting for the device to show up. All I needed to do was to unplug it and then reconnect it and the flash process starts. 

So I flashed the rom and it was all good but then again the wifi signal keeps acting out and now I have downloaded a new rom. Hope this is the final one. I will update to marshmallow if it gets stable. May the doze work 

### References

1. The xda link where I got the first stock rom [link](http://forum.xda-developers.com/hot-2/development/stock-rom-lollipop-5-1-1-x510-d5110-l-t3203255), [stackexchange](http://android.stackexchange.com/questions/119068/how-to-root-mtk-based-mobile-devices-using-a-linux-pc)
2. Installing sp tool in linux tutorial [link](http://www.needrom.com/download/how-to-setup-sp-flash-tool-linux-mtk/)
3. The home page for sp flash tool [link](http://spflashtool.com)
4. An alternative link for sp flash tool [link](http://androidmtk.com/smart-phone-flash-tool)
5. Alternative link for the stock rom [link](http://www.guruswizard.com/2016/01/install-android-6-0-marshmallow-ota-infinix-hot-2-x510.html)
6. An awesome tutorial on how to install adb/fastboot if your device isn't getting detected [link](http://bernaerts.dyndns.org/linux/74-ubuntu/328-ubuntu-trusty-android-adb-fastboot-qtadb)


-----
