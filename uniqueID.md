# Creating a deviceID and a unique deviceID

## Device ID Format

There is no standard way to uniquely identify most electronic devices types. One approach is to concatenate the following fields as shown to give us a unique identifier.

**product\_type-manufacturer-part(model)**

- product type: desktop
- manufacturer: asustek\_computer\_inc
- part/model: 1000h

**Example:** desktop\_computer-asustek\_computer\_inc-1000h-94oaaq021116

## Unique Device ID

Add a serial_number (or IMEI in the case of mobile devices) to the end of the deviceID to generate a unique ID for a specific device.

**Example** product\_type-manufacturer-part(model)\_number-serial=- serialnumber: 94oaaq021116

## Hash / Encryption

This information needs to be hashed/encrypted, with only the *hash* being stored on-chain.   Any person with knowledge of the device details (serial number etc) could easily identify it's associated blockchain asset token by following the protocol.

A standard hash/encryption methodology needs to be defined.  (sha512?)

## Standardized data keys

For this data to be interoperable, common terms for "product type" and "manufacturer name" must be used.  We propose these standard terms.

Or perhaps a numbered list would be better to avoid any concerns over naming

**Product Types**
- computer_accessory
- computer_part
- consumer_electronics
- desktop_computer
- display
- laptop
- laptop_part
- mobile_device
- networking_device
- printer
- scrap
- storage_device

**Manufacturer Names**
- apple
- cisco
- dell
- fujitsu
- hp
- ibm
- intel
- lenovo
- oracle
- samsung
- toshiba

These list will be extended as needed.






