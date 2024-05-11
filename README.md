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
- 
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
- You should try to connect your monitor to **HDMI port** because **Display port** or **VGA port** may not work for this stage.
- Display port

### Pre-install instruction
There are 02 option for the first boot for the installation macOS on the PC.
- Option 1: I disabled the iGPU and Audio patching to prevent any conflicts. If you are newbie, you are highly recommended to choose this.
- Option 1: I enabled the iGPU patching to show a little smoothness when installation. This one is for experienced user.

### Post-install instruction

## Credits:
- [1rocketdude](https://github.com/1rocketdude/Optiplex_3050_SFF) for Displayport patching
- [mavethee](https://github.com/mavethee/Hackintosh-OpenCore-EFI-DELL-Optiplex-3050) for EFI folder
- [Lilu](https://github.com/acidanthera/Lilu/)
- [RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)
- [HibernationFixup](https://github.com/acidanthera/HibernationFixup)
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC)
- [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads)
- [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
- [OpenCanopy's resources](https://github.com/acidanthera/OcBinaryData)
