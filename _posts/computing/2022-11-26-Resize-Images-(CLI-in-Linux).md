---
layout: post
author: Nathanael
categories: Computing Linux
tags: Technology Images
cover_image: /assets/images/computing/2022-11-26-Resize-Images-(CLI-in-Linux)/ImageMagick_logo_1024x683.png
excerpt_separator: "<!--more-->"
---
How to quickly resize images from Linux command line.
<!--more-->

## ImageMagick

<https://imagemagick.org>

```
sudo apt-get install imagemagick
```

Use the ```convert``` command with the ```-resize 1024x683```

Example

```
convert -resize 1024x683 example.jpg example_1024x683.jpg
```

[How-To-Geek](https://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/) has a great writeup.
