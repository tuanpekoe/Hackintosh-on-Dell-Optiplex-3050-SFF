<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

### Hackintosh-on-Dell-Optiplex-3050-SFF
Welcome to the Hackintosh tutorial on Dell Optiplex 3050 SFF tutorial. This repository provides a pre-made EFI setup for the OpenCore bootloader specifically designed for the Dell Optiplex 3050 SFF.
I hope you can install macOS on your PC successfully. Please read this guide carefully.
### Hardware detail:
Here is my Dell PC specification:
- Model: Dell Optiplex 3050 SFF
- CPU: Intel Core i5 7500
- Ram: DDR4 8GB
- Integrated graphics: Intel UHD 630
- Audio card: Realtek ALC234
- Ethernet card: Realtek RTL8111
### Software detail:
- OpenCore version: 1.0.0
- macOS: Ventura 13.6.6
- SMBIOS: iMac18,1
### Working list:
- Integrated graphics: Intel UHD 630
- Audio card: Realtek ALC234 (Internal speaker, Headphone jack)
- Ethernet card: Realtek RTL8111
- HDMI port and HDMI audio
- DisplayPort
### Not Working list:
- VGA port
### Uselful tips:
- Tip 01: You should try to connect your monitor to **HDMI port** because **DisplayPort** or **VGA port** may not work for you in this stage.
- Tip 02: Plug installation USB to **2.0 port** instead of 3.0 port. That will help you to prevent some silly errors when booting.
- Tip 03: Sometimes you need to choose option "**Reset NVRam**" at the Opencore's boot screen to refresh NVRam. You may need to press "Space bar" at the boot screen to show up the option.
- Tip 04: If you want to install macOS Sonoma, you need to change the SMBIOS to **iMac19,1**
### BIOS setting
- Step 01: Reset BIOS to default. This step is important, do not skip it.
- Step 02: Disable those parameters: "Sercure Boot", "Enable Legacy Option ROMs", "Intel SGX", "Serial COM/port"
- Step 03: Enable those parameters: "AHCI"
- Step 04: Save and exit BIOS. Press F12 to choose boot from macOS installation USB.
### Pre-install instruction
This is the most important step of the tutorial, a lot of people failed and gave up. So I give you 02 options for the first boot to macOS installation on the PC.
- Option 01: I disabled the **iGPU** and **Audio** patching to prevent any conflicts when booting. (Note: If you are newbie, you are highly recommended to choose this)
- Option 02: I enabled the **iGPU** patching to show a little smoothness at the installation step (iGPU/video acceleration). (Note: This option is only for experienced user)
### Post-install instruction
Please be aware that this Pre-made EFI can work perpectly on your Dell Optiplex or can not, because harware is not the same. You may need to modify some parameters to match your hardware, please check the Credits part to do it by yourself.
I already fixed some major problems on my Dell Optiplex 3050 SFF as follow:
- Problem 01: Pink/tint/magent screen color when connect to HDMI port. I fixed the **connector-type** in config.plist.
- Problem 02: Monitor suddenly turns off (black screen) at the login screen (or after apple logo boot). I added **agdpmod=vit9696** to Boot Arrgument in config.plist.
- Problem 03: DisplayPort can not export signal to the monitor. I fixed the **connector-type** in config.plist.
- Problem 04: Headphone jack issue (distort sound) because of wrong **alcid** ID. I already set **alcid=11** in config.plist and it works very well.
- Problem 05: Some USB 2.0 and 3.0 ports can not recognize USB sticks. I fixed it by USBMap method.
## Credits:
- [1rocketdude](https://github.com/1rocketdude/Optiplex_3050_SFF) for Displayport patching
- [mavethee](https://github.com/mavethee/Hackintosh-OpenCore-EFI-DELL-Optiplex-3050) for EFI Pre-made
- [acidanthera](https://github.com/acidanthera/HibernationFixup) for Hibernate fix
- [corpnewt](https://github.com/corpnewt/USBMap) for USBMap fix
- [EliteMacx86](https://elitemacx86.com/threads/how-to-fix-pink-screen-on-intel-hd-and-uhd-graphics-on-macos-sierra-and-later-on-desktops-clover-opencore.434/) for Pink/tint/magent screen color fix
- [EliteMacx86](https://elitemacx86.com/threads/how-to-enable-intel-hd-and-uhd-graphics-on-macos-intel-framebuffer-patching-guide.931/) for HDMI and DisplayPort fix
- [dortania](https://dortania.github.io/GPU-Buyers-Guide/misc/bootflag.html) for Boot flags
- [dortania](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/intel-patching/) for iGPU patching
- [Audio fix](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html) for Audio patching
