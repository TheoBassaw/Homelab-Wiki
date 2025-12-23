# Networking buying guide, tips and tricks.

## For Beginners
information compiled from: https://www.reddit.com/r/homelab/comments/50llv5/best_beginnerfriendly_switches_will_update_wiki/

To determine what the best switch for you, you need to determine what your requirements are - what kinds of things you want to do with it, how important noise and power consumption is, port speeds, port types, and number of ports. 

The majority of enterprise installations use Cisco switches, so if you want to learn enterprise networking, It's worth considering buying a Cisco switch. The Cisco 3750G is often recommended; which has fans and will pull up to 100 watts (more on PoE versions), has up to 48 ports, and can do "Layer 3 Routing". However, it has no web GUI, so you'll really have to learn Cisco CLI. Note that the Cisco 3750E model has 10GbE, is stackable, and is cheaper, *but* has "univeral licensing", which means you can't get new features without a subscription. (Note that the default "IP Base" feature set likely will handle anything a homelabber would want it to do.) To get around this constraint, you *can* buy versions of the 3750E that are running a more full-featured software set.  The key is a model number that ends with -E at the end, for example WS-3750-24PD-E.

Expect enterprise grade switches to pull 75-100 watts at idle. 

## Network Switches

The best value for money as of October 2017 (if you want to buy a new switch) is the [TP-Link T1700G-28TQ](https://www.amazon.com/TP-Link-JetStream-24-Port-Ethernet-T1700G-28TQ/dp/B01CHP5IAC) (Amazon link, you can probably find cheaper) switch. This is a **fanless** (silent!) device, with 24 Gigabit ports, plus 4 10gbit SFP+ ports. It supports VLANS, has a Web UI, and has a similar configuration syntax to Cisco switches.

## Gigabit Switches

Avaya [ERS3500](https://support.avaya.com/products/P0998/ethernet-routing-switch-3000-series). The baby of the larger Avaya switches. Early versions were re-branded Nortel switches. Interface is maddening (using Chrome pisses it off), but the switches are good options for POE (Power Over Ethernet) devices. Upgrade process requires serial connectivity, and an active Avaya service contract. 

Common Switch Models|Main Ports|Uplink Ports|Modules|Config|Stack|VLANs|PoE|Routing|Watts|Notes
:--|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:--
Asus XG-U2008 | 10x 1Gbase-T | 2x 10Gbase-T | - | Unmanaged | - | No | No | No | *NEED* | *NEED* | -
Avaya/Nortel 5510 | 24-48xG | 2xG SFP | No | Both `GUI | Yes | Yes | No | Yes | ~150W idle | Worse power usage than 5520
Avaya/Nortel 5520 | 24-48xG | 4xG SFP | No | Both `GUI | Yes | Yes | PoE | Yes | *NEED* | Better power usage than 5510 with PoE Disabled on unused ports
Avaya/Nortel 5650TD / TD-PWR | 48xG | 2XG XFP | No | Both `GUI | Yes see 1 | Yes | Non &amp; PoE | Static, OSPF | *NEED* | Higher-end backplane and stacking throughput than 55xx series
Cisco 3560G | 24-48xG | 2-4xG SFP | No | CLI | No | Yes | Some PoE | Static, Dynamic | ~60W idle | Cheapest, oldest, cisco Gigabit+L3
Cisco 3750G | 24-48xG | 2-4xG SFP | No | CLI | Yes | Yes | Some PoE | Static, Dynamic | ~60W idle, roughly 30w per poe phone - 48 port PoE model ~100w idle | Slightly more $$ b/c of stacking
Cisco 3560-E | 24/48xG | 2 X2 10Gb (convertible to 2x1G SFP) | No | CLI | No | Yes | Some PoE | Static, Dynamic | ~100W idle (48P) | Slightly newer than 3560G, with 10Gig support
Cisco 3750-E | 24/48xG | 2 X2 10Gb (convertible to 2x1G SFP) | No | CLI | Yes | Yes | Some PoE | Static, Dynamic | *NEED* | More $$$ because stacking; otherwise same as 3560-E
Juniper EX2200 | 24-48xG | 4xG SFP | No | CLI & GUI | Virtual chassis | Yes | No | Static, OSPFv2 | ~30W idle, ~70w under heavy load | Cheapest Juniper switch around
HP 1810-24G | 24xG | 2xG SFP | No | GUI | No | Yes | No | No | 30W Max | Cheap, Fully Passive, No Dynamic LAGGs, Lifetime Warranty
HP 1910-24G | 24xG | 4xG SFP | No | GUI & CLI* | No | Yes | Some | No | 60W Max | Some models Passive, No Dynamic LAGGs, Lifetime Warranty
Mikrotik CSS326-24G-2S+RM | 24xG | 2x10G SFP+ | No | GUI | No | Yes | No | No | 19W Max | Unusual Lights, Runs SwOS
Dell 5524P | 24xG | 2x10G SFP+ | No | CLI & GUI | Yes | Yes | Yes | Static | 39W Non-POE, 380W POE | Loud, Lifetime Waranty
Dell 6248 | 48xG | 4x1G SFP | Yes | CLI & GUI | Yes | Yes | No | Yes | ~62.5W idle | Stacking modules use CX4 cables, fans on are on the sides. Sunon Fan Mod possible.
Dell 6248P | 48xG | 4x1G SFP | Yes | CLI & GUI | Yes | Yes | No | Yes | 120W All Ports active Non-POE, 499W all POE on | Stacking modules use CX4 cables, fans on are on the sides. 15.4W POE per port.

` indicates preferred.

### Dell PowerConnect 5000/6000 series (6224, 6248, possibly P models)
A fan mod exists to replace the loud stock fans with quieter Sunon MagLev KDE1204PKV3 40x40x20mm fans.  Most youtube videos show two fans being used.  The fans' header pins must be rearranged to work with the unit.

## 10 Gigabit Info

As mentioned above, the best bang-for-your-buck as of October 2017 is the [TP-Link T1700G-28TQ](https://www.amazon.com/TP-Link-JetStream-24-Port-Ethernet-T1700G-28TQ/dp/B01CHP5IAC) switch with 24 gigabit and 4x10gb SFP+ ports.

###10GbE (Ethernet)

10gb Ethernet is not very popular, as it requires significant amounts of power to drive the signal for more than a few meters. Whilst there are a few 10gbE SFP+'s available, none of them are 'standards compliant', as the SFP+ port does not provide enough power, so they will only work over short runs (5-10 meters). It is unusual to find in the wild, as SFP+ DAC (**D**irect **A**ttach **C**oax) cables have become the standard for short (up to 10m) runs.

###10Gb DAC

DAC cables have become the standard way to connect short runs of 10gb Networking. They work with a standard SFP+ port (see below), but are not as fragile as Fibre, and are significantly cheaper.  Due to technical and power limitations, the longest DAC cable you can buy is 10 meters.  DAC cables are also available in 'Passive' or 'Active' designs. A passive design is, technically, roughly equivalent to a standard CAT6 cable. There is no intelligence or amplification/clarification of the signal being passed through the device. This reduces complexity of the DAC, which reduces the price. 

DAC cables 5 meters or over in length should be Active cables. An Active cable rebuilds and cleans up the signal on both ends of the connection, removing interference and reducing load on the switch.  Active cables use significantly more power, and can be up to twice the price of a Passive cable, but for any run 'between racks' you should use an Active cable.  The power usage concerns have turned out to be irrelevant in most devices. The only well-known device that has heat and power limitations (that I, /u/xrobau, know of) is the HPE VC-Flex10 interface card that is used in the C-Class chassis. No other device appears to have limits on the amount of power than can be drawn that is less than the standard requires (eg, all other devices can support fully populated SFP+ ports)

[Link to fs.net examples](https://www.fs.com/c/10g-sfp-dac-1114) of DAC cables. They are very common to find on eBay, normally for less than USD$10.

###10Gb Fiber

This will cover all things 10Gb fiber related, first we have to understand SFP vs SFP+ and the different cards that can be purchased.

#####**What's an SFP vs SFP+?**

SFP, or Small Form-Factor Pluggable, supports data rates up to 2.5Gbps, but is typically used for 1Gb uplink connections between switches.

SFP+ is an enhanced version of SFP which supports data rates up to 16Gbps, but is typically used for 10Gbps uplinks on newer switches, and for server NIC cards which support SFP+ modules.


#####**LR vs SR, what the hell is that?**

SFP and SFP+ come in two common standards, one is LR - Long Range ; and SR - Short Range. There are others but they are generally for long-haul (think cross-continent) fiber backbones.

SR Lengths 

| Fibre type(micrometers) | Range (m) |
|-------------------------|-----------|
| OM1 (62.5)              | 33        |
| OM2 (50)                | 82        |
| OM3                     | 300       |

LR Supports up to 40Km; more if signal boosters are used. They do not do as well over short (sub-5 meter) links and will sometimes fail to link up in those cases.

The most common SFP/SFP+ are SR models unless you specifically look for the LR equivalent. 

SR (Short Range) SFP/SFP+ typically utilize MultiMode Fiber which is cheaper per meter.

LR (Long Range) SFP/SFP+ typically utilize SingleMode Fiber which allows for far greater transmission distances, but comes at a higher cost per meter. 

For more information on this, please see [the link here](http://www.multicominc.com/training/technical-resources/single-mode-vs-multi-mode-fiber-optic-cable/)

###10Gb Active Optical Cable

These are similar in concept to DAC cables, but instead of using copper, they use fixed fibre. This extends their length from the maximum 10m of DAC cables to 30m. They do not have removable fibre ends, the fibre is part of the entire cable. [Link to fs.net examples](http://www.fs.com/c/10g-sfp-aoc-2689)

###Well, what NIC's do I need?

Depending on the use, a general all around 10Gb (with SFP+) card will be Chelsio cards, depending on the model such as the T420-CR which supports 2 SFP+'s. It is well favored for use by iXsystems (who make TruNAS and FreeNAS) as well as ESXi,Windows, and OSX.

I, DXM765 use the Chelsio T420 CR cards in my ESXi hosts and my FreeNAS 9.10 server with no issues, and had it functioning in my Mac Pro 2009 as well without issue; they are pretty solid cards, are cheap (~140$) and the SFP+'s are ~30$ each as cheap as 15$ or so.

Another commonly used 10G card is the Mellanox ConnectX-2, as are any of the Intel X520 series, though they tend to be pricier. Both have good support under Linux, Windows, and FreeBSD/FreeNAS (though the Mellanox are best used under the most current version).

The HP NC523SFP NICs are good value second hand, **but be warned**: These cards run VERY hot, and _must be in a case with active cooling_ - this means a normal PC case without an active front-to-back airflow will cause the card to overheat and lock up.  It is possible to find cards with fans on the heatsink, but they are rare.

From /u/wolffstarr: [Econo 10GbE Homelab hardware config](https://www.reddit.com/r/homelab/comments/54nsu5/10gb_switch_question/d83keva/) Oct, 2016

###Cheap 10GBe Gear?

Cards:

    HP nc523sfp / p/n: 593715-001

Dirt-cheap dual-SFP card. Doesn't work well at all in Windows 10 (I had boot and shutdown issues with it installed). Also this card gets HOT. I've measured ~85c at the heatsink with only one SR SFP+ module installed.

Possibly worth it in a well-cooled rackserver (almost like it was designed to be used in one of those, hmm). Hard pass for desktop use.

    Mellanox ConnectX-2 / mnpa19-xtr

Also pretty cheap. Works out of the box for me on vsphere 6.7, Windows 10, Windows Server 2019 and CentOS7. Runs pretty cool to boot, so a great choice imho.

Fiber SFP's:

    Generic fs.com SR receiver / "Generic Compatible 10GBASE-SR SFP+ 850nm 300m DOM Transceiver Module"

Works out of the box on the Mellanox cards and a Mikrotik CRS305. Autonegotiates to 10Gbe as well, no need to configure anything.

    Finisar Intel FTLX8571D3BCV-IT

I got these because they're cheap at 10$. Unfortunately they didn't work for my setup. Autonegotiation didn't work and the highest I was able to force was 1gbit. 10gbit just gave me no-link errors. It may have to do with Mikrotik's implementation (which is a bit finicky with dual-rate transceivers) but with new generic transceivers at 20 dollars it's probably not worth the hassle.

Switches

    Mikrotik crs305-1g-4s+in

Works great out of the box and switches at 10GBe no problem. Just don't expect line-speed routing performance. One additional bonus is the 1Gb management port is also switched with the 10Gbe SFP+ ports, which is great if you want to bridge your 10Gb network to the 1Gb network. Earlier reports of poor "downstepping" seem to have been resolved, I get a great 115MB/s from my 10Gb NAS to a 1Gb client.

From /u/citruspers: Cheap 10GBe gear (information/compatibility) https://www.reddit.com/r/homelab/comments/d86i1x/cheap_10gbe_gear_informationcompatibility/ Sept, 2019

Graphic: [Physical Terminations Guide](http://packetlife.net/media/library/22/physical_terminations.pdf)

### 10 Gigabit Switches

Common Switch Models|Main Ports|Uplink Ports|Modules|Config|VLANs|Routing|Watts|Noise|Notes
:--|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:--
Arista DCS-7124S | 24x SFP+ | - | - | CLI | Yes | Static, Dynamic | ~120W idle | ~64.3 dBa | -
Arista 7124SX | 24x SFP+ | - | - | CLI | Yes | Static, Dynamic | ~100W idle | ~55 dBa | -
Cisco Nexus 5010 | 20x SFP+ | - | 1 module slot | CLI | Yes | No | ~280W idle, ~310W under load | *NEED* | Can also be found as the UCS 6120xp which could be reflashed to Nexus firmware
Juniper EX4550-32T | 32x Base-T | - | 1x NIC module slot / 1x Virtual Chassis module slot | CLI/GUI | Yes | Static, Dynamic | *NEED* | *NEED* | As of 2017, still very expensive
MikroTik CRS317-1G-16S+ RM | 16x SFP+ | - | - | CLI/GUI | Yes | Static, Dynamic^(1,2) | *NEED* | *NEED* | -
Netgear XS708E v2 | 7x Base-T / 1 Base-T/SFP+ combo | - | - | GUI | Yes | No | *NEED* | *NEED* | -
Ubiquiti ES-16-XG | 12x SFP+ / 4x Base-T^(3) | - | - | CLI/GUI | Yes | Static, Dynamic^(1) | *NEED* | Passively Cooled | -
Arista 7050T-36 | 32x Base-T, 4x SFP+ | - | - | CLI | Yes | Static, Dynamic | ~135W idle | ~55 dBa | -


* (1) L3 routing is not full wire-speed (i.e. not capable of 10Gbps routing)
* (2) RouterOS required for routing
* (3) known to have performance issues causing the port to not really work at 10Gbps

### Transceiver and DAC Compatibility Chart and Tips
(Note: source and destination are arbitrary)

|  SOURCE               | OPTIC                 | CABLE                                    | OPTIC                 | DESTINATION                                 | Works? | Notes | Contributed by |
| --------------------- | --------------------- | ---------------------------------------- | --------------------- | ------------------------------------------- | ------ | ----- | -------------- |
| HP CN1000E (ESXi 6.5) | -                     | Cisco SFP-H10GB-CU3M Passive SFP+ DAC    | -                     | Netgear GSM7352Sv2 (Port 49, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Arista SFP-10G-SRL    | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Netgear AXM761        | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Finisar FTLX8571D3BCL | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Netgear AXM761        | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Netgear AXM761        | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Finisar FTLX8571D3BCL | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Netgear AXM761        | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Arista SFP-10G-SRL    | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Finisar FTLX8571D3BCL | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Arista SFP-10G-SRL    | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| HP CN1000E (ESXi 6.5) | Arista SFP-10G-SRL    | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Finisar FTLX8571D3BCL | Netgear GSM7352Sv2 (Port 50, built in SFP+) | YES    |       | /u/dxing97     |
| Mellanox ConnectX-2 (ESXi 6.5u1) | Cisco SFP-10G-SR    | 2m LC-LC 62.5/125 | Cisco SFP-10G-SR | Cisco UCS 6120xp | YES    |       | /u/gac64k56
| Mellanox ConnectX-2 (ESXi 6.5u1) | -    | Cisco SFP-H10GB-CU3M Passive SFP+ DAC | - | Cisco UCS 6120xp | YES    |       | /u/gac64k56
| Mellanox ConnectX-2 (ESXi 6.5u1) | Cisco SFP-10G-SR    | 2m LC-LC 62.5/125 | Cisco SFP-10G-SR | Cisco C3560E-48PD-S | YES    |       | /u/gac64k56
| Mellanox ConnectX-2 (Windows 7) | Cisco SFP-10G-SR    | Tyco 100m LC-LC 50/125 | Cisco SFP-10G-SR | Cisco UCS6120xp | YES    |       | /u/gac64k56
| Mellanox ConnectX-2 (Windows 7) | Cisco SFP-10G-SR    | Tyco 100m LC-LC 50/125 | Cisco X2-10GB-SR | Cisco C3560E-48PD-S | YES    |       | /u/gac64k56
| Intel i350-T4 | -    | CAT6 | Cisco GLC-T | Cisco UCS 6120xp | YES    | You have to specify speed 1000 to activate / use      | /u/gac64k56
| QLogic QLE8152 (Windows Server 2012) | Cisco SFP-10G-SR    | 2m LC-LC 62.5/125 | Cisco X2-10GB-SR | Cisco UCS6120xp | YES    | Drivers will install both Ethernet and Fiber Channel interfaces      | /u/gac64k56
| QLogic QLE8152 (Windows Server 2012) | -    | Cisco SFP-H10GB-CU3M Passive SFP+ DAC | - | Cisco UCS6120xp | YES    | Drivers will install both Ethernet and Fiber Channel interfaces      | /u/gac64k56
| Emulex OCE10102 (ESXi 6.5u1) | -   | Brocade 3M FCoE Twinax Active SFP+ DAC | - | Brocade FCX-624-I (4x10g module installed) | YES | -  | /u/klmx30302
| Mellanox ConnectX-2 (ESXi 6.5u1 / Windows 8.1 Pro / Ubuntu 16.04) | - | Cisco SFP-H10GB-CU3M Passive SFP+ DAC | - | Arista DCS-7124S | YES | switch must be configured with `enable3px` | /u/namodev
| Mellanox ConnectX-2 (Windows 8.1 / Ubuntu 16.04) | Arista SFP-10G-SRL | fs.com 30m LC-LC armored OM3 | Arista SFP-10G-SRL | Arista DCS-7124S | YES | | /u/namodev
| Intel X520 (ESXi 6.5u1) | - | Ipolex "For Ubiquiti" 0.5m SFP+ DAC | - | Arista DCS-7124S | YES | switch must be configured with `enable3px` | /u/namodev
| Intel X520 (ESXi 6.5u1) | - | fs.com 2M 10G SFP+ Passive DAC (Arista compatible) | - | Arista DCS-7124S | YES | - | /u/namodev
| Broadcom BCM957810A1006G | Arista SFP-10G-SRL | Monoprice 2m OM3 LC-LC Fiber Optic Cable | Finisar FTLX8571D3BCL | HP 5800-24G-PoE+ (JC099A, H3C branded, HP firmware) | YES* | Syslog in HP switch reports "FIBER_SFPMODULE_NOWINVALID" warning, but works anyway, no configuration/commands needed | /u/dxing97

* Netgear switches generally don't require branded optics (source: fs.com)

## Infiniband

While Ethernet is considered the gold standard amongst communication at the data-link level, there are other major standards used by a lot of commercial equipment, one of which is Infiniband. For applications that require incredibly high throughput and low latency, I've found that aging Infiniband equipment can be a very cost effective way of providing this connection. Keep in mind that like fibre-channel and Ethernet, Infiniband is a data-link layer protocol. In order to connect Infiniband devices to an ETH/FC network, you'll need some form of router, bridge, or gateway device that can talk both protocols. 

### Infiniband Standards

#####**SDR**

10Gbps connection that uses a CX4 connector. Very old equipment, but very cheap!

#####**DDR**

DDR Infiniband is the second iteration of the standard. It operates at 20Gbps (16Gbps after throughput loss due to encoding) and uses either CX-4 or QSFP. Most DDR devices I've seen use CX-4. Personal opinion: CX-4 is such an ugly connector. Who designed that? Topspin switches are cheap and cool for learning Infiniband, and most of them operate on this standard.

#####**QDR**

Switches that operate to this standard usually provide connections rated at a throughput of 40Gbps (32Gbps after encoding loss) and a latency significantly lower than Ethernet's. The connection type for most 40Gb Infiniband is (QSFP+). A lot of newer Mellanox switches offer something they call VPI, which allows configuration on a port by port basis as to which protocol you'd like to use (Ethernet or Infiniband). I personally like this feature, because it allows for flexibility within my lab. 

Before they were bought out by 100 different companies, there was a company called Voltaire that made QDR switches. If you're looking for the cheapest QDR switch you can find, that's probably a route worth exploring.

#####**FDR-10/FDR**

The F stands for F@&amp;% that's expensive! Alternatively it stands for FAST. I run an SX6018 at home. It draws about 40W under a modest load and is the quietest IB switch I've ever owned.

### Networking with Infiniband

Infiniband uses a subnet manager all to its own. Most newer switches come with this feature built-in. This feature will need to be enabled before you can connect hosts to the network. Some of the older switches out there do not have this functionality. If you have a Linux box on your network, you can use your package manager to download "OpenSM." OpenSM is a subnet manager that you can install on a host machine in order to get hooked up to your switch. As far as I'm aware, you should only ever need one machine running the subnet manager in order to connect all of your machines to the switch.