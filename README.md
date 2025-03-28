<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Apple_logo_black.svg/488px-Apple_logo_black.svg.png" width="48" height="60"/> <img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

## Hackintosh on Dell Optiplex 3050 SFF and Kaby Lake system:
Welcome to the Hackintosh tutorial on Dell Optiplex 3050 SFF tutorial and Kaby Lake system. This repository provides a pre-made EFI setup for the OpenCore bootloader specifically designed for the Dell Optiplex 3050 SFF as well as Kaby Lake system.
I hope this post can help you to install macOS on your PC successfully. Please read this guide carefully and I wish you get luck.
## Hardware detail:
Here is my Dell PC specification:
- Model: Dell Optiplex 3050 SFF
- CPU: Intel Core i5 7500
- Ram: DDR4 8GB
- Integrated graphics: Intel UHD 630 (Intel HD Graphics 630)
- Audio card: Realtek ALC255
- Ethernet card: Realtek RTL8168/8111
## Software detail:
- Bootloader: OpenCore 1.0.3 (date 2025/02/04)
- macOS: Ventura 13.7.3 (date 2025/02/04)
- SMBIOS: iMac18,1
## Working list:
- Integrated graphics: Intel UHD 630 (Intel HD Graphics 630)
- Audio card: Realtek ALC255 (Internal speaker, Headphone jack)
- Ethernet card: Realtek RTL8168/8111
- HDMI port and HDMI audio
- DisplayPort
- All USB ports: Both 2.0 and 3.0
## Not Working list:
- VGA port
- Sleep/awake
## Uselful tips:
- Tip 01: You should try to connect your monitor to **HDMI port** because DisplayPort (or VGA port) may not work for you when booting. If HDMI port does not work, try DisplayPort (or VGA port).
- Tip 02: Do not use an Adaptor to connect your PC to Monitor (Example: Displayport to DVI, HDMI to VGA, etc). It may cause exporting signal problem and then your ports will not work properly.
- Tip 03: Plug installation USB to **2.0 port** instead of 3.0 port. That will help you to prevent some silly errors when booting. You may need to map USB ports before booting to avoid booting errors and make sure that USB Keyboard/Mouse will work on Recovery OS.
- Tip 04: Sometimes you need to choose option "**Reset NVRam**" at the Opencore's boot screen to refresh NVRam. You may need to press "Space bar" at the boot screen to show up the option.
- Tip 05: **iMac18,1** is the best fitted SMBIOS to for Intel Kaby Lake with macOS Ventura. If you want to install macOS Sonoma, you need to change the SMBIOS to **iMac19,1**, otherwise macOS can not boot. Download the latest release of _RestrictEvents.kext_, and use it with the boot flag (boot argument) _revpatch=sbvmm_. 
- Tip 06: If booting gets stuck/panic, try different **Boot flags** (see Credits section). Example: _-igfxvesa_ to force GPU into VESA mode (no GPU acceleration).
## BIOS setting:
- Step 01: Reset BIOS to default. This step is important, do not skip it.
- Step 02: Disable and Enable several parameters as table bellow.
- Step 03: Save and exit BIOS. Press F12 to choose boot from macOS installation USB.

| ❌ You should disable     | ✅ You should enable |
|---------------------------|---------------------- |
| Secure Boot               | Sata Operation: AHCI  |
| Serial/COM Port           | Intel Virtualization  |
| Enable Legacy Option ROMs | VT for Direct I/O     |
| Intel SGX                 | Fastboot: Thorough    |
| Serial COM/port           |                       |

## Pre-install instruction:
This is the most important step of the tutorial, a lot of people failed and gave up on first booting. So I give you 02 options for the first boot to macOS installation on the PC.
- Option 01: I disabled the **iGPU** and **Audio** patching to prevent any conflicts when booting. (Note: If you are newbie, you are highly recommended to choose this)
- Option 02: I enabled the **iGPU** patching to show a little smoothness and transparent window at the installation step, it is called GPU acceleration. (Note: This option is only for experienced user)
## Post-install instruction:
Please be aware that this Pre-made EFI can work perpectly on your Dell Optiplex 3050 SFF or can not, because our harware is not exactly the same. You may need to modify some parameters to match your hardware, please check the Credits part to do it by yourself.
In Post-installation step, I already fixed some major problems on my Dell Optiplex 3050 SFF as follow:
- Problem 01: Pink/tint/magent screen color when connect to HDMI port. I fixed the **connector-type** in config.plist.
- Problem 02: Monitor suddenly turns off (black screen) at the login screen (or after apple logo boot). I added **agdpmod=vit9696** to Boot Arrgument in config.plist.
- Problem 03: DisplayPort can not export signal to the monitor. I fixed the **connector-type** in config.plist.
- Problem 04: Headphone jack issue (distort sound) because of wrong **alcid** ID. I already set **alcid=11** in config.plist and it works very well.
- Problem 05: Some USB 2.0 and 3.0 ports can not recognize USB sticks. I fixed it by USBMap method.
## OpenCore Update instruction:
1. Replace all **efi** files:
- EFI/BOOT/BOOTx64.efi
- EFI/OC/OpenCore.efi
- EFI/OC/Drivers/OpenRuntime.efi
- EFI/OC/Drivers/OpenCanopy.efi
- EFI/OC/Drivers/ResetNvramEntry.efi
2. Update all **Kexts** of Acidanthera. Example: AppleALC.kext, Lilu.kext, WhateverGreen.kext
2. Check **Config.plist** update by **OCConfigCompare** and **ocvalidate** tools.
3. If your Bios can not detect OpenCore update, you should go to Bios and add EFI entry for OpenCore.
- EFI/BOOT/BOOTx64.efi
4. There are some tools for OpenCore automatic update. Example: OCAT
## Credits:
- [1rocketdude](https://github.com/1rocketdude/Optiplex_3050_SFF) for Displayport patching
- [mavethee](https://github.com/mavethee/Hackintosh-OpenCore-EFI-DELL-Optiplex-3050) for EFI Pre-made
- [acidanthera](https://github.com/acidanthera/HibernationFixup) for Hibernate fix
- [corpnewt](https://github.com/corpnewt/USBMap) for USBMap fix
- [USBToolBox](https://github.com/USBToolBox/tool) for USBMap fix
- [EliteMacx86](https://elitemacx86.com/threads/how-to-fix-pink-screen-on-intel-hd-and-uhd-graphics-on-macos-sierra-and-later-on-desktops-clover-opencore.434/) for Pink/tint/magent screen color fix
- [EliteMacx86](https://elitemacx86.com/threads/how-to-enable-intel-hd-and-uhd-graphics-on-macos-intel-framebuffer-patching-guide.931/) for HDMI and DisplayPort fix
- [dortania](https://dortania.github.io/GPU-Buyers-Guide/misc/bootflag.html) for Boot flags
- [dortania](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/intel-patching/) for Intel iGPU patching
- [Audio fix](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html) for Audio patching
