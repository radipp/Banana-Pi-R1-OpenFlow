# Banana-Pi-R1-OpenFlow

This is my campus project which I and my group was instructed to turn an SBC called Banana Pi R1 into an Openflow-Capable SDN Switch. Correct me if I'm wrong but there is little to no information about creating an Openflow Switch especially in linux kernel 4.X and above, in which SWConfig no longer ported, which I will explain about later.

## About
When people looked at a Banana Pi R1, they probably thought that, well, it's an SBC with 5 ethernet ports. True, but this is one of those 'looks can be deceiving' cases. It looks and feels like it has 5 ethernet ports, While in fact, it is actually only had one that was logically connected to the processor, while physically, the only port was connected with a Distributed Switch Architecture with 5 physical port.

## Resources
A Really Useful Guide about Banana Pi R1:
https://bananapi.gitbooks.io/bpi-r1/content/en/

Link to Download the OS for the Banana Which We Will Be Using (Armbian):
https://www.armbian.com/lamobo-r1/

A Guide about the OS and How to Configure it:
https://docs.google.com/document/d/1LVuukSuby7aCuAaQezFn-kM8ZQM-I0kuGiI_XnT0sDg/edit

Guide for Configuring Banana Pi R1 Openflow Switch on previous kernel:
https://ma405th.wordpress.com/2016/10/18/install-openvswitch-on-banana-pi-r1/
(It's in Chinese)

Guide for Lamobo

## History



