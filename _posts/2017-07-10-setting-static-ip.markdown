---
layout: post
title:  "Setting a Static IP"
date:   2017-07-10 15:52:06 -0400
categories: uncategorized
---

Needed to learn how to setup some machines with static IPs recently, since we were using an internal network without a DHCP service. So here we gooo.

<u>Definitions:</u>

Network Interface – connects the computer to the network

IP Address – allows your computer to be identified by the network

DNS – resolves domain names to IP addresses. Ex. google.com => 8.8.8.8


Gateway – the IP address of the access point or router that connects your internal network to the outside world

Subnet Mask – Identifies the subnetwork that this machine belongs to. The subnetwork is identified by XORing the mask with the IP address. Ex. 192.168.1.3 with mask 255.255.255.0 has a subnet of 192.168.1.0/24

Broadcast – The broadcast IP address will broadcast datagrams to all machines on a subnet

DHCP – Assigns IP address (and other relevant things from above) to any machine that joins the network, so that you don’t have to manually do it. If your network has DHCP, you will most likely not need to statically assign an IP.

 

<h3>Ubuntu:</h3>

Get the network interface name by running the command: ip link.

The name will be the interface that is not named ‘lo’. Usually it is eth0 or enp0s3 or something similar.

Edit the network interface file: /etc/network/interfaces.

Add the lines:

{% highlight text %}

auto <interface name>

iface <interface name> inet static

address <desired ip address>

netmask <subnet mask>

gateway <gateway>

You can also optionally add:

network <subnet>

dns-nameservers <DNS IP>

broadcast <broadcast IP>

For example:

auto enp0s3

iface enp0s3 inet static

address 10.0.0.4

netmask 255.255.255.0

gateway 10.0.0.1

network 10.0.0.0

dns-nameservers 10.0.0.10

{% endhighlight %}

Then restart the network with: sudo /etc/init.d/networking restart

 

<h3>Centos:</h3>

Similarly to Ubuntu:

Get the network interface name by running the command: ip link.

The name will be the interface that is not named `lo`. Usually it is `eth0` or `enp0s3` or something similar.

Edit the network interface file: `/etc/sysconfig/network-scripts/ifcfg-<interface name>`. Ex. `/etc/sysconfig/network-scripts/ifcfg-ens160`

Edit the lines so that:

{% highlight text %}

BOOTPROTO=static

ONBOOT=yes

IPADDR=<IP Address>

NETMASK=<netmask bits>

GATEWAY=<gateway>

Optionally:

DNS1=<DNS IP1>

DNS2=<DNS IP2>

Optionally you can specify manually specif DNS in /etc/resolv.conf instead:

nameserver <DNS IP1>

nameserver <DNS IP2>

Then restart the network with: sudo /etc/init.d/network restart

{% endhighlight %}

<h3>Windows:</h3>

Via Control Panel or right clicking the internet icon on the task bar and go to `Network and Sharing Center`

Click `Change Adapter Settings`

Right click your network adapter (Ex. Local Area Connection) and go to `Properties`

Click `Internet Protocol Version 4 (TCP/IPv4)` then go to `Properties`

Hit the radio button `Use the following IP address` and input the desired IP Address, Subnet Mask, and Default Gateway

Optionally hit the `Use the following DNS server addresses` and specify an IP for DNS

Hit ‘OK’ to close all the windows
