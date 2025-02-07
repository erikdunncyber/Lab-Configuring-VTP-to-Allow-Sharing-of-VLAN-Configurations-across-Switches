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
Next, I'll try configuring SW2 in VTP transparent mode and add VLAN 40. To do this I'll use the command "vtp mode transparent" and then the "vlan 40" command on SW2: <br/>
<img src="https://i.imgur.com/TpmdnLI.png" height="80%" width="80%"/>
<br />
<br />
Since SW2 is in transparent mode, VLAN 40 should have only been added to SW2 and not the other swtches, SW1 nor SW3. I'll verify this by using the "do show vlan brief" command on SW1. VLAN 40 does not appear on the list of VLANs on the brief as expected. VTP transparent mode on SW2 configures the switch to not send VTP advertisements but doesn't prevent SW1 and SW3 from forwarding VTP advertisements to each other: <br/>
<img src="https://i.imgur.com/VyDpy65.png" height="80%" width="80%"/>
<br />
<br />
Now I'll configure SW3 to VTP client mode with the command "vtp mode client". If I want to add a VLAN through SW3 I won't be able to since it is in vtp client mode. I would have add the VLAN through SW1 and have it advertise the changes to SW3: <br/>
<img src="https://i.imgur.com/G5XnaZo.png" height="80%" width="80%"/>
<br />
<br />
For the final configurations I'll configure all switchports so they are connected to hosts in the correct VLAN and manually configure them as access ports. I'll start with SW3 and its interfaces connected to VLANS, 10, 20, and 30. So I'll select the first interface I want to configure with the command "int f0/1", configure it as an acces port with the command "switchport mode access", and declare the VLAN the port is routed to with the command "switchport access vlan 10". I'll follow these same steps to configure interfaces f0/2 - f0/3 routed to VLAN 30 and f0/4 routed to VLAN 20 and all other interfaces on SW1 and SW2. With these final configurations I've successfully implemented VTP on the switches that are connected to hosts on the VLANs I've created: <br/>
<img src="https://i.imgur.com/gsUNMRu.png" height="80%" width="80%"/>
<br />
<br />
</p>

