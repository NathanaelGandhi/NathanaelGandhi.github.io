---
layout: post
author: Nathanael
categories: 3D-Printing
tags: 
cover_image: /assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/20191215_235358.webp
excerpt_separator: "<!--more-->"
---
How to setup octoprint/octopi on a RPI 4
<!--more-->

## My Setup

- Raspberry Pi 4
- 5V 3A microUSB power supply
- MicroUSB to USB C adapter
- Micro SD Card
- Micro SD Card Reader/USB adapter
- 3D printer USB Cable

OctoPrint recommends using the OctoPi image maintained by Guy Sheffer. This is the route I took. I downloaded and extracted this from the [OctoPrint website](https://octoprint.org/download/), however, you could also get it from [Guy’s GitHub](https://github.com/guysoft).

Next, I downloaded and installed [Etcher](https://www.balena.io/etcher/). Etcher is used for installing the extracted .img OctoPi file onto the sd card. First I selected the OctoPi image.

![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture1.png){: .image.post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture2.png){: .image.post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture3.png){: .image.post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture4.png){: .image.post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture5.png){: .image.post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture6.png){: .image post_wide}
![](/assets/images/3d-printing/2019-12-15-Setup-Octoprint-on-a-Raspberry-pi-4/capture7.png){: .image.post_wide}

Etcher ejects the sd card once it completes so I reinserted it to set up the wifi settings. Using VSCode (you could also use Atom or notepad++) I edited octopi-wpa-supplicant.txt on the sd card.

Now time to boot the Raspberry Pi 4 with the configured OctoPi sd card and connect via ssh. To do this I logged into my router and found the new IP address assigned to the raspberry pi. I then logged in using command line *‘ssh pi@IP-address’*. To finish off configuring OctoPi I ran *sudo raspi-config*, changed my password and rebooted.

Accessing OctoPrint using <http://octopi.local> doesn’t work on windows without Bonjour Print Services for Windows. Instead, I used <http://<your> pi’s ip address>.  This allowed me to finish the set up of OctoPi.

Now a locally available remote for my 3D printer is good, but not quite perfect. To be able to access the controls from anywhere in the world with an internet connection I will need to set up a VPN. I did this by following [Kyle Rector’s guide to installing Hamachi on Raspberry Pi](https://medium.com/@KyleARector/logmein-hamachi-on-raspberry-pi-ad2ba3619f3a).

This is one part of my [Remote 3D Printing Setup](http://nathanaelgandhi.com/3d-printing/2019/12/05/Remote-3D-Printing-Setup.html) project.
