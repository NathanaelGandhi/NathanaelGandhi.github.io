---
title: "OneDrive in Ubuntu 20.04"
excerpt_separator: "<!--more-->"
categories:
  - Computing
tags:
  - Software
---

This tutorial is for those that are new to Ubuntu 20.04 and want a way to sync all or part of their Microsoft OneDrive.

This tutorial is based on the abraunegg's docs outlined on git. If you are confident in setting up linux programs I highly recommend to follow the official documentation.<br>
Git: [github.com/abraunegg/onedrive](https://github.com/abraunegg/onedrive)

# 1. Install onedrive via Ubuntu PPA Archive:
```
sudo add-apt-repository ppa:yann1ck/onedrive
sudo apt-get update
sudo apt install onedrive
```

# 2. Authorize the application with your OneDrive Account

## 2.1 Get the onedrive URI
This command will provide you a URI that will need to be copy & pasted into a browser.
```
onedrive
```

## 2.2 Enter the response URL

Once you have pasted the previous URI into a browser, press *"enter"* (or equivalant). 
You will be asked to log into your OneDrive account.<br> 
*Note: If you are not asked to login to your OneDrive account you may have already been logged in on that browser.*

The resulting *"blank"* page is not a mistake. Copy the URL (in full) and paste it *(ctrl+shift+v)* into the terminal where the program says *"Enter the response url:"*.

# 3. (OPTIONAL) Enable selective sync

## 3.1 Create a file named sync_list in the onedrive config folder. 

```
nano ~/.config/onedrive/sync_list
```

## 3.2 list files/folders to sync.

List these one path per line. 

*For example: If I have three folders in my OneDrive, "Pictures", "Videos" & "Music". I could type the following to only sync pictures and music folders:*
```
Pictures
Music
``` 

## 3.3 Close the nano editor

Press *"ctrl+x"* to exit.<br>
Press *"y"* to save changes.<br>
Press *"enter"* to accept the existing filename.

# 4. Show your configuration

```
onedrive --display-config
```

# 5. Test your configuration

This does not download any files. If the output looks right but there are a lot of files being checked press *"ctrl+c"* to exit early, otherwise wait till it finishes. 
```
onedrive --synchronize --verbose --dry-run
```

# 6. Sync your changes

```
onedrive --synchronize --resync
```

# 7. Start onedrive on boot

OneDrive service running as a non-root user via systemd. This service will be launched at startup.<br>
*Note: replace "username" with your username in the below command. Example: systemctl enable onedrive@nathanael.service*

```
systemctl enable onedrive@username.service
```

# 8. Start onedrive service now

The command above only starts the onedrive service on startup. You could reboot your system or type the following.<br>
*Note: replace "username" with your username in the below command. Example: systemctl start onedrive@nathanael.service*

```
systemctl start onedrive@username.service
```

# 9. (OPTIONAL) Check that the service is running correctly

```
systemctl status onedrive@username.service
```

# 10. Check out your work

Have a look at your onedrive files in Ubuntu and wonder why Microsoft are too lazy to release an official client themselves. At least we have an amazing open source community dedicated to helping each other.

*Remember to go give your praise on github to the folks that released this updated version of onedrive client at: [github.com/abraunegg/onedrive](https://github.com/abraunegg/onedrive)*

