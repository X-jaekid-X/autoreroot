# Auto Reroot for LineageOS Updates

This script uses inotify to automatically patch downloaded OTAs with Magisk to preserve root access. **Note: Older Android devices do not need this script.**

---

## Prerequisites

1. Install Termux from F-Droid (https://f-droid.org/packages/com.termux/)

2. Install Termux:Boot from F-Droid (https://f-droid.org/packages/com.termux.boot/) (required for auto-start on boot)

3. Install required packages:

pkg install tsu inotify-tools termux-api

4. Grant Termux storage permissions:

termux-setup-storage

---

## Installation

Option 1: One-Line Installation

Place `auto_reroot_inotify.sh` in your Downloads folder, then run:

pkill -f auto_reroot_inotify && mkdir -p ~/.termux/boot && cp -f ~/storage/downloads/auto_reroot_inotify.sh ~/.termux/boot/ && chmod +x ~/.termux/boot/auto_reroot_inotify.sh && setsid ~/.termux/boot/auto_reroot_inotify.sh >/dev/null 2>&1 &

### Option 2: Manual Installation

1. Create the scripts directory:

mkdir -p ~/scripts

2. Save the script to:

~/scripts/auto_reroot_inotify.sh

3. Make the script executable:

chmod +x ~/scripts/auto_reroot_inotify.sh

4. Start the script manually:

nohup ~/scripts/auto_reroot_inotify.sh > /dev/null 2>&1 &

5. Enable auto-start on boot:

mkdir -p ~/.termux/boot

cp ~/scripts/auto_reroot_inotify.sh ~/.termux/boot/

---

## Usage

Once installed, the script will:
- Monitor `/data/lineageos_updates` for new OTA files
- Automatically patch OTAs with Magisk when detected
- Preserve root access after updates

Important: When LineageOS prompts you to reboot after downloading an OTA, **do NOT reboot yet**. Wait for the script to patch the OTA first (you'll see a toast notification if Termux:API is installed), then the device will reboot automatically.

---

## Verification

To check if the script is running:

ps aux | grep auto_reroot

To view the log:

cat ~/auto_reroot.log

---

## Troubleshooting

- Script not starting on boot? Make sure Termux:Boot is installed and has been opened at least once
- Permission errors? Ensure `tsu` is installed and working: `pkg install tsu`
- No notifications? Install Termux:API for toast notifications: `pkg install termux-api`

---

## Notes

- The script requires root access via `tsu`
- Your device must support A/B seamless updates
- Magisk must be installed and functioning properly
