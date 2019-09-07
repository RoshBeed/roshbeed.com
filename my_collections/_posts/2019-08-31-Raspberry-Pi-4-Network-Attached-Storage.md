---
layout: post
title: "Raspberry Pi 4 Network Attached Storage"
author: Rosh Beedassee
categories: tech
tags: [nfs, linux, ssh, raspberry pi]
image: /img/Raspberry-Pi-Network-Attached-Storage/Raspberry-Pi-Network-Attached-Storage-1.jpg 
image_alt: Network Cables
---
I’m on a quest to find cost-effective ways to store my data. The offerings from cloud providers are enticing, but the subscription payment method can cost a lot over time. Pre-built NAS boxes another option, but they come with a high upfront cost. I decided to create a storage solution using a Raspberry Pi 4 and an SSD drive. In this post, learn how to store data in a centralised location within a local area network and access that data from other devices.

## Content

* [Raspberry Pi Setup](#raspberry-pi-setup)
* [SSH Setup](#ssh-setup)
* [NFS Server Setup](#nfs-server-setup)
* [Disk Setup](#disk-setup)
* [NFS Client Setup](#nfs-client-setup)
* [Software used](#software-used)
* [Conclusion](#conclusion)

## Raspberry Pi Setup

We must install the Raspbian operating system and enable SSH onto the Raspberry Pi.

Download latest Raspbian image
```
$ wget https://downloads.raspberrypi.org/raspbian_lite_latest
```

Extract the image
```
$ unzip raspbian_lite_latest
```

Write image to our SD card
<pre>
# dd if=./*raspbian*.img of=/dev/sd<b>&lt;XX&gt;</b>
</pre>

Mount the boot partition from our SD card
<pre>
# mount /dev/sd<b>&lt;X&gt;</b>1 ./boot
</pre>

Enable SSH 
```
$ touch ./boot/ssh
```

Unmount boot partition
```
$ umount ./boot
```

Clean up files no longer needed
```
$ rm *raspbian*
```

The SD card has been prepared. We have configured it start SSH.

Insert the SD card into our Raspberry Pi and connect the power supply.

## SSH Setup
Setup the SSH connection.

<pre>
ssh-keygen -q -t rsa -f $HOME/.ssh/id_rsa -P "<b>&lt;passphrase&gt;</b>"
</pre>

Copy SSH public key to Raspberry Pi

```
$ ssh-copy-id pi@raspberrypi.local
```

SSH into Raspberry Pi
```
$ ssh pi@raspberrypi.local
```

Change the default password to something secure

<pre>
# echo 'pi:<b>&lt;newpassword&gt;</b>' | chpasswd
</pre>

Disable SSH password authentication
```
$ sudo grep -q "^[^#]*PasswordAuthentication" /etc/ssh/sshd_config && sed -i "/^[^#]*PasswordAuthentication[[:space:]]yes/c\PasswordAuthentication no" /etc/ssh/sshd_config || echo "PasswordAuthentication no" >> /etc/ssh/sshd_config
$ systemctl restart sshd
```


## Disk Setup

We need to format our disk drive and mount it before we can share it on the network.

Format Disk to ext4
<pre>
# mkfs.ext4 /dev/sd<b>&lt;X&gt;</b>1
</pre>

Create NFS mountpoint
```
# mkdir /media/nfs
```

Mount Disk
<pre>
# mount /dev/sd<b>&lt;X&gt;</b>1 /media/nfs
</pre>

Mounting at boot
<pre>
# echo "/dev/sd<b>&lt;X&gt;</b>1 /media/nfs ext4 defaults 0 0" >> /etc/fstab
</pre>

## NFS Server Setup
NFS is a client/server application which allows us to share directories over the network.

Install NFS server
```
# apt-get update -y && apt-get install nfs-kernel-server
```

Add directory to `/etc/exports`
```
# echo "/media/nfs *(ro,all_squash,insecure)" >> /etc/exports
```

Re-export changes
```
# exportfs -arv
```

## NFS Client Setup

Install the components required for the NFS client

Arch:
```
# pacman -Syu nfs-utils
```

Ubuntu:
```
# apt-get install nfs-common
```

Create a mountpoint
```
# mkdir /media/nfs /media/nfs
```

Mount the NFS share on the client
<pre>
# mount raspberrypi.local:/media/nfs /media/nfs
</pre>

Mounting at boot
<pre>
# echo "raspberrypi.local:/media/nfs /media/nfs nfs defaults 0 0" >> /etc/fstab
</pre>



## Software used
* [nfs](https://tools.ietf.org/html/rfc7530) 
* [ssh](https://www.openssh.com/)


## Conclusion
The latest Raspberry Pi now has USB 3 as well as Gigabit networking which is a vast improvement over the previous models. The ability to create high throughput network storage with Raspberry Pis is now possible.

NFS is not fast by default. Optimisations can improve performance. Other protocols (e.g. rsync) may offer better performance.

This was a quick tutorial on how to setup NFS. The next steps are to secure the  NFS share. Overall it was a successful project. It was cheaper than a pre-built NAS box.
