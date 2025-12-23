# FAQ

## General

### Why build a homelab? / What do you do with your lab?

The introduction wiki post located [here](https://www.reddit.com/r/homelab/wiki/introduction/) is an excellent start to your labbing.

### Where do I start?
You don't have to spend a lot of money to set up a homelab. You might not have to spend any at all. Just start with what you have laying around. Install [VirtualBox](https://www.virtualbox.org/) on your computer and run a few different operating systems on it to learn about them. Figure out what you want to do (see [Introduction](https://www.reddit.com/r/homelab/wiki/introduction)) and start learning the [software](https://www.reddit.com/r/homelab/wiki/software) associated with that. Once you are ready to start buying hardware, you can usually get decommissioned enterprise gear very cheaply. See the [Hardware](https://www.reddit.com/r/homelab/wiki/hardware) page and check out [Muffin's Buying Guide](https://www.reddit.com/r/homelab/wiki/hardware/muffinsguide) for some pointers.

### Why should I backup my data?
What would you do if your home flooded, caught fire, or your computer or hard drive was dropped? These are just a few examples of ways that you could lose the data that you are hosting at home. An option for how to determine whether all or some of your data should be backed up is by asking the following: 
 - Is the data replaceable? (movies, tv shows, files that are commonly downloaded from the internet)
 - Is this data irreplaceable? (home movies, family/friends pictures, tax documents)

You may choose to categorize your data in many ways, but some common, simple categories are:
 
  - Critical - Cannot lose at all costs
  - Preferred - I don't *want* to lose, but it can be replaced
  - Replaceable - I can replace this data

A common method to follow for backing up your data is the 3-2-1 method. 
 
  - 3 copies of your data
  - 2 different mediums (hard drive, tape, cloud, etc)
  - 1 offsite backup

By following the 3-2-1 method for backups, you are more likely to ensure that you do not lose your data.

Another resource with a more complete view of the 3-2-1 method can be found from VMware: https://www.vmwareblog.org/3-2-1-backup-rule-data-will-always-survive/

## Solution Suggestions

### What AP(s) should I get?
Ubiquiti's [UniFi](https://www.ubnt.com/enterprise/) line of APs, especially the [UAP-AC-LITE](https://www.ubnt.com/unifi/unifi-ap-ac-lite/) is generally the most recommended. If you are eligible, you can attend a webinar and receive a free [Cisco Meraki AP](https://meraki.cisco.com/products/wireless). Click [here] (https://meraki.cisco.com/freeap) for details.

### Recommendations for NAS?
If you just want a software solution, generally [FreeNAS](http://www.freenas.org/) is the way to go. Check out our [Software](https://www.reddit.com/r/homelab/wiki/software#wiki_storage) page for more ideas. If you want hardware, Synology is generally recommended for an "out-of-the-box" solution. 

### How do I make a diagram of my network?
If you have it, [Visio](https://products.office.com/en-us/visio/flowchart-software). If you don't, check out some of our suggestions on the [Software](https://www.reddit.com/r/homelab/wiki/software#wiki_network_diagrams) page. Or just use pen and paper if you roll like that. I'm not judging.

### [Can I virtualize FreeNAS?](https://www.reddit.com/r/homelab/wiki/hardware/virtfreenas)

### How can I multiple servers connected to a single UPS be configured to shutdown together on power failure?
Checkout the standard `apcupsd` Linux services, specifically: [master-slave-shutdown](http://www.apcupsd.org/manual/manual.html#master-slave-shutdown)

