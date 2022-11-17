# Clevo-NL4x_5xCU-Hackintosh
Opencore Bootloader for Clevo NL4xCU / NL5xCU series laptop

## Configuration

This repositry has been made based on a Machenike Machcreator-A laptop, which is a Clevo NL4x/5xCU rebrand

### NL40CU

| Specifications | Detail                                                  |
| ------------------- | ------------------------------------------- |
| Computer model | Machenike Machcreator-A |
| Processor | Intel Core i3-10110U |
| Memory | 8GB DDR4 2667 MHz |
| Hard Disk | WD NVMe 256 Gb (Upgraded to Crucial P2 NVMe 1 Tb)|
| Integrated Graphics | Intel UHD Graphics 620 |
| Monitor | FHD 1920x1080 (15.6 inch) |
| Sound Card | Realtek ALC293 (layout-id: 28) |
| Wireless Card | Intel Wireless-AC 9462 |
| Ethernet Card | Realtek |
| Trackpad | ? |
| SD Card Reader | ? |

## Current Status

- **HDMI** ~~not tested~~ fixed in last release
- **Touchpad** is only working fine in polling mode
  - added -vi2c-force-polling in boot-args, not working otherwise. Tried GPIO pinning with no success.
- **Intel Bluetooth** does not support some older Bluetooth devices
  - On macOS12+, Intel Bluetooth supports more Bluetooth 4.x devices
- **Battery manager** doesn't work properly with SMCBatteryManager.kext (percentage not updating), solved by using Rehabman's ACPIBatteryManager.kext
  - Recompiled from source using latest XCode
- Everything else works well
---

### OpenCore

- Tested on macOS 12 Monterey (12.6)

## Installation

### Identify Your Model 

Go to your BIOS and see if the device name is NL4x_5xCU. If it's the case, your device may be similar enough to test those files.

### First-time installation

- Please refer to the following installation tutorial
  - https://dortania.github.io/OpenCore-Install-Guide/
  - You may try modifying the EFI folder to adapt it to your device after reading the install guide
  - Don't forget to edit the SMBIOS data in config.plist 
  - Don't forget to add the Ressources folder (follow the guide to download it)

### CFG Unlock

Boot with OpenCore Bootloader, show auxiliary by typing space and use the included GRUB Shell. Then type "setup_var_cv CpuSetup 0x3E 0x01 0x00". Check if it has been done correctly using ControlMseE2.efi.
  - Follow this guide for more detailed infos : https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html
  
### Post-Installation 

- Use the following Guide https://dortania.github.io/OpenCore-Post-Install/

## Credits

- Thanks to [cholonam](https://github.com/cholonam) for providing [Sinetek-rtsx](https://github.com/cholonam/Sinetek-rtsx)
- Thanks to [Acidanthera](https://github.com/acidanthera) for providing [AppleALC](https://github.com/acidanthera/AppleALC), [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM), [HibernationFixup](https://github.com/acidanthera/HibernationFixup), [Lilu](https://github.com/acidanthera/Lilu), [NVMeFix](https://github.com/acidanthera/NVMeFix), [OcBinaryData](https://github.com/acidanthera/OcBinaryData), [OpenCorePkg](https://github.com/acidanthera/OpenCorePkg), [RestrictEvents](https://github.com/acidanthera/RestrictEvents), [VirtualSMC](https://github.com/acidanthera/VirtualSMC), [VoodooInput](https://github.com/acidanthera/VoodooInput), [VoodooPS2](https://github.com/acidanthera/VoodooPS2), and [WhateverGreen](https://github.com/acidanthera/WhateverGreen).
- Thanks to [OpenIntelWireless](https://github.com/OpenIntelWireless) for providing [AirportItlwm](https://github.com/OpenIntelWireless/itlwm) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware).
- Thanks to [RehabMan](https://github.com/RehabMan) for providing [OS-X-ACPI-Battery-Driver](https://github.com/RehabMan/OS-X-ACPI-Battery-Driver)
- Thanks to [VoodooI2C](https://github.com/VoodooI2C) for providing [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C).
