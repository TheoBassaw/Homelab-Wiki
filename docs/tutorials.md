#Tutorials and How-To's

This is a work-in-progress for now, take what you see here with a grain of salt.


## SNMP Quick Setup on Debian based machines
    sudo apt-get install snmpd
    sudo mv /etc/snmp/snmpd.conf  /etc/snmp/snmpd.conf.org
    sudo nano /etc/snmp/snmpd.conf

rocommunity  public

syslocation  "Reddit"

syscontact  admin@reddit.com

    sudo nano /etc/default/snmpd

\#SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid -c /etc/snmp/snmpd.conf'

    sudo nano /etc/init.d/snmpd restart


##Unlocking a R720XD Google T4 appliance

If you're considering an R710, an R720XD would likely be a better choice. 

If you've acquired one of these it's easy to reset the bios password and make it a standard R720XD.


**Resetting the BIOS password**


Download the ISO from this [link](https://www.dell.com/support/home/us/en/04/drivers/driversdetails?driverid=0xm0c): And make it bootable with Rufus. 

Boot the server off the usb (should do it automatically) And let the updates finish.

The BIOS should be updated to the newest version, along with the firmware for all other system components. There's a jumper near the PSU/behind the CPU's. Set it to reset the password (since you ran the update disc the BIOS will recognize the jumpers)

http://i.imgur.com/WpRzszb.png

Don't forget to move the jumpers back to where they were after the password has been cleared.

Now you're done. Throw in the drives and create a new array! 


**(Optional) Removing the Google Branding.**


After following this process, the system will be identified as a Dell R720XD DBE. The Dell boot logo will be restored, along with the iDRAC and software update logos within your OS. 

Another benefit of removing the Google branding is that the DRAC licensing option will be restored, allowing you to apply an iDRAC enterprise key. 

Please note that this change is not currently reversible. There are no known drawbacks to following this procedure.

- Boot the server, and enter the setup menu (press F2 when prompted)
- Select 'iDRAC Settings' and then 'Network'
- Choose one of the onboard NICs to use for iDRAC communication (LOM1-4) and attach it to your network. Enter IP address information further down the page. You won't be able to use the dedicated NIC until an enterprise license has been activated.
- Go back to the previous page and choose 'User Configuration'
- Remove the default Google iDrac username and password and set your own.
- Press 'Finish' to apply your settings. You may need to reboot the server for the changes to take effect.

- Download the compressed Identity module [here](https://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=4WYV6).
- Extract the Identity module.
- Browse to http://ip-address-of-the-iDRAC and enter the credentials that you specified above.
- In the left-hand menu, expand the option 'iDRAC Settings' and choose 'Update and Rollback'
- Choose the extracted Identity module and then 'Upload'
- Under the 'Update Details' section, select your .pm file and 'Install'
- In the left-hand menu, expand the option 'Server' and choose 'Job Queue'
- Once the job has completed, reboot the server. The system will come up with the branding again but a message will pop up stating that the branding is being modified. Once complete, your server will reboot and the branding will have gone. You may need to remove power to the server so that the iDRAC can reset properly.

- You can now apply an iDRAC7 enterprise key. These can be purchased from eBay or from a Dell partner. To apply a 30 day trial, download and boot from the following [ISO](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=3NHMY).
- You can pop off the cover for the dedicated NIC and configure the iDRAC to use it instead of one of the LOM ports.



##UPS AUTO SHUTDOWN

###SAFETY FIRST

**Human Safety**

**NEVER PULL A POWERED UPS POWER CABLE FROM THE MAINS**

The UPS must **always maintain proper earth grounding** during simulated power outage tests. Use the switch on a power strip in-line between the UPS and the Mains to simulate a power outage. This will keep the ground wire connected at all times. Do not connect your servers to this power strip as it will be turned on and off repeatedly to simulate power outages. 

[Grounding Requirements for APC Products](http://www.apc.com/us/en/faqs/index?page=content&id=FA157422)

**Data Safety**

Connect all servers (or one power supply on dual equipped servers) directly to the Mains. Use a different power strip from the one powering the UPS. The server should **not** be powered by the UPS during the initial software setup. This will reduce the risk of accidental data loss resulting from a hard shutdown as some settings can instruct the UPS to turn off abruptly. 

**Simulated Power Outage**

Use the power switch on the power strip inline to the UPS to simulate an outage. Flip the switch and monitor the logs. (e.g. tail -f /var/log/apcupsd.events) The server should begin to notice the loss of power in 30-60 seconds. Make adjustments to your configuration and repeat the tests. Once the shutdown software testing is stable, move the server power cables back to the UPS for final load testing. Adjust the shutdown percentages or shutdown times as needed.

###QNAP

    System Settings -> External Device -> UPS

**USB**

A USB cable is auto detected. QNAP shows battery percentage on the web GUI page (System Settings / External Device / UPS). Set to "Turn off the server AC after power fails". Tested with an APC Back-Ups RS 700G with included RJ45->USB cable. 

    # Settings to check in GUI
    USB Connection
    Turn off the server after the AC power fails for minutes: 1

**Network**

IP address of the APC AP9617 network card required. Uses SNMP protocol. Battery runtime populated automatically. Tested with SMART-UPS 1400 & AP9617 card. 

    # Settings to check in GUI
    SNMP Connection
    IP Address: 10.0.0.5
    Turn off the server after the AC power fails for minutes: 1

**Notes**

QNAP took 3+ minutes to shutdown. An event entry was created. A single beep noted the shutdown, but nothing was visible on the QNAP LCD during shutdown. 

[QNAP Docs](http://docs.qnap.com/nas/4.0/en/index.html?ups.htm)

###Proxmox

Install apcupsd

    apt install apcupsd

Edit the settings in /etc/apcupsd/apcupsd.conf as appropriate for your cable type. 

    nano /etc/apcupsd/apcupsd.conf

**Serial**

    UPSCABLE smart      # gray apc smart cable
    UPSCABLE 940-0095A  # or use the cable part number
    UPSTYPE apcsmart
    DEVICE /dev/ttyS1

**Network**

Set DEVICE ip:apc:passphase where passphrase is the Authentication Phrase set from the AP9617 internal web gui System / User Manager (older firmware). Configuration / Shutdown (newer v6.4.0 firmware)


    UPSCABLE ether
    UPSTYPE pcnet
    DEVICE 10.0.0.5:apc:apc1234567890apc

**SNMP Network**

DEVICE is hostname:port:vendor:community

    UPSCABLE ether
    UPSTYPE snmp
    DEVICE 10.0.0.5:161:APC:private


**USB**

    UPSCABLE usb
    UPSTYPE usb
    #DEVICE #device is not needed. UPS is auto detected. 

**Common Settings**

    UPSNAME officeups1  #arbitrary UPS name
    BATTERYLEVEL 50     #Shutdown at 50% power remaining
    MINUTES 5           #Shutdown at 5 minutes power remaining
    TIMEOUT 60          #Shutdown when on battery for 60 seconds - 0 to disable and use percentage

**Final Setting**

Then set in /etc/default/apcupsd

    ISCONFIGURED=yes

Reboot or run 

    /etc/init.d/apcupsd start 

**Troubleshooting**

Forgetting to set ISCONFIGURED will result in apcupsd acting like it is not working at all. 
    
    service apcupsd restart           # Restart the service
    tail -f /var/log/apcupsd.events   # Check the logs
    apcaccess                         # Show current apcupsd status


###VMWare

**Prerequisites**

  * APC 9617 Network Card with a fixed IP
  * All virtual machines must have VMWare Tools installed
  * APC VMWare Appliance with a fixed IP. PowerChute Network Shutdown v4.1 VMWare Virtual Appliance ([Download PCNS v4.1](http://www.apc.com/tools/download/download.cfm?sw_sku=SFPCNS41-V&software_id=AKRN-9ZPCT8&family=&part_num=SFPCNS41-V&swfam=&tsk=&swtyp=)) 

**Network Card**

Setup a fixed ip address and email notifications. A black APC serial cable may be needed to configure the card. The default apc/apc username and password will work, but an Authentication Phrase must be setup in System / User Manager (older firmware) or Configuration / Shutdown (newer v6.4.0 firmware). I used 'apc1234567890apc', it will be needed in the VM setup. Firewall might need UDP 3052 & TCP 3052, 6547, & 80 opened, but was not needed on a stock ESXi 6.0.0 test. 

**Appliance VM**

Install the OVA appliance file using the vSphere Client desktop application. File -> Deploy OVF Template. Once uploaded, start the VM in the Console and configure basic network settings. Reboot for final configuration via web browser. Open https://ipaddress:6547 to access the PCNS web page. Select 'Configure Events'. Enable shutdown in the 'UPS on Battery', 'Runtime remaining below threshold', and 'Battery Discharged shutdown' settings.  

**vSphere settings**

Set the APC Appliance to be first in the Configuration tab -> Virtual Machine Startup/Shutdown -> Properties -> Startup Order as that will make it last to shutdown. Set the Shutdown Action to Guest Shutdown. Make sure all VMs have the VMWare Client Tools installed. Check the Summary tab of each virtual machine to verify.  

[How to: Shutdown ESXi host in case of a power failure](https://www.vmguru.com/2013/06/how-to-shutdown-esxi-host-in-case-of-a-power-failure/)

[How to: Shutdown Synology DSM 6.0 from APC](https://www.reddit.com/r/homelab/comments/4ry5n8/powerchuteesxisynology/)

###FreeNAS

**USB**

Back-Ups RS700 (BR700G) USB

    Services -> Wrench icon
    Driver: 'APC UPS 2 Back-UPS RS USB USB (usbhid-ups)'

Search for the USB port

    [root@freenas] ~# grep usb /var/log/messages
    Dec 30 20:14:11 freenas ugen1.6: <American Power Conversion> at usbus1
    Dec 30 20:15:53 freenas notifier: Connected to UPS [ups]: usbhid-ups-ups

    Port: /dev/ugen1.6   #as found in the search.

The remaining setting can be left at their defaults. User: upsmon Password: fixmepass work fine. Enable Email updates and enter an address. 

**To monitor the UPS**

A working battery looks like this.

    [root@freenas] ~# tail -f /var/log/ups.log
    20151230 205553 100 121.0 0 [OL] NA NA
    20151230 210053 100 121.0 0 [OL] NA NA
    20151230 210553 100 122.0 0 [OL] NA NA

**Serial**

APC SMART-UPS 1400 using Gray APC 940-0095A Smart Signaling UPS Cable, driver 'APC ups 1 Back-UPS 940-0095A/C cables (genericups upstype=1)' and port '/dev/cuau0'. 

    [root@freenas] ~# tail -f /var/log/ups.log
    20151230 223820 NA NA NA [OL] NA NA
    20151230 224320 NA NA NA [OL] NA NA

Note the lack of voltage values, but the Online code OL is present. 

    [root@freenas] ~# grep uart /var/log/messages
    Dec 30 16:43:09 freenas uart1: <16550 or compatible> port 0x2f8-0x2ff irq 3 on acpi0
    Dec 30 16:43:09 freenas uart0: <16550 or compatible> port 0x3f8-0x3ff irq 4 flags 0x10 on acpi0

Black APC 940-0024C Smart Signaling UPS cable does not appear to be supported. They appear to be more like null modem cables for use in configuring the network interfaces on AP9617 cards. 

**Network**

    Driver: APC PDU3 (various) SNMP monitoring card (SNMP-UPS)
    Port: 10.0.0.5 (ip address of APC 9617 card)
    Auxiliary parameters (ups.conf):
    mibs=apcc
    community=public

###Drobo Pro

iSCSI connected Drobo Pro to server on a UPS. After your server shuts down, your Drobo device will go into standby mode (orange or yellow power indicator). When your computer shuts down, any data in transit to the Drobo device will be safely transferred to the disks. Your data is safe.

###Downloads

[APC Serial cable Wiring diagrams](http://lists.alioth.debian.org/pipermail/nut-upsuser/2005-August/000118.html)

##Setting up Microsoft Certificate Authority for Smart Card authentication

Smart Cards are a reasonable inexpensive means of hardware-based authentication. You can even find a smart card in your chip-based credit/debit card. However it won't work for our purposes.

The thing with smart cards is that the driver for the reader doesn't matter as much as the driver for the card itself. I have had good luck with a [PivKey C910](https://www.amazon.com/PIVKey-C910-PKI-Smart-Card/dp/B00SJV2CNK/) and a [generic smart card reader](https://www.amazon.com/Rocketek-RT-SCR1-Military-Compatible-Windows/dp/B00PY0CNYM/). Honestly it won't matter what reader you get for the most part. I just got the cheapest one I could find.

Now, you have to have a Windows environment with Active Directory and an Enterprise certificate authority. This is not a guide on how to install and configure those so I'll leave that bit out for now. This assumes your certificate authority is set up correctly. 

First, open MMC (Win-R, type "mmc" and press enter). In the File menu, add the Certificate Templates and Certification Authority snap-ins. In Certificate Templates, duplicate "Smartcard User" template. Change the OS compatability based on what server and client OS you will be using. Give it an appropriate name and change the validity period to 5 years.

In the Request Handling tab, make sure the purpose is "Signature and Encryption" and check the box "Include symmetric algorithms allowed by the subject." Also be sure that the "Enroll subject without requiring any user input" is selected.

In the Cryptography tab, check "Requests must use one of the following providers" and then use "Microsoft Base Smart Card Crypto Provider"

In the Insssuance tab, check "This number of authorized signatures" and put in 1. Make sure that Policy Type is "Application Policy" and Application Policy is "Certificate Request Agent."

Next, right click on the "Certificate Templates" node, then select "New" and then select "Certificate Template to Issue". Select the certificate template you just made.

Next, on a client machine, open MMC and open the Certificate snap-in for My User. In "Personal" request a certificate for "Enrollment Agent." If there is no Enrollment Agent certificate, then use the same steps above to add the existing Enrollment Agent certificate template to the Certification Authority.

Now you are ready to enroll smart cards. If you are enrolling a card for yourself, request a certificate for the Smart Card template you made earlier, and that's it! Obviously you will want to change the user and admin PIN. To change the user pin, insert the card, press CTRL-ALT-DELETE and select "Change Password". There should be a piece of text that says "Sign-in Options". Press that, select the smart card icon, and there you are. Depending on your smart card your pin will have some restrictions, e.g. for the C910 it has to be 6 characters.

##Installing NextCloud on Ubuntu 16.04 with Apache2, LetsEncrypt, Redis, and APCU.

[Link to vroomtech.io  tutorial](https://vroomtech.io/2016/09/15/installing-nextcloud-on-ubuntu-16-04-lts-with-apache2-lets-encrypt-redis-and-apcu/)

[Link to Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-16-04)

##Setting up Nginx reverse proxy with Let's Encrypt certificates.
[Well written serverfault answer](https://serverfault.com/a/784940)

[Link to part 1]() [DEAD LINK]

[Link to part 2]() [DEAD LINK]

##Installing Guacamole 0.9.13 on Ubuntu 16.04 LTS with MySQL Authentication
[Link to Tutorial and Script](http://chasewright.com/guacamole-with-mysql-on-ubuntu/)

##Router on a stick with pfSense
[Permalink to homelab post](https://www.reddit.com/r/homelab/comments/5ntzh4/the_one_ethernet_pfsense_router_vlans_and_you_or)

##UPS server on Raspberry Pi
[Permalink to homelab post](https://www.reddit.com/r/homelab/comments/5ssb5h/ups_server_on_raspberry_pi/)

##How to use non-HP drives in ProLiant G5/G6/G7 without the fans spinning up
~~[Permalink to homelab post](https://redd.it/5zmlpf)~~

##What can/should I do whilst labbing Active Directory and Windows at home?
~~[Link to guide](https://powernerd.xyz/homelabbing-windows-active-directory/)~~

[archive.org version](https://web.archive.org/web/20170403192440/https://powernerd.xyz/homelabbing-windows-active-directory/)

##A very detailed build log and tutorial on the 60TB FreeNAS server I put together a few months ago
[Permalink to homelab post](https://www.reddit.com/r/homelab/comments/648cbc/a_very_detailed_build_log_and_tutorial_on_the/)

##How to Reverse Airflow in a Cisco C3750X Fan Module (C3KX-FAN-23CFM)
[Permalink to homelab post](https://www.reddit.com/r/homelab/comments/7onneu/a_visual_guide_to_reversing_the_airflow_in_a/)

##Grafana/InfluxDB Tutorial
[GoogleDocs Link]  (https://docs.google.com/document/d/11TlMypqyeeKK4vLGz9MfcITFMQyIrRjokCdc89YbMAM/edit?usp=sharing)

##Activating Windows Server SKUs and Hyper-V VMs with AVMA.
[Permalink to homelab post] (https://www.reddit.com/r/homelab/comments/megxpe/how_to_activating_windows_server_skus_and_hyperv/)

##Nutanix CE Guides
[Homelab link to part 1]
(https://www.reddit.com/r/homelab/comments/nibqe1/nutanix_ce_a_installation_guide_startup/)
[Homelab link to part 2]
(https://www.reddit.com/r/homelab/comments/niszb6/nutanix_guide_part_2/)

[NTX Files link] (https://www.reddit.com/r/homelab/comments/nlx33o/nutanix_services_files/)

