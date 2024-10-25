
# EFI folder for Dell E6430 (macOS Big Sur)

![Big Sur](ScreenShot/Screenshot%202024-10-20%20at%206.32.05%20PM.png)

Its a EFI folder used for Catalina but updated for Big Sur.

If you want install macOS 11+ then use OCLP(https://github.com/dortania/OpenCore-Legacy-Patcher)


## Laptop Specs

- Intel® Core™ i7 i7-3740QM 2.7 GHz (Ivy Bridge)
- 8 GB DDR3-SDRAM 1600 MHz
- 256 GB SSD
- Intel® HD Graphics 4000

**Note:** My model doesn't have a Nvidia Card. If you have one, my instructions might not work correctly.

## USB Creation 

For making a bootable Big Sur installer

- Format a 16GB+ USB to FAT32
- Using gibMacRecovery download Big Sur Recovery package
- Then copy com.apple.recovery.boot folder over to the USB
- Generate a SMBIOS for MacBookPro11,1 using Gen-SMBIOS
- Then paste the above EFI to the USB
- Then boot to the USB 


## BIOS Setting (For ALL PC's)

**Disable:**
- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- VT-d (can be enabled if you set DisableIoMapper to YES)
- CSM
- Thunderbolt(For initial install, as Thunderbolt can cause issues if not setup correctly)
- Intel SGX
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection)(This must be off, if you can't find the option then enable AppleXcpmCfgLock under Kernel -> Quirks. Your hack will not boot with CFG-Lock enabled)

**Enable:**
- VT-x
- Above 4G decoding
- Hyper-Threading
- Execute Disable Bit
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode
- DVMT Pre-Allocated(iGPU Memory): 64MB or 128MB
- SATA Mode: AHCI


## macOS Big Sur Installation

Reboot your Laptop with the USB Installer stick plugged in. Press `F12`, choose `UEFI`, it should boot to Clover. Pick your USB Installer in the menu, the Mojave Installer will start to load. You can encounter various graphics glitches during this step, it's fine.

Once you reach the Mojave Installer, launch the Disk Utility app and in the menubar, in the "presentation" menu (or similar, don't remember the name), enable "Show all devices". That way, we will see our internal hard drive completely in Disk Utility. Format it as Mac OS X Extended (Journaled) and pick the scheme "GUID Partition Map" or similar.

Now close the Disk Utility and start the Installer.

## Post-Installation

Now follow this guide for Post-Installation : https://dortania.github.io/OpenCore-Post-Install/

## What works

Almost everything works but if you notice something not working, you can contact me below

## Known-issues during Installation

- After you launch the installer from OpenCore Menu you will have blank screen for sometime and then it starts

- If you face this error RT.GV wake-failure error. Wait for sometime and then it will start.

- Some Random graphical glitch will appear

## Credits

- Thanks to tonymacx86 for their guide
