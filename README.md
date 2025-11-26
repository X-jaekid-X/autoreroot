Auto Reroot for LineageOS Updates

This script will cause inotify to auto patch your downloaded OTA's using Magisk to keep root.  Older Android devices do not need this script.


Installation Guide

1. Install Termux from F-Droid.

2. Install Termux:Boot from F-Droid (required for auto-start on boot).

3. Open Termux and run:

 pkg install inotify-tools
 

-- ONE LINE INSTALLATION --

Make sure that auto_reroot_inotify.sh is in your Downloads folder then run this entire command:

mkdir -p ~/.termux/boot && cp -f ~/storage/downloads/auto_reroot_inotify.sh ~/.termux/boot/ && chmod +x ~/.termux/boot/auto_reroot_inotify.sh && nohup su -c "/data/data/com.termux/files/usr/bin/sh ~/.termux/boot/auto_reroot_inotify.sh" &


-- OR --

Install manually

4. Save the Script

Save your auto reroot script to:

 ~/scripts/auto_reroot_inotify.sh

5. Make the Script Executable

Run this command:

 chmod +x ~/scripts/auto_reroot_inotify.sh

6. Start the Script Manually

Run this command:

 nohup ~/scripts/auto_reroot_inotify.sh &

7. Enable Auto-Start on Boot

Run these commands:

 mkdir -p ~/.termux/boot

 cp ~/scripts/auto_reroot_inotify.sh ~/.termux/boot/

8. The script will now start on boot and monitor your /data/lineageos_updates folder for an OTA and auto patch it with Magisk to retain root when an OTA is detected.  Do not reboot your device when prompted by LineageOS, you only need to download the OTA when using this script.
