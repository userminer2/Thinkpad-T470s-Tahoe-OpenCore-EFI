[![Home](https://img.shields.io/badge/🏠_README-blue?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI)
[![Hardware](https://img.shields.io/badge/🛠️_HARDWARE-brightgreen?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/HARDWARE.md)
[![Issues](https://img.shields.io/badge/⚠️_Issues-red?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/KNOWN_ISSUES.md)
[![Releases](https://img.shields.io/badge/🚀_Releases-Download-blueviolet?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/releases)

# 🛠️ Tested Hardware & Buyer's Guide

> Which parts to buy for a T470s hackintosh, what I actually tested, what works, and what to avoid.
> Everything in the **Tested** tables was verified on macOS Tahoe with this EFI.
> Items marked *(expected)* were not personally tested but should work based on hardware research — buy at your own risk.

---

## Table of Contents

1. SSDs / Storage
2. RAM
3. CPUs
4. Batteries & Power Draw
5. Screens
6. Wi-Fi / Bluetooth Cards
7. Buying Checklist

---

## 💾 SSDs / Storage

The T470s has **one M.2 2280 slot**. Both SATA and NVMe drives fit, but they do **not** behave the same on macOS.

## Personal recommendation so far is the stock m.sata 256GB SSD <br>

   Status | Model | Capacity | Type | Tested on | Known issues | Notes | Recommended |
 |--------|-------|----------|------|-----------|---------------|-------|------------|
 | ✅ Tested | Intenso 1TB (m.SATA) | 1 TB | SATA | Tahoe 26.3 → 26.7.2 | Icons and assets take a second to load on cold boot and forces CPU to never go below C2 locking CPU to 1.7W+ | Works fine otherwise, purely cosmetic. Cheap per GB | ⚠️ yes if you don't mind 3-5h battery life |
 | ✅ Tested | stock 256GB SSD (m.SATA) | 256 GB | SATA | Tahoe 26.7+ | Icons take a second to load on cold boot | C states work and gives the best battery life tested so far | ✅ Yes |
 | ✅ Tested | Kingston NV2 1TB (NVMe) | 1 TB | NVME | Tahoe 26.7.1 | C states are completely broken even with NVMeFIX.kext and overheating with freezing. May have damaged my thinkpad as I experience BIOS and freezing issues though I have not tested my og SSD to see if a stable OS works | Icons load fast everything is instant  | ❌ No |
 | ⏳ Pending test | Opal "stock" SSD (NVMe) | 256 GB | NVME | N/A | N/A | looks promising | Unknown |
 | ⏳ Pending test | SKHynix OEM 256GB SSD (m.SATA) | 256 GB | SATA | N/A | N/A | N/A | Unknown |

### What to look for when buying

- ✅ **NVMe drives** — faster, and no icon-loading delay. `NVMeFix.kext` is included since EFI v0.96 for stability.
- ✅ **SATA M.2 drives** — Work really well, but slower asset/icon loading in macOS (purely cosmetic on cold boot).
- ℹ️ With `NVMeFix.kext` (v0.96+), most mainstream NVMe drives (Samsung, WD, Crucial, Kingston) should be plug-and-play. Report your results so this table can grow.

---

## 🧠 RAM

The T470s has **4 GB soldered** + **one free SODIMM slot** (DDR4-2133). Max total = **4 + 32 GB = 36 GB**.
 | Config | Total | EFI version | Tested on | Verdict |
 |--------|-------|-------------|-----------|---------|
 | 4 + 16 GB | 20 GB | pre 0.9 -> 0.96 | Tahoe 26.3 → 26.7 (my daily driver) | ✅ **Recommended.** 30+ tabs open, smooth. Frame drops only in Launchpad occasionally |
 | 4 + 4 GB | 8 GB | 0.90 - 0.96 | Tahoe 26.7.1+ | ✅ Absolutely works I used this and I have gotten the ram to no longer be a big issue |
 | 4 + 4 GB | 8 GB | pre 0.9 | Tahoe 26.5 / Ventura 13.7 | ✅ Works, but sluggish on Tahoe — couldn't handle 10+ apps smoothly. Downgrading to Ventura made everything "just work". **Update: since EFI v0.95 + macOS 26.7, 8 GB is now smooth** |
 
### Recommendations by RAM (macOS version)
 | Your RAM | My recommendation |
 |----------|--------------------|
 | 8 GB | **Tahoe 26.7+ on EFI v0.95+** — earlier Tahoe was rough on 8 GB, it's fixed now |
 | 16–20+ GB | **Tahoe** — my personal setup |

- ⚠️ Buy a **DDR4-2133 SODIMM** (the slot is limited to 2133 MHz, faster-rated sticks will just downclock).
- ⚠️ Some cheap no-name SODIMMs can cause instability — prefer name brands (Crucial, Samsung, Kingston, Corsair).

---

## ⚙️ CPUs

All T470s CPUs are 6th-gen Skylake (HD Graphics 520) — fully Metal-supported, which is why this model works so well.
 | CPU | Cores/Threads | GPU | Tested on | Verdict |
 |-----|---------------|-----|-----------|---------|
 | i7-6600U | 2C/4T, up to 3.4 GHz | HD 520 | Tahoe 26.3 → 26.7 | ✅ **My CPU.** Full Metal acceleration, Apple VideoToolbox works, 60+ fps HandBrake transcoding *on battery* |
 | i5-6300U | 2C/4T, up to 3.0 GHz | HD 520 | Tahoe 26.5, Ventura 13.7 | ✅ Works (Needs testing on newer EFI) |
 | i5-6200U | 2C/4T, up to 2.8 GHz | HD 520 | _not tested_ | Expected to work identically |
 | i5-6300U vPro / i7-6600U vPro | — | HD 520 | _not tested_ | vPro features irrelevant on macOS, rest identical |

**Buying advice:** any 6th-gen T470s CPU works — don't pay extra for the i7, the difference on macOS is small (both are 15 W dual-cores). Prioritize RAM and an NVMe SSD instead.

---

## 🔋 Batteries & Power Draw

The T470s has a **dual battery system** (internal + external). Fixed percentage reporting works since 18 Jul 2026.

### Recorded power draw (my i7-6600U, 20 GB RAM)
 | Scenario | CPU power | System draw | Battery life |
 |----------|-----------|-------------|--------------|
 | Idle | 0.2–1 W | ~6 W | around 8h |
 | Normal use (browsing, coding, notes) | 2–5 W | 8–11 W | 6–7 h |
 | Gaming / rendering | 12–20 W | 17–29 W | ~2 h |

### Recorded temperatures
 | Scenario | Temp |
 |----------|------|
 | Idle | 35 °C |
 | Normal use | 40–50 °C |
 | Gaming / rendering | 65–72 °C |

### Battery checklist when buying used

- [ ] I use Ifixit batteries and they have been good for the past 240+ cyles still at 105% design Capacity
- [ ] I use  00HW022 24wH and 01AV406 23Wh though my total battery capacity is at roughly 50Wh not 47.
- [ ] The dual-battery percentage reporting is **fixed on this EFI** — if percentages look wrong, update to the latest release

> **Tip:** on Tahoe, Battery Saver is optional since EFI v0.95 / macOS 26.7, but it still removes thermal spikes when plugged in at a cost of 0–15% performance.

---

## 🖥️ Screens
 | Panel | Resolution | Tested | Notes |
 |-------|------------|--------|-------|
 | 14" FHD IPS, 1920×1080 | 1080p | ✅ My setup | backlight control via WhateverGreen |

- ✅ HDMI (audio + video) works out of the box.
- ✅ Brightness control works.
- **Buying advice:** get an FHD IPS model — the TN panel is the single worst thing about cheap T470s units.

---

## 📶 Wi-Fi / Bluetooth Cards
 | Card | Tested | Notes |
 |------|--------|-------|
 | Intel AC 8260 (stock) | ✅ Tested | Works via `itlwm`/`AirportItlwm` fork. Native Wi-Fi since EFI v0.95 (HeliPort obsolete). Bluetooth works perfectly. WPA-Enterprise works. **AirDrop is still finicky/partially broken** |
 | Intel AC 8265 (stock) | ✅ Tested | Works via `itlwm`/`AirportItlwm` fork. Native Wi-Fi since EFI v0.95 (HeliPort obsolete). Bluetooth works perfectly. WPA-Enterprise works. **AirDrop is still finicky/partially broken** |
 | Broadcom BCM94360CS2 (with adapter) | _not tested_ | The classic hackintosh card *(expected)*: native AirDrop/Handoff would work. Untested on this EFI — report if you try it |

- ⚠️ AirDrop is the **only remaining known hardware limitation** on the stock Intel card.
- ℹ️ This EFI assumes the stock Intel card — if you swap to Broadcom, you may need to remove the itlwm kexts yourself.

---

## ✅ Buying Checklist

If you're buying a T470s specifically to run macOS with this EFI:

- [ ] **Any 6th-gen CPU** (i5-6200U/6300U or i7-6600U) — all work
- [ ] **FHD IPS screen** over TN, always
- [ ] **NVMe SSD** (Samsung/WD/Crucial/Kingston) over m.SATA/SATA
- [ ] **4 + 16 GB RAM** if you can (8 GB total is fine since v0.95+)
- [ ] **Stock Intel Wi-Fi** is fine — everything but AirDrop works
- [ ] **Check battery health** — dual battery reporting is fixed, but old cells are old cells

---
