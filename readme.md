# Lab - Configure Router-on-a-Stick Inter-VLAN Routing

## топология задаиня

![картинка1](https://github.com/Rustam-Sibagatullin/Lab---Configure-Router-on-a-Stick-Inter-VLAN-Routing/blob/main/Topology.JPG "Топология ДЗ")


## вводные данные
Addressing Table
Device	| Interface	| IP Address	| Subnet Mask	 | Default Gateway
--------|-----------|-------------|--------------|-------------
R1	    |G0/0/1.3	  |192.168.3.1	|255.255.255.0 |	N/A
R1	    |G0/0/1.4	  |192.168.4.1	|255.255.255.0 |	N/A
R1	    |G0/0/1.8	  |N/A	|N/A|	N/A
S1	    |VLAN 3	    |192.168.3.11	|255.255.255.0	|192.168.3.1
S2	    |VLAN 3	    |192.168.3.12	|255.255.255.0	|192.168.3.1
PC-A	  |NIC	      |192.168.3.3	|255.255.255.0	|192.168.3.1
PC-B	  |NIC	      |192.168.4.3	|255.255.255.0	|192.168.4.1

VLAN Table
VLAN|	Name	     |Interface Assigned
----|------------|--------------------
3	  |Management	 |S1: VLAN 3
3   |Management  |S2: VLAN 3
3   |Management  |S1: F0/6
4	  |Operations	 |S2: F0/18
7	  |ParkingLot	 |S1: F0/2-4, F0/7-24, G0/1-2 
7   |ParkingLot  |S2: F0/2-17, F0/19-24, G0/1-2
8	  |Native	     |N/A



## Step-2: Configure basic settings for the router
a.	Console into the router and enable privileged EXEC mode.  
**Router>enable**

b.	Enter configuration mode.  
**configure ter**

c.	Assign a device name to the router.  
**Router(config)#hostname R1**

d.	Disable DNS lookup to prevent the router from attempting to translate incorrectly entered commands as though they were host names.  
**R1(config)#no ip domain-lookupno ip domain-lookup**

e.	Assign class as the privileged EXEC encrypted password.  
**enable secret class**

f.	Assign cisco as the console password and enable login.  
**R1(config)#line console 0**  
**R1(config-line)#password cisco**  
**R1(config-line)#login**  
**R1(config-line)#exit**  


g.	Assign cisco as the VTY password and enable login.  
**R1(config)#line vty 0 15**  
**R1(config-line)#password cisco**  
**R1(config-line)#exit**  

h.	Encrypt the plaintext passwords.  
**R1(config)#service password-encryption**

i.	Create a banner that warns anyone accessing the device that unauthorized access is prohibited.  
**banner motd $ Authorized Users Only! $**

j.	Save the running configuration to the startup configuration file.  
**R1#copy running-config startup-config**

k.	Set the clock on the router.  
**R1#clock set 21:25:00 7 October 2020**


log    |
-------|
Router>enable 
Router#configure ter
Router(config)#hostname R1
R1(config)#no ip domain
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console
R1#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#no
R1(config)#no ip
R1(config)#no ip 
R1(config)#no ip 
R1(config)#no ip 
R1(config)#no ip domain-lookup 
R1(config)#line
R1(config)#line con
R1(config)#line console 0
R1(config)#line console 0
R1(config-line)#pass
R1(config-line)#password cisco
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#exi
R1(config-line)#exit 
R1(config)#lin
R1(config)#line vt
R1(config)#line vty 0 15
R1(config-line)#password cisco
R1(config-line)#exit
R1(config)#enable secret class
R1(config)#service password-encryption 
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console
R1#clock set 21:25:00 7 October 2020
R1#cop
R1#copy run
R1#copy running-config st
R1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
R1#



## Step 3: Configure basic settings for each switch.


a.	Console into the switch and enable privileged EXEC mode.  
**Switch>enable**  

b.	Enter configuration mode.  
**Switch#configure terminal**  

c.	Assign a device name to the switch.  
**Switch(config)#hostname S1**
**Switch(config)#hostname S2**

d.	Disable DNS lookup to prevent the router from attempting to translate incorrectly entered commands as though they were host names.  
**S1(config)#no ip domain-lookup**  

e.	Assign class as the privileged EXEC encrypted password.  
**S1(config)#enable  secret class**  

f.	Assign cisco as the console password and enable login.  
**S1(config)#line console 0  
S1(config-line)#password cisco  
S1(config-line)#login  
S1(config-line)#exit**  

g.	Assign cisco as the vty password and enable login.  
**S1(config)#line vty 0 15  
S1(config-line)#password cisco  
S1(config-line)#login  
S1(config-line)#exit**  

h.	Encrypt the plaintext passwords.  
**S1(config)#service password-encryption**  

i.	Create a banner that warns anyone accessing the device that unauthorized access is prohibited.  
**S1(config)#banner motd $ Authorized Users Only! $**  

j.	Set the clock on the switch.
Note: Use the question mark (?) to help with the correct sequence of parameters needed to execute this command.  
**S1#clock set 13:11:00 11 October 2020**  

k.	Copy the running configuration to the startup configuration.  
**S1#copy running-config startup-config**  
**S2#copy running-config startup-config**


log         
Switch-1    |Switch-2
------------|-------------
Switch>enable |	Switch>enable
Switch#configure terminal  |	Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z. |	Enter configuration commands, one per line. End with CNTL/Z.
Switch(config)#hostname S1 |	Switch(config)#hostname S2
S1(config)#no ip domain-lookup  |	S2(config)#no ip domain-lookup
S1(config)#enable  secret class |	S2(config)#enable secret class
S1(config)#line |	S2(config)#line console 0
S1(config)#line conslo |	S2(config-line)#password cisco
S1(config)#line console |	S2(config-line)#login
S1(config)#line console 0 |	S2(config-line)#exit
S1(config-line)#password cisco |	S2(config)#line vty 0 15
S1(config-line)#login |	S2(config-line)#password cisco
S1(config-line)#exit |	S2(config-line)#login
S1(config)#line vty 0 15 |	S2(config-line)#exit
S1(config-line)#password cisco |	S2(config)#service password-encryption
S1(config-line)#login |	S2(config)#banner motd $ Authorized Users Only! $
S1(config-line)#exit |	S2(config)#exit
S1(config)#ser |	%SYS-5-CONFIG_I: Configured from console by console
S1(config)#service pa |	S2#clo
S1(config)#service password-encryption  |	S2#clock set
S1(config)#banner motd $ Authorized Users Only! $ |	S2#clock set 13:33:00 11 October 2020
S1(config)#exit |	S2#cop
S1#clock set 13:11:00 11 October 2020 |	S2#copy ru
S1#copy running-config startup-config  |	S2#copy running-config st
Destination filename [startup-config]?  |	S2#copy running-config startup-config
Building configuration... |	Destination filename [startup-config]?
[OK] |	Building configuration...
S1# |	[OK]



## Step 4: Configure PC hosts.

![картинка2](https://github.com/Rustam-Sibagatullin/Lab---Configure-Router-on-a-Stick-Inter-VLAN-Routing/blob/main/IP_PCs.JPG "PC hosts")


# Part 2: Create VLANs and Assign Switch Ports

## Step 1: Create VLANs on both switches

## Step 2: Assign VLANs to the correct switch interfaces.

S1>enable   
Password:   
S1#  
Enter configuration commands, one per line.  End with CNTL/Z.  
S1(config)#vlan 3  
S1(config-vlan)#name Management  
S1(config-vlan)#vlan 4  
S1(config-vlan)#name Operations  
S1(config-vlan)#vlan 7  
S1(config-vlan)#name ParkingLot  
S1(config-vlan)#vlan 8  
S1(config-vlan)#name Native  
S1(config-vlan)#interface vlan 3  
S1(config-if)#  
%LINK-5-CHANGED: Interface Vlan3, changed state to up  
ip address 192.168.3.11 255.255.255.0  
S1(config-if)#no shutdown
S1(config-if)#exit
S1(config)#ip default-gateway 192.168.3.1  
S1(config)#interface range f0/2 - 4 , f0/7 - 24 , g0/1 - 2  
S1(config-if-range)#switchport mode access  
S1(config-if-range)#switchport access vlan 7  
S1(config-if-range)#shutdown  

%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/4, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/7, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/8, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/9, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/10, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/11, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/12, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/13, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/14, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/15, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/16, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/17, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/18, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/19, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/20, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/21, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/22, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/23, changed state to administratively down

%LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to administratively down

%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down  
S1(config-if-range)#interface f0/6  
S1(config-if)#switchport mode access  
S1(config-if)#switchport access vlan 3  
S1(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan3, changed state to up  

S1(config-if)#show vlan brief  
                ^
% Invalid input detected at '^' marker.  
	
S1(config-if)#exit  
S1(config)#exit  
S1#  
%SYS-5-CONFIG_I: Configured from console by console  
S1#show vlan brief  

VLAN Name                            |  Status   | Ports
-------------------------------------|-----------|-------------------------------
1    default                         |active     | Fa0/1, Fa0/5
3    Management                      | active    | Fa0/6
4    Operations                      | active    |
7    ParkingLot                      | active    | Fa0/2, Fa0/3, Fa0/4, Fa0/7  <br> Fa0/8, Fa0/9, Fa0/10, Fa0/11 <br> Fa0/12, Fa0/13, Fa0/14, Fa0/15 <br> Fa0/16, Fa0/17, Fa0/18, Fa0/19  <br> Fa0/20, Fa0/21, Fa0/22, Fa0/23  <br> Fa0/24, Gig0/1, Gig0/2
8    Native                          | active    |
1002 fddi-default                    | active    |
1003 token-ring-default              | active    |
1004 fddinet-default                 | active    |
1005 trnet-default                   | active    |






S2#configure terminal   
Enter configuration commands, one per line.  End with CNTL/Z.  
S2(config)#vlan 3  
S2(config-vlan)#name Management  
S2(config-vlan)#vlan 4  
S2(config-vlan)#name Operations  
S2(config-vlan)#vlan 7   
S2(config-vlan)#name ParkingLot  
S2(config-vlan)#vlan 8  
S2(config-vlan)#name Native  
S2(config-vlan)#interface vlan 3   
S2(config-if)#  
%LINK-5-CHANGED: Interface Vlan3, changed state to up  
ip address 192.168.3.12 255.255.255.0  
S2(config-if)#no shutdown  
S2(config-if)#exit  
S2(config)#ip default-gateway 192.168.3.1  
S2(config)#interface range f0/2 - 17, f0/19 - 24 , g0/1 - 2  
S2(config-if-range)#switchport mode access  
S2(config-if-range)#switchport access vlan 7  
S2(config-if-range)#shutdown  
S2(config-if-range)#interface f0/18  
S2(config-if)#switchport mode access  
S2(config-if)#switchport access vlan 4  
S2(config-if)#exit  
S2(config)#exit  
S2#  
%SYS-5-CONFIG_I: Configured from console by console  

S2#show vlan brief

VLAN Name                             |Status   | Ports
--------------------------------------|---------|-------------------------------
1    default                          |active   | Fa0/1
3    Management                       |active   | 
4    Operations                       |active   | Fa0/18
7    Native                           |active   | Fa0/2, Fa0/3, Fa0/4, Fa0/5 <br>Fa0/6, Fa0/7, Fa0/8, Fa0/9 <br>Fa0/10, Fa0/11, Fa0/12, Fa0/13 <br>Fa0/14, Fa0/15, Fa0/16, Fa0/17 <br>                                             Fa0/19, Fa0/20, Fa0/21, Fa0/22 <br> Fa0/23, Fa0/24, Gig0/1, Gig0/2
1002 fddi-default                     |active   | 
1003 token-ring-default               |active   | 
1004 fddinet-default                  |active   | 
1005 trnet-default                    |active   | 
S2#





## Part 3: Configure an 802.1Q Trunk Between the Switches


S1>en
S1>enable 
Password: 
S1#con  
S1#conf  
S1#configure t  
S1#configure terminal   
Enter configuration commands, one per line.  End with CNTL/Z.  
S1(config)#interface f0/1  
S1(config-if)#switchport mode trunk  

S1(config-if)#  
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to down  

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up  

S1(config-if)#switchport trunk native vlan 8  
S1(config-if)#  
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (8), with S2 FastEthernet0/1 (1).  

%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on FastEthernet0/1 (8), with S2 FastEthernet0/1 (1).  
%SPANTREE-2-RECV_PVID_ERR: Received BPDU with inconsistent peer vlan id 1 on FastEthernet0/1 VLAN8.  

%SPANTREE-2-BLOCK_PVID_LOCAL: Blocking FastEthernet0/1 on VLAN0008. Inconsistent local vlan.  


S1(config-if)#switchport trunk allowed vlan 3,4,8  
S1(config-if)#%SPANTREE-2-RECV_PVID_ERR: Received BPDU with inconsistent peer vlan id 1 on FastEthernet0/1 VLAN8.  

%SPANTREE-2-BLOCK_PVID_LOCAL: Blocking FastEthernet0/1 on VLAN0008. Inconsistent local vlan.  


S1(config-if)#exit  
S1(config)#show interfaces trunk  
            ^
% Invalid input detected at '^' marker.  
	
S1(config)#exit  
S1#  
%SYS-5-CONFIG_I: Configured from console by console  

S1#show interfaces trunk  
Port        Mode         Encapsulation  Status        Native vlan  
Fa0/1       on           802.1q         trunking      8  

Port        Vlans allowed on trunk  
Fa0/1       3-4,8  

Port        Vlans allowed and active in management domain  
Fa0/1       3,4,8  

Port        Vlans in spanning tree forwarding state and not pruned  
Fa0/1       none  

S1#  
S1#  
S1#show interfaces trunk  
Port        Mode         Encapsulation  Status        Native vlan  
Fa0/1       on           802.1q         trunking      8  

Port        Vlans allowed on trunk  
Fa0/1       3-4,8  

Port        Vlans allowed and active in management domain  
Fa0/1       3,4,8  

Port        Vlans in spanning tree forwarding state and not pruned  
Fa0/1       3,4  

S1#  


S1#configure terminal   
Enter configuration commands, one per line.  End with CNTL/Z.  
S1(config)#  
S1(config)#interface f0/5  
S1(config-if)#switchport mode trunk  
S1(config-if)#switchport trunk native vlan 8  
S1(config-if)#switchport trunk allowed vlan 3,4,8  
S1(config-if)#exit  
S1(config)#  




S2>enable   
Password:   
S2#  
S2#  
S2#configure terminal   
Enter configuration commands, one per line.  End with CNTL/Z.  
S2(config)#  
S2(config)#interface f0/1  
S2(config-if)#switchport mode trunk  
S2(config-if)#switchport trunk native vlan 8  
switchport trunk allowed vlan 3,4,8  
S2(config-if)#  
S2(config-if)#switchport trunk allowed vlan 3,4,8  
S2(config-if)#  
S2(config-if)#exit  
S2(config)#exit  
S2#  
%SYS-5-CONFIG_I: Configured from console by console  

S2# show interfaces trunk  
Port        Mode         Encapsulation  Status        Native vlan  
Fa0/1       on           802.1q         trunking      8  

Port        Vlans allowed on trunk  
Fa0/1       3-4,8  

Port        Vlans allowed and active in management domain  
Fa0/1       3,4  

Port        Vlans in spanning tree forwarding state and not pruned  
Fa0/1       none  

S2#  



## Part 4: Configure Inter-VLAN Routing on the Router


R1>en  
R1>enable   
Password:   
R1#  
R1#configure terminal   
Enter configuration commands, one per line.  End with CNTL/Z.  
R1(config)#  
R1(config)#interface g0/0/1  
R1(config-if)#no shutdown  

R1(config-if)#  
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up  

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up  

R1(config-if)#exit  
R1(config)#interface g0/0/1.3  
R1(config-subif)#  
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.3, changed state to up  

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.3, changed state to up  
description Management_Network
R1(config-subif)#encapsulation dot1q 3  
R1(config-subif)#ip address 192.168.3.1 255.255.255.0   
R1(config-subif)#interface g0/0/1.4  
R1(config-subif)#  
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.4, changed state to up  

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.4, changed state to up  
description Operations_Network  
R1(config-subif)#encapsulation dot1q 4  
R1(config-subif)#ip address 192.168.4.1 255.255.255.0  
R1(config-subif)#interface g0/0/1.8  
R1(config-subif)#  
%LINK-5-CHANGED: Interface GigabitEthernet0/0/1.8, changed state to up  

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1.8, changed state to up  

R1(config-subif)#description Native_VLAN  
R1(config-subif)#encapsulation dot1q 8 native  
R1(config-subif)#exit  
R1(config)#exit  
R1#
%SYS-5-CONFIG_I: Configured from console by console  

R1#show ip interface brief  
Interface              IP-Address      OK? Method Status                Protocol     
GigabitEthernet0/0/0   unassigned      YES unset  administratively down down     
GigabitEthernet0/0/1   unassigned      YES unset  up                    up     
GigabitEthernet0/0/1.3 192.168.3.1     YES manual up                    up   
GigabitEthernet0/0/1.4 192.168.4.1     YES manual up                    up   
GigabitEthernet0/0/1.8 unassigned      YES unset  up                    up   
Vlan1                  unassigned      YES unset  administratively down down  
R1#  
R1#show ip interface brief  
Interface              IP-Address      OK? Method Status                Protocol   
GigabitEthernet0/0/0   unassigned      YES unset  administratively down down   
GigabitEthernet0/0/1   unassigned      YES unset  up                    up   
GigabitEthernet0/0/1.3 192.168.3.1     YES manual up                    up   
GigabitEthernet0/0/1.4 192.168.4.1     YES manual up                    up   
GigabitEthernet0/0/1.8 unassigned      YES unset  up                    up   
Vlan1                  unassigned      YES unset  administratively down down  




## Part 5: Verify Inter-VLAN Routing is Working


# Step 1: Complete the following tests from PC-A. All should be successful

a.	Ping from PC-A to its default gateway.  
C:\>ping 192.168.3.1  

Pinging 192.168.3.1 with 32 bytes of data:  

Reply from 192.168.3.1: bytes=32 time=1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time=1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time<1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time<1ms TTL=255  

Ping statistics for 192.168.3.1:  
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),  
Approximate round trip times in milli-seconds:  
    Minimum = 0ms, Maximum = 1ms, Average = 0ms  


b.	Ping from PC-A to PC-B    
C:\>ping 192.168.3.1  

Pinging 192.168.3.1 with 32 bytes of data:  

Reply from 192.168.3.1: bytes=32 time=1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time=1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time<1ms TTL=255  
Reply from 192.168.3.1: bytes=32 time<1ms TTL=255  

Ping statistics for 192.168.3.1:  
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),  
Approximate round trip times in milli-seconds:  
    Minimum = 0ms, Maximum = 1ms, Average = 0ms  
    
c.	Ping from PC-A to S2  

C:\>ping 192.168.3.12  

Pinging 192.168.3.12 with 32 bytes of data:  

Request timed out.  
Reply from 192.168.3.12: bytes=32 time<1ms TTL=255  
Reply from 192.168.3.12: bytes=32 time<1ms TTL=255  
Reply from 192.168.3.12: bytes=32 time<1ms TTL=255  

Ping statistics for 192.168.3.12:  
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),  
Approximate round trip times in milli-seconds:  
    Minimum = 0ms, Maximum = 0ms, Average = 0ms  

![картинка3](https://github.com/Rustam-Sibagatullin/Lab---Configure-Router-on-a-Stick-Inter-VLAN-Routing/blob/main/Ping_from_PC-A.JPG "Ping_from_PC-A")


# Step 2: Complete the following test from PC-B.

From the command prompt on PC-B, issue the tracert command to the address of PC-A.  

Packet Tracer PC Command Line 1.0  
C:\>tracert 192.168.3.3  

Tracing route to 192.168.3.3 over a maximum of 30 hops:   

  1   1 ms      0 ms      0 ms      192.168.4.1  
  2   1 ms      0 ms      0 ms      192.168.3.3  

Trace complete.  

![картинка4](https://github.com/Rustam-Sibagatullin/Lab---Configure-Router-on-a-Stick-Inter-VLAN-Routing/blob/main/tracert_from_PC-B_to_PC-A.JPG "tracert_from_PC-B_to_PC-A")




Question:
What intermediate IP addresses are shown in the results? 

Answer: intermediate IP is 192.168.4.1. It relates to G0/0/1.4 according IP plan



