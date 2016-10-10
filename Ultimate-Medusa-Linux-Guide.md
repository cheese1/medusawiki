### The Ultimate Medusa Linux Guide

This guide will detail setting up Medusa on a Linux machine, along with all the bells and whistles. This ultimate guide was written based on a real-world setup, and, may or may not be what your end desire is, but it should be generalized enough to help you on your quest for the solution that fits your needs perfectly.

###### Specific Sections:
* Installation
    * [Prerequisites](#prerequisites)
    * [Linux Setup](#linux-setup)
    * [Medusa Installation](#medusa-installation)
    * [Deluge Installation](#deluge-installation)
    * [Plex Media Server Installation](#plex-media-server-installation)
    * [OpenVPN](#openvpn)
    * [Apache](#apache)
* Configuration

#### Prerequisites

This guide will cover a lot of material, and includes a lot of optional components. As not all of these will apply to you. Please go over the list carefully, as I'll try to detail what you'll need in most situations.

1. A Linux box. Mine is also my LAN's router/gateway, but, this can be anything reasonably powerful. Please don't try to run this full setup on a Pi. Distro matters very little, but this guide is written based on an Arch setup. If you know enough about your distro, this shouldn't be any problem for you at all. Obviously you're here to install Medusa, so making this part optional would be pointless.

2. A Bit Torrent client or an NBZ setup. For my needs, I went with Deluge, but almost any daemon that SR supports will work just fine. If you want to go NZB, SABNZB+ has worked quite well for me in the past. One or the other is required, both if you wish. Pointless to have a Medusa with out this, so, again, mandatory.

3. Plex Media Server. Totally optional but highly recommended, Medusa integrates quite nicely into it.

4. An OpenVPN provider. Yes, we're totally going there with this. OpenVPN providers are fairly cheap and a great way to ensure your downloading your shows will not attract the attention of your ISP. I use [TigerVPN](http://www.tigervpn.com) but anything that supports OpenVPN will work just fine. And again, totally optional.

#### Linux Setup

We're going to install Medusa on our linux system manually. Why not use the package manager? Well, it can cause problems under certain circumstances (Medusa will update itself from git), and, this is just a much cleaner solution. If you absolutely insist on using the package manager, be warned that upgrades can easily break and your package manager can fail to update the package, so you'll have to --force it or something similar.

First, we need to decide where this installation and all our media files will live. This will be a fairly large amount of data, so, it should be on a big enough partition to handle it. Mine is in _/srv/media_ but yours can be anywhere you want/have enough space.

Second, we need to pick a user to run this all as. We're going to be using a single user account on the linux box to run Medusa, Deluge, and, Plex, so that we don't run into major file permissions and other things down the road. For me, I created a user of _media_ with a UID and GID of _420_. Since we're **not** using the distro's package manager, we'll have to create this user manually. If you are using your distro's package manager, **do not** skip this step, and make sure you run the _additional_ step below afterwards.

    groupadd -g 420 media
    useradd -g media -u 420 -d /srv/media -s /usr/bin/nologin -m

The first line will add a group named _media_ with a GID of 420. The second line will create a user named _media_ in the group _media_, with a UID of 420, with a home directory of _/srv/media_ and a login shell of _/usr/bin/nologin_ (to prevent the shell from being able to be logged into directly).

_If you decided to use your distro's package manager after all, please edit your **/etc/passwd** and **/etc/group** files, and alter the UID and GID of the **Medusa** user to be the same as the UID/GID of the **media** (420). This will ensure that Medusa runs as the "media" user **anyway** with out having to manually change all the configuration files every time your distro wants to upgrade Medusa (which is unnecessary, usually)._

#### Medusa Installation

Now, we need to perform the actual installation of Medusa. If you have used your distro's package manager, you can skip this step. We created _/srv/media_ earlier when we created the _media_ user, so, that's where we'll put it.

    cd /srv/media
    git clone https://github.com/pymedusa/Medusa.git

Next, we need to create the startup file that controls Medusa. If you're on a recent distro, you're possibly running _systemd_ in which case, this script will work for you. If you are **not** on a _systemd_ distro, you will need to get your own startup script (or, use the one that came with your package manager).

Edit the file _/etc/systemd/system/medusa.service_ (it will not exist, so, create it).
Copy and paste the following into it:

    [Unit]
    Description=Medusa Daemon
    After=network.target

    [Service]
    Restart=always
    User=media
    Group=media
    ExecStart=/usr/bin/env python2 /srv/medusa/SickBeard.py --quiet --config /srv/medusa/config.ini --datadir /srv/medusa

    [Install]
    WantedBy=multi-user.target

Save it, and enable it to run at startup: `systemctl enable medusa.service`

Congrats, you've installed Medusa. Now, we'll need to install the other mandatory pieces, and, configure the whole thing.

#### Deluge Installation

We're going to just use the package manager to install Deluge, as it doesn't self-update, or tend to conflict with itself. If you're on Arch, the command is: `pacman -S deluge`

After it has been installed, edit your _/etc/passwd_ and _/etc/group_ files to replace the UID and GID for the _deluge_ user with the UID/GID from the _media_ user (420). We want Deluge running as _media_ as well.

Lastly, make sure you enable it to run at startup:
    systemctl enable deluged.service
    systemctl enable deluge-web.service

#### Plex Media Server Installation

The easiest way to install Plex is to just use the package manager. Some distros have two, one for plex, one for plex-pass. Both usually install to the same location, and only one can be installed at a time, so pick which ever one meets your needs, and install it via the package manager. If it isn't in your package manager, you'll want to install it via the official instruction at the [Plex Website](https://support.plex.tv/hc/en-us/articles/200288586). Please note that you should set up your media server nearly fully, at this point, excluding any media libraries you want to have. We'll set those up later, in _/srv/media_.

One thing you'll need to do, in addition to the installation procedure at Plex's website, is change the user ID that the server runs as. So before you begin to configure it - before you even start the service for the first time, you'll want to edit your _/etc/passwd_ and _/etc/group_ files once more, and change the UID and GID of the _plex_ user/group to _420_ just like we did for the torrent daemon above. We want Plex to also run as the _media_ user for easy management and access to our content.

#### OpenVPN Installation

We'll need to install OpenVPN, and configure it, if you are going to go this route, too. The reason for using a VPN is a moot dicussion here - either you want or need to use one, or, you do not. The how and why of your decision is not relevant to the instuctions, and is not something that the Medusa team wishes to debate. If you do not wish to use a VPN, please skip this section. Otherwise, please continue.

OpenVPN is best installed through your package manager. I am unaware of any distributions (aside from those with out a package management system, AKA Linux From Scratch) which do not have it available. And if you're using Linux From Scratch, you probably don't need the step by step here, just the magic at the bottom on how to get the multiple routes working nicely.

Once the package is installed, we're going to mostly be relying on your VPN provider's setup instructions, with a few modifications to meet our specific requirements. Your provider (if they're anything like mine) will have given you an OpenVPN configuration file (likely named openvpn.conf) which contains sane defaults for most people. Well, we are not "most people", and as such, there's a few things that we need to do differently. Here is the contents of my config file, and a comment above each line detailing what it does. Your file may contain other directives that aren't in mine, and, it may contain directives with different values than mine. I'll attempt to detail what you'll need to change in your config file, and why, so that your settings do what they should will providing the functionality we need. If you do have any questions about this step, please contact us in IRC to ask for help.

First, rename this file to something unique. My VPN is provided by TigerVPN, and I'm using their NL server specifically, so, I named my file tiger-nl.conf, and tossed it in my OpenVPN root dir (/etc/openvpn). 

	# tiger-nl.conf - VPN Client Config
	# 
	# Remote server IP or hostname, port, protocol - this one is UDP
	remote <hostname> 1194 udp
	# Remote server IP or hostname, port, protocol - this one is TCP
	remote <hostname> 443 tcp-client
	# Pull settings from server when possible
	pull
	# Authentication is username/password based, as opposed to certificate based.
	auth-user-pass
	# Type of compression to use
	comp-lzo adaptive
	# Certificate file for your provider. Name it ca.crt and place in /etc/openvpn, or, change this value.
	ca /etc/openvpn/ca.crt
	# Device type to use - tun or tap. Use tun if at all possible.
	dev tun
	# Our client speaks TLS
	tls-client
	# The security level of the config. 2 means we allow external scripts - you need this!
	script-security 2
	# Cypher to use for the VPN.
	cipher AES-256-CBC
	# Mute level
	mute 10

	# Our VPN username and password is stored in this file. Make it owned by root, with 600 perms, so only root can read it.
	auth-user-pass /etc/openvpn/tiger-nl.cred

	# DNS stuff
	resolv-retry infinite
	# Provider specific key setting.
	persist-key
	# Enable this if you can. Preferred, but not strictly needed.
	persist-tun
	# Provider specific certificate setting.
	remote-cert-tls server

	# Most of the below you explicitly need... Make sure you include it.
	# This tells OpenVPN to not make the execute the default routing instructions. This way, your normal traffic doesn't use the VPN.
	route-noexec
	# Delay 2 seconds to invoke routing scripts.
	route-delay 2
	# When the VPN goes up, execute this script. Name yours the same as mine, or, change this value.
	up /etc/openvpn/tiger-nl.up.sh
	# When the VPN goes down, execute this script. Name yours the same as mine, or, change this value.
	down /etc/openvpn/tiger-nl.down.sh

Now that we have the main config file out of the way, you can see the real magic is that we explicitly disable OpenVPN from using the VPN as the default route, and instead, opt to run our own script when the VPN goes up or down. We will be keeping this VPN up 24/7 but the connection drops and gets restarted depending on the internet connection, the VPN server's stability, and a lot of other factors. Here are the scripts you'll need.

	# tiger-nl.up.sh
	#!/bin/sh

	ip route flush table 10
	ip route add table 10 to $route_vpn_gateway/$ifconfig_broadcast dev $dev
	ip route add table 10 to default via $route_vpn_gateway dev $dev

	ip rule add fwmark 10 lookup 10

	sysctl -w net.ipv4.conf.tun0.rp_filter=2

	sed -i '/vpn.internal.ip/d' /etc/hosts
	echo "$ifconfig_local vpn.internal.ip" >>/etc/hosts

	iptables -t nat -I POSTROUTING -m mark --mark 10 -o $dev -j MASQUERADE

	# tiger-nl.down.sh
	#!/bin/sh
	ip rule del fwmark 10 lookup 10
	ip route flush table 10

	sed -i '/vpn.internal.ip/d' /etc/hosts

	iptables -t nat -D POSTROUTING -m mark --mark 10 -o $dev -j MASQUERADE

Make sure those two scripts are named approproately for your config file, and, that they are chmod 755.

Next, we'll need to make OpenVPN start at boot with this config file, and, restart when the connection is dropped. So that means more _systemd_ tuning. First, lets see if you have an openvpn@ service in the first place. You want to execute the command _systemctl list-unit-files | grep openvpn_ and see if there's anything returned. If you simply get another shell prompt, we're missing that service file, which is fine. We'll create it now. If you have it listed, however, that's fine too, we'll use it, but skip the next paragraph and unit file after it. This assumes your OpenVPN config directory is /etc/openvpn - if it isn't, ensure you change that to yours.

So you're missing your openvpn@ service file. This is not entirely unexpected. The @ means it's expecting an argument, which in the case of OpenVPN, is the name of the config file. This lets you have multiple simultaneous VPNs to different networks controlled, and is the best way to go. No, we don't care if you have an openvpn entry with out the @. You'll want to edit _/etc/systemd/system/openvpn@.service_ and stick the following into it...

	[Unit]
	Description=OpenVPN connection to %i
	After=network-online.target

	[Service]
	Type=forking
	ExecStart=/usr/bin/openvpn --cd /etc/openvpn --config /etc/openvpn/%i.conf --daemon openvpn@%i --writepid /run/openvpn@%i.pid
	PIDFile=/run/openvpn@%i.pid
	Restart=always
	RestartSec=30

	[Install]
	WantedBy=multi-user.target

If you have an openvpn@.service entry, however, and did not just create one using the above directions, you'll need to do the following to make your OpenVPN connection restart whenever it drops. Those people who did the above can skip this section and config file, as I've included your required parameters in the core service file itself.

First, create the directory _/etc/systemd/system/openvpn@.service.d_ and please note that you may need to backslash the @ if using a terminal to do this. Inside this directory, we're going to place two files into it: _customdependency.conf_ and _restart.conf_.

customdependency.conf:

	[Unit]
	After=network-online.target

restart.conf

	[Service]
	Restart=always
	RestartSec=30

Now, you should be able to enable systemd to start your VPN connection at boot, and it will reconnect when it gets dropped. Lets tell systemd to start it at boot: _systemctl enable openvpn@tiger-nl.service_ (make sure you replace tiger-nl with your config file name before the .conf part)

If all goes well, your VPN should pop up. You can check the logs with _journalctl_ to debug it, or a simple _ip link_ to see if the interface is up.

#### Apache

I could write a book on configuring Apache. No, really. This section is also very much optional, and for a different reason than everything else. My setup uses Apache, on an external host, to protect my Medusa and Deluge management system running on my LAN. The reason for this is three-fold:
1. Access inside and outside my LAN to the web interface with the same configuration.
2. Protection from people finding my server externally if they're trying to look for it.
3. Better SSL termination, performance, and protection from rogue requests. 

If you don't care to access your interfaces outside your LAN, you can 100% skip this section. If you don't care if anybody can find your installation by port scanning your IP address, you can 100% skip this section. If you don't care about the performance hit of some automated function hitting your installation, you too can 100% skip this section. For the rest of you (or, if you're just curious), read on.

So my Apache installation is actually *not* on the same box that I run everything else on. It's on a linux machine (VPS, specifically) somewhere else, and, this makes it harder for others to find my installation, and easier for me to make sure my clients work everywhere (on, and, off my LAN). While some apps like ShowsRage allow you to connect differently to the same server depending on your SSID, the same is not true for the vast majority of things, and, some routers don't accept connections to port forwards from the LAN side of things. There's also the challenge that some ISPs block incoming connections on some ports, or, you may not want your stack exposed to just anybody. After all, a bunch of GET requests to a wordpress template file isn't going to do Medusa any good, nor the attacker any good either, but they're going to try no matter what. So the best way I've found to handle all of this is to just use Apache as a front end, remotely, and proxy everything over it, allowing only my VPS's IP address to connect directly to Medusa and Deluge's web interfaces. This has another benefit: hiding it behind a vhost.

Apache is best installed through the package manager, and, should require fairly minimal configuration. You want to ensure your Apache package has mod_proxy and mod_ssl installed along with it (some distros include these, others are additional installs). mod_ssl is usually separate, while mod_proxy is usually included, but your mileage may vary. 

Once Apache and the modules are installed, you will need to enable them. Your distrobution will (very likely) have detailed instructions on how best to go about this. Arch was just editing my _/etc/httpd/conf/httpd.conf_ and uncommenting the **LoadModule** line containing the mod_proxy directives (mod_proxy, mod_proxy_connect, and mod_proxy_http). On Gentoo, it's even easier, editing _/etc/conf.d/apache_ and adding "-D PROXY" to the config line. Ubuntu has their own [recommended method](https://help.ubuntu.com/community/ApacheReverseProxy) for those on that particular distro.

Once you have that particular module enabled, we're going to do the rest in a vhost config file to make life really easy. Here is my vhost config file for Deluge. It lives in _/etc/httpd/conf/extra/vhost-deluge.conf_ (your vhost dir may vary).

	<VirtualHost *:443>
	    ServerAdmin email@address
	    ServerName deluge.domain.tld
	    SSLEngine on
	    SSLOptions +StdEnvVars
	    SSLCertificateFile "/etc/letsencrypt/live/deluge.domain.tld/fullchain.pem"
	    SSLCertificateKeyFile "/etc/letsencrypt/live/deluge.domain.tld/privkey.pem"
	    SSLProxyVerify none
	    SSLProxyCheckPeerCN off
	    SSLProxyCheckPeerName off
	    SSLProxyCheckPeerExpire off
	    ProxyRequests Off
	    <Location />
	        ProxyPass https://router-dyn-dns-entry:3001/
	        ProxyPassReverse http://router-dyn-dns-entry/
	        ProxyPassReverseCookieDomain router-dyn-dns-entry %{HTTP:Host}
	        RequestHeader append X-Deluge-Base "/"
	    </Location>
	    ErrorLog "/var/log/httpd/deluge.domain.tld-error_log"
	    CustomLog "/var/log/httpd/deluge.domain.tld-access_log" common
	</VirtualHost>

Obviously, change _deluge.domain.tld_ to your specific subdomain, and change _router-dyn-dns-entry_ to your router's dynamic DNS address. If you have a static IP address on your LAN, you can use it instead. If you don't, get a dyndns provider (there's a few free ones), though you can set up an SSH tunnel or use ngrok if you need to. Both are beyond the scope of this guide (for now).

Please note that the above also is for HTTPS and does SSL encryption. You can change the _:443_ to _:80_ and remove the first 4 _SSL*_ lines (not the _SSLProxy*_ ones, unless you have SSL disabled on Deluge or whatever you're using, in which case change https to http in the router-dyn-dns-entry line) if you don't want that. Note that my encryption certificates are provided by the free CA [letsencrypt.org](https://letsencrypt.org). Lastly, we're using port 3001 to talk to the LAN, so if your service is located at a different port, use it instead or we'll set up a forward for it later.

My Medusa vhost is located at _/etc/httpd/conf/extra/vhost-medusa.conf_ (your vhost dir may vary) and looks like this:

	<VirtualHost *:443>
	    ServerAdmin email@address
	    ServerName medusa.domain.tld
	    SSLEngine on
	    SSLProxyEngine on
	    SSLOptions +StdEnvVars
	    SSLCertificateFile "/etc/letsencrypt/live/medusa.domain.tld/fullchain.pem"
	    SSLCertificateKeyFile "/etc/letsencrypt/live/medusa.domain.tld/privkey.pem"
	    SSLProxyVerify none
	    SSLProxyCheckPeerCN off
	    SSLProxyCheckPeerName off
	    SSLProxyCheckPeerExpire off
	    ProxyRequests Off
	    <Location />
	        ProxyPass https://outer-dyn-dns-entry:3000/
	        ProxyPassReverse https://outer-dyn-dns-entry/
	        ProxyPassReverseCookieDomain outer-dyn-dns-entry %{HTTP:Host}
	    </Location>
	    ErrorLog "/var/log/httpd/medusa.domain.tld-error_log"
	    CustomLog "/var/log/httpd/medusa.domain.tld-access_log" common
	</VirtualHost>

Again, same as above, change _medusa.domain.tld_ to your specific subdomain, and change _router-dyn-dns-entry_ to your router's dynamic DNS address. Pretty much the same notes apply here, too: port 3000 is being used to talk to Medusa, if you're running on a different port, change it here, or, we'll set up a port forward later.

Of note, you'll probably want a default :443 vhost which gets loaded whenever somebody hits an undefined subdomain, or, your apache server's raw IP address. This means that they won't get Medusa or Deluge's web interface unless they know exactly what hostname to connect to. It provides some protection against people finding your installation, but more importantly, it provides a sanity screening for the automated exploit bots all over the internet. I can't count the number of requests I get per hour of bots looking for wordpress vulnerabilities, or IIS buffer overflows, etc. While they won't harm Medusa or Deluge, both stacks are written in python which is a bit slower than Apache, and arguably take up more resources to get hit, so, the fewer things that aren't necessary hitting those two stacks the better - let them hit Apache instead.