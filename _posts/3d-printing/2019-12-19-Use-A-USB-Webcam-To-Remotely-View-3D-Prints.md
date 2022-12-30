---
layout: post
author: Nathanael
categories: 3D-Printing
tags: coffee baratza
cover_image: /assets/images/3d-printing/2019-12-19-Use-A-USB-Webcam-To-Remotely-View-3D-Prints/octoprint_webcamview.png
excerpt_separator: "<!--more-->"
---
One of the many great perks of running OctoPi and OctoPrint for your 3D printer is the USB webcam support allowing you to remotely view your 3D prints.<!--more-->

To edit the resolution and framerate of this camera feed you need to change the mjpg-streamer parameters found in the config file */boot/octopi.txt* by opening it with your favourite text editor (i.e. nano). Here are a few ways to do this:

- Insert the OctoPi SD card into another computer
- Edit directly from the Raspberry Pi
- ssh into the Raspberry Pi

Personally, my favourite option is to ssh into the Raspberry Pi. This is because we have already got the Raspberry Pi running on our network, connected to the 3D printer without a screen, keyboard or mouse. There is no messing about with wires or SD cards and once we have finished editing the file we can even reboot from the command line (using sudo reboot).

Now to editing */boot/octopi.txt*
With the config file open you will be looking for this line:

```
#camera_usb_options=”-r 640×480 -f 10″
```

Remove the comment ‘#’ from the start of the line to enable this option.

To change the resolution replace ‘640×480’ with your desired resolution.

Editing the framerate is similar, replace ’10’ with your desired framerate. When editing your framerate keep in mind that making this too high may affect your print quality if the raspberry pi is struggling to process everything. A rule-of-thumb I have seen across many forums is to increase this number to 15.

Keep in mind that you can only access OctoPrint on your local network. If you want to be able to access it over the internet you could use a VPN. As mentioned in my [SET UP OCTOPRINT/OCTOPI ON A RASPBERRY PI 4](http://nathanaelgandhi.com/3d-printing/2019/12/15/Setup-Octoprint-on-a-Raspberry-pi-4.html) post, I followed [Kyle Rector’s guide to installing Hamachi on Raspberry Pi](https://medium.com/@KyleARector/logmein-hamachi-on-raspberry-pi-ad2ba3619f3a).

This is one part of my [Remote 3D Printing Setup](https://nathanaelgandhi.wordpress.com/2019/12/05/remote-3d-printing-setup/) project.
