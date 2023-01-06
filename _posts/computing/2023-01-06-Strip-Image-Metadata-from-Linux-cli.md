---
layout: post
author: Nathanael
categories: Computing Linux
tags: cli images exif
cover_image: /assets/images/computing/2023-01-06-Strip-Image-Metadata-from-Linux-cli/index.png
excerpt_separator: "<!--more-->"
---
How to strip the metadata out of your images from the linux commandline
<!--more-->

I want to start posting more images to this website, however, sometimes the metadata includes things I would prefer not to share openly. This was the motivation for looking up ways to remove this metadata conveniently, and for me [ExifTool by Phil Harvey](https://exiftool.org/) is perfect.

Johannes Eva has a great writeup about this tool: [How to edit EXIF metadata via the command line with ExifTool](https://libre-software.net/linux/edit-metadata-exiftool/)

The commands I plan to keep on hand are:

### Keep the original file & remove all metadata from a file

``` linux
exiftool -all= filename.extension
```

### Keep the original file & remove all metadata from the current directory

``` linux
exiftool -all= .
```

### Overwrite the original file & remove all metadata from a file

``` linux
exiftool -all= -overwrite_original filename.extension
```

### Overwrite the original file & remove all metadata from the current directory

``` linux
exiftool -all= -overwrite_original .
```
