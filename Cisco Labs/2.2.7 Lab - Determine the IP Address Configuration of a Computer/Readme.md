# Lab 2.2.7 - Determine the IP Address Configuration of a Computer

## Objective - In this lab you will determine the IP Address assigned to your computer

## Required Resources:
* 1 PC (Windows 10/11)
* Network Access

## Instructions

### Part 1 - Determine the IP address using Command Prompt

#### Step 1: Verify Network Access
<ol type="a">
  <li>Open a Web Browser</li>
  <li>Navigate to any website such as www.netacad.com</li>
</ol>

#### Step 2: The Command ipconfig
The ipconfig command provides you with the IP address, subnet mask, and default gateway
1. Open a **Command Prompt**. Click **Start**. Search for **Command Prompt**
2. At the prompt, enter **ipconfig** to determine the IP address assigned to each network adapter on your computer

```
C:\Users\Student> ipconfig

Ethernet adapter Enternet0:

  Connection-specific DNS Suffix .:
  Link-Local IPv6 Address.........: fe80::ac29:44a8:6409:c30e%6 
  IPv4 Address....................: 192.108.1.11
  Subnet Mask.....................: 255.255.255.0
  Default Gateway.................: 192.108.1.1
````
The IPv4 Address of the computer is 192.108.1.11

The Subnet Mask of the computer is 255.255.255.0

The Default Gateway of the computer is 192.108.1.1

#### Step 3: The command ipconfig /all
1. At the prompt, enter **ipconfig/ all** command to view the IP configuration on PC-A
2.
~~~
   C:\Users\Student> ipconfig /all

Ethernet adapater Ethernet0:
Connection-specific DNS Suffix  . :  
Description . . . . . . . . . . . : Intel(R) 82574L Gigabit Network Connection 
Physical Address. . . . . . . . . : 00-00-12-34-58-C1 
DHCP Enabled. . . . . . . . . . . : Yes 
Autoconfiguration Enabled . . . . : Yes 
Link-local IPv6 Address . . . . . : fe80::ac29:44a8:6409:c30e%6(Preferred) 
IPv4 Address. . . . . . . . . . . : 192.168.1.11(Preferred) 
Subnet Mask . . . . . . . . . . . : 255.255.255.0 
Lease Obtained. . . . . . . . . . : Sunday, July 24, 2016 9:33:49 AM 
Lease Expires . . . . . . . . . . : Monday, July 25, 2016 10:33:17 AM 
Default Gateway . . . . . . . . . : 192.168.1.1 
DHCP Server . . . . . . . . . . . : 192.168.1.1 
DHCPv6 IAID . . . . . . . . . . . : 50312345 
DHCPv6 Client DUID. . . . . . . . : 00-00-00-01-02-03-04-DE-00-00-00-B1-E1-C1 
DNS Servers . . . . . . . . . . . : 8.8.8.8 
8.8.4.4 
NetBIOS over Tcpip. . . . . . . . : Enabled 
~~~

-The DNS server for the computer is hsd1.ma.comcast.net
-The MAC Address of the network adapter is 00-00-12-34-58-C1
-The DHCP is enabled and the IP address to the DHCP server is 192.168.1.1
-The date when the lease was obtained is July 24, 2016 9:33:49 AM
-The date when the lease expires is July 25, 2016 10:33:17 AM

### Part 2: The the Network Interface TCP/IP Stack

#### Step 1: Test TCP/IP stack using the lookback address

To verify that the TCP/IP protocol is functioning, pinging your loopback address. Enter the **ping 127.0.0.1** at the prompt

```
C:\Users\Student> ping 127.0.0.1
```

#### Step 2: Test TCP/IP stack using the configured IP address.
You can also ping your IP address. In this example, enter the **ping 192.168.1.11** command at the prompt.

Record one of the replies from your ping command.

<img width="511" height="222" alt="image" src="https://github.com/user-attachments/assets/9c467d48-5cc0-4f7a-87bd-256c4367ee63" />
