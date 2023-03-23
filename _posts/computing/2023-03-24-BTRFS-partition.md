---
title: "Setup a hard drive with BTRFS and a partition table"
layout: post
author: Nathanael
categories: Computing Linux
tags: 
cover_image: https://archive.kernel.org/oldwiki/btrfs.wiki.kernel.org/images-btrfs/c/c5/Btrfs_logo.svg
excerpt_separator: "<!--more-->"
---
BTRFS is new and with plenty of features, however, the default setup doesn't always play nice with legacy systems. This guide gives you the best of both worlds
<!--more-->

## Why I am writing this?

I setup an OpenMediaVault server to store my files. BTRFS seemed like an interesting filesystem with many of the features to ensure data integrity built in. I setup the drives in a raid 1 array, started a sync and then waited days for it to complete. After this I noticed the drives did not show up in all the expected places. I could access them and write data to them, however, OMV gui did not detect them all the time. This lead me to hearing about a lack of support from some software for hard drives that did not use a GUID table.

BTRFS doesn't require a GUID partition table, however, it can operate with one just fine. Seems like the perfect middle ground, type two extra commands to setup and ensure compatibility with the software I currently use and all the potential software I may in the future.

This guide is quick. The days I had to wait in between partitioning my drives and resyncing the raid array wasn't. Don't be like me, do this from the start.

## The Wiki

You can find the BTRFS wiki [here](https://archive.kernel.org/oldwiki/btrfs.wiki.kernel.org/)

## Setup using 'parted'

- Start parted on the hard drive you wish to create the partition table on

    ```
    sudo parted /dev/sdb
    ```

- You can confirm you have selected the correct drive by viewing the drive information

    ```
    (parted) print
    ```

- Create a new GUID Partition Table

    ```
    (parted) mklabel gpt
    ```

- Create a partition using BTRFS starting at the 4th MiB and using the remaining space on the disk

    ```
    (parted) mkpart part-name btrfs 4MiB 100%
    ```
