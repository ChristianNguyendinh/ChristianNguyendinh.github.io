---
layout: post
title:  "Networking Mode Quicki"
date:   2016-12-11 15:52:06 -0400
categories: uncategorized
---

<h3>NAT: (Network Address Translation)</h3>

Your virtual machine belong to a virtual subnet with its own IP range. Your virtual machine CAN see other machines on the real subnet, but machines on the real subnet CANNOT see your virtual machine. Activity will on your virtual machine will appear as if it is coming from your host machine. To outside machine to access your VM, for example SSH, you can port forward to an open port on your host machine, and connect that way.

![NAT](/assets/images/nat-christian-drawing.png)

<h4>Bridged:</h4>

Your virtual machine will appear as another node on the real subnet, will have an IP address in that range, etc. Your virtual machine CAN see all machines on the real subnet, and the machines on the real subnet CAN see your virtual machine. It will appear as if your virtual machine is just another entity in the network.

![bridged](/assets/images/bridged-christian-drawing.png)

<h4>Host-Only:</h4>

Your virtual machine will be assigned an IP, but it will be isolated from the real subnet. This means your virtual machine CANNOT see machines on the real subnet, and the machines on the real subnet, CANNOT see your virtual machine. This means that only network interactions with the Host and the virtual machine are allowed.

![host-only](/assets/images/hostonly-christian-drawing.png)
