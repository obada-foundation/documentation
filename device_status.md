## Need a minimum List of statuses for device_statusID

Device Status:  i.e. new, refurbished, stolen, disposed.

Many naming conventions exist for labeling "device statuses" and not all product categories have the same needs.   For example cell phones may have a status of "locked" but power supplies probably will not.  So the granular data sets provided by the existing conventions comes in multiple formats without consistent labeling.

Researchers need a way to analyze reuse and recyling rates, authorities need to be able to analyze for compliance, and users need to check if a device is stolen or has been disposed (like a car title marked "salvage") before they buy it.  

OBADA supports any data format for recording device status, as long as a "link" to the standard is added.   


standards will require "translation/lookup tables" making it difficult at best.But 


To enable basic research and compliance, OBADA proposes a separate field reporting the most basic status information to allow a researcher/authority/user to determine the status of any device without revealing any detailed device or a identifying the owner or transfer history.

This also enables protocol rules and smart contracts to be written acting on a device status.   For example allowing no further trades of devices marked "stolen" should be impossible to trade.

So a short list of simple keywords to communicate the most basic details is proposed.  Short because they must generalize (and be translatable) from the more granular statuses provided by standards.   Simple because they should be as unchanging as possible.  "Disposed" will still be "disposed" in ten years.

* Proposed List
1. new 
2. used
3. refurbished
4. disposed
5. stolen
6. etc..  (please update/add to this)

To be discussed: Possible that only a specific authority could set (or maybe just sign) a device status.  For example anyone could mark a device "disposed" but a signature from an authority could be added to validate it was "disposed properly".
