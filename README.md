[![Home](https://img.shields.io/badge/🏠_README-blue?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI)
[![Hardware](https://img.shields.io/badge/🛠️_HARDWARE-brightgreen?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/HARDWARE.md)
[![Issues](https://img.shields.io/badge/⚠️_Issues-red?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/KNOWN_ISSUES.md)
[![Releases](https://img.shields.io/badge/🚀_Releases-Download-blueviolet?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/releases)

 &nbsp;

# Tahoe 470s | T470s macOS Tahoe EFI

<img width="1920" height="1080" alt="Capture d’écran 2026-08-23 à 12 16 49" src="https://github.com/user-attachments/assets/69922a4a-6d12-43ee-a153-1aa8c3ba522b"/>

## Table of Contents

1. [Introduction](#-introduction)
2. [My Setup](#-my-setup)
3. [Another User's Setup](#-another-users-setup)
4. [Personal Note](#-personal-note)
5. [General Info](#-general-info)
6. [What Works](#-what-works)
7. [What Doesn't Work](#-what-doesnt-work)
8. [Setup Required](#-setup-required)
9. [Post-Install](#-post-install)
10. [Changelog](#-Changelog)
11. [Credits](#-credits)

---

## Introduction

This is a **sanitized version** of the EFI I use daily on my ThinkPad T470s hackintosh. I couldn't find a proper guide for this exact model so I made this EFI and shared it so this can hopefully help someone who was in my position.

> **Tip:** Hold Esc or Alt at boot to show the OpenCore boot picker.

### My experience so far

- **Full metal GPU acceleration** — Smooth animations and usability just the occasional lag spike and 100% cpu usage if loading assets for the first time.
- I use m.SATA SSD and it turns out it is more responsive than my uncle's 2019 16 inch macbook pro though objective performance is obviously far worse.
- **Apple Video Toolbox works** — video editing in Kdenlive and CapCut worked out of the box.
- **HandBrake transcoding** — consistently over 60 fps *on battery*, compressing 10 GB footage down to \~500 MB in a few minutes.
- **Roblox runs better** than on Windows or Linux.
- **Battery life:** 2 h gaming · 4–5 h web browsing · 6–7 h coding &amp; document editing.
- **Bluetooth works perfectly.**
- **Wi-Fi is nearly fully functional** (missing a thing or two — see below).
- **I frequently have 30+ tabs open** the system remains smooth thanks to the 20GB of ram though occasional frame drops can be seen with launchpad.
- **Apps open in a bounce or two** settings, terminal and most apps open in either a bounce  or two max on cold launch.

### My workflow

- Coding in **C** and **Python** for classwork.
- **Python** web backends with Flask
- **Pulsar** as my main IDE (JetBrains IDE also run really well as in better than windows or linux)
- Compiling **EclipsedOS** (somehow still working on this despite this project and school)
- Light video editing using kdenlive and compressing footage with HandBrake + Intel QSV (Apple VideoToolbox)
- I Also do take notes in class allowing me to have 5-7 hour battery life usually (intensive tasks are obviously going to kill the batteries)
- Running VMs for code compilation and testing for memory leaks
---

## My Setup


| Spec          | Value                            |
| ------------- | -------------------------------- |
| EFI version   | v0.97                            |
| Model         | Lenovo ThinkPad T470s            |
| CPU           | Intel Core i7-6600U              |
| RAM           | 4 + 16 GB                        |
| GPU           | Intel HD Graphics 520            |
| Disk          | intenso 1TB m.sata SSD           |
| start version | **26.3 Tahoe**                   |
| macOS version | **26.7 Tahoe**                   |
| SMBIOS        | MacBookPro13,1                   |


## Personal Benchmarks

| Test          | Result                            |
| ------------- | ----------------------------------|
| Youtube Safari 1080p60fps | 19 dropped frames out of 19655 Most dropped in the first second and only one dropped near the end of the 1 minute clip. CPU remained at 50-55°C |
|Handbrake compression of 1080p30 from .mov to .mp4 AppleVideoToolbox | 60fps average varies from 45 fps up to 90 fps vs 30 fps average 15 min 47 max on intel QSV Handbrake windows 10 and Ubuntu 22.04|

**Recorded temps:** 35 °C idle (1 W CPU) · 40–50 °C normal use (2–5 W CPU) · 65–72 °C gaming/rendering (12–20 W CPU) <br>
**Recorded battery draw:** 6W idle · 8-11W normal use · 17-29W gaming/rendering<br>

> No known issues outside of no AirDrop being buggy.
> Virtually all issues have been resolved.

---

## ℹ️ General Info

- **System SMBIOS:** `MacBookPro13,1`
- **Supported:** macOS Tahoe (older versions will probably work, but untested)

Known update issues:

> SimpleHDA + AppleALC has replaced both HDAUniversal and VoodooHDA.kext solving all known audio issues.

---

## What Works

**Hardware &amp; features**

- ✅ Bluetooth
- ✅ Keyboard (function keys included)
- ✅ Trackpad (all gestures work)
- ✅ Trackpoint
- ✅ Function keys
- ✅ Graphics acceleration (full Metal)
- ✅ Wi-Fi
- ✅ Audio (fully functional with `HDAUniversal.kext`)
- ✅ HDMI (audio + display)
- ✅ USB-C
- ✅ Seamless booting
- ✅ Dual battery (fixed percentage reporting, since 18 Jul 2026)
- ✅ CPU power management, C-states and VF curve (0.9 W up to 20 W)
- ✅ Native OTA updates
- ✅ Apple ID and FaceTime with App Store and other Apple ID adjacent features
- ✅ WPA-Enterprise Wi-Fi
- ✅ SD Card reader


## ❌ What Doesn't Work

- ❌ AirDrop (Partially broken still WIP)

---

## 🔧 Setup Required

1. **Generate your own serial number** — this EFI ships without mine (use [corpnewt's GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)).
2. Copy the EFI folder to your EFI partition after install.

---

## 🚀 Post-Install (As of v0.97)

> **Is this set-and-forget?** Yes, for the most part! Once EFI is copied to the disk, you can forget about it - any bugs that arise will be fixed by future versions.

> **Do I need post-install root patches?** No patches at all everything listed as working works out of the box.

### 📋 Checklist

- [ ] Copy the EFI folder to the EFI partition
- [ ] Reboot and profit?

Since there are no root patches, updates shouldn't break much — if anything at all. <br>
Any breakages do get fixed and posted here. All apps and assets used are provided by this repo.<br>
feel free to use them if you can't find them.<br>

---
## Credits


| Contributor                                                   | For                                                                   |
| ------------------------------------------------------------- | --------------------------------------------------------------------- |
| **userminer2**                                                | Making the EFI for the T470s                                          |
| [**Dortania**](https://dortania.github.io/)                   | OpenCore                                                              |
| [**acidanthera**](https://github.com/acidanthera)             | `Lilu.kext`, `WhateverGreen.kext`, `VirtualSMC`                       |
| [**corpnewt**](https://github.com/corpnewt)                   | ProperTree and GenSMBIOS                                              |
| [**OpenIntelWireless**](https://github.com/OpenIntelWireless) | Intel Wi-Fi and Bluetooth                                             |
| **tetenc555**                                                 | `SSDT-BATX.aml` — dual battery patch (from their T480 EFI, I believe) |
| [**zhen-zen**](https://github.com/zhen-zen)                   | YogaSMC                                                               |
| [**exelban**](https://github.com/exelban/stats)               | Stats app                                                             |
| [**laobamac**](https://github.com/laobamac/itlwm)             | AirportItlwm WiFi & SimpleHDA.kext                                    |
| u/No-Independant-9209                                         | Testing old version of the EFI raising the 8GB of ram issue           |


---

## Changelog

5/11/2026 - v0.97:
<br>
```
- Removed Ventura - Sequoia support.
- Cleaned up the config.plist file removing redundancies.
- Fixed Freezing bug though more testing will be made.
- Fully removed itlwm.kext
- Disabled AppleCpuPmCfgLock Quirk (useless on skylake cpu and higher).
```
<br>
<br>
3/11/2026 - v0.96 (canary/nightly):
<br>

```
- Replaced HDAUniversal.kext with SimpleHDA.kext
- Restored AppleALC via SimpleHDA.kext injected by the bootloader making HDAUniversal.kext obsolete
- C states now go down to 0.2W
- Improved NVMe stability thanks to NVMeFIX.kext
```

⚠️Warning v0.96 is not stable and is prone to random freezes do not use for production!
<br>
<br>
2/11/2026 - v0.95 (stable):
<br>

```
- Changelog begins at v0.95
- I tested 8GB of ram and I don't know what changed but 8GB of ram is now smooth.
- RAM requirements lowered from 12 to 8GB
- Power Saver is now completely optional
- Heliport is now obsolete native WiFi is back
- Indexing is now confirmed to only take 5-15 minutes instead of 1 hour on the stock m.sata SSD.
- Lag during indexing phase is fixed you now only have to deal with heat but minimal lag on indexxing.
- You can now use the Hackintosh out of the box without waiting after install.
- Deprecated itlwm.kext (disabled in config.plist)
```
<br>

--- 

## ⚠️ Disclaimer

While the EFI is now stable enough that I can rely on it as my workhorse, I can not guarantee stability on your systems. If you encounter any issues feel free to ask questions or report bugs.
