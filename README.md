# macOS OpenCore Hackintosh EFI

This repository contains the functional OpenCore EFI configuration required to run **macOS** on non-Apple hardware.

> [!WARNING]
> Do not clone this repository and use it blindly. Hackintosh configurations are highly hardware-specific. Use this as a reference guide alongside the official [Dortania OpenCore Install Guide](https://github.io).

---

## 💻 Hardware Specifications

| Component | Specification |
| :--- | :--- |
| **CPU** | Intel Core i7-10700K (Comet Lake) / AMD Ryzen 5 3600 |
| **Motherboard** | ASUS ROG STRIX Z490-E GAMING |
| **GPU** | AMD Radeon RX 580 8GB / Intel UHD Graphics 630 |
| **RAM** | 32GB Corsair Vengeance DDR4 3200MHz |
| **Storage** | Samsung 970 EVO Plus NVMe M.2 SSD 1TB |
| **Audio** | Realtek ALC1220 |
| **Ethernet** | Intel I225-V 2.5Gb Ethernet |
| **Wi-Fi/BT** | Broadcom BCM94360NG |
| **OpenCore Version** | v1.0.x |

---

## 🛠️ Status & Features

### 🟢 Working
* [x] **Graphics Acceleration** (QE/CI) via WhateverGreen
* [x] **Audio** (Internal Speakers, Microphone, Headphones Jack) via AppleALC
* [x] **Wi-Fi & Bluetooth** (AirDrop, Continuity, Handoff)
* [x] **All USB Ports** (Custom mapped via USBMap.kext)
* [x] **Sleep / Wake**
* [x] **iMessage, FaceTime, iCloud, and App Store**
* [x] **FileVault** and **NVRAM** encryption

### 🔴 Not Working / Bugs
* [ ] DRM video playback in Safari (Netflix/Apple TV+) — *Fixable via secondary GPU or booting layout fixes.*

---

## 🗂️ EFI Folder Structure Reference

```text
EFI/
├── BOOT/
│   └── BOOTx64.efi
└── OC/
    ├── ACPI/
    ├── Drivers/
    ├── Kexts/
    └── config.plist
```

### 🧩 Included Kexts
* [Lilu.kext](https://github.com) — Arbitrary kext patcher (Required).
* [VirtualSMC.kext](https://github.com) — Advanced SMC emulation (Required).
* [WhateverGreen.kext](https://github.com) — Graphics patches (Required).
* [AppleALC.kext](https://github.com) — Native macOS HD audio patching.

---

## 🚀 Installation & Setup

### 1. BIOS Settings
Ensure your motherboard BIOS is configured correctly before booting:

**Disable:**
* Fast Boot
* Secure Boot
* Serial Port/COM Port
* CSM (Compatibility Support Module)
* Intel Platform Trust Technology (PTT) *[Optional, required for Win11 but can conflict with older macOS]*

**Enable:**
* VT-x / VT-d
* Above 4G Decoding
* Hyper-Threading
* EHCI/XHCI Hand-off
* SATA Mode: AHCI

### 2. Generate SMBIOS
Before using the `config.plist`, you **MUST** generate your own unique serial numbers using [GenSMBIOS](https://github.com):
1. Select your appropriate SMBIOS profile (e.g., `iMac20,1`).
2. Populate the following keys inside `PlatformInfo -> Generic`:
   * `SystemSerialNumber`
   * `MLB`
   * `SystemUUID`
   * `ROM`

---

## 📄 Credits & Acknowledgments
* [Acidanthera](https://github.com) for developing OpenCore, Lilu, VirtualSMC, and most essential kexts.
* [Dortania](https://github.io) for the ultimate OpenCore installation guide.
