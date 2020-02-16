---
layout: post
title: "1TB iPod Classic Mod"
author: Rosh Beedassee
categories: tech
tags: [ipod, mod, rockbox, linux]
image: /img/1TB-iPod-Classic-Mod/1-The1TBiPodguide.jpg
image_alt: 1TB iPod Classic Mod
---
With the maximum size of an iPod classic at 160GB, I found myself quickly filling up the available storage with lossless FLAC files. I sought for a way to increase the storage capacity. In this post, I will go through the steps I took to upgrade my iPod to 1TB. I like to call it ‘The TeraPod’.

In order to complete this you will need a few things:

| mSATA SSD  | ZIF to mSATA adapter  |
|---|---|
| I used the [Samsung 840 EVO](https://www.samsung.com/us/computer/memory-storage/MZ-MTE1T0BW-specs). | I used Tarken Akdam's [iFlash-Sata – mSata adapter](http://www.tarkan.info/store/iflash-sata) |
| ![][2]  | ![][3]  |


## Open your iPod
You will need to get inside your iPod. I would suggest using plastic opening tool so you do not damage your iPod. If you have purchased a replacement back panel then you can bend your one out of shape while getting it off more easily.

![][4]

Be careful of the battery cable! It's pretty easy to rip the whole connector off.

![][5]

This is what you should see once you open your iPod

![][6]

## Removing the HDD
Flip the hard drive down to reveal the connecting cable

![][7]

Carefully remove the connecting cable

![][8]

The HDD has been removed!

![][9]

## Connecting the SSD
Now it's time to do the reverse with an SSD

![][10]

Plug the connecter into the ZIF to mSATA adapter board

![][11]

There's a few more things left to do


![][12]

## Closing the iPod
Attach the battery cable

![][13]

Close the iPod back up

![][14]

## Restore iPod with iTunes
Connect your iPod to your computer and open iTunes. Press Menu + Select for 10 to 15 seconds which will put your iPod in DFU mode. iTunes should detect your iPod and offer to restore it for you.

![][15]

## Install RockBox (optional)
If your iPod is not recognising all of the storage. It may be limited by the stock OS. You can install [RockBox](http://www.rockbox.org/) to overcome this limitation.
RockBox also has a lot of new features that are not available in the stock OS and I recommend you check it out.

![][16]
![][17]

## Conclusion

The original HDD in the iPod draws 0.5A whereas the SSD draws 1.9A. Playback works great but I had issues copying songs onto the iPod: The load of hitting the SSD would drain the iPod's battery completely before the songs had copied. I remedied this by preloading the bulk of my music using an mSATA to USB adapter, other workarounds include copying batches of songs and waiting for the battery to recharge. Another option would be to go with a ZIF to SD card adapter as they use less power.

I also had problems with the battery connection on the motherboard breaking off after a few connection cycles. It was easy to find a replacement online but I found it difficult to solder on due to how small it was.

[1]: /img/1TB-iPod-Classic-Mod/1-The1TBiPodguide.jpg

[2]: /img/1TB-iPod-Classic-Mod/2-mSATASSD.jpg

[3]: /img/1TB-iPod-Classic-Mod/3-ZIFtomSATAadapter.jpg

[4]: /img/1TB-iPod-Classic-Mod/4-OpenyouriPod.jpg

[5]: /img/1TB-iPod-Classic-Mod/5-BatteryCable.jpg

[6]: /img/1TB-iPod-Classic-Mod/6-Itsopen.jpg

[7]: /img/1TB-iPod-Classic-Mod/7-RemovingtheHDD.jpg

[8]: /img/1TB-iPod-Classic-Mod/8-RemovingtheHDD.jpg

[9]: /img/1TB-iPod-Classic-Mod/9-NoSpace.jpg

[10]: /img/1TB-iPod-Classic-Mod/10-SSDSwap.jpg

[11]: /img/1TB-iPod-Classic-Mod/11-ConnectingtheSSD.jpg

[12]: /img/1TB-iPod-Classic-Mod/12-ConnectedtheSSD.jpg

[13]: /img/1TB-iPod-Classic-Mod/13-BatteryCable.jpg

[14]: /img/1TB-iPod-Classic-Mod/14-Almostdone.jpg

[15]: /img/1TB-iPod-Classic-Mod/15-RestoreiPodwithiTunes.jpg

[16]: /img/1TB-iPod-Classic-Mod/16-InstallRockBox(optional).jpg

[17]: /img/1TB-iPod-Classic-Mod/17-930GB.jpg
