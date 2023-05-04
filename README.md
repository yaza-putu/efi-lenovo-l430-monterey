# lenovo-thinkpad-l430 
## Monterey 12.6.5
![lenovo thinkpad l430](https://res.cloudinary.com/dk0053zbe/image/upload/v1683217467/monterey_gbnihv.png)

## spesifikasi :
- Bootloader Opencore 0.7.9
- processor core i3 3120M (Ivy Bridge)
- vga intel hd 4000
- audio alc269 layout-id 29
- Ethernet RTL8168E-VL
- Intel(R) Centrino(R) Advanced-N 6205
- Intel 7 Series Chipset
- Touchpad ELAN

## Working :
- iGpu intel HD 4000 (PATCH)
- USB port
- Sound Alc269
- Touchpad
- etc
- Sleep (Not perfect)
- shotdown
- Restart
- Must be set SMBIOS MacBookPro12,1 to be install Monterey (on instalations) and SET to MacBookPro10.2 with boot args no_compat_check (POST Istall) to fixing Power management Issue in ivy bridge Monterey (SSDT-PM.aml generated from catalina)
- Brightness, Fn + p (brightness up) and Fn + k (brightness down)
- Display Port
- WLAN Intel(R) Centrino(R) Advanced-N 6205

## Not Working :
- VGA port

## Patch SSDT:
- PNLF (Fix Brightness)
- PM (CPU power management) (POST Install)
- EC (Fixes the embedded controller)
- XOSI (Makes all _OSI calls specific to Windows work for macOS (Darwin) Identifier. This may help enabling some features like XHCI and others.)
- IMEI (Needed to add a missing IMEI device on Ivy Bridge)
- HPET (Fixing IRQ Conflicts) https://dortania.github.io/Getting-Started-With-ACPI/Universal/irq.html
- SBUS-MCHC fix SMBUS
- SSDT-THINK (enable fan control YOGA SMC kext) (POST INSTALL)
- SSDT-RCSM (virtual power control YOGA SMC) (POST Install) 
- SSDT-ECRW (EC Reading YOGA SMC) (POST Install)


## Important to install monterey
- you need change SMBIOS to MacBookPro12,1 before install macOS Monterey (remove ssdt-pm.aml)
- after finish install you need copy ssdt-pm.aml to folder ACPI and set SMBIOS to MacBookPro10.2 to enable perfect power management


## Patch iGPU Intel HD4000
Apple dropped support for the HD 4000 graphics , so before run patch make sure set in config.plist :

- Go to Misc/Security, find the entry SecureBootModel and set it to Disabled
- Go to NVRAM/Add/7C436110-AB2A-4BBB-A880-FE41995C9F82, find csr-active-config and set it to 030A0000

After restart run Opencore Legacy Patcher [link](https://dortania.github.io/OpenCore-Legacy-Patcher/)

## Kext Version Control
- AppleALC              : V1.8.1 (RELEASE)
- Lilu                  : V1.6.4 (RELEASE)
- RealtekRTL8111        : V2.4.2 (RELEASE)
- VirtualSMC            : V1.3.1 (RELEASE)
- VoodooPS2Controller   : V2.2.3 (RELEASE)
- WhateverGreen         : V1.6.4 (RELEASE)
- YogaSMC               : V1.5.3 (RELEASE)
- USBMap                : Generated (CUSTOM)
- AirportItlwm.kext     : V2.1.0 (STABLE)

## Change Log
- 4 May 2023 , change SMBIOS MacBookPro12.1 to MacBookPro10.2 to fix power management (old SSDT PM generated from catalina) issue CORE REQ always high for Ivy Brige processor in BIGSUR
- 4 May 2023 Patch iGPU intel HD4000 with Opencore Legacy Patcher
- 4 May 2023 Update SSDT-PNLF to support in monterey

## Issue
- sleep not perfect
