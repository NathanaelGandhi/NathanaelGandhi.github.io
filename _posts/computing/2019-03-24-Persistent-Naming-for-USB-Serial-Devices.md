---
layout: post
author: Nathanael
categories: Computing Linux
tags: Technology
cover_image: /assets/images/computing/2019-03-24-Persistent-Naming-for-USB-Serial-Devices/5162231371_9fd1f53830_b.jpg
excerpt_separator: "<!--more-->"
---
Set a USB devices name in Linux
<!--more-->

## Rule Layout

```SUBSYSTEM==”tty”, ATTRS{idVendor}==”0403″, ATTRS{idProduct}==”6001″, ATTRS{serial}==”A6006B1W”, SYMLINK+=”um7″```

### Step 1: Find device USB port name

```udevadm monitor```

### Step 2: Plug/unplug your device and look for “ttyUSB0”

```
KERNEL[59094.407544] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/ttyUSB0/tty/ttyUSB0 (tty)
KERNEL[59094.407631] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/ttyUSB0 (usb-serial)
KERNEL[59094.407759] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0 (usb)
KERNEL[59094.408442] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4 (usb)
KERNEL[59094.408825] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0 (usb)
KERNEL[59094.409507] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3 (usb)
UDEV [59094.425841] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/ttyUSB0/tty/ttyUSB0 (tty)
UDEV [59094.426082] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0 (usb)
UDEV [59094.426230] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/ttyUSB0 (usb-serial)
UDEV [59094.426960] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0 (usb)
UDEV [59094.427408] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4 (usb)
UDEV [59094.428014] remove /devices/pci0000:00/0000:00:14.0/usb1/1-3 (usb)
```

### Step 3: Find SUBSYSTEM, idVendor, idProduct and serial of the device

Note: Change “ttyUSB0” to the device you are interested in. Udevadm info starts with the device specified by the devpath and then walks up the chain of parent devices. Therefore only use the first value output for each field.

```
udevadm info -a -n /dev/ttyUSB0 | grep -E ‘SUBSYSTEM|{idVendor}|{idProduct}|{serial}’
```

### Step 4: Create UDEV rules file

```
sudo nano /etc/udev/rules.d/99-myrobot.rules
```
