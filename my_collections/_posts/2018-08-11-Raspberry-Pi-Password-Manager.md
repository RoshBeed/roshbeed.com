---
layout: post
title: "Raspberry Pi Password Manager"
author: Rosh Beedassee
categories: tech
tags: [gpg, pass, git, ssh]
image: /img/Raspberry-Pi-Password-Manager/Raspberry-Pi-Password-Manager-1.png 
image_alt: Raspberry Pi
---
As data breaches become increasingly common, securing our online accounts is more important than ever. Cloud-based password managers serve to free us from the need to remember passwords but what of those who don’t want to store their passwords online (or are excessively paranoid)? In this post, we will set up a Raspberry Pi 3 with Raspbian and a Git repository which we will use to store our passwords.

We will use pass to manage our passwords.

Once set up we will have the ability to access our password from any *nix operating system.

## Content

* [Raspberry Pi setup](#raspberry-pi-setup)
* [Local machine setup](#local-machine-setup)
* [Secondary machine setup](#secondary-machine-setup)
* [Software used](#software-used)
* [Conclusion](#conclusion)

## Raspberry Pi setup

This part documents how to install the Raspbian operating system, setup a SSH connection, create a Git repository and a little configuration to secure our device.

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

Set Wi-Fi credentials
<pre>
$ echo "network={\n \
    ssid=\"<b>&lt;your ssid&gt;</b>\"\n \
    psk=\"<b>&lt;your password&gt;</b>\"\n \
}" &gt; ./boot/wpa_supplicant.conf
</pre>

Unmount boot partition
```
$ umount ./boot
```

Clean up files no longer needed
```
$ rm *raspbian*
```

The SD card has been prepared. We have configured it to automatically connect to our Wi-Fi network and enabled SSH.

It is time to insert the SD card into our Raspberry Pi and turn it on.

The next step is to setup the SSH connection and Git repository.

Generate SSH key pair

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

Install Git
```
# apt-get update -y && apt-get install git -y
```

Initialise Git repository
```
$ git init --bare ~/.password-store
```

## Local machine setup

![Password Store](/img/Raspberry-Pi-Password-Manager/Raspberry-Pi-Password-Manager-2.png "Local machine setup")

Now we will initialise the password store and push it to the repository we have created on the Raspberry Pi.

Install gnupg and pass 

The command you need will differ depending on your distribution, e.g.:

Arch:
```
# pacman -Syu gnupg pass
```

Ubuntu:
```
# apt-get install gnupg pass
```

#### GPG setup

Create GPG keys


<pre>
$ cat &gt;foo &lt;&lt;EOF
     Key-Type: default
     Key-Length: 4096
     Subkey-Type: default
     Subkey-Length: 4096
     Name-Real: <b>&lt;John Doe&gt;</b>
     Name-Email: <b>&lt;johndoe@example.com&gt;</b>
     Passphrase: <b>&lt;passphrase&gt;</b>
     %commit
EOF
$ gpg --batch --generate-key foo
$ rm foo
</pre>

Export the GPG key pair

<pre>
$ gpg --export-secret-keys --armor <b>&lt;johndoe@example.com&gt;</b> > \&lt;<b>&lt;johndoe@example.com&gt;</b>\&gt;.gpg-secret
$ gpg --export --armor <b>&lt;johndoe@example.com&gt;</b> > \&lt;<b>&lt;johndoe@example.com&gt;</b>\&gt;.gpg-public
</pre>

You might want to look into using seperate siging keys for each device. This would make it easier to revoke a single key if you lose that device.

#### Pass setup

Initialise password store
<pre>
$ pass init <b>&lt;johndoe@example.com&gt;</b>
</pre>

Initialise Git repo
```
$ pass git init
```

Add remote Raspberry Pi repository 
```
$ pass git remote add origin pi@raspberrypi.local:~/.password-store
```

Push to Raspberry Pi repository
```
$ pass git push
```

## Secondary machine setup

We will learn how to use our password store on other devices

Generate new SSH key pair for new machine

<pre>
ssh-keygen -q -t rsa -f <b>&lt;id_newmachine&gt;</b> -P "<b>&lt;passphrase&gt;</b>"
</pre>

Copy public SSH key to Raspberry Pi
<pre>
$ ssh-copy-id -i <b>&lt;id_newmachine&gt;</b> pi@raspberry.local
</pre>

Copy private SSH key to new machine
<pre>
$ scp <b>&lt;id_newmachine&gt;</b> <b>&lt;user@newmachine&gt;</b>:~/.ssh/id_rsa
</pre>

Copy GPG key pair to new machine
<pre>
$ scp \&lt;<b>&lt;johndoe@example.com&gt;</b>\&gt;.gpg-&#42; <b>&lt;user@newmachine&gt;:~/</b>
</pre>

SSH into new machine
<pre>
$ ssh <b>&lt;user@newmachine&gt;</b>
</pre>

Import GPG keys
<pre>
$ gpg --import \&lt;<b>&lt;johndoe@example.com&gt;</b>\&gt;.gpg-public
$ gpg --allow-secret-key-import \&lt;<b>&lt;johndoe@example.com&gt;</b>\&gt;.gpg-secret
</pre>

Use Git to clone password store from Raspberry Pi to our machine
```
$ git clone ssh://pi@raspberry.local:~/password-store
```

You should now be able to use pass in the same way as you do on your other machine.

## Software used
* [gpg](https://www.gnupg.org/)
* [pass](https://www.passwordstore.org/)
* [git](https://git-scm.com/)
* [ssh](https://www.openssh.com/)


## Conclusion
You can only push and pull passwords when on the same local network as the Raspberry Pi.

You must pull your passwords when on your local network. You are able to use them while disconnected. If you add new passwords while disconnected you must join your local network to be able to push them to the Raspberry Pi.

Here's the  reason I chose not to expose my password store to the Internet: There could be undiscovered security bugs in the software used. If it is exposed to the the Internet and a bug is discovered, in the time between realising the issue and updating the software the passwords may be comprimised

If you would like access to you password store over the internet you will need to forward ports on your router to allow access to your Raspberry Pi.

In the next post we will look at how to use your password store on other operating system (Android & Windows).
