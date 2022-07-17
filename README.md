# x1c7-hackintosh
The EFI folder for a Lenovo Thinkpad X1 Carbon 7th gen (20R1)

Different macOS versions supported:

  * Ventura
  * Monterey
  * Big Sur
  * Catalina
  * Mojave
  * High Sierra
  
## Setup
First, download the github repository by either cloning it or just downloading the entire thing as a zip file.

Second, we need to download the wifi kext, so open [this website](https://github.com/OpenIntelWireless/itlwm/releases/latest) and download the correct version of the macos you want to run. Do not download the plain itlwm file.

Select the os version you want to download, and it will produce a zip file. Go into that zip file and extract the `AirportItlwm.kext` file. If you are on Windows or Linux it will look like a folder. Now move that new file/folder into the `EFI/OC/Kexts` folder from this github repo. You can now follow these instructions to figure out how to download the macos installer, and where to place the EFI folder. Do not use the efi folder they provide, use the one from here instead.
