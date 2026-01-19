# Acer Predator Hackintosh (Intel 9th Gen) - OpenCore

This repository contains the EFI folder for the **Acer Predator** with an Intel 9th Gen processor.

## 💻 System Specifications
* **CPU:** Intel® Core™ i7-9750H (Coffee Lake)
* **iGPU:** Intel® UHD Graphics 630
* **dGPU:** NVIDIA GTX 1660 Ti (**Disabled**)
* **Bootloader:** OpenCore

---

## 🛠 SMBIOS Setup (Required)

To ensure iMessage, iCloud, and Find My work correctly, you must generate your own unique serial numbers. We will use **GenSMBIOS** to inject these directly into your `config.plist`.

### Step-by-Step Instructions:

1.  **Download GenSMBIOS:**
    * Download the [GenSMBIOS-master](https://github.com/corpnewt/GenSMBIOS) repository and extract the ZIP.
2.  **Run the Script:**
    * **Windows:** Double-click `GenSMBIOS.bat`.
    * **macOS:** Right-click `GenSMBIOS.command` and select *Open*.
3.  **Install/Update MacSerial:**
    * Type `1` and press **Enter** to download the latest version of MacSerial.
4.  **Select your Config.plist:**
    * Type `2` and press **Enter**.
    * Locate your `EFI/OC/config.plist` file and drag it into the terminal window, then press **Enter**.
5.  **Generate SMBIOS Data:**
    * Type `3` and press **Enter**.
    * Type `MacBookPro15,1` and press **Enter**. (This matches your i7-9750H architecture).
    * The script will automatically update your `config.plist` with a new Serial Number, Board Serial (MLB), and SmUUID.
6.  **Verify the Serial:**
    * Copy your new serial number and check it on the [Apple Check Coverage](https://checkcoverage.apple.com/) page. 
    * **Goal:** You want to see "Invalid Serial Number" or "Purchase Date not Validated." If it shows an active warranty or a real Mac, run GenSMBIOS again to generate a different one.

---

## ⚙️ BIOS Settings
* **SATA Mode:** AHCI
* **Secure Boot:** Disabled
* **Fast Boot:** Disabled
* **VT-d:** Disabled

## ✅ Status
* **Working:** UHD 630, Audio, Trackpad (I2C), Wi-Fi, Sleep.
* **Disabled:** GTX 1660 Ti (via `boot-args`).

---
**Disclaimer:** Use at your own risk. This project is for educational purposes.
