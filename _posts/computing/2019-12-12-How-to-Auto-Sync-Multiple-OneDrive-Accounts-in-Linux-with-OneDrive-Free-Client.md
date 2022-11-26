---
layout: post
author: Nathanael
categories: Computing Linux
tags: 
cover_image: /assets/images/computing/2019-12-12-How-to-Auto-Sync-Multiple-OneDrive-Accounts-in-Linux-with-OneDrive-Free-Client/42531-82515-onedrive-xl.jpg
excerpt_separator: "<!--more-->"
---
This guide was made using Ubuntu 18.04.
<!--more-->
OneDrive Free Client is a CLI client by Skilion that can be configured to auto-start on boot.

    Follow the Setup instructions for Dependencies, Installation, First run & Configuration found in the README.

___

We can now set up multiple accounts.
Start by making new local onedrive and .config folders

```
mkdir ~/OneDriveWork && mkdir ~/.config/onedriveWork && cp ~/.config/onedrive/config ~/.config/onedriveWork/
```

Edit sync_dir in the config file to sync_dir = “~/OneDriveWork”
*(ctrl+o to save. ctrl+x to exit)*

```
cd .config/onedriveWork && nano config
```

Create an autostart script

```
nano onedriveAutostart.sh
```

Enter the following and save

```
#!/bin/bash
/user/local/bin/onedrive –monitor –confdir=”~/.config/onedrive” & /user/local/bin/onedrive –monitor –confdir=”~/.config/onedriveWork” &
```

Make the script executable by changing the permissions

```
chmod +x onedriveAutostart.sh
```

Add the script to automatically start on boot

```
crontab -e
```

Go to the bottom of the file and add

```
@reboot ~/.config/onedriveWork/onedriveAutostart.sh
```

Run onedrive once and repeat the first time run instructions, similar to the initial setup, this time with your work account login.

```
onedrive –monitor –confdir=”~/.config/onedriveWork
```

Reboot

```
sudo reboot
```

*Let me know if this helped you!*
