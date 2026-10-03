# macOS OpenCore Hackintosh EFI 🍏🍏🍏

## Voilá, now you can use macOS on non Apple hardware! So, instead of buy an 700$ bucks Mac, just follow this steps to install it on your old PC.

<img width="2082" height="1152" alt="image" src="https://github.com/user-attachments/assets/9c4974b7-161c-4434-a4a4-18fb6790eba6" />
(_Credits: the screenshots are'nt mine_)
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

OBS.: You can see an screen like this, but dont worry it's normal.

<img width="715" height="195" alt="image" src="https://github.com/user-attachments/assets/33f44d5b-c90f-4720-8142-2fea2fc4ac17" />

### 🧩 Included Kexts
* [Lilu.kext](https://github.com) — Arbitrary kext patcher (Required).
* [VirtualSMC.kext](https://github.com) — Advanced SMC emulation (Required).
* [WhateverGreen.kext](https://github.com) — Graphics patches (Required).
* [AppleALC.kext](https://github.com) — Native macOS HD audio patching.

---

## 📄 Credits & Acknowledgments
* [Acidanthera](https://github.com) for developing OpenCore, Lilu, VirtualSMC, and most essential kexts.
* [Dortania](https://github.io) for the ultimate OpenCore installation guide.

<img width="1380" height="752" alt="image" src="https://github.com/user-attachments/assets/a4bbc31b-907a-4620-a716-aeadd4df9beb" />

