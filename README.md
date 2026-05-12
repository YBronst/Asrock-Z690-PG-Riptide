<div align="center">
<img width="256" alt="Снимок экрана 2026-03-29 в 01 04 48" src="https://github.com/user-attachments/assets/362c57fa-40b6-4a5a-ab26-eec0cf93222b" />

# Asrock-Z690-PG-Riptide-hackintosh
</div>

# 👉 Disclaimer:
This repository is intended for personal use only and may be unstable on hardware configurations other than those listed below.
It contains fully configured EFI OpenCore and Clover Folders.
I assume no liability for the use of this repository. Use it at your own risk!

- ⚠️ Attention! If you have RX5700 (XT) graphics card, you have to use the Framebuffer (ATI,Adder) to avoid WindowServer crashes!

## 🛠️ Hardware configuration:
* CPU: i7-12700kf AlderLake
* MB: Asrock Z690 PG Riptide [`More info`](https://pg.asrock.com/mb/Intel/Z690%20PG%20Riptide/index.ru.asp#Overview). 
* RAM: 64GB (2x32GB) DDR4 3200 Crucial Technology      
* GPU: Radeon Sapphire Nitro+ RX5700XT 8G GDDR6 SE [`More info`](https://www.sapphiretech.com/ru-ru/consumer/nitro-radeon-rx-5700-xt-se-8g-gddr6).
* SSD: WD_BLACK SN850X 1000GB NVME M2 (PCI-e 4.0) - macOS Tahoe macOS 26.5 (25F71).
* SSD: WD_BLACK SN850X 1000GB NVME M2 (PCI-e 4.0) - Windows 11 (25H2).
* SSD: Samsung 860 EVO 500GB (SATA-6 AHCI) - macOS Ventura 13.7.8 (22H730).
* WIFI / BT: BCM94360 FENVI FV-HB1200 AC PCI-E adapter.
* For full functionality FENVI FV-HB1200 on Mac OS Sonoma and Sequoia, required:
* [`OCLP patch 2.4.1 or newer`](https://github.com/dortania/OpenCore-Legacy-Patcher).
* For full functionality FENVI FV-HB1200 on macOS Tahoe, required:
* [`OCLP-Plus 3.2.2 (Tahoe Patch Set)`](https://github.com/YBronst/OCLP-Plus/releases)
  
## ✅ Functional Features

- Full graphics acceleration (RX 5700 XT)
- AirDrop, Handoff, Universal Clipboard
- Wi-Fi + Bluetooth (Broadcom FENVI FV-HB1200)
- App Store, iMessage, FaceTime
- Ethernet working

### Application issues:
* System version mismatch error when root patching
* Use an experimental [`"PurgePendingUpdate" tool`](https://github.com/YBronst/Asrock-Z690-PG-Reptide/blob/main/purgePendingUpdate.zip) 

### Uninstall:

* I. Reverting root patches:

* Open the OCLP application and go into the Post Install Root Patch menu, choose Revert Root Patches. 
*  **Supported on Monterey and later**.
*  **Big Sur does not support snapshot reversion and requires a reinstall.**
*  **Reinstall can be done without a wipe if the macOS installer version used is the same or newer.**

* II. Uninstalling the application:

* To uninstall the OCLP application including LaunchAgent and PrivilegedHelperTool, download the uninstaller package from [`the releases page`](https://github.com/dortania/OpenCore-Legacy-Patcher/releases)

### Update BIOS: [`21.01 2025/10/30 10.80MB`](https://pg.asrock.com/mb/Intel/Z690%20PG%20Riptide/index.ru.asp#BIOS)

* 1. Optimized system compatibility.
* 2. Enhance platform security with Control IOMMU Pre-boot Behavior, VT-d, and the IOMMU option.

### BIOS setup: 

* Default

### All archives of bootable EFI folders have already been updated to the latest versions of OpenCore and Clover but you can download them:
* [`⚛️OpenCore loader 1.0.7`](https://github.com/dortania/build-repo/releases/download/OpenCorePkg-507907a/OpenCore-1.0.7-RELEASE.zip) 
* [`🍀Clover Release-5172`](https://github.com/YBronst/CloverBootloader/releases)


## ❗️Warning:
* FileVault2 not working in Sonoma/Sequoia and Tahoe with the OCLP patch!
 
## 📝 Notes:
* All macOS features are working including DRM playback and sleep/wake S3 and FileVault2 in macOS Ventura 13.x.x versions.
* Clover has issue with update under T2 mac models
* Before use, you need to generate your own MLB and SMBIOS data using a Py script that uses acidanthera's macserial to generate SMBIOS and optionally saves them to a plist [`More info`](https://github.com/corpnewt/GenSMBIOS)
