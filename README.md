USBCDCEthernet
==============

DEPRECATED: Solved by Infineon ->
https://community.infineon.com/t5/USB-superspeed-peripherals/EZ-USB-GX3-CYUSB3610-M1-Mac-Drivers/m-p/360709#M31543

WIP: The CYUSB3610 internals have not been inserted into the `init` and `start` driver methods yet.
This project is the scaffolding starting from a working kext for another hardware on top of 
the Apple USBCDCEthernet example.

This implements a driver for the USB-Ethernet adapter based on EZ-USB GX3 / CYUSB3610 on macOS 12+ M1, such as CalDigit's `USB-C Dock` ethernet:

```
 Product ID:    0x3610
  Vendor ID:    0x04b4  (Cypress Semiconductor)
```

Why does this project exist?
----------------------------

The official driver does not exist for macOS 12+ on M1 and there does not appear to be a date for delivery:
https://community.infineon.com/t5/USB-superspeed-peripherals/EZ-USB-GX3-CYUSB3610-M1-Mac-Drivers/m-p/281767

The linux 

How do I install it?
--------------------

- Download the source here from Github and compile it with XCode
- Determine the path of the built kext and copy it to the `/Library/Extension` directory.
```bash
ls ~/Library/Developer/Xcode/DerivedData/USBCDCEthernet-*/Build/Products/Debug/USBCDCEthernet.kext
# remove extras
sudo cp -rf ~/Library/Developer/Xcode/DerivedData/USBCDCEthernet-*/Build/Products/Debug/USBCDCEthernet.kext /Library/Extensions/
```

- Change the user permissions on the extension.
```bash
sudo chown -R root:wheel /Library/Extensions/USBCDCEthernet.kext
sudo chmod -R 755 /Library/Extensions/USBCDCEthernet.kext
```

- Load the extension
```bash
sudo kextload /Library/Extensions/USBCDCEthernet.kext
```


Thanks and Acknowledgements
---------------------------

- Driver Davicom from Haiku project.
- Based on USBCDCEthernet example from IOUSBFamily-560.4.2.
- samuelv0304 https://github.com/samuelv0304/USBCDCEthernet
- jayluxferro https://github.com/jayluxferro/USBCDCEthernet

License
-------

This code is licensed under Apple Public Source License. See LICENSE for more details.

