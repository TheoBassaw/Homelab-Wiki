# Sound Levels, Heat and Power

One of the most talked about topics when getting into home-labbing is HEAT and NOISE. Most hardware spec sheets will include pertinent information regarding heat output (in BTU/Hour) and noise (dBa). The following information has been aggregated from official documentation. 


##A Word on Data

###General

Since data presented varies from company to company (and from model to model) the most conservative (usually worst case), generalized values were used from given spec sheets to give the best indication of noise and heat output. These values are manufacturer best-case, usually at room temperature (23-25 degC) and no load.

###What about Watts?

Power wattage of a power supply for any given device is not indicative of ACTUAL wattage used, but can be used to get a quick value for the absolute maximum wattage the system could use (useful for when calculating the minimum current rating you should have on a circuit running the server). This varies wildly from configuration to configuration. How many CPUs, how many Hard Drives and how many sticks of RAM all change the actual wattage pulled. Therefore it is not included here as there are no official values for this kind of data. Actual Wattage used can be calculated using a device such a a Kill-A-Watt or using the below configuration tools from HP and Dell to configure their respective servers for an estimated value. Devices such as switches are a little more consistent with their usage and you may find information regarding their typical usage or typical usage at certain loads (PoE vs. non-PoE, how many physical connections, modules, etc)


###dB (Idle) vs dB (Operating) vs. Other

These two values are the most common found across all data sheets. Idle represents the machine running while Operating will represent hard drive activity noise (not necessarily stress) Some other states include Standby(dBa) and Stress(dBa). These states are not included as they are not universal.

###BTU/hr

These values have a lot of variance. From what can be gathered the BTU/hr SHOULD represent the entire device as a whole, but may only be the power supply itself. Older generation and fixed power supply devices will report one value for BTU/hr. These values are all calculated at a manufacturer rated wattage. Voltages will make these values change slightly, all of the below values are for 120 Vrms. The HP servers (and some Dell) show multiple values, this is because of the modular nature of the HP Common Slot power supplies which will change the BTU/hr rating depending on which ones are present in the server.

###Dell Rack Config Utility

For Dell servers (current models) you can go to the following configuration tool instead of looking up spec sheets. This will calculate cost, BTU, dB and kWh. ~~[Here](http://essa.us.dell.com/DellStarOnline/DCCP.aspx?c=us&l=en&s=gen&Template=6945c07e-3be7-47aa-b318-18f9052df893)~~ DEAD LINK

Dell has upgraded their Rack Config Utility to the Enterprise Infrastructure Planning Tool: [Here](http://dell-ui-eipt.azurewebsites.net/#/)

###HP Power Advisor

For HP servers, this will calculate power and BTU along with giving you the granularity of configuring specific parts to calculate estimated Wattage and cost. Really great tool and works for older generations. Does not include dB level of servers which is the only drawback. [Here](http://www.hpe.com/servers/poweradvisor/online)


#Servers

Brand | Model | dB (Idle) | dB (Operating) | BTU/hr
-------|--------|------------|------------------|---------				
HP|Microserver G8|18|21|682 (150W) / 840 (200W)
HP|ML 310e G8|26|28|1773
HP|ML 350 G5|33|33|4112
HP|ML 350 G6|32.48|32.4|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 360 G4|50|53|2000
HP|DL 360 G5|60|75|2910
HP|DL 360 G6 (1 CPU)|	27|32|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 360 G6 (2 CPU)|	33|38|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 360 G7 (1 CPU)|	27|32|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 360 G7 (2 CPU)|	33|38|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 360p G8|34|35-42|
HP|DL 380 G4|58|58|2508
HP|DL 380 G5|44|44|3530
HP|DL 380 G6|22|28|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 380 G7|22|28|1173 (460W) / 2892 (750W) / 3375 (1200W)
HP|DL 380p G8|25|35|1794 (460W) / 2925 (750W) / 3530 (1200W)
Dell|R210|49|49|1039
Dell|R210 II (Core i3)|38|38|1040
Dell|R210 II (E3-1200)|40|41|1040
Dell|R510 (4 bay)	|40|40|1840
Dell|R510 (8 bay)	|42|42|2200
Dell|R510 (12 bay)|51|51|2450
Dell|R610 (1 CPU)|34|37|2446
Dell|R610 (2 CPU)|35|37|2446
Dell|R610 (2 CPU + PERC6/E)|44|44|2446
Dell|R710|39|42|1944(570W) / 2968 (870W)
Dell|R720|25|26|1908 (495W) / 2891 (750W) / 4100 (1100W)
Dell|R720XD|28|30|1908 (495W) / 2891 (750W) / 4100 (1100W)
Dell|R810| x | x |4012


#Switches

Brand | Model | dB (Idle) | dB (Operating) | BTU/hr
-------|--------|------------|------------------|---------	
Arista|7124S|-|70|-
Cisco|3560-24TS|	-|42|89
Cisco|3560-48TS|	-|42|153
Cisco|3560-24PS|	-|42|144
Cisco|3560-48PS|	-|42|293
Cisco|3560G-24TS|-|42|249
Cisco|3560G-48TS|-|48|422
Cisco|3560G-24PS|-|38-44|325
Cisco|3560G-48PS|-|52-58|443
HP|2910-24G al|-|39.4 - 53.5|279
HP|2910-48G al|-|39.4 - 53.5|356
HP|2910-24G-PoE+ al|-|38.1 - 51.5	|447
HP|2910-48G-PoE+ al|-|38.1 - 51.5	|667
Juniper|EX2200-48T|-|31 (JUNOS 12.3R5.7 or lower) - 40 | 140
Ubiquiti|48P Non-POE|-|21|