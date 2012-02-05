---
date: '2002-12-11 19:51:18'
layout: post
slug: securing-wifi-with-openvpn
status: publish
comments: true

title: Securing WiFi with OpenVPN
wordpress_id: '61'
categories:
- Technology
---

Ever since I set up my wireless LAN at home, I've been looking into how to make it more secure. Because WEP is not really secure, I was looking into setting up a VPN. But all the solutions I found (FreeS/WAN, CIPE), were way too complicated for the simple act of creating a secure tunnel between my desktop machine and my laptop.
Enter [OpenVPN](http://openvpn.sf.net),  a real quick VPN solution. (don't worry, it can also be made much more complicated)

So, let's cut straight to how I set things up:

The OpenVPN tarball contains a spec file, so you can build an RPM with a simple rpm -ta openvpn-VERSION.tar.gz. But the spec file links OpenVPN with the LZO compression library. [Querying RPMfind](http://rpmfind.net/linux/rpm2html/search.php?query=lzo) finds a prepackaged RPM for Red Hat, which works.

After installing OpenVPN, we need to generate a secret key. The command for that is openvpn --genkey --secret static.key, which will create a file called static.key. This gets copied into the /etc/openvpn directory on both the laptop and the desktop.

The next step is to write the configuration files. First, the configuration for the laptop (laptop.conf):

    
    
    #
    # Sample OpenVPN configuration file for
    # using a pre-shared static key.
    #
    # '#' or ';' may be used to delimit comments.
    
    # Use a dynamic tun device.
    dev tun
    
    # Our remote peer
    remote 192.168.1.1
    
    # 10.4.0.1 is our local VPN endpoint
    # 10.4.0.2 is our remote VPN endpoint
    ifconfig 10.4.0.2 10.4.0.1
    
    up /etc/openvpn/laptop.up
    # Our pre-shared static key
    secret /etc/openvpn/static.key
    
    



Important is the line _up /etc/openvpn/laptop.up_, this tells OpenVPN to call this script, after the tunnel has been established. This script gets called with all kinds of parameters, best check the manpage for details.
We just need one parameter, the correct tun-device. That's $1, so laptop.up looks like this:

    
    
    #!/bin/sh
    
    route add default $1
    
    


Don't forget to _chmod 755_ it.

The desktop configuration looks almost the same, just some changes and switches concerning the IPs:

    
    
    #
    # Sample OpenVPN configuration file for
    # using a pre-shared static key.
    #
    # '#' or ';' may be used to delimit comments.
    
    # Use a dynamic tun device.
    dev tun1
    
    # Our remote peer
    remote 192.168.1.131
    
    # 10.4.0.1 is our local VPN endpoint
    # 10.4.0.2 is our remote VPN endpoint
    ifconfig 10.4.0.1 10.4.0.2
    
    # Our pre-shared static key
    secret /etc/openvpn/static.key
    
    



So, what does all this do?

It creates an encrpyted tunnel between 192.168.1.1 (desktop) and 192.168.1.131 (laptop), using the IPs 10.4.0.1 (desktop) and 10.4.0.2 (laptop). Then on the laptop, it adds a default route to the tunneling device, so all external connections are going through the encrypted link.
Since this is the first time I did this, there might be some kinks in it, so if anybody finds some faults or improvements, please let me know, so I can incorporate them.
  *[VPN]: Virtual Private Network
