# ThinkPad E580 EFI for Opencore 0.6.1
Tested on 20KSA00SAU model with macOS Catalina (10.15.6)

### Specs
CPU: Intel Core i5-8250U 1.6 GHz
RAM: 16 GB (2 x 8 GB) DDR4-2400
SSD: Western Digital Blue NVMe SSD 250GB
GPU: Intel UHD 620 Graphics
WiFi: Dell Wireless 1560
Display: 15.6" FHD IPS 1920x1080


### BIOS Settings
* I used BIOS version 1.40, it may work on lower versions too
* Disable VT-d
* Enable Intel Virtualisation
* Disable Secure Boot

### What hardware doesnt work?
* Line/Mic Input (3,5")
* Card reader
* Cant use more than 3 fingers on the trackpad at once
* Samsung PM981 NVMe SSD
* The Realtek wifi card some models of this laptop come with
* FN keys do not work for their normal use (volume, brightness, etc..) after sleep, this is a common issue with 80/90 series thinkpads like this one

### WiFi

The specfic model E580 i got came with the RTL8822BE wifi card, this is not compatible under macOS in any circumstance, other models of the E580 come with the Intel AC3165 which will work (although not well at the moment) with the itlwm kext and the heliport application. I swapped my wifi card out for a DW1560 and this config comes with the required kexts to make that work.

### The Stock NVMe SSD

If you purchased the model E580 with the m.2 NVMe drive, you will need to swap it out for another NVMe drive or put a sata ssd into the sata slot in the laptop. the PM981 will cause kernel panics when trying to install to it, format it, clone os and resize it, etc...

### Post-Install

I recommend once you have installed macOS and copied over the EFI folder to the hard drives EFI partition that you randomise your UUID and serial number. You should also be able to remove `-v` from the boot args if it is booting stable.

### You may run into other issues, you use this efi folder on your system at your own risk
