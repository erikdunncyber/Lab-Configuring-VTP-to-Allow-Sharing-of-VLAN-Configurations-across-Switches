<h1>Packet Tracer - Configuring VTP to Allow Sharing of VLAN Configurations across Switches</h1>

<p align="center">
This is a network diagram of 4 VLANs interconnected by 3 switches where I'll be configuring VTP (VLAN Trunk Protocol) on the switches. It's important to note that the switchports connecting the switches (G0/1, G0/2) are configured as trunk ports and DTP (Dynamic Trunk Protocol) is disabled on these ports: <br/>
<img src="https://i.imgur.com/Yp0GO4S.png" height="80%" width="80%"/>
<br />
<br />
I'll start by configuring VTP on SW1. First I'll assign a VTP domain name of 'ccna' with the command "vtp domain ccna" then I'll create VLANs 10, 20, and 30 with the "vlan" commnd: <br/>
<img src="https://i.imgur.com/h0xbs9U.png" height="80%" width="80%"/>
<br />
<br />
At this point SW2 and SW3 should have added VLANs 10, 20, and 30 since they should of recieved VTP advertisements from SW1 and joined SW1's VTP domain, syncing their VLAN databases. I'll try to confirm this by going on SW2 and use the command "do show VTP status". The status brief SW2 generated shows that it is apart of the VTP domain 'ccna" that I created on SW1. I'll also use the "do show vlan brief" command to check if the VLANs I created on SW1 has been shared successfully. The brief shows that VLANs 10, 20, and 30 are all up on SW2: <br/>
<img src="https://i.imgur.com/bATixkk.png" height="80%" width="80%"/>
<img src="https://i.imgur.com/VyDpy65.png" height="80%" width="80%"/>
<br />
<br />
I'll start by configuring VTP on SW1. First I'll assign a VTP domain name of 'ccna' with the command "vtp domain ccna" then I'll create VLANs 10, 20, and 30 with the "vlan" commnd: <br/>
<img src="https://i.imgur.com/h0xbs9U.png" height="80%" width="80%"/>
<br />
<br />
</p>

