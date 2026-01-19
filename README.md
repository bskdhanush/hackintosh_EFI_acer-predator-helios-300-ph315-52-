# Acer Predator Hackintosh (Intel 9th Gen) - OpenCore

This repository provides an OpenCore EFI folder specifically tuned for the **Acer Predator** with an Intel 9th Gen processor. This configuration is confirmed working with #**macOS 26 Tahoe**, the final macOS release with native Intel support.

## 💻 System Specifications
* **CPU:** Intel® Core™ i7-9750H (Coffee Lake)
* **iGPU:** Intel® UHD Graphics 630
* **dGPU:** NVIDIA GTX 1660 Ti (**Disabled** - Not supported)
* **Target OS:** macOS 26 Tahoe (and earlier)

---

## 🛠 1. Download macOS (macrecovery)

To get the official macOS Tahoe recovery files, use the `macrecovery` script included in the OpenCore package.

1.  Navigate to your `EFI/OC/Utilities/macrecovery/` folder in a terminal.
2.  Run the download command for **macOS Tahoe (macosx26)**:
    * **Windows:** `python3 macrecovery.py -b macosx26 -m 00000000000000000 download`
    * **macOS/Linux:** `./macrecovery.py -b macosx26 -m 00000000000000000 download`
3.  Create a folder on your USB root called `com.apple.recovery.boot`.
4.  Move the resulting `BaseSystem.dmg` and `BaseSystem.chunklist` into that folder.

---

## 🔑 2. Generate Serial Numbers (GenSMBIOS)

Do not use the EFI without generating a unique serial first, or your Apple ID could be flagged.

1.  Open **GenSMBIOS-master**.
2.  Select Option `2` and point it to this repo's `EFI/OC/config.plist`.
3.  Select Option `3` and enter `MacBookPro15,1`.
4.  Check your new serial on [Apple's Coverage Site](https://checkcoverage.apple.com/). If it says "Invalid Serial," you are good to go.

---

## 🚀 3. Installation Steps

1.  **BIOS Config:**
    * **SATA Mode:** AHCI (Required)
    * **Secure Boot:** Disabled
    * **VT-d:** Disabled
2.  **Booting:** Plug in the USB and boot from it. Choose "Install macOS Tahoe" in the OpenCore menu.
3.  **Drive Prep:** In Disk Utility, format your internal SSD as **APFS** with **GUID Partition Map**.
4.  **Install:** Follow the prompts. The system will reboot 3–4 times.

---

## 🛠 4. Post-Install (Wi-Fi & Bluetooth)

In macOS Tahoe, certain Wi-Fi and Bluetooth cards require root patching to function.

1.  Download the latest [OpenCore Legacy Patcher (OCLP)](https://github.com/dortania/OpenCore-Legacy-Patcher/releases).
2.  Open the app and select **"Post-Install Root Patch"**.
3.  Click **"Start Root Patching"**. This will re-inject the legacy drivers for your Intel/Killer wireless card.
4.  Reboot your laptop.

---

## ✅ Current Status
* **Working:** Liquid Glass UI, Spotlight, Audio, Trackpad (I2C), Wi-Fi, Sleep/Wake.
* **Disabled:** GTX 1660 Ti (NVIDIA Turing is not supported in macOS).

---
**Disclaimer:** This is for educational use.
