# Cisco PT DHCP, Routing, Switching

![image](https://github.com/user-attachments/assets/39de094d-f804-496c-b062-aa98d4e81384)


## Lab Objectives
- PCs 1,3 in VLAN 10, Subnet 10.16.0.0 /24
- PC 2,4 in VLAN 20, Subnet 172.16.0.0/24
- DHCP assigned addressed for PCs
- DHCP/Web server in VLAN 777, Subnet 192.168.1.0/24, using .100
- Default G/W is .1 in each subnet
- Verify clients can ping each other
- Verify clients can open the web page of server at TheKeithBarker.com

## What you'll need:
- Download and launch the OGIT-2020-04-07 PT Lab.pkt

Do the lab on your own. If you need help, you can use the below procedure as a guide to solve this challenge.
You can watch the tutorials by [Keither Barker on Youtube](https://www.youtube.com/playlist?list=PLQQoSBmrXmrysEaVNia7KVwf85qATIi1V)

## Procedure

### A) Configure Switch 1, 2, and 3 (SW1, SW2, SW3)
1. Open Notepad and type the following commands in this order:
2.   conf t
3.   no ip domain-lookup
4.   line con 0
5.   logging synch
6.   no exec-timeout
7.   privi level 15
8.   exit
9.   spann mode rapid
10.   spann portf default
11.   hostname
12. Go to CLI of Switch 1 (SW1)
13. Enter "en" and press enter
14. Paste the following commands from Notepad
15. Enter "SW1" and press enter.
16. Enter "end"
17. Enter" wr"
18. Go to Switch 2 and follow the same steps (12-15) and name the switch "SW2" and type "end".
19. Go to Switch 3 and follow the same steps (12-15) and name the switch "SW3" and type 
"end".

### B) Configure Trunks, VLANS, and VTPs
1. Enter the following commands into Notepad
2. conf t
3. vtp domain OGIT
4. int range fa 0/11, fa 0/22
5. switch mode trunk
6. end
7. Paste this in Switch 1 and Switch followed by end
8. Go to Switch 1
9. Enter "conf t"
10. Enter "int gig 0/1"
11. Enter "sw mode trunk"
12. Enter "end"
13. Do the same for Switch 2 for gig 0/2
14. Go to Switch 3
15. Enter "conf t"
16. Enter "int range gig 0/1-2"
17. Enter "sw tr encapsulation dot1q"
18. Enter "switchport mode trunk"
19. Enter "vtp domain OGIT"
20. Enter "exit"
21. Enter "vlan 10"
22. Enter "vlan 20"
23. Enter "vlan 777"
24. Confirm Vlans "show vlan brief". No active access ports
25. Confirm trunk "show in trunk". Via trunk ports Vlans are supported
26. Confirm the using commands from Step 24 and Step 25 for SW1 and SW2

### C) Assign PC1 & PC3 to VLAN 10 AND PC2 & PC4 to VLAN 20
1. Go to CLI in SW1
2. Enter "conf t"
3. Enter "int fa 0/1"
4. Enter "sw mode access"
5. Enter "switchport access vlan 10"
6. Enter "int fa 0/2"
7. Enter "sw mode access"
8. Enter "switchport access vlan 20"
9. Enter "end"
10. Confirm VLAN assignment by entering "show vlan brief"
11. Do the samw for Sw2 by assigning fa0/3 to Vlan 10 and fa0/4 to Vlan 40
12. Do the same for fa0/5 by assinging it to Vlan 777

### D) Configure the DHCP server with the respective IP address pools
1. Go to Server1
2. Go to SERVICES-> DHCP
3. Turn on Services (Interface -> FastEthernet() -> Services -> ON)
4. Change Pool Name: VLAN 10
5. Default Gateway: 10.16.0.1
6. DNS Server: 192.168.1.100
7. Start IP Address: 10.16.0.10
8. Subnet Mask: 255.255.255.0
9. Max # of Users: 10
10. Press "Add"
11. Repeat the steps for VLAN 20 by changing Pool Name to VLAN 20, G/W: 172.16.0.1, and Start IP Address: 172.16.0.10

### E) Configure the Multi-layer Switch by assigning the IP address pools to the respective VLANs
1. Go to Cli in SW3
2. Enter "conf t"
3. Enter "int vlan 10"
4. Enter "ip add  10.16.0.1 255.255.255.0"
5. Enter "int vlan 20"
6. Enter "ip add 172.16.0.1 255.255.255.0"
7. Enter "int vlan 777"
8. Enter "ip add 192.161.1.1 255.255.255.0"
9. Enter "end"
10. Enter to confirm settings "show ip interface brief"
11. Ping Server1 to confirm  connectivity
12. Enter "ping 192.168.1.100"

### F) Create DHCP IP Helper relays in SW3
1. Go to ClI in Sw3
2. Enter "conf t"
3. Enter "int vlan 10"
4. Enter "ip helper-address 192.168.1.100"
5. Enter "int vlan 20"
6. Enter "ip helper-address 192.168.1.100"
7. Enter "end"

### G) Enable IP routing in Multilayer switch SW3
1. Go to CLI in SW3
2. Enter "conf t"
3. Enter "ip routing"
4. Enter "end
5. Enter "show ip route"
   


Source: [Keith Barker](thekeithbarker.com)
