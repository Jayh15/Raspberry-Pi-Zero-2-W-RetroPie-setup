# Raspberry-Pi-Zero-2-W-RetroPie-setup
ROM (All ROMs used are from homebrew/public domain or legally owned cartridges.) transfer methods, troubleshooting, boot fixes, and more.

# 🎮 RetroPie Setup on Raspberry Pi Zero 2 W
*By Jaylen Howe*  
A full documentation of my RetroPie installation, ROM setup, controller configuration, and troubleshooting on a Raspberry Pi Zero 2 W.

---

## 🔧 Hardware Used

- Raspberry Pi Zero 2 W
- 16GB microSD card (SanDisk)
- USB OTG adapter
- Wired USB game controller
- HDMI to micro-HDMI cable
- Power: 5V 2.5A micro-USB charger
- Optional: USB flash drive (for offline ROM transfer)

---

## 🛠️ Installation Steps

### 1. Download the Right Image

From: [retropie.org.uk/download](https://retropie.org.uk/download/)  
**Image Used**: `RetroPie 4.8.2 for Pi 1 / Zero / Zero 2 W`

### 2. Flash the Image to SD Card

**Tool Used**: Raspberry Pi Imager  
- Selected OS: Custom (RetroPie .img.gz)
- Enabled SSH
- Entered Wi-Fi details (SSID + password)
- Set username/password
- Wrote image to SD card

🛠️ Got error `-69760 Unable to write to the last block of the device`  
✅ Fixed by formatting the SD card with Disk Utility (Mac) using `MS-DOS (FAT)` + `MBR` scheme.

---

## 🚀 First Boot Setup

- Inserted microSD into Pi
- Connected HDMI, controller, and power
- First boot resized filesystem, auto-rebooted into EmulationStation

🛠️ **No LED/no power issue**  
✅ Solved by:
- Using correct power port (labeled "PWR")
- Reflashing image
- Using verified 5V/2A power adapter
- Confirming SD card was functional

---

## 🎮 Controller Configuration

- On first boot, held a button to start controller mapping
- Skipped unused buttons by holding any button
- Can reconfigure anytime via:
Start → Configure Input


---

## 📂 ROM Transfer Methods

### 📡 Method A – Wi-Fi (when working)

1. Connected Pi to Wi-Fi via `Start → Wi-Fi`
2. On Windows PC:  
 `\\retropie` or `\\<pi-ip>`  
 Opened:
roms/nes/
roms/snes/
roms/gb/

3. Dropped legal ROMs into folders  
4. Restarted EmulationStation:  
`Start → Quit → Restart EmulationStation`

### 🔌 Method B – USB Drive (offline, no Wi-Fi)

1. Formatted USB as FAT32/exFAT
2. Created folder: `retropie`
3. Plugged USB into Pi (let it initialize)
4. Removed → opened on PC → dropped ROMs into:
retropie/roms/<system>/

5. Plugged USB back into Pi → waited 1–2 mins
6. Restarted EmulationStation to see games

**🧠 Tip**: You can remove the USB drive after ROMs transfer. They’re copied to the SD card.

---

## ✅ Confirming ROM Transfer

- Watch Pi’s green LED blink during transfer
- Wait 2–3 mins if unsure
- Restart EmulationStation to see new systems appear
- Or verify with terminal:
```bash
ls ~/RetroPie/roms/nes

🧪 Troubleshooting Summary
Problem	Fix
No power / no LED	Used correct port + good cable + reflashed SD
Flash errors	Used "Erase" in Imager or Disk Utility (FAT + MBR)
ROMs not showing	Waited longer, restarted EmulationStation
USB + controller issue	Transferred ROMs first, then unplugged USB to free port
Wi-Fi didn’t appear	Manually added network to /etc/wpa_supplicant/wpa_supplicant.conf
Reconfigure controller	Start → Configure Input
🔧 Future Plans

    Add USB OTG hub for dual controller/USB support

    Install themes and launch splash screen

    Optional: Use kiwix or flask on same SD to run offline tools

📎 License

All ROMs used are from homebrew/public domain or legally owned cartridges.
