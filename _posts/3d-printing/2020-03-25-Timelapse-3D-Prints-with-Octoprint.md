---
layout: post
author: Nathanael
categories: 3D-Printing
tags: 
cover_image: /assets/images/3d-printing/2020-03-25-Timelapse-3D-Prints-with-Octoprint/capture-1.webp
excerpt_separator: "<!--more-->"
---
OctoPrint is full of features and one great built in one allows you to take timelapses of your prints. <!--more-->

The way this works is OctoPrint waits for a z-axis change which signals going from one layer to the next. This is the trigger that takes a photo. After your print has completed all the photos are rendered together giving you a timelapse video of your print.

The configuration settings are quite simple and easy to modify. Keep in mind that you can not edit the configuration settings while you have a print running and be sure to tick “Save as default” once you have your settings dialed in.

![](/assets/images/3d-printing/2020-03-25-Timelapse-3D-Prints-with-Octoprint/capture.png){: .image.post_wide}

This feature works great out of the box however there are a few things to keep in mind. The photo is taken on layer change which could mean the bed and/or nozzle is in a different position every photo. This can leave you with a timelapse that is a bit jerky and disorientating to watch. To combat this problem I will be setting up Octolapse which allows you to set a bed and nozzle position for each photo on layer change.

3D Print Timelapse – Flexible webcam mount
<https://youtu.be/v97WJOu5JM4>

3D Print Timelapse – ChristmasFigures Duende
<https://youtu.be/P9j3Ga4w68w>

This is one part of my [Remote 3D Printing Setup](http://nathanaelgandhi.com/3d-printing/2019/12/05/Remote-3D-Printing-Setup.html) project.
