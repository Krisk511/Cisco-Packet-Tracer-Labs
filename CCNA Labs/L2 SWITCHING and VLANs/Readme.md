# Level 2 Switching and VLANS

![image](https://github.com/user-attachments/assets/59aec3fa-9dc4-446c-b2b0-32f476fb4e9e)


## Lab Objective: Laptop opens Web page on Server at 10.67.83.35
- Use VLAN 10 for the Laptop and Server
- VLAN 10 is supporting the IPv4 network 10.67.83.32 /27
  - Trunking is already configured between switches
  - DHCP services are already enabled for VLAN 10

## What you'll need:
- Download and launch the 2020-03-29-Switching and VLANs.pka file

Do the lab on your own. If you need help, you can use the below procedure as a guide to solve this challenge.

## Procedure
### A) Verify Server's IP Address
1. Hover with your mouse over the Server (Srvr) or click on it CONFIG -> FASTEthernet -> IP Configuration
2. You can verify that the IP Address is 10.67.83.35

### B) Verify that DHCP servives are on
1. Click on Services
2. Click on DHCP under SERVICES
3. Confirm that INTERFACE is set to FASTETHERNET() and SERVICVE button is set to ON

### C) Verify Server is in VLAN 10
1. Go to Switch (SW3) and hover it OR click on SW3 and click on CLI tab
2. Type: "show vlan brief"
3. Confirm Fa0/2 has been assigned as an access port in VLAN 10

### D) Confirm Laptop's IP address 
1. Click on Laptop and go to Physical and turn on Power button
2. Hover over the Laptop and confirm the incorrect IP address

### E) Check if Switch 1 (SW1) has a port assigned for VLAN 10
1. Click on Switch 1 and go to CLI
2. Type: "show vlan brief"
3. Confirm that Fa0/1 is in VLAN1 and no port for VLAN 10 has been assigned

### F) Configure port in Switch 1 (SW1) to support VLAN 10
1. Type: "conf t" (to configure the terminal)
2. Type: "switchport mode access" and press ENTER
3. Type: "switchport access vlan 10" and press ENTER
4. After switch creates VLAN 10, enter "end" and press ENTER
5. Once you're back in Switch confign mode: SW1#
6. Enter "show vlan brief" and press ENTER
7. Confirm that Fa0/1 has now been associated with VLAN 110
8. Power Laptop off and on to see if a va;id IP has been assigned

While VLAN 10 has been enabled to the SW1 access port, you'll notice that the DHCP still has not 
assigned a valid IP address to the laptop. Even if you assign a static IP address and subnet mask of 10.67.83.36 255.255.255.224,
if you try to ping the the server from the laptop using CMD (ping 10.67.83.35), the requests time out.

### G) Confirm Switch 2 (SW2) is setup for VLAN 10
1. Go to CLI in Sw2
2. Enter: show int trunk (since trunking is enabled)
3. Enter: show vlan brief (confirm that VLAN 10 is not set up)
4. Type and enter: config t 
5. Type and enter: vlan 10
6. Type and enter: end
7. Enter: show vlan brief (No access port assigned to VLAN 10)
8. Enter: show int trunk (both Fa0/1 and Fa0/10 forwarding VLAN 10) 

### H) Confirm on laptop (client) that DHCP has now assigned IP
1. Go to Laptop and click on CONFIG -> Wireless0
2. See the IP assigned
3. Go to DESKTOP and then COMMAND PROMPT
4. ping server 10.67.83.35
5. Go to DESKTOP and click on WEB BROWSER
6. Go to 10.67.83.35 website and see if  webpage loads
7. If yes, you've successfully completed this lab

Source: [Keith Barker](thekeithbarker.com)
