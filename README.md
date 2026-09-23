

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
10. [Credits](#-credits)

---

## Introduction

This is a **sanitized version** of the EFI I use daily on my ThinkPad T470s hackintosh. I couldn't find a proper guide for this exact model, so I built my own EFI from scratch — and decided to share a clean version with the community.

> **Tip:** Hold Esc or Alt at boot to show the OpenCore boot picker.

### My experience so far

- **Full metal GPU acceleration** — Smooth animations and usability just the ocasional lag spike and 100% cpu usage if loading assets for the first time.
- Icons may take a second to load if you use an m.sata SSD to fix this use an NVMe SSD. (Visual does not impact usability)
- **Apple Video Toolbox works** — video editing in Kdenlive and CapCut worked out of the box.
- **HandBrake transcoding** — consistently over 60 fps *on battery*, compressing 10 GB footage down to \~500 MB in a few minutes.
- **Roblox runs better** than on Windows or Linux.
- **Battery life:** 2 h gaming · 4–5 h web browsing · 6–7 h coding &amp; document editing.
- **Bluetooth works perfectly.**
- **Wi-Fi is nearly fully functional** (missing a thing or two — see below).

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
| Model         | Lenovo ThinkPad T470s            |
| CPU           | Intel Core i7-6600U              |
| RAM           | 4 + 16 GB                        |
| GPU           | Intel HD Graphics 520            |
| start version | **26.3 Tahoe**                   |
| macOS version | **26.7 Tahoe**                   |
| SMBIOS        | MacBookPro13,1                   |


**Recorded temps:** 35 °C idle (1 W CPU) · 40–50 °C normal use (2–5 W CPU) · 65–72 °C gaming/rendering (12–20 W CPU) <br>
**Recorded battery draw:** 6W idle · 8-11W normal use · 17-29W gaming/rendering<br>

> No known issues outside of no AirDrop and no WPA-Enterprise Wi-Fi.

---

## Another User's Setup

Many thanks to **u/No-Independant-9209** for DMing me their config and results:


| Spec          | Value               |
| ------------- | ------------------- |
| CPU           | Intel Core i5-6300U |
| RAM           | 4 + 4 GB            |
| GPU           | Intel HD 520        |
| start version | **26.5 Tahoe**.     |
| macOS version | 13.7.8 Ventura      |


**Their experience:**

- Slightly sluggish on Tahoe — not MacBook levels; couldn't handle 10+ apps smoothly
- Usable, but the trackpad occasionally crashed
- After downgrading to Ventura, **Continuity and everything else just worked**

---

## Personal Note

From what I've understood:


| Your RAM                | My recommendation                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| 8 GB                    | **Ventura** — unless you need Tahoe app compatibility and don't mind a few frame drops and cosmetic glitches |
| 12+ GB                  | **Tahoe** should be a good way to go                                                                         |
| 16–20+ GB               | **Tahoe** — good performance, occasional visual artefacting                                                  |


>  **If you use Tahoe:** enable Battery Saver to avoid fans ramping up when plugged in, and for better performance.

---

## ℹ️ General Info

- **System SMBIOS:** `MacBookPro13,1`
- **Supported:** macOS Ventura → macOS Tahoe (older versions will probably work, but untested)

Known update issues

- `VoodooHDA.kext` only works on **macOS 26.5.2 and lower**. macOS 26.6+ requires `HDAUniversal.kext`, provided via PKG.
- Outside of that, no known issues when updating via the Settings app.
- /Library/Extensions/VoodooHDA.kext works seamlessly up to macOS 26.5.2 Tahoe without reinstall.
- /Library/Extensions/HDAUniversal.kext works without reinstall on macOS 26.6+ Tahoe.



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



## ❌ What Doesn't Work

- ❌ WPA-Enterprise Wi-Fi (limitation of HeliPort + itlwm)
- ❌ AirDrop (requires AirportItlwm, which is WIP)

---

## 🔧 Setup Required

1. **Generate your own serial number** — this EFI ships without mine (use [corpnewt's GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)).
2. **No root patching required** — except adding `HDAUniversal.kext` and the HeliPort app.

---

## 🚀 Post-Install

> **Is this set-and-forget?** Yes, for the most part! Once audio and Wi-Fi are set up, you can forget about it — except for major updates like 26.5.2 → 26.6 where audio may break (fixable via the PKG).

> **Do I need post-install root patches?** No. Just install HDAUniversal via the provided PKG, install HeliPort app and run one terminal command to fix overheating.

**Enable battery saver (recommended on Tahoe):**

```bash
sudo pmset -a lowpowermode 1
```

…or simply toggle it in **Settings**.

### 📋 Checklist

- [ ] Install **HDAUniversal** via the provided PKG
- [ ] Run the `pmset` command above (or enable Battery Saver in Settings)
- [ ] Download [HeliPort](https://github.com/OpenIntelWireless/HeliPort) provided and move it to `/Applications`
- [ ] Add HeliPort to **Login Items**
- [ ] (Optional) Install the [Stats](https://github.com/exelban/stats) app to show battery without the yellow icon
- [ ] disable wifi and battery icons in menubar
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


---

## ⚠️ Disclaimer

This EFI is still work in progress and experimental. It is now stable enough that I can use it as a daily driver but I can not guarantee stability on your systems. If you encounter any issues feel free to ask questions or report bugs.
