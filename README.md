# Opencore 0.6.1 EFI for the Lenovo ThinkPad E580
Tested on 20KSA00SAU model with macOS Catalina (10.15.6)

## Disclaimer

As you may already know, swapping out hardware (in the case of the E580, the NVMe drive and the WiFi card) in order to use macOS will void your warranty, it is a safe assumption that most E580s out there are still in warranty now as it isnt that old of a laptop

Also worth noting this EFI might not work as well for you as it did for me. You may need to change some things along the way so it is worth brushing up on Opencore knowledge. The best place for this would be in Dortanias Opencore install guide linked below under Install.

Although unlikely to happen, it is not my fault if this somehow fucks up your hardware.

### Specs
* **CPU**: Intel Core i5-8250U 1.6 GHz
* **RAM**: 16 GB (2 x 8 GB) DDR4-2400
* **SSD**: Western Digital Blue NVMe SSD 250GB
* **GPU**: Intel UHD 620 Graphics
* **WiFi**: Dell Wireless 1560
* **Display**: 15.6" FHD IPS 1920x1080

### BIOS Settings
* I used BIOS version 1.40, it may work on lower versions too
* Disable VT-d
* Enable Intel Virtualisation
* Disable Secure Boot

### What hardware doesnt work?
1. Line/Mic Input (3,5")
2. Card reader
3. Cant use more than 3 fingers on the trackpad at once
4. Samsung PM981 NVMe SSD
5. The Realtek wifi card some models of this laptop come with
6. FN keys do not work for their normal use (volume, brightness, etc..) after sleep, this is a common issue with 80/90 series thinkpads like this one

### WiFi

The specfic model E580 i got came with the RTL8822BE wifi card, this is not compatible under macOS in any circumstance, other models of the E580 come with the Intel AC3165 which will work (although not well at the moment) with the itlwm kext and the heliport application. I swapped my wifi card out for a DW1560 and this config comes with the required kexts to make that work.

### The Stock NVMe SSD

If you purchased the model E580 with the m.2 NVMe drive, you will need to swap it out for another NVMe drive or put a sata ssd into the sata slot in the laptop. the PM981 will cause kernel panics when trying to install to it, format it, clone os and resize it, etc...

The m.2 slot will not accept a sata m.2 ssd, it will only accept NVMe ssds, i found this out the hard way.

### FN Key Actions

This config includes the required SSDT in order to use the FN key actions as they normally would work under windows, settings button, mic mute, etc...

All you need to do after installing macOS is install the ThinkpadAssistant program which can be found at: https://github.com/MSzturc/ThinkpadAssistant

This however falls fate of the FN key issue on 80/90 series thinkpads, see hardware issue no. 6 above

### Install

https://dortania.github.io/OpenCore-Install-Guide/installer-guide/

follow this guide through making the macos installer itself, up to the point where you add the base opencore files, instead of adding them just add the EFI folder from this repo into your installer usbs EFI partition.

### Post-Install

I recommend once you have installed macOS and copied over the EFI folder to the hard drives EFI partition that you randomise your UUID and serial number. You should also be able to remove `-v` from the boot args if it is booting stable.
