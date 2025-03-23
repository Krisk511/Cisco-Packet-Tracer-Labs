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

### Configure Switch 1, 2, and 3 (SW1, SW2, SW3)
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

### Configure Trunks, VLANS, and VTPs
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
15. 

Source: [Keith Barker](thekeithbarker.com)
