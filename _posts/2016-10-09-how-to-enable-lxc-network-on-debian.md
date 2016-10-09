---
layout: post
title: How to enable lxc network on debian jessie?
description: lxc network
tags: lxc network debian
comments: true
permalink: how-to-enable-lxc-network-on-debian-jessie
sitemap:
  lastmod: 2016-10-09
---
The LXC packages in Ubuntu ships enable LXC networking properly. This is basically done by a init script called lxc-net which setups the lxcbr0 bridge and a number of iptables rule to set up networking. In this post I describe how to use network in debian jessie.(Debian Jessie ships with an updated version of LXC 1.06 but does not set up the LXC networking by default)

First download the [lxc-net](http://flockport.com/download/lxc-net) script here and follow the instructions below.

```bash
apt-get install lxc dnsmasq-base bridge-utils
touch /etc/default/lxc
echo 'USE_LXC_BRIDGE="true"' > /etc/default/lxc
cp lxc-net /etc/init.d/
chmod +x lxc-net
systemctl enable lxc-net
systemctl start lxc-net
systemctl status lxc-net
```

To ensure containers created have the lxcbr0 bridge enabled by default add the config below to /etc/lxc/default.conf


```bash
lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:xx:xx:xx
```
[Head to the readme](http://stackoverflow.com/questions/16222738/how-do-i-install-ruby-2-0-0-correctly-on-ubuntu-12-04) to learn more.

