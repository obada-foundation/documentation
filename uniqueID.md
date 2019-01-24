# Creating a deviceID and a unique deviceID


There is no standard way to create a unique ID (from a database perspective) for an electronic device.   Serial numbers can't be used because they aren't unique across manufacturers.  To create a unique database ID, a common pratice of inventory management systems for IT resellers is to concatenate the product's manufacturer, part(model), and serial number.

For example "APPLE-A1822-WG09HWX88E"

**10/9/19 At WG tech call we agreed to this approach.**

## Hash / Encryption

This information needs to be hashed/encrypted, with only the *hash* being stored on-chain.   Any person with knowledge of the device details (serial number etc) could easily identify it's associated blockchain asset token by following the protocol.

**1/09/19:  In the tech discussion at end of working group call we agreed to use SHA-256.** 

## Standardized data keys

For this data to be interoperable, common terms for "product type" and "manufacturer name" must be used.  We propose these standard terms.

**Dec 18: At WG group we agreed to use this list for now (in absence of any other)
**Jan 19: On standards call it was suggested we use a numbered list.   To be discussed at RLA conf.


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






