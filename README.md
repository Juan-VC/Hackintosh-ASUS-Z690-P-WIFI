Alder Lake Hackintosh!

Specs:

Motherboard: ASUS PRIME Z690-P WIFI

Processor: Intel Core i7-12700K

GPU: MSI AMD RX 6600 XT MECH 2X -> Intel's 12th gen iGPU is not supported as there are no real Macs with any Alder Lake CPU hence no iGPU drivers. Some Navi 2 GPU drivers were added on macOS 11.4 like RX 6800, RX 6800 XT, RX 6900 XT while for RX 6600 and RX 6600 XT drivers were added on macOS 12.1, thus minimum install version for this setup

SSDs: 2x WD_BLACK SN850 1TB

RAM: 2x Kingston Fury Beast 16GB DDR5 5200 MHz

WIFI + BT: Fenvi T919 -> Packs a BCM94360CD which is natively supported (the chipset is used in real Macs) for seamlessly support

What works?
- Everything I can think of (Wifi + BT + sleep + DRM content + Apple services + jack audio + DP/HDMI audio, etc) except digital on-board audio output (custom AppleALC codec layout id is needed for this) -> ALC 897

Short-guide (for experimented users):

0. Boot into UEFI and load default (or optimized settings as it is shown) then move to step 1
1. diskutil list
2. diskutil partitionDisk /dev/disk# GPT JHFS+ "USB" 100%
3. sudo "/Applications/Install macOS Monterey.app/Contents/Resources/createinstallmedia" --volume /Volumes/USB
4. Copy EFI folder to the EFI partition from the USB
5. Create a boot-entry that points to OpenCore.efi -> This can be achieved for using Hasleo EasyUEFI
6. In OpenCore menu press space bar, scroll & open CFGLock.efi tool
7. It will find the CFGLock variable offset, accept to toggle its value to turn it off as it cannot be changed from the firmware settings
8. Boot the installer and proceed normally
9. When you finally boot macOS make sure to setup configure correctly the unique values each mac comes to access Apple services like AppStore, FaceTime, iMessage, etc -> This is usually found on the internet like "hackintosh fix apple services" or similar
10. Enjoy macOS on non-Apple hardware :)
