# An Introduction to Homelabs

### Why build a homelab?

The answer is easy: to learn. IT professionals, amateurs, and people who just really like computers use homelabs to experiment in. It's a sandbox environment where if you break it, you fix it, and more importantly it isn't costing money while it's down. 

*Homelab [hom-læb] (n): a laboratory of (usually slightly outdated) awesome in the domicile*

Some people use them to study - for example, a Cisco certification - and some people use them in production to learn new technologies.

Chances are, if you're considering building a lab, you already have a purpose in mind. If not, if I can give you one piece of advice then let it be this: think carefully about what you want to achieve. 24 core, dual-CPU R710s are great fun but unnecessary if you want a web development server. Likewise, a CCNA lab will be useless to you if your plans include hyper-converged cloud computing. It sounds obvious, I know; but it's all too easy to get distracted by a great eBay deal, impulse buy then end up with a 900w paper weight.

Looking at some posts around here, you'll notice a wild variety of labs. Some of my all time favourites include [/u/illallangi](https://reddit.com/u/illallangi)'s [apartment friendly nuc lab](https://imgur.com/a/GO43m), [/u/Mutant_Tractor](https://reddit.com/u/Mutant_Tractor)'s [power guzzling Dell-fest](http://imgur.com/a/zXpsQ) and [/u/onyx9](https://reddit.com/u/onyx9)'s [CCNA lab](https://www.reddit.com/r/homelab/comments/1hb6ly/my_ccnaccnp_lab/?). There's a lot of variation here. The point is that you should build the lab that you want or need depending on your intentions.

### Some uses for a lab

* [Self hosting](https://reddit.com/r/selfhosted) - Host popular services on your own hardware. Just for the fun of it.
 * [Ubooquity](https://vaemendis.net/ubooquity/) - home server for comics and ebooks.
 * [MusicBrainz](https://musicbrainz.org/doc/MusicBrainz_Server/Setup) - mirror for the IMDB of music, works with Headphones.
 * [Headphones](https://github.com/rembo10/headphones) - manage your music.
 * [MadSonic](http://beta.madsonic.org/pages/index.jsp) - stream your music collection.
 * [Calibre](https://manual.calibre-ebook.com/index.html) - eBook server
 * [Muximux](https://github.com/mescon/Muximux) - lightweight portal to manage your webapps.
 * [Organizr](https://github.com/causefx/Organizr/) - Another feature-packed lightweight portal to manage your webapps.
* Game servers - Host a Minecraft server to play privately with friends or because you enjoy playing god.
* Media servers - Multi-room streaming or a centralised location for your music and movies
 * [Plex](https://www.plex.tv/) - most popular and best supported option out there, and along with Plex you can run a whole collection of support services.
 * [Emby](https://emby.media/) - a popular alternative to Plex.
 * [Jellyfin](https://jellyfin.org) - open-source alternative to Plex and Emby.
 * [Tautulli](https://github.com/Tautulli/Tautulli) - tons of stats for your Plex server's usage. (Formally PlexPy)
 * [Sonarr](https://sonarr.tv/) - manage your TV shows.
 * [SickRage](https://sickrage.github.io/) - manage your TV shows.
 * [Radarr](https://radarr.video/) - a new way to manage your movies.
 * [CouchPotato](https://couchpota.to/) - manage your movies.
 * [Mylar](https://github.com/evilhero/mylar) - manage your comic books.
 * [NZBHydra](https://github.com/theotherp/nzbhydra) - NZB Indexer aggregator, similar in form to Jackett.
 * [Jackett](https://github.com/Jackett/Jackett) - translates queries from apps (Sonarr, Radarr, SickRage, CouchPotato, Mylar, etc) into tracker-site-specific http queries.
* Storage - Archives, backups, centralised storage.
 * [NextCloud](https://nextcloud.com/) - Who needs DropBox / Google Drive / Amazon Drive when you can roll your own?
 * [Veeam](https://www.veeam.com/blog/how-to-get-free-veeam-nfr-key.html) - Learn Veeam to backup your VMs
 * [FreeNAS](http://www.freenas.org/) - Free NAS software, can be virtualized or run on physical hardware
* Web hosting - Host websites for friends or family for free.
 * [IIS](https://www.iis.net/) - Microsoft Internet Information Services.
 * [Apache](https://www.apache.org/) - Open source Web Server. 
 * [Nginx](https://nginx.org/en/) - An alternative to Apache.
* Virtualisation - The fundamental OS in many homelabs is a hypervisor. They allow budding sysadmins to setup nested, throwaway environments starting on just one piece of hardware (it doesn't even need to be an enterprise grade server).
 * [Docker](https://www.docker.com/)
 * [ESXi](https://www.vmware.com/products/vsphere-hypervisor.html)
 * [unRAID](https://lime-technology.com/)
 * [Hyper-V](https://technet.microsoft.com/en-us/library/hh846766\(v=ws.11\).aspx)
 * [Proxmox](https://www.proxmox.com/en/)
* Networking - Everyone should learn a bit about networking. Did you know you can simulate entire networks using software?
 * [GNS3](https://www.gns3.com/)
 * [pfSense](https://pfsense.org/)
 * [OPNsense](https://opnsense.org/)
 * [Pi-hole](https://pi-hole.net/)
 * [Network Monitor](https://www.spiceworks.com)
 * [OpenVPN](https://openvpn.net/)
 * [VyOS](https://vyos.io/)
 * [IPFire](https://www.ipfire.org/)
* Certifications - Certifications are a great way to make your CV stand out over other candidates and expand/hone your skills. It's possible to get your CCNA or VCP without a lab but hands on practice will be a lot more enjoyable.
* Monitoring
 * [Splunk](https://www.splunk.com/) - data analytics and logging, including a SYSLOG server
 * Syslog - log collation built into *nix to feed Splunk (or other Security Information Event Manager)
 * [What's Up Gold](https://www.ipswitch.com/application-and-network-monitoring/whatsup-gold) monitoring and alerting!
* Security Software
 * [Snort](https://www.snort.org/) - intrusion prevention software (IPS)
* Infrastructure Tools
 * [Chef](https://www.chef.io), [Puppet](https://www.puppet.com), or [Ansible](https://www.ansible.com/) - server configuration and deployment managers, heavily used in data centers
 * [Guacamole](https://guacamole.incubator.apache.org/) clientless remote gateway to access your server from elsewhere


###What can I do with it all?

First off, take a look at the common projects section. Second, don't think of it as "what do I do with this stuff" or "what can I do", but look at it in terms of "what can you learn". Many homelab owners use theirs to either brush up on technology they're already familiar with or give themselves a leg up on things they've never worked with before. When it comes to working in IT, there is no such thing as learning too much about your systems.

The easiest thing to do (and where most start out) is to look at your work environment. For example, a small business might have AD (Active Directory), some hosted storage, and maybe an Exchange server. If you don't know how to set up AD, then there's your first project! Build an AD server and see if you can connect your home computer to it, then try experimenting with permissions. Learn through experimentation and trial & error; you're not going to be able to do these in a production environment, and that's what a homelab is for!

### Final thoughts

Labs are largely used for experimentation before rolling stuff into a production environment, learning and/or practice involving all of the above plus much more. They're fun. They're expensive. They're a hobby. Ultimately, for most people, a homelab is a plaything that occasionally gets out of hand.

