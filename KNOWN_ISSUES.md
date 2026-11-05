# ⚠️ Known Issues

> Every issue currently affecting this EFI on macOS Tahoe, what causes them, and how to fix or work around them.
> If something isn't listed here, [open an issue](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/issues) — I test reports whenever I can.

[![Home](https://img.shields.io/badge/🏠_README-blue?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI)
[![Hardware](https://img.shields.io/badge/🛠️_HARDWARE-brightgreen?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/HARDWARE.md)
[![Issues](https://img.shields.io/badge/⚠️_Issues-red?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/blob/main/KNOWN_ISSUES.md)
[![Releases](https://img.shields.io/badge/🚀_Releases-Download-blueviolet?style=for-the-badge)](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/releases)

---

## Table of Contents

1. Active issues
2. Resolved issues
3. Audio driver matrix
4. Update caveats
5. Reporting a bug

---

## 🔴 Active issues
   Issue | Severity | Affected versions | Workaround |
 |-------|----------|-------------------|------------|
 | **AirDrop / Continuity is finicky** — partially works, not reliable | Mild | All Tahoe versions | New fork of `AirportItlwm` improved things on 28/10/2026, but not perfect. A real fix needs a Broadcom Wi-Fi card or OCLP-T2 |
---

## ✅ Resolved issues
 | Issue | Severity | Fix | Resolved |
 |-------|----------|-----|----------|
 | **v0.96 (canary/nightly) random freezes and crashes** | Severe | Resolved with v0.97 | 5/11/2026 |
 | WPA-Enterprise Wi-Fi not working (itlwm instead of AirportItlwm) | Mild | New fork of `AirportItlwm` / use OCLP-T2 | 28/10/2026 |
 | Trackpad gestures only partially working | Moderate | Never a bug — 3-finger gestures were disabled in Settings | 23/09/2026 |
 | System severely overheating when plugged in | Moderate | Enable Power Saver mode (`sudo pmset -a lowpowermode 1`) | 02/04/2026 |
 | Poor performance & overheating from Liquid Glass | Severe | Wait for Spotlight indexing to finish after initial install | 25/03/2026 |
 | Poor battery life & fan ramp-up from Liquid Glass | Severe | Fixed by waiting ~15 m for indexing; since EFI v0.9+ / macOS 26.7+, Battery Saver no longer required | 25/03/2026 (updated 28/10/2026) |
 | Dual battery wrong percentage reporting | Moderate | `SSDT-BATX.aml` (from tetenc555's T480 EFI) | 18 Jul 2026 |
 | Sluggish performance on 8 GB RAM | Moderate | Fixed in EFI v0.95 + macOS 26.7 — 8 GB is now smooth | 02/11/2026 |

---

## 🔊 Audio driver matrix

Audio breaks between some macOS versions — check this table before filing an audio bug:
 | Audio driver | macOS version | Notes |
 |--------------|---------------|-------|
 | `VoodooHDA.kext` | 26.0 → 26.5.2 | Works without reinstall up to 26.5.2 |
 | `HDAUniversal.kext` | 26.6 → current | Install via the provided PKG; functional volume slider; survives updates |
 | `SimpleHDA.kext` | All versions | Currently in beta — will replace HDAUniversal for a truly native experience |


---

## ⚠️ Update caveats

- `VoodooHDA.kext` **only works on macOS 26.5.2 and lower** — on 26.6+ use `HDAUniversal.kext` (provided via PKG).
- Outside of audio, **no known issues** when updating via the Settings app (native OTA updates work).
- No root patching is required post-install.

---

## 🐛 Reporting a bug

1. Check the Active issues table and existing [issues](https://github.com/userminer2/Thinkpad-T470s-Tahoe-OpenCore-EFI/issues) first.
2. Include: your EFI version, macOS version, CPU, RAM config and SSD (see  for the format).
3. Describe what you expected vs. what happened, and whether it happens on battery, plugged in, or both.

> The EFI is still work in progress — I can't guarantee stability on every system, but breakages do get fixed and posted here.
