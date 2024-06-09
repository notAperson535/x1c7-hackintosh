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

Select the os version you want to download, and it will produce a zip file. Go into that zip file and extract the `AirportItlwm.kext` file. If you are on Windows or Linux it will look like a folder. Now move that new file/folder into the `EFI/OC/Kexts` folder from this github repo. 

Next, download [this utility](https://github.com/corpnewt/GenSMBIOS), and open it. Next, select Option 3 and type in `MacBookPro15,4` as the SMBIOS. The ouput of mine looked like this:

```
  #######################################################
 #            MacBookPro15,4 SMBIOS Info               #
#######################################################

Type:         MacBookPro16,3
Serial:       FVFYD0SHL40Y
Board Serial: FVF9101024N0000FB
SmUUID:       F6C6F37B-F6BF-4E75-BAF5-D37D70B374B8
Apple ROM:    D89E3FF879C0

```

Now add the values to the `config.plist` file found in the `EFI/OC` directory (you can use [propertree](https://github.com/corpnewt/ProperTree) if you like), using the chart below

| GenSMBIOS Value | config.plist       |
| --------------- | ------------------ | 
| Type            | SystemProductName  | 
| Serial          | SystemSerialNumber |
| Board Serial    | MLB                |
| SmUUID          | SystemUUID         |
| Apple ROM       | ROM                |

The `config.plist` should now look something like this, there may be some other values, just ignore them:

```
    <key>MLB</key>
    <string>FVF9101024N0000FB</string>
    <key>ROM</key>
    <data>D89E3FF879C0</data>
    <key>SpoofVendor</key>
    <true/>
    <key>SystemProductName</key>
    <string>MacBookPro16,3</string>
    <key>SystemSerialNumber</key>
    <string>FVFYD0SHL40Y</string>
    <key>SystemUUID</key>
    <string>F6C6F37B-F6BF-4E75-BAF5-D37D70B374B8</string>
```

You can now follow [these instructions](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer) to figure out how to make the installer USB. Do not use the EFI folder they provide, use the one from here instead.
