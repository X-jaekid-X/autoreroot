Auto Reroot for LineageOS Updates

This script will cause inotify to auto patch your downloaded OTA's using Magisk to keep root.  Older Android devices do not need this script.

1) Install Termux from F-Droid if not already installed.
2) Install inotify for Termux by running the following command:

 pkg install inotify-tools

3) Save the Auto Reroot script into the following Termux folder:

 ~/scripts/auto_reroot_inotify.sh

4) Run the following commands:

 chmod +x ~/scripts/auto_reroot_inotify.sh

 nohup ~/scripts/auto_reroot_inotify.sh &

 cp ~/scripts/auto_reroot_inotify.sh ~/.termux/boot/

5) The script will now start on boot and monitor your /data/lineageos_updates folder for an OTA and auto patch it with Magisk to retain root when an OTA is detected.  Do not reboot your device when prompted by LineageOS, you only need to download the OTA when using this script.
