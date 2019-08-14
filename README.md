# Banana-Pi-R1-OpenFlow

This is my campus project which I and my group was instructed to turn an SBC called Banana Pi R1 into an Openflow-Capable SDN Switch. Correct me if I'm wrong but there is little to no information about creating an Openflow Switch especially in linux kernel 4.X and above.

## About
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/BPI-R1%201.JPG "Banana Pi R1")

When people looked at a Banana Pi R1, they probably thought that, well, it's an SBC with 5 ethernet ports. True, but this is one of those 'looks can be deceiving' cases. It looks and feels like it has 5 ethernet ports, While in fact, it is actually only had one that was logically connected to the processor, while physically, the only port was connected with a Distributed Switch Architecture with 5 physical port.

![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/master%20fisik.png "Banana Raw Architecture")

This is not a suitable environment to run an Open vSwitch Program, which requires that all physical port mapped logically and independently. The Idea is to split the only logical port, eth0, into 5 different sub-ports, each with their on VLAN tag which also are corresponding with the VLAN tag of the physical port. The result is a computer with the logical port connecting one on one with they physical port as shown below. Usually, it was done with a program known as SWconfig, but it was no longer ported to kernel 4.X and above as people claimed that it causes stability issues.

![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/hasilarmbian.png "Banana Result Architecture")

## Resources
A Really Useful Guide about Banana Pi R1:
https://bananapi.gitbooks.io/bpi-r1/content/en/

Link to Download the OS for the Banana Which We Will Be Using (Armbian):
https://www.armbian.com/lamobo-r1/

A Guide about the OS and How to Configure it:
https://docs.google.com/document/d/1LVuukSuby7aCuAaQezFn-kM8ZQM-I0kuGiI_XnT0sDg/edit

Guide for Configuring Banana Pi R1 Openflow Switch on previous kernel (with SWConfig):
https://ma405th.wordpress.com/2016/10/18/install-openvswitch-on-banana-pi-r1/
(It's in Chinese, get your Google Translate ready)

If you want to learn more about Distributed Switch Architecture, Here's an Amazing Paper:
https://www.netdevconf.org/2.1/papers/distributed-switch-architecture.pdf

Special thanks to the great people from the Armbian Forums and Banana Pi Forums for creating the startup and basic guides so that this project could be completed. Also thanks to Petra and Fandi as my project mates (I'll link them when they create an account), and my project counselors and lectures at my Uni. 

## How To
This guide will provide a simple how to in installing the SBC and will provide a script that will solve the networking issues with the DSA.

### Setting up the Banana Pi
Check the link above to download the OS for Banana Pi. I am using the Armbian_5.31_Lamobo-r1_Debian_jessie_next_4.9.7 version for my project. Let it burn to a MicroSD card, put it in, and Connect a 5V 2A power source to the furthermost Micro USB Port (the one nearest to the corner). The other Micro USB port is for OTG USB and it may damage the device when inserted with a power source.

Once it boots, you can log in with username: root and password: 1234. Next you will be prompted to change the password.

Before you add any scripts, you should probably encounter this when you do ifconfig:
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/ifconfigbefore.PNG "Network Before")

### Adding Script
After the initial configuration, add the dsa_config script in /etc/network/if-pre-up/ and add interfaces_add to the /etc/network/interfaces
If you do this, you should have this instead when you do ifconfig everytime you boot up:
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/ifconfigbefore.PNG "Network After")


### Installing Open vSwitch
Installing Open vSwtich can be done with
apt-get install openvswitch-switch

After the apt is installed, the DSA will function like an ordinary Open vSwitch that can understand commands like ovs-vsctl and ovs-ofctl.

Voila, you should have an OpenvSwitch Switch for about $100 you can tinker and test your apps

## Testing and Results
I configure my OpenvSwitch so that eth0.10 to eth0.40 are the switch ports and the eth0.50 is the management port that connects to the SDN controller
I use open Daylight and run a standard switching flow with 2 clients and to servers as shown below:
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/bananapitesting.PNG "Results")

The result is, pretty bad, on full load, you can only expect 160 Mbps with 6 Mbps deviation.
But I guess it is enough for testing your SDN skills and apps on an open environment, you wouldn't use it on a production scale.

## Verdicts
I'm done with this project, I already get my results and maybe if I had time, I can show you the Open Daylight apps that me and my team create for our Uni project
[]

