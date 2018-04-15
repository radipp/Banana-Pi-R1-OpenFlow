# Banana-Pi-R1-OpenFlow

This is my campus project which I and my group was instructed to turn an SBC called Banana Pi R1 into an Openflow-Capable SDN Switch. Correct me if I'm wrong but there is little to no information about creating an Openflow Switch especially in linux kernel 4.X and above.

## About
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/BPI-R1%201.JPG "Banana Pi R1")

When people looked at a Banana Pi R1, they probably thought that, well, it's an SBC with 5 ethernet ports. True, but this is one of those 'looks can be deceiving' cases. It looks and feels like it has 5 ethernet ports, While in fact, it is actually only had one that was logically connected to the processor, while physically, the only port was connected with a Distributed Switch Architecture with 5 physical port.
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/master%20fisik.png "Banana Raw Architecture")

This is not a suitable environment to run an Open vSwitch Program, which requires that all physical port mapped logically and independently. The Idea is to split the only logical port, eth0, into 5 different sub-ports, each with their on VLAN tag which also are corresponding with the VLAN tag of the physical port. The result is a computer with the logical port connecting one on one with they physical port as shown below. Usually, it was done with a program known as SWconfig, but it was no longer ported to kernel 4.X and above as people claimed that it causes stability issues.
![alt text](https://github.com/radipp/Banana-Pi-R1-OpenFlow/blob/master/images/hasilarmbian.png "Banana Result Architecture")

This guide will provide a simple how to in installing the SBC and will provide a script that will solve the networking issues with the DSA.

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

## Installing the OS
Check the link above to download the OS required to 


