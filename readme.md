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
**R1(config)#line console 0
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#exit**


g.	Assign cisco as the VTY password and enable login.
**R1(config)#line vty 0 15
R1(config-line)#password cisco
R1(config-line)#exit**

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

