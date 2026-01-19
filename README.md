# Acer Predator Hackintosh (Intel 9th Gen) - OpenCore Support 
EFI will work with MAC os Tahoe

This repository contains the EFI folder for the **Acer Predator** with an Intel 9th Gen processor (i7-9750H).

## 💻 System Specifications
* **CPU:** Intel® Core™ i7-9750H (Coffee Lake)
* **iGPU:** Intel® UHD Graphics 630
* **dGPU:** NVIDIA GTX 1660 Ti (**Disabled**)
* **Bootloader:** OpenCore

---

## 🛠 1. Prepare the macOS Installer (macrecovery)

Since this repo only provides the EFI, you need to download the macOS recovery files using the OpenCore `macrecovery` tool.

1.  Open your terminal/command prompt and navigate to your `EFI/OC/Utilities/macrecovery/` folder.
2.  Run the following command to download **macOS Sonoma** (or your preferred version):
    * **Windows:** `python3 macrecovery.py -b macosx14 -m 00000000000000000 download`
    * **macOS/Linux:** `./macrecovery.py -b macosx14 -m 00000000000000000 download`
3.  Once finished, you will see two files: `BaseSystem.dmg` and `BaseSystem.chunklist`.
4.  Create a folder named `com.apple.recovery.boot` on the root of your USB drive and move those two files into it.

---

## 🔑 2. SMBIOS Setup (GenSMBIOS)

You must generate unique serial numbers to use Apple Services.

1.  Download and run [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2.  Select Option `2` to select your `config.plist`.
3.  Select Option `3` and enter `MacBookPro15,1`.
4.  Verify the serial on [Apple’s Check Coverage](https://checkcoverage.apple.com/) page; it should say "Invalid Serial" (this means it's safe to use).

---

## 🚀 3. Installation Steps

1.  **USB Layout:** Your USB drive should look like this:
    * `USB/EFI/` (Contains the BOOT and OC folders from this repo)
    * `USB/com.apple.recovery.boot/` (Contains BaseSystem files)
2.  **BIOS Settings:**
    * **SATA Mode:** AHCI
    * **Secure Boot:** Disabled
    * **VT-d:** Disabled
3.  **Boot:** Restart your laptop, tap `F12` to enter the Boot Menu, and select your USB.
4.  **Install:** Select "Install macOS" from the OpenCore picker. Use **Disk Utility** to format your target drive as `APFS` with a `GUID Partition Map`.

---

## 🛠 4. Post-Install (Wi-Fi & Bluetooth)

Once you reach the desktop, your Wi-Fi and Bluetooth might not be active yet if they require root patches (common for Intel or Broadcom cards in newer macOS versions).

1.  **Download OpenCore Legacy Patcher (OCLP):** Download the latest GUI version.
2.  **Apply Root Patches:**
    * Open OCLP and click on **"Post-Install Root Patch"**.
    * If your hardware is detected, click **"Start Root Patching"**.
3.  **Reboot:** After the patching process finishes, reboot your system. Your Wi-Fi and Bluetooth should now be functional.



---

## ✅ Current Status
* **Working:** UHD 630 Graphics, Audio, Trackpad (I2C), Sleep/Wake.
* **Not Working:** NVIDIA GTX 1660 Ti (Disabled for stability).

---
**Disclaimer:** Use at your own risk. 
