*Working draft*

# Definition

*Some sections of the Lean Canvas.*

## Problems
1. Non-sandardized way of sharing devices between systems
2. Device quality in trading
3. Environmental and legal compliance

## Solutions
1. Global product passport
2. Store standardized device quality report

## Unique value propostiion
1. Blockchain as trusted proof of record
2. Standardzied open-source system

# Actors
*Users of the system / stakeholders*

1. (Re)seller.
2. Owner.
3. (Re)manufacturer.
4. Government.
5. Researcher.

# Non-functional requirements
*General things to consider that affect the project, usually imposed by actors in order to user the system, or something specially appealing.*

- Privacy. Re (manufacturers) and resellers don't want competitors to know the devices they interact with. **what else?**
- Trust?

# Use cases per actor
*An use case is like an objective. It answers the question of "what does X actor want to do with the system?" It is better to add more use-cases and postpone their development later.*

1. (Re)seller
	1. Know the legal status of a device in order to buy it. This does not mean that the reseller wants to know fi a device is disposed but that *everything is correct*. We have to **define legal values.**
	2. Know the quality of the device in order to buy it. We have to **define quality values**.
	3. Check if components of the device are the original ones in order to buy it, or after receiving the device from a customer. **Who is introducing such info?**
	4. Automatically introduce device information from the refurbisher / manufacturer in their system.
	5. Check authenticity of a device.
2. Owner
	1. Check authenticity of their device.
	2. Check data-wiping status after using a data-wiping service.
	3. Prove ownership.
3. (Re)manufacturer
	1. Share information that reseller wants to see.
	2. Share information that owners wants to see.
	3. Check repair history.
4. Government
	1. Check chain of custody of devices, specially disposition information.
5. Researcher
	1. Access aggregated data. **how this data must be to be useful for the researcher?**

*From the use cases above we need to specify how they can accomplish the task (for example, which actions they should to to the system or who should upload the required info); when they want to do this (in which part of their process). For some, even the why can provide more context.*

To achieve the use cases we need to identify devices at component level and be able to communicate with the actor's existing systems. To be able to communicate we need to "talk the same language" (i.e. defining a OBADA common schema). 

From these requirements and use-cases we should be able to understand the system decisions we take, for example, **why** a public, semi-public, private blockchain.

In the following sub-sections we define each use-case in more detail.

## 1.1 Reseller: Know the legal status of a device
Things to consider:
- Disposition status
- Has the device been stolen
- Is the device locked by a carrier
- If the device has been disposed.

## 1.2 Quality of a device
*Define list of quality values (eReuse is working on it)*

...

# The Schema
Links:

- [Devicehub's device schema](http://devicehub.ereuse.org/devices.html)

## Device identifiers
- Mobile: IMEI as SN
- Networking: Mac as SN
- Telecom: CLEI codes (any page to reffer to? See CTIA)

