<div align="center">
<img width="256" alt="Asrock Z690 PG Riptide Hackintosh Logo" src="https://github.com/user-attachments/assets/362c57fa-40b6-4a5a-ab26-eec0cf93222b" />

# Asrock-Z690-PG-Riptide-hackintosh

</div>
<div align="center">
<img width="800" height="666" alt="asrock-z690-pg-riptide-guvn5_7525caa26f0b4f3cae5078fcfd87f556_master" src="https://github.com/user-attachments/assets/3180efe9-8293-43ed-bb00-96a3af9ed510" />
</div>

## 👉 Disclaimer
This repository is intended for personal use only and may be unstable on hardware configurations other than the one listed below. It contains fully configured OpenCore and Clover EFI folders. I assume no liability for the use of this repository. Use it at your own risk!

> ⚠️ **Attention!** If you have an RX 5700 (XT) graphics card, you must use the **Framebuffer (ATI,Adder)** to avoid WindowServer crashes!

## 🛠️ Hardware Configuration
* **CPU:** Intel i7-12700KF (Alder Lake)
* **MB:** Asrock Z690 PG Riptide — [`More info`](https://pg.asrock.com/mb/Intel/Z690%20PG%20Riptide/index.ru.asp#Overview)
* **RAM:** 64GB (2x32GB) DDR4 3200MHz Crucial Technology      
* **GPU:** Radeon Sapphire Nitro+ RX 5700 XT 8G GDDR6 SE — [`More info`](https://www.sapphiretech.com/ru-ru/consumer/nitro-radeon-rx-5700-xt-se-8g-gddr6)
* **SSD 1:** WD_BLACK SN850X 1000GB NVMe M.2 (PCIe 4.0) — macOS Tahoe 26.6.2 (25G83)
* **SSD 2:** WD_BLACK SN850X 1000GB NVMe M.2 (PCIe 4.0) — Windows 11 (25H2)
* **SSD 3:** Samsung 860 EVO 500GB (SATA-6 AHCI) — macOS Ventura 13.7.8 (22H730)
* **Wi-Fi / BT:** BCM94360 FENVI FV-HB1200 AC PCI-E adapter

---

## ℹ️ macOS Tahoe 26.xx Notes
**No root patches are required anymore for macOS 26.xx.**

* **SimpleBCM**: Restores Broadcom Wi-Fi support on macOS Tahoe.
* **SimpleHDA**: Restores native AppleHDA on macOS Tahoe.
* **AppleVTD (IOMMU)**: Fully enabled (`DisableIoMapper = false` and `DisableIoMapperMapping = false`).
  * Modified **BroadcomVTD.kext** (with D11 rev 42/43 support for BCM94360 `14e4:43a0`).
  * Uses custom `SSDT-DMAR.aml` (Host Address Width = 39 / `0x27`).
  * [BroadcomVTD-Tahoe](https://github.com/YBronst/BroadcomVTD-Tahoe/releases)
 
> 📌 **Note:** For macOS Sonoma and Sequoia only, [`OCLP patch 2.4.1 or newer`](https://github.com/dortania/OpenCore-Legacy-Patcher) is still required.

---

## ✅ Functional Features
- Full graphics acceleration (RX 5700 XT)
- AirDrop, Handoff, and Universal Clipboard
- Wi-Fi + Bluetooth (Broadcom FENVI FV-HB1200)
- App Store, iMessage, and FaceTime
- Native Ethernet functionality

## ❌ Known Issues & Troubleshooting

### ❗️ Warning
* **FileVault 2** does not work in Sonoma and Sequoia when OCLP patches are applied!

### 📝 Notes
* All macOS features work flawlessly, including DRM playback, sleep/wake (S3), and FileVault 2 (only on macOS Ventura 13.x.x versions).
* Clover has a known issue with updates under T2 Mac models.
* **Before use:** You need to generate your own MLB and SMBIOS data using a Python script that utilizes acidanthera's `macserial` tool, and then add them to your `config.plist`. [`More info`](https://github.com/corpnewt/GenSMBIOS)

---

## 🛠️ Installation & Maintenance

### ⚙️ BIOS Settings & Updates
* **Current Update:** [`21.01 2025/10/30 10.80MB`](https://pg.asrock.com/mb/Intel/Z690%20PG%20Riptide/index.ru.asp#BIOS)
  1. Optimized system compatibility.
  2. Enhanced platform security with *Control IOMMU Pre-boot Behavior*, *VT-d*, and *IOMMU* options.
* **BIOS Setup:** Load Optimized Defaults.

### 🗑️ Uninstalling Patches & Apps
#### I. Reverting Root Patches
Open the OCLP application, navigate to the **Post Install Root Patch** menu, and select **Revert Root Patches**. 
* **Supported on Monterey and later.**
* *Note: Big Sur does not support snapshot reversion and requires a full system reinstallation.*
* *Reinstallation can be performed without data loss if the macOS installer version used is the same or newer.*

#### II. Uninstalling the Application
To completely remove the OCLP application (including `LaunchAgent` and `PrivilegedHelperTool`), download the official uninstaller package from the [`releases page`](https://github.com/dortania/OpenCore-Legacy-Patcher/releases).

---

## 💾 Bootloader Downloads
All bootable EFI folder archives have been updated to the latest stable releases:
* [`⚛️ OpenCore Loader 1.0.8`](https://github.com/acidanthera/OpenCorePkg/releases/download/1.0.8/OpenCore-1.0.8-RELEASE.zip)
* [`🍀 Clover Release-5175`](https://github.com/YBronst/CloverBootloader/releases)
