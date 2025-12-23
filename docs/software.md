#  Homelab Software

## Free Microsoft Licenses for Students
###[Microsoft Azure for Students (formerly Imagine/DreamSpark)](https://azure.microsoft.com/en-us/free/students/)
Students enrolled in secondary and post-secondary education are eligible for free licenses for all editions of Windows Server and some other software such as SQL Server through Microsoft Azure for Students. Downloads are accessible once student status is verified, even if the Azure credit is never claimed. Certain schools may be eligible for more software such as Office, System Center or desktop editions of Windows.

## Microsoft Licenses for Small Business Owners (Or Sole Proprietorship)
###[Microsoft Action Pack](https://partner.microsoft.com/en-us/membership/action-pack/)
People who run their own small businesses or Sole Proprietorship are eligible for Internal Use (Personal Use) licenses for all editions of Windows Server and some other software such as SQL Server, System Center or desktop editions of Windows. Signing up will also give you 5 copies of Office 365 E3 and $100 of Azure credits every month. Cost is about $450 a year. 

## Bare Metal Hypervisors (Type 1)

###[Oracle VM Server for x86](https://www.oracle.com/virtualization/vm-server-for-x86/index.html)
A lesser-known Type 1 variant of the well known Oracle VM VirtualBox, featuring an open-source server that uses the Linux Kernel 
and a freeware manager to manage the virtual machines (a SPARC variant is also available)

###[VMware vSphere ESXi](http://www.vmware.com/uk/products/vsphere/features/esxi-hypervisor.html)
The vSphere hypervisor, commonly known as "ESXi", is a bare-metal hypervisor with each virtual machine sharing the same physical resources.

###[VMware vSphere Hypervisor \(Free Edition\)](http://www.vmware.com/uk/products/vsphere-hypervisor/)
Broadcom discontinued free licenses. This option is no longer available.
VMware vSphere Hypervisor is a free bare-metal hypervisor that virtualizes servers so you can consolidate your applications on less hardware. Please note, that the free version comes with some limitations (e.g. 8 vCores per VM). They do not affect normal usecases, but more complex scenarios such as HA, complex virtual networking may reequire a paid license.

###[VMware Hypervisor \(VMUG, $200/year\)](https://www.vmug.com/evalexperience)
The VMware User Group offers a suite of fully-enabled and up to date VMware products for $200/year. Package includes ESXi, vCenter, vCloud Suite and several others. Registration at myvmware.com provides download access to ancillary programs such as vSphere Data Protection and vSphere Standalone Converter.

###[Hyper-V Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-hyper-v-server-2016)
Free stripped-down version of Windows with Hyper-V related roles only.

###[bhyve](http://bhyve.org)
BHyVe is a legacy-free hypervisor developed by the FreeBSD team. It is now included with releases of FreeBSD from version 10 and upwards. It's activated by loading a single kernel module and ready for production use with Linux and FreeBSD guests.

###Windows Server
Windows Server supports working as a bare metal hypervisor using the Hyper-V role. Each Standard license allows one installation on bare metal and 2 VMs on a single server. Datacenter licenses allow for unlimited VMs that can be [automatically activated with no network access](https://technet.microsoft.com/en-us/library/dn303421\(v=ws.11\).aspx).

###[XenServer](http://xenserver.org/)
XenServer is an enterprise-class, cloud-proven, virtualization platform that delivers all of the critical features needed for any server and datacenter virtualization implementation.

###[XCP-ng](https://xcp-ng.org/)
A fork of XenServer, developed by the community. It has almost everything good about XenServer, but without the licensing and fully open source. XCP-ng can be managed preferably through [Xen Orchestra](https://xen-orchestra.com#!/xo-home) (XO).

###[Linux KVM](https://www.linux-kvm.org/page/Main_Page)
KVM (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It consists of a loadable kernel module, kvm.ko, that provides the core virtualization infrastructure and a processor specific module, kvm-intel.ko or kvm-amd.ko.
Using KVM, one can run multiple virtual machines running unmodified Linux or Windows images. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, etc.
KVM is open source software. The kernel component of KVM is included in mainline Linux, as of 2.6.20. The userspace component of KVM is included in mainline QEMU, as of 1.3.

###[Umbrel](https://umbrel.com/)
While Umbrel isn't exactly a hypervisor, it is built to be the perfect solution for homelabbers. It is free, open-source, and has a lot of the software below ready to be installed at the press of a button. Being based on debian/ubuntu, it can also manage docker, podman, and KVM/Qemu.

### [oVirt](https://www.ovirt.org/)
oVirt is free, open-source virtualization management platform. It was founded by Red Hat as a community project on which Red Hat Enterprise Virtualization is based. It allows centralized management of virtual machines, compute, storage and networking resources, from an easy to use web-based front-end with platform independent access. KVM on x86 64 architecture is the only hypervisor officially supported, but there is an ongoing effort to support PPC and ARM architectures in the future releases.

* [oVirt Cluster Setup ^tutorial](https://www.reddit.com/r/homelab/wiki/software/ovirt)

###[Proxmox Virtual Environment](https://www.proxmox.com/en/proxmox-ve)
Proxmox Virtual Environment is an open-source server virtualization environment. It is a Debian-based Linux distribution with a modified RHEL kernel and allows to deploy and manage virtual machines and containers.

###[SmartOS](https://www.joyent.com/smartos)
SmartOS is an open-source in memory operating system built on [illumos](https://en.wikipedia.org/wiki/Illumos) (the continuation of OpenSolaris), using [zones](https://en.wikipedia.org/wiki/Solaris_Containers) (lightweight containerization, called "OS VMs"), and KVM or bhyve for hardware virtualization. SmartOS is the base of [Triton](https://www.joyent.com/triton) (formerly known as SmartDataCenter) as well as [Project-FiFo](https://project-fifo.net/), two open-source cloud orchestration platforms.

###[Nutanix Community Edition](https://www.nutanix.com/products/community-edition/)
Bare-metal *converged* hypervisor based off of KVM. Nutanix AHV (Acropolis Hypervisor) is widely used in commercial and government spaces. Free edition will run on a single, three, or four hosts. Will automatically tier storage between SSD and spinning disk, among a bunch of other cool things.

## Hosted Hypervisors (Type 2)

###[VMware Workstation](http://www.vmware.com/uk/products/workstation)
VMware Workstation Pro transforms the way technical professionals develop, test, demonstrate and deploy software by running multiple x86-based operating systems simultaneously on the same PC.
###[VMware Fusion](https://www.vmware.com/au/products/fusion.html)
VMware Fusion gives Mac users the power to run Windows on Mac along with hundreds of other operating systems side by side with Mac applications, without rebooting. Fusion is simple enough for home users and powerful enough for IT professionals, developers and businesses.
###[Oracle VirtualBox](https://www.virtualbox.org/)
VirtualBox is a powerful x86 and AMD64/Intel64 software virtualization product for enterprise as well as home use. Not only is VirtualBox an extremely feature rich, high performance product for enterprise customers, it is also the only professional solution that is freely available as Open Source Software under the terms of the GNU General Public License (GPLv2).
###[Parallels Desktop 12 \(Mac\)](http://www.parallels.com/products/desktop/)
Use both Mac and Windows applications on your Mac without rebooting! Microsoft Office for Windows, Internet Explorer, Access, Visual Studio, AutoCAD, Project, Visio, and hundreds of others.


## Networking
### [OPNsense](https://opnsense.org/)
OPNsense is open source, FreeBSD-based firewall and routing software developed by Deciso, a company in the Netherlands that makes hardware and sells support packages for OPNsense. Additionally, it can be setup on hardware or virtualized, touted for its reliability, offering great features with no cost. It is a fork of pfSense, which in turn was forked from m0n0wall, which was built on FreeBSD. It was launched in January 2015.
###[pfSense](https://www.pfsense.org/)
pfSense is easily /r/homelab's go to software firewall, with many enterprise options and it's easy management it's great for all users, skilled or not. pfSense is an open source firewall/router computer software distribution based on FreeBSD. It is installed on a physical computer or a virtual machine to make a dedicated firewall/router for a network and is noted for its reliability and offering features often only found in expensive commercial firewalls.
### [OpenWRT](https://openwrt.org/)
The OpenWrt Project is a Linux operating system targeting embedded devices. Instead of trying to create a single, static firmware, OpenWrt provides a fully writable filesystem with package management. It is targeted towards numerous WLAN routers, which means you can customize the router to your preferences, without having to deal with locked, proprietary firmware.
### [DD-WRT](https://dd-wrt.com/)
DD-WRT is the project OpenWRT was based on, and is generally viewed as legacy only. DD-WRT does not include a package management system, unlike OpenWRT
### [Open vSwitch](http://openvswitch.org/)
Open vSwitch is a production quality, multilayer virtual switch licensed under the open source Apache 2.0 license.  It is designed to enable massive network automation through programmatic extension, while still supporting standard management interfaces and protocols.
### [VyOS](https://wiki.vyos.net/wiki/Main_Page)
VyOS is a Linux-based network operating system that provides software-based network routing, firewall, and VPN functionality. VyOS is a free, open-source community fork of Vyatta. It can run on any hypervisor and features a fully scriptable CLI. It supports major network protocols like BGP, OSPF, MPLS, IPsec and several others. One of the coolest features of VyOS is its DMVPN support.  It allows you to have VPNs back to a Hub, then allow for the automatic creation of spoke-spoke VPN tunnels as needed.
### [Sophos UTM Home Edition](https://www.sophos.com/en-us/products/free-tools/sophos-utm-home-edition.aspx)
Sophos UTM 9 Home offers enterprise Firewall protection and various other features for free.  "It features full Network, Web, Mail and Web Application Security with VPN functionality and protects up to 50 IP addresses."
### [Sophos XG Firewall Home Edition](https://www.sophos.com/en-us/products/free-tools/sophos-xg-firewall-home-edition.aspx)
Sophos XG Firewall Home offers "Next-Gen" enterprise firewall protection, and is the spiritual successor to UTM 9.  Much like UTM 9, this is free as well.  "Features full protection for your home network, including anti-malware, web security and URL filtering, application control, IPS, traffic shaping, VPN, reporting and monitoring, and much more."

## Storage
### [DrivePool](https://stablebit.com/DrivePool)
DrivePool is a state of the art disk pooling application that features file and directory duplication.  It combines any drive you wish to add to the pool so that Windows thinks is one drive (it’s a virtual drive).  It uses the NTFS filesystem that is standard in all Windows machines and can be controlled as such.  There are no limits to the size of the disk that can be added to the pool and you can have different sized disks in the same pool while going beyond the 16TB NTFS maximum.
### [DriveBender](http://www.division-m.com/drivebender/)
The class leading storage pooling technology for Microsoft Windows. Developed by Division-M, Drive Bender allows for file redundancy via file duplication, and unlike RAID, does not require any proprietary drive format or complicated setup. (Now free)
### [CloudExtender] (http://www.division-m.com/cloudxtender/)
Local Windows storage, powered by the cloud... with optional, state of the art TNO (trust no one) file encryption built right in. Create a Windows drive or folder that maps directly to your favorite storage platform in minutes.
### [unRAID](https://lime-technology.com/)
A network-attached storage operating system that can be run from a USB stick to share our disks. The newest version (6.2), enables dual-parity drives, cache pooling, and up to 24 assignable disks.
### [SnapRAID](http://www.snapraid.it/)
A backup program for disk arrays. It stores parity information of your data and it recovers from up to six disk failures.
### [flexRAID](http://www.flexraid.com/)
A family of storage data protection products that provide great flexibility and various innovations. The current product line includes: RAID over File System (RAID-F) Transparent RAID (tRAID).
### [FreeNAS](http://www.freenas.org/)
An operating system that can be installed on virtually any hardware platform to share computer data storage over a computer network. Please see the [FreeNAS Hardware Recommendation Thread](https://forums.freenas.org/index.php?threads/hardware-recommendations-read-this-first.23069/) for more info. 

[**Can I virtualize FreeNAS?**](https://www.reddit.com/r/homelab/wiki/hardware/virtfreenas)
###[napp-it](https://napp-it.org/)
A highend ZFS storage solution without the cost.
Please visit these threads for questions.  [Here is the ServeTheHome forum](https://forums.servethehome.com/index.php?threads/napp-it-and-omnios-esxi-zfs-appliance-it-works.2476/) where the dev 'Gea' helps out & also [here on Hardforum](https://hardforum.com/threads/opensolaris-derived-zfs-nas-san-omnios-openindiana-solaris-and-napp-it.1573272/)
### [Rockstor](http://rockstor.com/)
A free and open source NAS (Network Attached Storage) solution. It's a software solution and can be installed on any hardware or a virtual machine satisfying these minimum requirements.
### [XigmaNAS](http://www.xigmanas.com/)
The XigmaNAS operating system can be installed on virtually any hardware platform to share computer data storage over a computer network. [XigmaNAS hardware requirements](https://www.xigmanas.com/wiki/doku.php?id=xigmanas_users_hardware)
### [Xpenology](http://xpenology.com/)
The name of a Linux boot image, which allows to run operating system Sinology DSM on almost any hardware (not just Synology).
### [owncloud](https://owncloud.org/)
A self-hosted file sync and share server.
### [Nextcloud](https://nextcloud.com/)
A fork of ownCloud designed to be more community focused. Nextcloud is a drop-in replacement for ownCloud.
### [openFiler](https://www.openfiler.com/)
Provides a simple way to deploy and manage networked storage.
### [openATTIC](http://openattic.org)
openATTIC combines open source storage tools in such a way that their entire functionality can be managed through a central interface. Carefully matched components ensure both stability and security. Its open interface enables you to integrate openATTIC to provisioning, monitoring and backup systems.
### [OpenMediaVault](http://www.openmediavault.org/)
The open network attached storage solution. Great for beginners with a simple and intuitive web interface that does not require a lot of resources.
### [Storage Spaces Direct](https://blogs.technet.microsoft.com/filecab/2016/11/21/deep-dive-pool-in-spaces-direct/)
Available only on Windows Server 2016 and later, Storage Spaces Direct builds on the previous Storage Spaces technologies to offer a homogeneous shared-nothing storage solution that scales similarly to ScaleIO. Storage and compute are on the same nodes, reducing cost and complexity.

## Monitoring
### [Nagios](https://www.nagios.org/)
A powerful monitoring system that enables organizations to identify and resolve IT infrastructure problems before they affect critical business processes.
### [OMD](http://omdistro.org/)
OMD avoids the tedious work of manually compiling and integrating Nagios addons while at the same time avoiding the problems of pre-packaged installations coming with your Linux distribution. It bundles Nagios together with many important addons and can easily be installed on every major Linux distribution.
### [Pandorafms](http://pandorafms.com/)
The most flexible monitoring software in the market. With a single tool, Pandora FMS can monitor everything: infrastructure, applications, services, and business progress.
### [PRTG](https://www.paessler.com/prtg)
A network monitoring software that is powerful and easy to use. Free for 100 sensors.
### [Zabbix](http://www.zabbix.com/)
The ultimate enterprise-level software designed for real-time monitoring of millions of metrics collected from tens of thousands of servers, virtual machines and network devices.
### [Observium](http://www.observium.org/)
A low-maintenance auto-discovering network monitoring platform supporting a wide range of device types, platforms and operating systems.
### [LibreNMS](http://www.librenms.org/)
A fully featured network monitoring system that provides a wealth of features and device support.
### [Cacti](http://www.cacti.net/)
A complete network graphing solution designed to harness the power of RRDTool's data storage and graphing functionality.
### [Munin](http://munin-monitoring.org/)
Surveys all your computers and remembers what it saw. It presents all the information in graphs through a web interface.
### [ZenOSS](https://www.zenoss.com/)
An award winning, open source monitoring product that automatically discovers resources, without the use of agents, and provides visibility across all aspects of your IT environment whether physical, virtual.
### [AlienVault  OSSIM](https://www.alienvault.com/products/ossim)
An open source security information and event management system. OSSIM combines Snort, OpenVAS, Nagios, OSSEC, and other tools into a single portal with log collection and correlation.
### [Graylog](https://www.graylog.org/)
Centralize and aggregate all your log files for 100% visibility. Use our powerful query language to search through terabytes of log data to discover and analyze important information.
### [Sensu](https://sensuapp.org/)
Monitoring that doesn't suck. Monitor servers, services, application health, and business KPIs. Collect and analyze custom metrics. Get notified about failures before your users do.
### [Spiceworks Network Monitor](http://www.spiceworks.com/free-network-monitoring-management-software/)
Spiceworks is a free network monitoring software that runs on Windows. It's very easy to set up and use, although it's a bit limited.
### [Cabot](http://cabotapp.com/)
Self-hosted, easily-deployable monitoring and alerts service - like a lightweight PagerDuty.
### [Desktop Central](https://www.manageengine.com/products/desktop-central/)
Self-hosted, inventory and patch management for Windows and Linux.  Really nice to automate updates of OS and 3rd party.  Supports up to 25 devices for free. Also includes MDM for mobile devices.
### [Splunk](http://splunk.com/)
Splunk can ingest system data and logs and allow you to graph them. Deployment is simple, but configuring monitoring can be complex, but incredibly flexible. They offer 500mb/day free tier.
### [Domotz] (http://www.domotz.com)
Aimed more at device integrators, but very useful for homelabbers, Domotz includes simple SNMP monitoring (including CPU, mem, and network), as well as port monitoring, web site monitoring and they can do push notifications through their app. They also allow you remote access back to your network through their cloud. It is not free, but at ~$3/month, very inexpensive. 
### [Moloch](https://github.com/aol/moloch)
Moloch is an open source, large scale, full packet capturing, indexing, and database system for analyzing network traffic. 

## Configuration Management
### [Ansible](https://www.ansible.com/)
Ansible is an open source software that automates software provisioning, configuration management, and application deployment. Ansible connects via SSH, remote PowerShell or via other remote APIs.

### [The Foreman](https://theforeman.org/)
Foreman (also known as The Foreman) is an open source complete life cycle systems management tool for provisioning, configuring and monitoring of physical and virtual servers.

* [The Foreman ^tutorial](https://www.reddit.com/r/homelab/wiki/software/theforeman)

### [r10k](https://github.com/puppetlabs/r10k)
R10k provides a general purpose toolset for deploying Puppet environments and modules. It implements the Puppetfile format and provides a native implementation of Puppet dynamic environments.

* [r10k ^tutorial](https://www.reddit.com/r/homelab/wiki/software/r10k)

## Media
### [Plex](https://plex.tv/)
Plex is a media server software package that organizes all of your media and can allow you access to it anywhere in the world on nearly every device available.  It supports multiple file formats with movies, music, and photos while transcoding any media to devices that can’t support it.
### [Emby](https://emby.media/)
Media server for personal streaming movies tv music photos in mobile app or browser for all devices including android, iOS, windows phone, appletv, androidtv, smarttv, and dlna.
### [Kodi](https://kodi.tv/)
Kodi® Kodi® (formerly known as XBMC™) is an award-winning free and open source (GPL) software media center for playing videos, music, pictures, games, and more. Kodi runs on Linux, OS X, Windows, iOS, and Android, featuring a 10-foot user interface for use with televisions and remote controls.
### [Jellyfin](https://github.com/jellyfin/jellyfin)
The Free Software Media System. (Fully open source fork of Emby)

### [Oblecto](https://github.com/robinp7720/oblecto)
Oblecto is a fully open source media server with the ability to federate with other Oblecto instances.


## Remote Access
### [Guacamole](https://guacamole.incubator.apache.org/)
A clientless remote desktop gateway. It supports standard protocols like VNC and RDP.
### [Chrome Remote Desktop](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en)
Allows users to remotely access another computer through Chrome browser or a Chromebook.
### [mRemoteNG](http://www.mremoteng.org/)
A fork of mRemote, an open source, tabbed, multi-protocol, remote connections manager. mRemoteNG adds bug fixes and new features to mRemote.
### [NoMachine](https://www.nomachine.com/)
Get to your desktop at the speed of light. NoMachine is the fastest remote desktop you have ever tried. Control any computer in the world and start working on it
### [X2go](http://wiki.x2go.org)
Open source, FAST remote access to Linux desktops.  Forked from the NoMachine NX libraries before they went proprietary, X2go's advantages are being Free Software, actively developed, and running entirely through SSH tunnels.  No need to open vulnerable services to the WAN.  Clients available for Windows, Mac, Linux, BSD.
### [Terminals](https://github.com/terminals-Origin/Terminals)
Terminals is a secure, multi tab terminal services/remote desktop client for Windows that supports RDP/VNC/VMRC/SSH/Telnet/RAS/ICA Citrix, and HTTP/HTTPS viewers
### Remote Desktop Gateway
Remote Desktop Gateway (or RDG) is a Windows Server specific role which proxies Remote Desktop (RDP) connections from your favorite RDP client over an externally accessible HTTPS connection, allowing you to more easily bypass strict firewalls, as well as integrate it with your existing web infrastructure, such as behind a web application firewall, load balancer, or reverse proxy.
### [Domotz] (http://www.domotz.com/)
Aimed more at device integrators, but very useful for homelabbers, Domotz includes simple SNMP monitoring (including CPU, mem, and network), as well as port monitoring, web site monitoring and they can do push notifications through their app. They also allow you remote access back to your network through their cloud. It is not free, but at ~$3/month, very inexpensive.
### [OpenVPN] (https://openvpn.net/download-open-vpn/)
OpenVPN is a server, appliance, or service you can run on your network to allow secure access to your network. It is present on OPNsense and pfSense firewall appliances, as well as available to be installed on a server or deployed as a virtual appliance. Fully capable and allows for lots of customization and configuration for clients. 
### [Wireguard] (https://www.wireguard.com/)
WireGuard is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache. It intends to be considerably more performant than OpenVPN. Easy to setup on a [Raspberry Pi](https://pivpn.io/). 
### [Firezone] (https://github.com/firezone/firezone)
Open source remote access manager that uses WireGuard. It has a good web UI, and supports SSO and MFA. It can be hosted on most Linux distros.
### [Tactical RMM] (https://github.com/amidaware/tacticalrmm)
Tactical RMM is a remote access, monitoring & management tool, built with Django and Vue. It uses an agent written in golang and integrates with MeshCentral.
It supports Windows, Linux with Systemd and Mac including apple silicon.


## Remote Configuration / Management
### [Webmin](http://www.webmin.com/)
Webmin is a web-based interface for system administration for Unix. Using any modern web browser, you can setup user accounts, Apache, DNS, file sharing and much more. 
### [Ajenti](http://ajenti.org/)
Ajenti is a Linux & BSD web admin panel.
### [InterWorx](http://interworx.com)
InterWorx is a Linux-based web hosting control panel that provides a graphical interface and automation tools designed to simplify the process of hosting a website. Note: Resellers can provide a single-domain free license.
### [cPanel](http://www.cpanel.com/)
cPanel is a Linux-based web hosting control panel that provides a graphical interface and automation tools designed to simplify the process of hosting a web site.
### [Cockpit](http://cockpit-project.org/)
Cockpit is an interactive server admin interface for GNU/Linux. It is easy to use and very light weight.
###[Windows Admin Center](https://docs.microsoft.com/en-us/windows-server/manage/windows-admin-center/understand/windows-admin-center)
Windows Admin Center is a free new browser-based app made by Microsoft for managing Windows Servers, Clusters and Windows 10 PCs. It is the recommended solution to manage Windows Server Core installations and is incredibly easy to use.


## VoIP
### [Asterisk](http://www.asterisk.org/)
An open source framework for building communications applications. Asterisk turns an ordinary computer into a communications server.
### [FreePBX](https://www.freepbx.org/)
A web-based open source GUI (graphical user interface) that controls and manages Asterisk (PBX).
### [3CX](http://3cx.com/)
A Windows or Linux based VOIP Software. Free for 16 sim. calls.

## Backup
### [Duplicati](https://www.duplicati.com/)
Free backup software for Windows, macOS, and Linux supporting tons of backend destinations such as Backblaze B2, Tardigrade, Microsoft OneDrive, Amazon S3, Google Drive, box.com, Mega, hubiC
### [xapi-back](https://github.com/izderadicka/xapi-back)
A simple backup tool for XenServer or XCP – xen hypervisors using xapi toolstack. xapi-back is a command line tool with simple and clear interface (command + options). The tool is written in python.
### [Veeam Endpoint Backup Free](https://www.veeam.com/endpoint-backup-free.html)
Provides a simple solution for backing up Windows-based desktops and laptops.
### [FOG](https://fogproject.org/)
A free, open source computer cloning solution.
### [ERPXE](http://erpxe.com/)
A complete PXE solution featuring a broad range of recovery tools and various OS installations in one box.
### [VSquare](http://www.vsquarebackup.com/)
Backup suite for ESXi and Hyper-V. Supports the free ESXi version over SSH.
###[Veeam Availability Suite v9.5](https://www.veeam.com/data-center-availability-suite.html)
Veeam Availability Suite v9.5 is a combination of Veeam Backup & Replication™ and Veeam ONE™ , can backup Hyper-V and VMware ESXi ([Veeam v9.5u1](https://www.veeam.com/kb2222) supports VMware v6.5 products as of 20Jan17.)
###[unitrends free](http://www.unitrends.com/products/software/unitrends-free)
Virtual appliance-based backup for ESXi and Hyper-V with enterprise features, such as cloud integration and instant VM recovery, and protects up to 1.0 TB of data (for free!).
###[VDP](https://www.vmware.com/files/kr/pdf/vsphere/VMware-vSphere-Data-Protection-Overview.pdf)
End of Life announced 4/5/2017. vSphere 6.5 will be the last supported version.
VMware vSphere Data Protection, native ESXi backup. Easy to use but [requires](http://www.virtuallyghetto.com/2013/11/how-to-evaluate-vsphere-data-protection.html) internal forward and reverse DNS lookup.
###[vSphere Standalone Converter](https://my.vmware.com/web/vmware/info?slug=infrastructure_operations_management/vmware_vcenter_converter_standalone/5_5)
Not strictly a backup solution, this tool converts physical machines to virtual machines and permits conversion between vm formats.
###[XSI Backup](https://33hops.com/xsibackup-vmware-esxi-backup.html)
Compatible with both free and commercial versions of VMWare ESXi, from ESXi 5.1 upwards.
###[Export-VApp - vSphere PowerCLI](https://www.vmware.com/support/developer/PowerCLI/PowerCLI51/html/Export-VApp.html)
Exports a vApp or a single virtual machine as an .OVA or .OVF file. Requires installation of [PowerCLI](https://www.vmware.com/support/developer/PowerCLI/).
###[BackupPC](https://backuppc.github.io/backuppc)
A simple level file level backup manager. Supports compression and deduplication. Runs great from [Docker](https://hub.docker.com/r/adferrand/backuppc/)
###[Restic](https://restic.net/)
restic is a backup program that is fast, efficient and secure. It supports the three major operating systems (Linux, macOS, Windows) and a few smaller ones (FreeBSD, OpenBSD).

## Documentation
### [DokuWiki](https://www.dokuwiki.org/dokuwiki#)
A simple to use and highly versatile Open Source wiki software that doesn't require a database.
### [gollum](https://github.com/gollum/gollum)
A simple, Git-powered wiki with a sweet API and local frontend.
### [BookStack](https://www.bookstackapp.com/)
A simple, self-hosted, easy-to-use platform for organizing and storing information.
### [phpIPAM](http://phpipam.net/)
An open-source web IP address management application (IPAM).
### [Paperwork](https://openpaper.work/en/) / [Paperwork GitHub](https://gitlab.gnome.org/World/OpenPaperwork/paperwork)
Aims to be an open-source, self-hosted alternative to services like Evernote ®, Microsoft OneNote ® or Google Keep ®.
### [Confluence](https://www.atlassian.com/software/confluence)
Feature rich wiki software. Costs $10 (one time cost) and can be integrated with Atlassian's other software such as Jira and HipChat. Support for Atlassian server products ends on February 2, 2024
### [MediaWiki](https://www.mediawiki.org/wiki/MediaWiki)
MediaWiki is a free and open source software wiki package written in PHP, originally for use on Wikipedia.

## Network Diagrams
### [diagrams.net (formerly draw.io)](https://app.diagrams.net/)
Free online diagram creating with export/save functions!
### [Gliffy](https://www.gliffy.com/)
Create professional-quality Flowcharts, Wireframes, UML diagrams, and more.
### rackdiag
Simple diagrams for racks.
### [blockdiag](http://blockdiag.com/en/)
Simple diagrams for networks.
### [RackTables](http://racktables.org/)
A nifty and robust solution for data center and server room asset management.
### [yEd Graph Editor](https://www.yworks.com/products/yed)
A powerful desktop application that can be used to quickly and effectively generate high-quality diagrams.

## Dashboards
### [Netdata](https://github.com/firehol/netdata/)
### [PRTG](https://www.paessler.com/prtg) 
Offers 100 sensors for free. 
### [Kibana](https://www.elastic.co/products/kibana)
Integrates with Elasticsearch and Logstash to form the [ELK stack](https://www.elastic.co/webinars/introduction-elk-stack).
### [Grafana](http://grafana.org/)
### [freeboard](https://freeboard.io/)
### [JumpSquares](http://www.jumpsquares.net/)
###[SexiGraf](http://www.sexigraf.fr/) 
Baked in with Grafana and support for vCenter.
###[SexiLog](http://www.sexilog.fr/)
## IP Address and Infrastructure Management
### [NetBox](https://netbox.readthedocs.io/en/stable/)
Web based IP Address management and infrastructure management developed by DigitalOcean. Extremely easy to install using Docker containers. [GitHub repo is located here](https://github.com/digitalocean/netbox)
### [phpIPAM](http://phpipam.net/)
Open source IP address management
### [TEEMIP](http://www.combodo.com/teemip-194)
TeemIp is an Open Source web 2.0 application that enables professional IP Management activity within IT departments of all sizes.
It provides to network administrators a simple and powerfull toolset to manage their IPv4 and IPv6 plans, subnet space and IPs in accordance with best in class IP management practices.
### [NIPAP](http://spritelink.github.io/NIPAP/)
Python based IPAM software utilizing postgresql's powerful ipaddr column type. Powerful features include tagging, allocation pools, and a powerful search feature.  nipap is a sleek, intuitive and powerful IP address management system built to handle large amounts of IP addresses.
### [NSoT](https://github.com/dropbox/nsot)
Network Source of Truth (NSoT) a source of truth database and repository for tracking inventory and metadata of network entities to ease management and automation of network infrastructure.  NSoT is an API-first application that provides a REST API and a web application front-end for managing IP addresses (IPAM), network devices, and network interfaces.
### [Splunk](http://splunk.com/)
Splunk can ingest system data and logs and allow you to graph them. Deployment is simple, but configuring monitoring can be complex, but incredibly flexible. They offer 500mb/day free tier.
## More ideas
### [Awesome Selfhosted](https://github.com/Kickball/awesome-selfhosted)
This is a list of Free Software network services and web applications which can be hosted locally.