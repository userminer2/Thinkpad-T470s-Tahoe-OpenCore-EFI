![t470s-core-i7-6600u-20gb-ram-1tb-m-sata-ssd-running-macos-v0-g97ulb8gxrrg1 png](https://github.com/user-attachments/assets/64b272ad-c8cc-4615-b8d1-773c29bf7daf)

# Thinkpad T470s Tahoe OpenCore EFI

This is a sanitized version of the EFI file I used for my T470s hackintosh.
I could not find a propper guide for my model so I decided to make my own EFI and share a sanitised version with the internet.
to show the boot picker hold escape.

# My setup:

I got a Thinkpad T470s with:
core i7-6600u
4 + 16 GB of ram
intel HD 520

This EFI supports mac OS ventura - Mac OS Tahoe (older versions will probably work but I have not tested them).

# What works:

- Bluetooth
- Keyboard
- Trackpad (gestures are finicky)
- Trackpoint
- function keys
- Graphics acceleration
- WiFi
- Airdrop (sometimes)
- Audio
- seemless booting

# What does not work:

- Second battery is not detected (visual bug)
- WP2A Enterprise wifi (limitation of heliport and Itlwm)

# Setup Required:
You will need to generate a serial number as this EFI does not have my serial number.

I will make this repo cleaner but hey.
