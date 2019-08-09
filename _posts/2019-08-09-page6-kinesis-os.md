---
layout: post
title: Kinesis OS
subtitle: Don't try this at home
tags: [scripting, bash, distro, linux]
comments: true

slider:
  text_color: white
  shadow_color: black
  slides:
    - image: /img/k_os/final-kde.jpg
    - image: /img/k_os/manual-install.png
    - image: /img/k_os/pacman-install.png
    - image: /img/k_os/pacman-install-2.png
---

## Ready to achieve my dream

Years ago, I was making various devices ranging from phones to laptops
out of sheets of cardboard from my cereal boxes. I also designed the
motherboard and circuits of these cardboard devices. They weren't 'real'
devices that turned on though. Ever since I started making these, I dreamt
of building my own operating system one day. Of course I did my research
at that time but didn't understand much.

After moving to linux distros, I gradually felt that this dream I had was
achievable. I didn't know if I was ready but I wanted to try making my
own linux distro and thus my own operating system.

## What a guide

I started out by following the guide of 
[Linux from Scratch](http://www.linuxfromscratch.org/). It is an excellent
guide where one can understand how a Linux system operates and how the
filesystem is laid out. The first couple pages of the guide teaches all
about how to prepare partitions and introduces how to install packages
manually. Basically, a partition is created to host the new OS that will
be made. Then packages, which will contain libraries and utilities that
the new OS will use are downloaded, extracted and compiled in a directory
on that newly created partition.

Finally, the guide instructs to change root to that new partition and
compile packages for the final system. A couple of other steps needs to be
performed in order to boot the final system, to get WiFi working and to
obtain a graphical user interface (GUI) amongst other things.

## A week full of difficulties

For this blog post, I'll be employing SBUs to explain difficulties I faced.
1 SBU refers to the time it takes to compile the Binutils package.

The first trouble I faced was that I was creating Kinesis OS on my laptop
which was rocking an Intel Celeron processor. 1 SBU was equal to around 4
minutes which takes an absurbly long time when packages of like 90+ SBUs need
to be installed. Moreover, I couldn't do anything else smoothly meanwhile because
all of my laptop's resources was being used to compile packages. I then 
successfully repaired a broken laptop I had and turned it into a work bench.
It was significantly faster with a SBU of around 1.5 minutes and I used it
to compile all my packages and build Kinesis OS. 

The second issue I faced was entirely my fault. Instructions were given and
needed to be followed to the letter but I forgot about the last one. Packages
come in an archive format. These archives need to be extracted and once in 
the specific extracted directory, commands need to be issued to compile that
package. Sometimes, packages need to be recompiled again due to their 
dependencies. When this needs to be done, the respective archive needs to be
extracted again and the package needs to be again recompiled from scratch.
But that recompilation at times differs from the options used during 
the first compilation. My mistake was that I wasn't deleting the extracted
directory of a package after the first compilation and was again compiling it
the second time using the options I used during the first.

Thirdly, it was really difficult to figure out how to get the internet working
via a wireless connection. There were several ways to do it but the instructions
and steps were too blurry. In my case, I was going with a dynamically allocated 
IP address. In the end, I managed to find my way and make use of the 
`wpa_supplicant` package as well as `dhclient` from the `dhcpcd` package to
get my WiFi to work. Additionally, I had to create the `/etc/resolv.conf` file
with Google's nameservers in it in order for DNS to work correctly.

Lastly, I wanted to make use of a package manager; more specifically the
[pacman package manager](https://wiki.archlinux.org/index.php/pacman) from 
[Arch Linux](https://www.archlinux.org/). Unfortunately, no help was provided
by the [Linux from Scratch](http://www.linuxfromscratch.org/) guide in order to
install any package manager of some sort. This directly meant that if a linux
distro was being made after these instructions, any app or package you would
want would need to be manually installed from source, which takes a lot of time.
Any package manager would be able to do this faster and thus be more practical.
I had finished the guide several times by now. I once again restarted from
scratch because [pacman](https://wiki.archlinux.org/index.php/pacman) had
no idea and no way of knowing about the files of packages that I had already
installed manually. When I tried to install or update packages using
[pacman](https://wiki.archlinux.org/index.php/pacman), it failed miserably 
because it couldn't overwrite or replace files that were already there from
the packages that it was trying to install.

During my last attempt, I installed packages from the start using 
[pacman](https://wiki.archlinux.org/index.php/pacman) and finally managed
to get everything to work correctly even if I faced some minor issues.
I refined my Kinesis OS install, removed unnecessary files and created
scripts to help future users get going faster with the installation of
Kinesis OS. To end, I created a [website](https://os.kinesisgames.net) 
to host details and instructions about Kinesis OS.

All these difficulties I faced cost me a lot of time and I had to restart
from scratch several times; 8 times if my memory is correct. All of this could
have been easily avoided if more elaborate and longer instructions were
given in the book itself while I don't deny that I'm to blame to some limit.
I felt so down and wanted to give up so many times due to all the issues I faced
to be honest. I'd like to thank everyone who motivated me during this experience.
