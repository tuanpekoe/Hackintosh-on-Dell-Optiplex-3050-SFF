<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

### Hackintosh-on-Dell-Optiplex-3050-SFF
Welcome to the Hackintosh on Dell Optiplex 3050 SFF tutorial! 
This repository provides a pre-made EFI setup for the OpenCore bootloader specifically designed for the Dell Optiplex 3050 SFF.

### Hardware detail:
This this my Dell PC specification:
- Model: Dell Optiplex 3050 SFF
- CPU: Intel Core i5 7500
- Ram: DDR4 8GB
- Integrated graphics: Intel UHD 630
- Audio card: Realtek ALC234
- Ethernet card: Realtek RTL8111
### Software detail:
- OpenCore version: 1.0.0
- macOS: Ventura 13.6.6
- SMBIOS: iMac 18,1
### Working list:
- Integrated graphics: Intel UHD 630
- Audio card: Realtek ALC234 (Internal speaker, Headphone jack)
- Ethernet card: Realtek RTL8111
- HDMI port and HDMI audio
- Display port
### Not Working list:
- VGA port
### BIOS setting and some tips:
- You should try to connect your monitor to **HDMI port** because **DisplayPort** or **VGA port** may not work for this stage.
- Sercure boot: Disable
- 

### Pre-install instruction
This is the most important step of the tutorial, so I give you 02 options for the first boot to macOS installation on the PC.
- Option 1: I disabled the iGPU and Audio patching to prevent any conflicts. (Note: If you are newbie, you are highly recommended to choose this)
- Option 2: I enabled the iGPU patching to show a little smoothness when installation. (Note: This option is only for experienced user)

### Post-install instruction
Please aware that this Pre-made EFI can work perpectly on your Dell Optiplex or can not, because harware is varies. You may need to modify some parameter to match your hardware.
I already fixed some major problems on my Dell Optiplex 3050 SFF as follow:
- Problem 01: Pink/tint/magent screen color when connect to HDMI port. I fixed the **connector-type** in config.plist.
- Problem 02: Monitor suddenly turn off (black screen) at the login screen. I added agdpmod=vit9696 to Boot Arrgument in config.plist.
- Problem 03: DisplayPort can not export signal to the monitor. I fixed the **connector-type** in config.plist.
- Problem 04: Headphone jack issue (distort sound) because of wrong **alcid**. I already set **alcid=11** in config.plist and it works well.
- Problem 05: Some USB 2.0 and 3.0 ports can not recognize USB sticks. I fixed it by USBMap method.

## Credits:
- [1rocketdude](https://github.com/1rocketdude/Optiplex_3050_SFF) for Displayport patching
- [mavethee](https://github.com/mavethee/Hackintosh-OpenCore-EFI-DELL-Optiplex-3050) for EFI folder
- [HibernationFixup](https://github.com/acidanthera/HibernationFixup)
- [USBMap](https://github.com/corpnewt/USBMap)
- [Intel UHD 630 patch - Pink/tint/magenta color]([https://github.com/corpnewt/USBMap](https://elitemacx86.com/threads/how-to-fix-pink-screen-on-intel-hd-and-uhd-graphics-on-macos-sierra-and-later-on-desktops-clover-opencore.434/))
- [Intel UHD 630 patch - HDMI fix](https://elitemacx86.com/threads/how-to-fix-pink-screen-on-intel-hd-and-uhd-graphics-on-macos-sierra-and-later-on-desktops-clover-opencore.434/)
- [Audio fix](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html)
