# **Homelab Hardware**

## Server Buying Advice

## Preface
This has been updated for 2020 by /u/EmpathicOx56099, if there is information that isn't accurate, feel free to update accordingly. You might be tempted to go out and buy the first thing you see on Craigslist, Facebook Marketplace, or other local trading sites. Please don't be, oftentimes, the prices are inflated and not worth the hard-earned money you are spending. If you join the Discord server or spend some time in this subreddit, you might see an overwhelming influence to buy a **Rack Mounted** server. This is not always the best suggestion for you or your personal needs, so as you go through this hardware guide, keep your individual purpose in mind. 




---


# Rack Mounted

So you're looking for a Rack Mounted enterprise server, and you are wondering which one to get based on how much you want to spend, how much rack space you have, how loud it is, and how much power it will use. The below list is a **avoid at all costs list**

If you're looking for advice on the rack itself, see [this post](https://www.reddit.com/r/homelab/comments/15jz6mk/rack_mounting_tips_and_info_tutorial/)

**Gen 10**

- Dell 2900 or earlier
- HP DL380 G5
- Cisco UCS C210 M2

The below list is a **avoid as they suck power and you lose money long term list**

**Gen 11**

- Dell R710
- HP DL380 G6
- Cisco UCS M2


###General Pointers

Before diving into the specific make and models, here are some pointers for things to know in general.

**Which generation do I want?**
This is a common question in the Discord and among new HomeLabbers. Avoid HP servers prior to G7 and Dell servers prior to 12G (Rx20, e.g., R620, whereas the R710 are 11G) as they are loud, power-hungry, and not worth the investment to run. Although the costs might be higher to buy the gear, the long term impact will be more significant as the use and lifespan will last longer. If you can get an HP Gen9/10 or Dell 13/14G server, even better.

 **Power Consumption and Noise**
*It is worth noting again that rack mount hardware isn't for every homelab, especially if you are concerned with power consumption and noise.*
Although most newer servers are (mostly) quiet when idle, they can get rather loud at load. Every individual has different tolerances for noise, so a server that someone mentions to be "quiet" might not be quiet for you. Expect power consumption for the recommended servers to be about 100W - 140W idle (sitting at the desktop), and higher when at load. Older servers will consume upwards from 200W idle.



## **HP**

HP models prior to G8 have an issue with non-OEM drives. This causes what can be called thermal runaway and ramps the fans up to 90%, register inordinately high drive temperatures, and worse case shuts drives down during operation. In short, this is because the "Sea of Sensors" does not get a reading from sensor 29, or a bad reading at that. You can read more about it here, along with a list of known compatible and non-compatible drives:
[http://www.dascomputerconsultants.com/HPCompaqServerDrives.htm](http://www.dascomputerconsultants.com/HPCompaqServerDrives.htm)

#### **HP G6s**

It is extremely **ill-advised** to buy these. Yes, they are cheap, but they are also *very* loud and *very* old.

#### **HP DL360 G7 & DL380 G7**
These are the HP equivalent of the Dell R\*10 series. Expect these units to go cheaper but consume more power than newer generations. They have been known to idle between 120w (1CPU, 4x RAM sticks, & 2 SAS Drives), to 230W (2CPUs, 18 RAM sticks, 4x SAS Drives), though these figures have not been verified.

[Here](https://imgur.com/a/tLZZu4E) you can see the power usage for a 2CPU E5630, 18 RAM Sticks, 1x SAS Drive configuration, using 125w.

#### **HP DL360 G8 & DL380 G8**
These are the best bet for HP servers as the price point in the US is currently sitting around the $200 mark. They are an upgrade to the G7s without jumping to DDR4 and the higher price point in RAM and replacement parts. The DL360e/DL380e G8 have 12 DIMM slots (6 slots and 3 channels per CPU/socket, 2 DIMMs per channel) that can hold up to 192GB Registered (RDIMM) or 384GB Load Reduced (LRDIMM) DDR3 memory, and uses the E5-2400 and E5-2400 v2 processor families. The DL360p/DL380p G8 have 24 DIMM slots (12 slots and 4 channels per CPU/socket, 3 DIMMs per channel) that can hold up to 384GB Registered (RDIMM) or 768GB Load Reduced (LRDIMM) DDR3 memory and uses the E5-2600 and E5-2600 v2 processor families.
The e-models shipped with one of three controllers, the B120i 3Gb/s 6-port SATA controller, the B320i/512MB (6G/s 8-port SATA/SAS that depending server sku ither require license key to use SAS drives or already have it) or the P420/1GB(or 2GB on the SFF storage model).
The p-models all come with a P420i but depending on model ither with no FBWC ( Flash  Backed  Write  Cache) only capable of RAID 0/1/1+0 or with a 1GB or 2GB FBWC module capable of RAID 0/1/1+0/5/5+0/6/6+0. The memory/cache module is exchangeable so any P420i can be upgraded/downgraded by adding/changing/removing it.
- [DL360e Gen8 QuickSpecs](https://www.hpe.com/psnow/doc/c04123219.pdf)
- [DL380e Gen8 QuickSpecs](https://www.hpe.com/psnow/doc/c04128166.pdf)
- [DL360p Gen8 QuickSpecs](https://www.hpe.com/psnow/doc/c04128242.pdf)
- [DL380p Gen8 QuickSpecs](https://www.hpe.com/psnow/doc/c04123238.pdf)

#### **HP DL360 G9 & DL380 G9**
Welcome to the first HP generation that uses DDR4. They use Intel Xeon E5-2600v3/v4 processors and 24 DIMM slots (12 slots, 4 channels per CPU, 3 DIMMs per channel) that can hold up to 768GB RAM with RDIMMs or 3TB RAM with LRDIMM (and the right CPUs, 1.5TB with regular v3/v4). Also capable of up to 128GB of NVDIMM (16 x 8GB) with v4 CPUs. They come with ither just the B140i onboard UEFI only SATA controller or most commonly the P440ar and some times P840.
NOTE: the B140i will NOT operate in Legacy mode.
- [DL360 Gen9 QuickSpecs](https://www.hpe.com/psnow/doc/c04346229.pdf)
- [DL380 Gen9 QuickSpecs](https://www.hpe.com/psnow/doc/c04346247.pdf)

##### **HP RAID Controllers**
More recent HP's will come with a P410i, but it is important to find out which controller your system has.
Some servers ship with a BBWC (battery-backed write cache) and some will ship with an FBWC (flash-backed write cache). 

As the name implies, a BBWC uses a battery and some DRAM chips to cache information for faster performance.
A downside to this technology is that the system won't be able to flush its write cache when the battery is dead.
You need to replace the battery when it dies. The FBWC uses an NVRAM / flash memory chip (kind of like in SSDs) to cache data and can store data until power is restored in the event of a power failure. The FBWC does not require a change of batteries because it does not use any.




## **Dell**
Have a look at this page to see a detailed list of Dell server specs : [Dell](https://www.reddit.com/r/homelab/wiki/dell)

#### **Gen 11- Dell R*10s**
Unfortunately, despite the length of service, the R710 has begun to show it's age and has joined the **do not buy list**. 

#### **Gen 12- Dell R*20s**
In the US and UK, 12th gen Dells are becoming the server de facto and an appealing choice. They are currently sitting at the sweet spot for price VS performance.

[Here](https://imgur.com/a/EFFXSWS) you can see the 154w power usage of an R720 (2x E5-2665, 12x DDR3 1333MHz 16GB sticks, 3x 15k SAS drives, 1x Intel X520 10GB Nic) running 10x VMs in VMWare ESXi. 

#### **Gen 13- Dell R*30s**
 This is the first-gen of Dells that use DDR4 and the best bet to choose if you want to invest in gear long term. Through searching and scavenging, some R430s can be had for as little as $250 in the US.

#### **Gen 14- Dell R*40s**
These are newer on the scene as the price point is still very high, but worth it if you can get a decent deal on them.


##### **Dell RAID Controllers**
Lots of the *older* Dell servers still have Perc6/i Raid cards in them. These cards will not be able to use a drive over 2TB, and Dell has no plans of ever updating the firmware to support the larger drives we want to use. If your server comes with a Perc6/i and you want to use larger drives, then you will need to upgrade it to a newer card. The two most popular options, if you want to stay with Dell, are the H200 or the H700.

Card | RAID Modes | BBWC | JBOD
---|---|---|---
H200 | 0, 1, 10 | No | Yes
H700 | 0, 1, 5, 6, 10, 50, 60 | Yes | No


Newer RAID cards are updated per generation. 

- R*20s have H310/H710/H710P
- R*30s have H330/H730/H730mm 

More information can be found on the [Dell Website](https://www.dell.com/learn/us/en/04/campaigns/dell-raid-controllers)

##### **Rebranded / OEM Dell Hardware**
You can often find Dell hardware that has been customized by other brands. Often these can be flashed back to stock Dell firmware, and the only real difference is the front cover. Most of these are outdated and run on gear that isn't on suggested gear. Items that are *italicized* are not suggested any more.

Brand| Model | Original Dell Model
---|---|----
Google | Search Appliance G100 T4 | R720xd
Google | Search Appliance T5 | R730xd 
*No* | *Longer* | *Suggested*
Cisco | *IronPort S370* | R710
Cisco | *IronPort C370*  | R710
Cisco | *IronPort M670* | R710
Cisco | *IronPort S670* | R710
EMC | *RecoverPoint Gen4* | R610
EMC | *Avamar ADS Gen3* | R710
Google | *Search Appliance GB-7007* | R710
IBM | *Infosphere Guardium* | R610
McAfee | *FW1100-F* | R610
McAfee | *WG5500* | R710
Riverbed | *Steelhead EX 560* | R210ii
ShoreTel | *Service Appliance 100* | R210ii
Websense | *V5000 G2* | R210ii

##### **DSU and Firmware**

Dell Firmware can be upgraded with the DSU, and you can either use the prebuilt CentOS live CD for your model at this link https://dell.app.box.com/v/BootableR710 (Replace the R710 with whatever model you have) or download a copy of CentOS 7 and run this script.

    curl -s http://linux.dell.com/repo/hardware/dsu/bootstrap.cgi | bash

You may also need to run an update and install it after importing the repository.

    yum update

    yum install dell-system-update    

Details and commands for the DSU can be found on the help docs at [Dells website](https://linux.dell.com/repo/hardware/dsu/) and if you experience issues with the prebuilt image check this [blog post](https://nullpointer.io/post/dell-deployment-bundle-error/) for more information



## **Cisco**
Cisco's are not as common to find in the HomeLab space as they are a little more expensive and harder to source secondhand.

#### **Cisco UCS C** M3**
Comparable to the Dell R720 and HP G8

#### **Cisco UCS C** M4**
Comparable to the Dell R730 and HP G9

#### **Cisco UCS C** M5**
Comparable to the Dell R740 and HP G10 




## **Supermicro**
This Supermicro guide was put together by /u/HittingSmoke and updated by /u/Stephonovich.

##### **Supermicro Motherboards**

The first letter designates the CPU type - X for Xeon, H for AMD.
The number following the letter designates the CPU generation. 
For AMD, 8 = Opteron (please don't do this to yourself), 11 = 1st gen EPYC, 12 = 2nd gen EPYC.
For Intel, the minimum you should be looking for is 9, which is the v1/v2 (Sandy Bridge/Ivy Bridge) generation.
10 is v3/v4 (Haswell/Broadwell), 11 is v5/v6 (Skylake/Kaby Lake) AKA 11th gen Xeon Scalable,
and 12 is 12th gen Xeon Scalable.

The next letter will be either `S`, `D`, or `Q` for **S**ingle-CPU, **D**ual-CPU, **Q**uad-CPU.
I'm assuming in /r/homelab we all want the D ;)

The next letter is the socket and/or board type. For AMD, this should be `S` for EPYC.
For Intel, it's a little more complicated. For single-socket, it's simply the socket type, and will match the CPU generation,
so you don't need to worry about it. For dual (and I assume quad) socket, an `A`, `D`, `G`, or `S` in this position
indicates the board type (Workstation, Datacenter-optimized, GPU-optimized, Storage-optimized), 
which may have features beneficial for that role. `B`, `R`, and `P` indicate the socket type.
You'll probably be looking at `R` boards, for LGA2011.

The 5th position can be more or less ignored, with the exception of `L` ("Low cost" - stripped of features) 
and `i`/`E` (SATA controller). Note that `LN` with a digit indicates multiple NICs (see table below), and not 
that it's a Low Cost board with NVMe support.

The 6th position is where the rest of the differentiation comes in, and some common ones are listed below.
`L` makes an appearance here again, for "Low Cost SKU."

* `L` = "Low Cost" models that skimp on features.
* `3` = SAS + SATA - Usually, 8x SAS via 2x 8087 from what I've seen.
* `6` or `7`= SAS2 and SAS2 6GB/s, respectively.
* `F` = IPMI support.
* `LN4` = 4x GBe ports. Make a special note of this one because `L` and `N` can be used individually as well.
* `LN6` = 6x GBe ports.
* `M25` = 25G SFP+ port.
* `N` = NVMe support - note that some boards (e.g. `X11SSH-F`) may have an M.2 slot even without this character.
* `S` = either "Cost Optimized" for single-socket Intel boards, or "Super I/O Module" for dual-socket Intel and all AMD boards.
* `T` = 10GBe port.
* `T4` = 4x 10GBe ports.
* `TP` = 10G SFP+ port.
* `TF` = 40G SFP+ port.
* `+` = Extra RAM support. In the case of the X9DR3, that's 24 sticks.
* `-O` and `-B` suffixes just mean retail or bulk.

The hyphen placement seems arbitrary from model to model. Most have the i/E/3/7 before the hyphen. L's have them after.
Those are the most important. Some models are more prevalent than others. `X9DR3-LN4F+` is the common one that has 8 SAS, 6 SATA, 24 DIMM slots for a maximum of 1.5TB of RAM, 4x ethernet ports, and IPMI. The `X9DR3-F` is the same thing with 16 DIMM slots and half the ethernet ports. If you punch `X9DR` into eBay and sort by motherboards, you'll get the results you're looking for. Add `3`, `7`, `i,` or `E` to start narrowing your search based on the type of storage controller you want.

##### **Supermicro Chassis**

| Chassis Model   | Backplane Model | Form Factor | Expander | Backplane Connector | >2TB Drives | Bandwidth | Power Supply  | Redundant | In Production |
|-----------------|-----------------|-------------|----------|---------------------|-------------|-----------|---------------|-----------|---------------|
| SC846E1-R710B   | BPN-SAS-846EL1  | 4U          | Single   | (1) SFF-8087        | No          | 3Gbps     | 710w DC       | Yes (2)   | No            |
| SC846E1-R900B   | BPN-SAS-846EL1  | 4U          | Single   | (1) SFF-8087        | No          | 3Gbps     | 900w          | Yes (2)   | No            |
| SC846E1-R1200B  | BPN-SAS-846EL1  | 4U          | Single   | (1) SFF-8087        | No          | 3Gbps     | 1200w Gold    | Yes (2)   | No            |
| SC846E2-R900B   | BPN-SAS-846EL2  | 4U          | Dual     | (2) SFF-8087        | No          | 3Gbps     | 900w          | Yes (2)   | No            | 
| SC846A-R920B    | BPN-SAS-846A    | 4U          | None     | (6) SFF-8087        | Yes         | 6Gbps     | 920w Platinum | Yes (2)   | No            |
| SC846E16-R1200B | BPN-SAS2-846EL1 | 4U          | Single   | (1) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |
| SC846E26-R1200B | BPN-SAS2-846EL2 | 4U          | Dual     | (1) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           | 
| SC846A-R900B    | BPN-SAS-846A    | 4U          | None     | (6) SFF-8087        | Yes         | 6Gbps     | 900w          | Yes (2)   | Yes           |
| SC846A-R1200B   | BPN-SAS-846A    | 4U          | None     | (6) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |
| SC846TQ-R900B   | BPN-SAS-846TQ   | 4U          | None     | (24) SAS2/SATAIII   | Yes         | 6Gbps     | 900w          | Yes (2)   | No           |
| SC846TQ-R1200B  | BPN-SAS-846TQ   | 4U          | None     | (24) SAS2/SATAIII   | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |

**A note on the Chassis with dual expanders:** Only 1 SFF-8087 connector is required to access all 24 drives. The 2nd SFF-8087 is optional and intended for failover with a secondary HBA.

**A note on the 846E1 and 846E16:** These are the two most commonly found models on eBay. The 846E1 is SAS1, and the 846E16 is SAS2. Often the 846E16 will be listed as 846EL1, which makes the listing look like it's selling the SAS1 version. 846EL1 actually refers to the backplane part number, and the sellers often get them mixed up. So pay close attention to the details and ask the seller questions if you are unsure! Shipping these things cost a fortune, so you don't want to order the wrong one.

## **Lenovo**
While not as popular as some of the other manufacturers, Lenovo servers are becoming more prevalent on the used market as hyperscalers (CSPs, HPC, etc.) begin to refresh their fleet.  Lenovo has 3 "families" of servers

- System x - Acquired from IBM; Grantley platform and older
- ThinkServer - Lenovo design; Grantley platform and older
- ThinkSystem Server - Lenovo design; Purley platform and newer

with the System x servers being the most plentiful on the used market.

All Lenovo servers include an IPMI-compliant BMC -- Integrated Management Module (IMM) in System x, ThinkServer System Manager (TSM) in ThinkServer, and XClarity Controller (XCC) in ThinkSystem.

One advantage of buying Lenovo servers is the availability of firmware updates.  You do not need a current support contract to access the [Lenovo Support website](https://support.lenovo.com/us/en/).  You can use Lenovo utilities such as [Bootable Media Creator](https://datacentersupport.lenovo.com/us/en/solutions/lnvo-bomc) to acquire/download the firmware updates and create a bootable ISO or USB key or [OneCLI](https://datacentersupport.lenovo.com/us/en/solutions/LNVO-TCLI) to script the acquisition / installation of firmware updates, configure UEFI settings, or configure the BMC settings.

Lenovo also has abundant information available in the [Lenovo Press](https://lenovopress.lenovo.com/).

#### **System x3550M5 and System x3650M5**
The System x3550M5 and System x3650M5 servers are 1U and 2U, respectively, supporting up to 2x Grantley processors.  Machine Types (MT) 5463 and 5462 originally shipped with Haswell processors, while the MT 8869 and 8871 originally shipped with Boradwell processors.  The x3550M5 supports either 4x 3.5" or up to 10x 2.5" SAS/SATA drives, while the x3650M6 supports either up to 12x 3.5" or up to 24x 2.5" SAS/SATA drives.

#### **ThinkServer RD550 and RD650**
The ThinkServer RD550 and RD650 servers are 1U and 2U, respectively, supporting up to 2x Grantley processors.  The RD550 supports either 4x 3.5" or up to 10x 2.5" SAS/SATA drives, while the RD650 supports either up to 12x 3.5" or up to 24x 2.5" SAS/SATA drives.

#### **ThinkSystem Server SR630 and SR650**
The ThinkSystem SR630 and SR650 servers are 1U and 2U, respectively, supporting up to 2x Purley processors.  The RD550 supports either 4x 3.5" or up to 10x 2.5" SAS/SATA/NVMe drives, while the RD650 supports either up to 12x 3.5" or up to 24x 2.5" SAS/SATA/NVMe drives.


---


#**Tower Servers**

## **HP Microserver**
HP also has a Line of Microservers that are small 4 Bay SATA servers and work great as a first box.
Most people use them to make a home NAS (using something such as FreeNAS) or for virtualization (although virtualization will require slightly more than the base spec to be effective).  

As for which version of the ProLiant Microserver series you want to buy, if you are only going to run it as a NAS for your network, then you can go for some of the older versions all the way back to the N40L.
But considering the price of the Gen8 ones at the moment, there is no real reason for not getting a Gen8 for your network.
At the time of writing, in the UK, these can be bought for £116 after cashback deals (Update: 17/01/2017, the average price is now upwards from £180, but cashback deals are stick common).

The Microservers do contain an onboard USB port, which makes them ideal for using an OS that can run from a flash memory stick (e.g., FreeNAS or ESXi), which will allow you to maximize your Disk space. 

If you need something a little bigger than the Microservers, but still don't want a Rack Mounted Device, one of the more popular "Tower" style servers from HP is the ML10.
The ML10 can be picked up from eBay for around the £250 mark and have 6x3.5" drive bays, so can do more storage than the Microservers.
In some countries, they are cheaper and much more readily available than the Microservers mentioned above.


## **Dell Towers**
If you are wanting to stay with the Dell infrastructure but don't want the hassle of Rack Mounted gear, look at the T*** versions. T620s and T630s are common for tower suggestions. But looking at a T140 for a smaller footprint is also an option.




---


# **Blade Chassis**
Being that blades can be entirely different monsters with their own nuances, they are separated. This has also not been updated by /u/EmpathicOx56099

## **Blade basics**
**Who?**
We're gonna give it to you straight -- blade systems are not for the faint of heart. They are big, heavy, loud, and can consume more power than regular systems. Why would you want to run them then?

For starters, you get that "cool" factor that you don't get from your average server buy/build (this is 110% subjective).
Second, the cost savings can be considerable.
Take, for example, the Dell R610 vs. its M610 blade cousin; at the time of this writing, the R610 (decently-equipped) can easily run you between ??? - ??? and even the barebones systems are around ??? or more.
A similarly-equipped M610 will be less than ??? (barebones w/heatsinks can be regularly picked up for /ea + shipping).

> Note: Because prices aren't listed for R610 vs. M610, I just looked, and the M610 is generally about 25% cheaper than the R610.

**What's an IOM?**
IOMs (short for I/O Modules) are what give the blades their network connectivity - whether it be Ethernet, InfiniBand or Fibre Channel.
They connect through the midplane to the blades.
Think of an IOM as a regular switch, the midplane as the cable, and the mezzanine card in the blade as the NIC.

**Mezza-what?**
Mezzanine cards are special NIC or HCA cards that connect the blades to the midplane (and ultimately the IOM on the other side).
These essentially replace the mainstream PCIe slots in the traditional sense of rackmount servers.
Except in a couple of edge cases, you **cannot** use any old PCIe card in a blade.


#### **HP C7000 and C3000**
The C7000 is a full-sized enclosure capable of hosting eight full-height blades or 16 half-height blades.
There is also a C3000, basically a half-sized C7000, capable of holding four full height or eight half-height blades.
Both of these enclosures have a large compatibility list, and if you get hold of one of these enclosures, you can have a mix of several different blades of virtually all generations (from G1 to G9).
You could, for example, mix a few x64 class Intel blades with some Itanium blades (e.g., BL860c) if you feel like dipping your toes in doomed architectures for some crazy reason.
[A brief list](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=mmr_kc-0100204-12) of compatible blades and combinations can be found here.
The appropriate enclosure PDFs will also confirm blade compatibility.

Keep in mind that these enclosures require firmware on their own since they are operating pretty complex power, cooling, and back-plane management.
Updates may be subject to HPE's policy of putting these behind a subscription.
An example is some show-stopping firmware bugs that tripped up the ESXi Hyper-Visor has been come across in Production environments.
While this realistically won't become an issue for a Homelab, enclosures are another level of maintenance and potential problems that you need to keep in mind.
If you need a basic to even higher-end Homelab, these high end, power-dense, and very noisy enclosures probably are not for you.

#### **Dell M1000e**

    This section is under construction.


####**Servers**

**11G**

Model|Height|Sockets|Socket Type|RAM Slots|RAM Type|SFF Bays|Extras|Spec Sheet
------|--------|--------|-------------|-----------|-----------|----------|--------|------------
M610|Half|2|LGA1366|12|DDR3|2||
M610x|Full|2|LGA1366|12|DDR3|2|2 full-size PCIe x16 slots)|
M710|Full|2|LGA1366|18|DDR3|4||
M710HD|Half|2|LGA1366|18|DDR3|2||

**12G**

Model|Height|Sockets|Socket Type|RAM Slots|RAM Type|SFF Bays|Extras|Spec Sheet
------|--------|--------|-------------|-----------|-----------|----------|--------|------------
M620|Half|2|LGA2011|24|DDR3|2||[Link](https://i.dell.com/sites/content/shared-content/data-sheets/en/Documents/Dell-PowerEdge-M620-Spec-Sheet.pdf)

**13G**

Model|Height|Sockets|Socket Type|RAM Slots|RAM Type|SFF Bays|Extras|Spec Sheet
------|--------|--------|-------------|-----------|-----------|----------|--------|------------
M630|Half|2|LGA2011-3|24|DDR4|2|Optional 4x 1.8" bays|[Link](https://i.dell.com/sites/doccontent/shared-content/data-sheets/en/Documents/Dell-PowerEdge-M630-Spec-Sheet.pdf)

#####**IOMs**

**Passthrough**

* don't buy these; they're not worth it.

**Ethernet**

* M6220 (Gigabit, 16 internal, 4 external RJ45, 2 expansion slots)
* M6348 (Gigabit, 32 internal, 16 external RJ45, 2 external CX4 stacking, 2 external SFP+)
* M8024-k (10Gb, 16 internal, 4 external RJ45, 4 external SFP+, 1 expansion slot)

**Fibre Channel**

* M4424 (4Gb/2Gb, 16 internal, 8 external SFP)
* M5424 (8Gb/4Gb/2Gb, 16 internal, 8 external SFP)


---



# **Individual Hardware**
The sections below will be focused on comparing various related hardware.

# **CPUs**
## **Intel**

**Quick overview**

Code Name| Socket| Series| Memory| Sockets
---|---|----|----|----|----
Nehalem| 1156 | 3400/3600| DDR3| 1
Nehalem EP| 1366| 5500 | DDR3| 2
Westmere | 1156 | 3600| DDR3 |1
Westmere EP | 1366 | 5600| DDR3 | 2
Westmere EX | 1567 | E7-2800| DDR3 | 2
Westmere EX | 1567 | E7-4800| DDR3 | 4
Westmere EX | 1567 | E7-8800| DDR3 | 8
Sandy Bridge| 1155 | E3-1200| DDR3 | 1
Sandy Bridge EN | 1356| E5-1400| DDR3| 1
Sandy Bridge EN | 1356| E5-2400| DDR3| 2
Sandy Bridge EP| 2011| E5-1600 | DDR3| 1
Sandy Bridge EP| 2011| E5-2600 | DDR3| 2
Sandy Bridge EX| 2011| E5-4600 | DDR3| 4
Ivy Bridge| 1155| E3-1200v2| DDR3 |1
Ivy Bridge EN | 1356| E5-1400v2| DDR3 | 1
Ivy Bridge EN | 1356| E5-2400v2| DDR3 | 2
Ivy Bridge EP | 2011| E-1600v2| DDR3| 1
Ivy Bridge EP | 2011| E-2600v2| DDR3| 2
Ivy Bridge EP | 2011| E-4600v2| DDR3| 4
Haswell| 1150| E3-1200v3| DDR3| 1
Haswell EN| 1356-3| E5-1400v3| DDR3| 1
Haswell EN| 1356-3| E5-2400v3| DDR3| 2
Haswell EP| 2011-3| E5-1600v3| DDR4| 1
Haswell EP| 2011-3| E5-2600v3| DDR4| 2
Haswell EP| 2011-3| E5-4600v3| DDR4| 4

**LGA1366 (LGA1156/LGA1150)**

HP G5/6/7 servers and Dell 11G servers, ship with socket LGA1366 Xeon CPUs.
An exception to this is the Dell R210/R310, which ships with the LGA1156 and the R210 II, which ships with LGA1150.

LGA1366 take Xeon 35xx, 36xx, and E5xxx series CPUs.
LGA1156 take Xeon 34xx series CPUs.
LGA1150 take Xeon E3-12xx v3/v4 series CPUs.

Xeon 5500 series are based on Nehalem architecture (45nm) and are less efficient than Xeon 5600 series Westmere architecture (32nm).
Xeon 5600 series CPUs and above come with AES-NI, which is handy for offloading encryption to the CPU.

The 3 main variants for LGA1366/LGA1156 CPUs are as follows:

* `X` Performance
* `E` Mainstream
* `L` Low Power/High Efficiency

If the server has an Exxxx series of Xeon processors, it is useful to double-check its specifications on the [Intel ARK website](http://ark.intel.com).
There are a couple of versions of this CPU that have a smaller cache, only support slower RAM, and, most importantly, DO NOT have Hyper-Threading.

**LGA2011/LGA2011-3**

These are Intel's biggest, baddest CPUs.
Normally they are in servers manufactured in the last 4-6 years.
Most newer Dells (12/13G) and HPs (G8/G9) will have these CPUs.
Also, this range of CPUs is very versatile; you could quickly go from a 4-core baby to a 16-core beast by only changing your CPU.

Please note, LGA2011 and LGA2011-3 are **NOT** compatible.

LGA2011/LGA2011-3 CPUs have the naming scheme `Ex-yyyy Vz,` where `x = 3/5/7`, `y` is the product family, and `z` is the version number (for more info, visit [About Intel Processor Numbers](http://www.intel.co.uk/content/www/uk/en/processors/processor-numbers-data-center.html)).
LGA2011 is mostly compatible with Xeon `Ex-xxxx v1/v2` series CPUs, and LGA2011-3 is mostly compatible with `Ex-xxxx v3/4` series CPUs.
However, if you're not sure, always double-check.

* `E3` Basic CPU (the baby of the family), most are under 8 cores and have only 1s scalability (more on that later).
* `E5` A step up from `E3`s, and where it starts to get a little more intense (the bigger brother). Most are 8+ cores up to 22 cores. It also can scale to 2s or 4s. This means that you can have 2 or 4 CPUs on your motherboard (*2s*ocket, *4s*ocket).
* `E7` The biggest brother, or "the big guns." This is the stuff you make huge Folding@Home labs with or massive video transcoding servers. Most of the E7s have 8s scalability, so you can have **8 sockets**! However, you can only get 8s if you have a top-of-the-line Supermicro server. In theory, you could have *192 CPU cores and 394 logical cores* if you had k to spend.

95% of 2011s have AES-NI, but a good place to double-check would be [Intel ARK](http://ark.intel.com), as mentioned above.

## **AMD**

EPYCs are still pretty pricey. They're more than capable of running any homelab, though. One caveat to be aware of is the [PSB vendor lock](https://www.servethehome.com/amd-psb-vendor-locks-epyc-cpus-for-enhanced-security-at-a-cost/), which mates CPUs to the motherboards a certain vendor. Avoid anything made before them, like Opteron.


# **Storage**

## **Drives**
[StorageReview.com](https://www.storagereview.com/reviews/enterprise) is a great site to see reviews of particular drives on the enterprise level. Compare that with [BackBlazes](https://www.backblaze.com/blog/backblaze-hard-drive-stats-q3-2019/) hard drive stats, and you can make a decision on which drives you to want to buy.

**Hard drive burn-in**

Before using drives in production, it is recommended to burn them in to foresee any issues; doing a SMART test might throw some data, but tools such as bad blocks test the drives completely. The tool [bht](https://github.com/ezonakiusagi/bht) helps in automating these tests. A tutorial is available [on YouTube](https://www.youtube.com/watch?v=9bh5ZK8z4ZA).

## **DAS**
Direct Attached Storage, also referred to as JBOD, is a way for you to add drive bays to your server. They are connected to a server by an external HBA or RAID card. Generally, you're going to want a DAS that has an SFF-8088 connector to support 6Gb SAS/SATA. 
**Currently there is a change in the prices, and buying Dell R620s, or R720xds are about the same price.**

Name|Form Factor|SAS Version|Drive Bays|Connection|Power Usage (Empty)|Noise|Price
-|-|-|-|-|-|-|-|-
Lenovo SA120|LFF|2|12|2x SFF-8088 per controller|~45w|?|$220-400|
Dell Xyratex Compellent HB-1235|LFF|2|12|3x SFF-8088 per controller|56w with 1 PSU|60dB|~$100|
Netapp Xyratek DS4243|LFF|1|24|2x QSFP+ per controller|~41w/PSU|50dB|~$150|
Netapp Xyratek DS4246|LFF|2|24|2x QSFP+ per controller|?|50dB|~$150|
HP D2700|SFF|2|25|2x SFF-8088 per controller|41w|70db|$125-$300|
EMC KTN-STL3|LFF|2|15|2x SFF-8088 per controller|33w|56dB|$100-300|


##### **SA120 Information**

As the SA120 is a popular recommendation, there are a couple of important "gotchas" of which potential buyers should be aware.

* Observed to pull anywhere between 45 watts and 60 watts at the wall, measured.  This depends on whether there are multiple power supplies and controllers.
* The fans can be controlled with the official Lenovo utility in Windows, or with the [lenovo-sa120-fanspeed-utility](https://github.com/AndrewX192/lenovo-sa120-fanspeed-utility).  This script runs under Linux, FreeBSD, FreeNAS, and others.  Setting the fan level to "1" makes for a relatively quiet enclosure.
* The cooling in them is REALLY bad. If you have drives that run even a little warm (looking at almost any 7200 RPM drive in larger sizes), you will need to run the fans higher. Level 2 is loud but still bearable. Level 3 is a jet engine. Ironwolf 8TB drives required level 3.
* Dual controllers (the top one specifically) are only for the second port on SAS drives  With SATA drives, there is no reason to have dual controllers. 
* The rear-drive cages use SATA interposers and run at 3Gbps. This severely limits the intended use for SSD cache drives.

##### **Dell Xyratex Compellent Information**
* There are two powerful Delta Electronics PFB0812DHE high-RPM fans in each of the two power supplies
* Fans may be replaced with one or two standard 3-pin aftermarket fans; the PSU fan error light may illuminate without impacting functionality.

##### **EMC KTN-STL3 Information**
* There is one powerful centrifugal style fan in each of the two power supplies
* Fans cannot be replaced with standard 3-pin aftermarket fans. The sound of the fan is different than most server equipment. It sounds more like rushing air than a whine of a fan.
* You MUST use a Lsi RAID or HBA card. It can be a rebranded Lsi card, but PMC-Serria and Adaptec cards will NOT work.
* The serial port on the back is not used for anything.
* There are three types of disk trays. One type is designed for the KTN-STL3 (SAS), and the other two are designed for the KTN-STL4 (FC-AL). They are not cross-compatible. It is recommended to purchase KTN-STL3 shelves full of either drives or trays.

##### **NetApp Information**
* Can take IOM3, IOM6, or Dell Compellent HB-1235 modules.
* Recognizes >2TB drives even with the IOM3 controller if using HBA/Raid card that supports SAS2.
* SATA drives can be used with or without interposers. 2 controllers needed if using interposers or SAS drives.
* SFF-8088 to QSFP+ cable required if using NetApp IOM3/IOM6 controllers.


## **RAID and HBA Cards**
### **RAID Cards**
RAID cards come in a variety of flavors, some boasting more features than others, but can come at a higher cost vs. ones with fewer features; however, they may be more appealing for its cost when compared to the higher-end model(s).
LSI RAID controllers are the most popular as they offer many tools and LSI's support is quite good should you have an issue, us here at /r/homelab or /r/datahoarder can't resolve.
Some cost-effective RAID cards are as followed with features as well:

* IBM M5015 (LSI based) is a 6Gb SAS RAID card supporting RAID 0,1,5,10,50 (and RAID6 and RAID 60 with an adv key) as well as a 512Mb or 1Gb cache w/ BBU
* LSI 9260 8i (LSI Based) is a 6Gb SAS RAID card supporting RAID 0,1,5,10,50, and 60 as well as a 512Mb or 1Gb cache w/ BBU; [which is supported by ESXi](http://partnerweb.vmware.com/comp_guide2/detail.php?deviceCategory=io&productid=12384)

When shopping for a RAID card that is LSI based, the ending number and letter such as "8i" specifies how many drives it supports, and if it is I=Internal or E=External, a 4i would support 4 internal drives.

Please also be sure that your selected OS has drivers for the RAID card you have chosen, if you're using VMware, please be sure to consult [VMware Compatibility Guide](http://www.vmware.com/resources/compatibility/search.php), or Google of course. 

### **HBAs**
HBAs (Host Bus Adapters) are used for several things.
One of the most common is to add additional hard drives when you've run out of onboard SATA ports, or if your motherboard does not have a compatible SATA controller for the OS to recognize.
Operating systems such as FreeNAS rely on HBAs with a specific phase/version of firmware to function properly.
FreeNAS recommends an LSI 9211-8i or an M1015; both of these cards utilize the same LSI controller and would then be flashed to IT firmware.
IT firmware allows the controller to operate in JBOD mode (to pass SMART and drive information onto the OS, whereas an RAID controller does not).

**Also Read:** [LSI/Broadcom HBAs ports and limitations](https://www.reddit.com/r/homelab/comments/16kktyk/lsibroadcom_hbas_ports_and_limitations/)

Popular Internal HBA's are as followed:

* IBM M1015 (Rebranded LSI 9211-8i controller)
* Dell Perc H200/H310 (SAS 2008 based and compatible with LSI 9211-8i IT firmware) (see above for more info on [Dell Cards](https://www.reddit.com/r/homelab/wiki/hardware#wiki_dell_raid_controllers))
* LSI 9211-8i

Popular External HBA's are as followed:

* LSI 9200-8e
* Dell 6Gbps SAS HBA

The 9200-8e could be used for a Lenovo SA120 DAS connected to a FreeNAS VM; in this example. 

When shopping for an HBA card that is LSI based, the ending number and letter such as "8i" specifies how many drives it supports, and if it is I=Internal or E=External, a 4i would support 4 internal drives.

Other HBA's can also provide the same function depending on the OS of choice; it is best to do some homework on what HBA you should use for your build based around what your OS supports and recommends. If purchasing an HBA to pass through to a VM be sure that your hardware supports PCI device passthrough to the VM

[Can I virtualize FreeNAS?](https://www.reddit.com/r/homelab/wiki/hardware/virtfreenas)

## **Uninterruptible power supplies (UPS)**
For keeping your homelab alive during brief power outages or during a complete power failure, it's important that everything is shut down gracefully to avoid data loss or even to prevent service outages in the event of a short power outage. An [uninterruptible power supply](https://en.wikipedia.org/wiki/Uninterruptible_power_supply) or UPS consists of a battery which is charged off the main power when not supplying power. As the power goes out, the servers (and other equipment) are transferred over to the battery when the UPS unit detects a blip in power. They are only meant to be used as emergency power sources, but the capacity (both runtime and maximum power draw) vary greatly.

There is a great tool on the [APC site](https://www.apc.com/shop/us/en/tools/ups_selector/) that has a nice calculator for your required VA needs. Uninterruptible power supplies come in both tower and rack mount form factors.



## **Routers**

### **Software**

- VyOS
- Ubiquiti Unifi
- pfSense
- OPNsense
- dd-WRT

### **Hardware**

It probably all depends on which system you want to dive into!

If you like Ubiquiti and want to stay in their ecosystem, your first choice is probably going to be the ER-X. That little guy is probably enough for most applications. If you want to have unifi integration (so that the device is visible in the unifi controller), go for the USG. 

But in the end, you will probably want more. Then looking at running an entire router operating system such as VyOS, OPNsense, or pfSense, are probably the way to go. You have many different options there. Here is a small list ordered by buying price:

- Put any software in a VM and get internetting. However, as soon as you reboot the host, your internet is going to be down. There are ways to get failover clusters setup, but this will require more work on your end.
- An old thin client that is super small and cheaper.
- Some off the shelf SFF PC, such as an Optiplex 3020 or HP EliteDesk 800 G1. Higher power consumption but really good performance.
- The SG-1100 official pfSense router. It is quite expensive for what it can actually do, but it doesn't consume a lot of power.
- Some people, like me, want to have a separate host for their virtual router. I use a Dell R230 and run VyOS on ESXi. The use cases for separate servers to act as router hosts is limited, but it still is an option.


# **Other Resources**

- [TheGammelGalopper's Comprehensive Introduction to Fujitsu Servers](https://www.reddit.com/r/homelab/wiki/hardware/fujitsuguide)
- [Intel Ark](http://ark.intel.com)
- [VMware Compatibility Guide](http://www.vmware.com/resources/compatibility/search.php)
- [Physical Terminations Guide](http://packetlife.net/media/library/22/physical_terminations.pdf)
- [(Outdated now) Muffin's Server Guide](https://www.reddit.com/r/homelab/wiki/hardware/muffinsguide)
