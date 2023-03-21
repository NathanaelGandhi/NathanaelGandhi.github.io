---
title: "Setting up Distrbox on Ubuntu 22.04"
layout: post
author: Nathanael
categories: Computing Linux
tags: Linux
cover_image: https://user-images.githubusercontent.com/598882/144294862-f6684334-ccf4-4e5e-85f8-1d66210a0fff.png
excerpt_separator: "<!--more-->"
---
Distrobox allows you to use any Linux distribution inside your terminal and run applications from these distributions as if they were installed natively.
<!--more-->

## Why I am writing this guide

At the time of writing, Distrobox was not available in the Ubuntu 22.04 repositories. So I tired the next logical step (at least for me), installing distrobox from the provided script. This didn't give me the plug-and-play experience I was hoping for, and as such, I delved more enthusiastically into the documentation. I found this little gem (PPAs) buried on the [compatibility page](https://github.com/89luca89/distrobox/blob/main/docs/compatibility.md#host-distros): <https://launchpad.net/~michel-slm/+archive/ubuntu/distrobox>

## Will I need this guide for Ubuntu 22.10 and later?

For those curious as to whether this guide will be necessary for Ubuntu 22.10 and later versions, Distrobox is available in the default repositories of Ubuntu 22.10 and 23.04 versions, courtesy of [michel-slm](https://github.com/michel-slm). Therefore, it will not be necessary to follow this guide in the future; simply execute "apt install distrobox."

While it is currently unclear whether Distrobox will continue to be available in later versions beyond 23.04, it stands to reason that the continued adoption of this amazing software will ensure its longevity.

## How to install Distrobox on Ubuntu 22.04?

1. Add the PPA

    ```shell
    sudo add-apt-repository ppa:michel-slm/distrobox
    ```

2. Update apt

    ```shell
    sudo apt update
    ```

3. Install distrobox

    ```shell
    sudo apt install distrobox -y
    ```

These steps successfully installed Distrobox on my system!

## Next steps

Now that I have Distrobox installed, I used it to quickly grab Elixir and run some scripts.

My next step is to experiment with exporting apps to my host system, followed by using different architectures. If I can compile and test  code "on" Arm, that would be a pretty useful.
