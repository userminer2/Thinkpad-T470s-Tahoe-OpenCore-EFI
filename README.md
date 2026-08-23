<img width="1920" height="1080" alt="Capture d’écran 2026-08-23 à 12 16 49" src="https://github.com/user-attachments/assets/69922a4a-6d12-43ee-a153-1aa8c3ba522b"/>

![t470s-core-i7-6600u-20gb-ram-1tb-m-sata-ssd-running-macos-v0-g97ulb8gxrrg1 png](https://github.com/user-attachments/assets/64b272ad-c8cc-4615-b8d1-773c29bf7daf)

# Tahoe 470s OpenCore EFI

This is a sanitized version of the EFI file I used for my T470s hackintosh.
I could not find a propper guide for my model so I decided to make my own EFI and share a sanitised version with the internet.
to show the boot picker hold escape or alt.

My personal experience is that full metal acceleration works. Animations are smooth and run almost like a normal Mac. Odd one or two lag spikes when high cpu load or gpu load like on startup or first time launching the animation if you have an m.sata SSD like me. Apple Video Toolbox works so video editing with kdenlive and cap cut both worked out of the box. Using handbrake for video transcoding has worked like a charm consistently doing over 60 fps on battery. Roblox runs better than on windows or linux. Performance is great and all audio problems have been resolved. Wifi is almost fully functional just missing a thing or two but sadly I could not get AirportItlwm to run stably. Battery ranges from 2 hours gaming to 4 hours web browsing to 6 hours coding and document editing. Bluetooth works perfectly. Last remaining major day to day use issue is the finicky trackpad that works for two finger gestures no problem but not so much for 3 finger or more gestures.

# My setup:

I got a Thinkpad T470s with:
core i7-6600u
4 + 16 GB of ram
intel HD 520
No known issues outside of finicky touchpad no airdrop and no WPA enterprise wifi.
Version used: MacOS 26.x Tahoe

# Thanks to u/No-Independant-9209 for DMing me his config and his results:

He got a Thinkpad T470s with:
core i5-6300u
4 + 4 GB of ram
indel HD 520
Version used: MacOS 13.7.8 Ventura

Slightly sluggish and not MacBook levels
Can not handle 10+ apps smoothly.
Usable but trackpad occasionally crashes.
He downgraded to Ventura and Continuity and other things just worked.

System SMBIOS -> MacbookPro 13,1
This EFI supports Mac OS Ventura - Mac OS Tahoe (older versions will probably work but I have not tested them).

# What works:

- Bluetooth
- Keyboard
- Trackpad (2 finger gestures work but not 3 finger gestures)
- Trackpoint
- function keys
- Graphics acceleration
- WiFi
- Audio
- seemless booting
- Dual battery since 18th Jul 2026
- Audio volume slider since addition of HDAUniversal.kext

# What does not work:

- WP2A Enterprise wifi (limitation of heliport and Itlwm)
- Airdrop (requires AirportItlwm which is WIP)

# Setup Required:
You will need to generate a serial number as this EFI does not have my serial number. No root patching is required except for adding HDAUniversal.kext and Heliport APP

I will make this repo cleaner but hey.
