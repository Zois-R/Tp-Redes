# Configuración de Dispositivos de Red

## R1

### Configuración básica


Router>enable
Router#configure terminal
Router(config)#hostname R1
R1(config)#line console 0
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#line vty 0 4
R1(config-line)#password cisco
R1(config-line)#login
R1(config-line)#logging synchronous
R1(config)#no ip domain-lookup
R1(config)#enable secret class
R1(config)#ipv6 unicast-routing
R1#write

## Serial 0/1/0 (hacia R4)


R1(config)#interface Serial 0/1/0
R1(config-if)#ip address 10.1.1.2 255.255.255.252
R1(config-if)#ipv6 address fe80::1 link-local
R1(config-if)#ipv6 address 2001::3/127
R1(config-if)#clock rate 128000
R1(config-if)#no shutdown
R1#write


## Serial 0/1/1 (hacia R2)


R1(config)#interface Serial 0/1/1
R1(config-if)#ip address 10.1.1.6 255.255.255.252
R1(config-if)#ipv6 address fe80::2 link-local
R1(config-if)#ipv6 address 2001::5/127
R1(config-if)#clock rate 128000
R1(config-if)#no shutdown
R1#write

## GigabitEthernet 0/0/0

R1(config)#interface gigabitEthernet 0/0/0
R1(config-if)#no ip address
R1(config-if)#no shutdown
R1#write

## Subinterfaces
## g0/0/0.10

R1(config)#interface gigabitEthernet 0/0/0.10
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip address 172.16.10.254 255.255.255.0
R1(config-subif)#ipv6 address fe80::10 link-local
R1(config-subif)#ipv6 address 2001:db8:0:10::/64
R1(config-subif)#no shutdown
R1#write


## g0/0/0.20

R1(config)#interface gigabitEthernet 0/0/0.20
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip address 172.16.20.254 255.255.255.0
R1(config-subif)#ipv6 address fe80::20 link-local
R1(config-subif)#ipv6 address 2001:db8:0:20::/64
R1(config-subif)#no shutdown
R1#write


## R2 Configuración básica

Router>enable
Router#configure terminal
Router(config)#hostname R2
R2(config)#line console 0
R2(config-line)#password cisco
R2(config-line)#login
R2(config-line)#line vty 0 4
R2(config-line)#password cisco
R2(config-line)#login
R2(config-line)#logging synchronous
R2(config)#no ip domain-lookup
R2(config)#enable secret class
R2(config)#ipv6 unicast-routing
R2#write


## Serial 0/1/0

R2(config)#interface Serial 0/1/0
R2(config-if)#ip address 10.1.1.9 255.255.255.252
R2(config-if)#ipv6 address fe80::22 link-local
R2(config-if)#ipv6 address 2001::6/127
R2(config-if)#clock rate 128000
R2(config-if)#no shutdown
R2#write


## Serial 0/1/1
R2(config)#interface Serial 0/1/1
R2(config-if)#ip address 10.1.1.13 255.255.255.252
R2(config-if)#ipv6 address fe80::23 link-local
R2(config-if)#ipv6 address 2001::8/127
R2(config-if)#clock rate 128000
R2(config-if)#no shutdown
R2#write

## Serial 0/2/1 (hacia R1)
R2(config)#interface Serial 0/2/1
R2(config-if)#ip address 10.1.1.5 255.255.255.252
R2(config-if)#ipv6 address fe80::21 link-local
R2(config-if)#ipv6 address 2001::4/127
R2(config-if)#no shutdown
R2#write


## GigabitEthernet 0/0/0
R2(config)#interface gigabitEthernet 0/0/0
R2(config-if)#ip address 10.1.1.21 255.255.255.252
R2(config-if)#ipv6 address fe80::24 link-local
R2(config-if)#ipv6 address 2001::12/127
R2(config-if)#no shutdown
R2#write

## GigabitEthernet 0/0/1

R2(config)#interface gigabitEthernet 0/0/1
R2(config-if)#ip address 10.1.1.17 255.255.255.252
R2(config-if)#ipv6 address fe80::25 link-local
R2(config-if)#ipv6 address 2001::10/127
R2(config-if)#no shutdown
R2#write

## R3 Configuración básica

Router>enable
Router#configure terminal
Router(config)#hostname R3
R3(config)#line console 0
R3(config-line)#password cisco
R3(config-line)#login
R3(config-line)#line vty 0 4
R3(config-line)#password cisco
R3(config-line)#login
R3(config-line)#logging synchronous
R3(config)#no ip domain-lookup
R3(config)#enable secret class
R3(config)#ipv6 unicast-routing
R3#write


## Serial 0/1/1

R3(config)#interface serial 0/1/1
R3(config-if)#ip address 10.1.1.14 255.255.255.252
R3(config-if)#ipv6 address fe80::32 link-local
R3(config-if)#ipv6 address 2001::9/127
R3(config-if)#no shutdown
R3#write

## GigabitEthernet 0/0/0

R3(config)#interface g0/0/0
R3(config-if)#no ip address
R3(config-if)#no shutdown
R3#write


##  Subinterfaces g0/0/0.70

R3(config)#interface gigabitEthernet 0/0/0.70
R3(config-subif)#encapsulation dot1Q 70
R3(config-subif)#ip address 172.16.70.254 255.255.255.0
R3(config-subif)#ipv6 address fe80::34 link-local
R3(config-subif)#ipv6 address 2001:db8:0:70::/64
R3(config-subif)#no shutdown
R3#write

## g0/0/0.80

R3(config)#interface gigabitEthernet 0/0/0.80
R3(config-subif)#encapsulation dot1Q 80
R3(config-subif)#ip address 172.16.80.254 255.255.255.0
R3(config-subif)#ipv6 address fe80::35 link-local
R3(config-subif)#ipv6 address 2001:db8:0:80::/64
R3(config-subif)#no shutdown
R3#write


## GigabitEthernet 0/0/1

R3(config)#interface g0/0/1
R3(config-if)#ip address 10.1.1.25 255.255.255.252
R3(config-if)#ipv6 address fe80::36 link-local
R3(config-if)#ipv6 address 2001::14/127
R3(config-if)#no shutdown
R3#write

## R4 Configuración básica

Router>enable
Router#configure terminal
Router(config)#hostname R4
R4(config)#line console 0
R4(config-line)#password cisco
R4(config-line)#login
R4(config-line)#line vty 0 4
R4(config-line)#password cisco
R4(config-line)#login
R4(config-line)#logging synchronous
R4(config)#no ip domain-lookup
R4(config)#enable secret class
R4(config)#ipv6 unicast-routing
R4#write


## Serial 0/1/0 (hacia R1)

R4(config)#interface Serial 0/1/0
R4(config-if)#ip address 10.1.1.1 255.255.255.252
R4(config-if)#ipv6 address fe80::41 link-local
R4(config-if)#ipv6 address 2001::2/127
R4(config-if)#no shutdown
R4#write

## Serial 0/1/1 (hacia ISP)

R4(config)#interface Serial 0/1/1
R4(config-if)#ip address 11.1.1.2 255.255.255.252
R4(config-if)#ipv6 address fe80::43 link-local
R4(config-if)#ipv6 address 2001::1/127
R4(config-if)#no shutdown
R4#write


## Serial 0/2/0

R4(config)#interface Serial 0/2/0
R4(config-if)#ip address 10.1.1.10 255.255.255.252
R4(config-if)#ipv6 address fe80::42 link-local
R4(config-if)#ipv6 address 2001::7/127
R4(config-if)#no shutdown
R4#write
ISP Router
plaintext
Copiar
Editar
Router(config)#interface serial 0/1/1
Router(config-if)#ip address 11.1.1.1 255.255.255.252
Router(config-if)#clock rate 128000
Router(config-if)#no shutdown
Router(config)#ipv6 unicast-routing
Router(config)#interface gigabitEthernet 0/0/0
Router(config-if)#ipv6 address 2800:110:1010::/64
Router(config-if)#ipv6 address fe80::50 link-local
Router(config-if)#no shutdown
Router(config)#interface serial 0/1/1
Router(config-if)#ipv6 address 2001::/127
Router(config-if)#ipv6 address fe80::54 link-local
Router(config-if)#clock rate 128000
Router(config-if)#no shutdown
Router#write



## SW1

Switch>enable
Switch#configure terminal
Switch(config)#hostname SW1
Switch(config)#vlan 10
Switch(config-vlan)#name ROJO
Switch(config)#interface gigabitEthernet 0/2
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 10
Switch(config)#vlan 20
Switch(config-vlan)#name CELESTE
Switch(config)#interface range fastEthernet 0/1-10
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 20
Switch(config)#interface GigabitEthernet 0/1
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10
Switch(config-if)#switchport trunk allowed vlan add 20
Switch#write


## SW2 Configuración básica

Switch>enable
Switch#configure terminal
Switch(config)#hostname SW2
Switch(config)#line console 0
Switch(config-line)#password cisco
Switch(config-line)#login
Switch(config-line)#line vty 0 4
Switch(config-line)#password cisco
Switch(config-line)#login
Switch(config-line)#logging synchronous
Switch(config)#no ip domain-lookup
Switch(config)#enable secret class
Switch(config)#ip routing
Switch(config)#ipv6 unicast-routing
Switch#write


## Interfaces de Ruteo G1/0/23

SW2(config)#interface gigabitEthernet 1/0/23
SW2(config-if)#no switchport
SW2(config-if)#ip address 10.1.1.18 255.255.255.252
SW2(config-if)#ipv6 address fe80::60 link-local
SW2(config-if)#ipv6 address 2001::11/127
SW2(config-if)#no shutdown
SW2#write

##  G1/0/24

SW2(config)#interface gigabitEthernet 1/0/24
SW2(config-if)#no switchport
SW2(config-if)#ip address 10.1.1.26 255.255.255.252
SW2(config-if)#ipv6 address fe80::61 link-local
SW2(config-if)#ipv6 address 2001::15/127
SW2(config-if)#no shutdown
SW2#write


# VLANs

SW2(config)#vlan 30
SW2(config-vlan)#name NEGRO
SW2(config)#interface range gigabitEthernet 1/0/1-10
SW2(config-if-range)#switchport mode access
SW2(config-if-range)#switchport access vlan 30
SW2(config)#interface vlan 30
SW2(config-if)#ip address 172.16.30.254 255.255.255.0
SW2(config-if)#ipv6 address fe80::62 link-local
SW2(config-if)#ipv6 address 2001:db8:0:30::/64
SW2#write


SW2(config)#vlan 40
SW2(config-vlan)#name AZUL
SW2(config)#interface range gigabitEthernet 1/0/11-20
SW2(config-if-range)#switchport mode access
SW2(config-if-range)#switchport access vlan 40
SW2(config)#interface vlan 40
SW2(config-if)#ip address 172.16.40.254 255.255.255.0
SW2(config-if)#ipv6 address fe80::63 link-local
SW2(config-if)#ipv6 address 2001:db8:0:40::/64
SW2#write

## SW3 Configuración básica

Switch>enable
Switch#configure terminal
Switch(config)#hostname SW3
Switch(config)#line console 0
Switch(config-line)#password cisco
Switch(config-line)#login
Switch(config-line)#line vty 0 4
Switch(config-line)#password cisco
Switch(config-line)#login
Switch(config-line)#logging synchronous
Switch(config)#no ip domain-lookup
Switch(config)#enable secret class
Switch(config)#ip routing
Switch(config)#ipv6 unicast-routing
Switch#write


## Interfaces y VLANs G1/0/24

SW3(config)#interface gigabitEthernet 1/0/24
SW3(config-if)#no switchport
SW3(config-if)#ip address 10.1.1.22 255.255.255.252
SW3(config-if)#ipv6 address fe80::65 link-local
SW3(config-if)#ipv6 address 2001::13/127
SW3(config-if)#no shutdown
SW3#write

## VLAN 50

SW3(config)#vlan 50
SW3(config-vlan)#name AMARILLO
SW3(config)#interface range gigabitEthernet 1/0/1-10
SW3(config-if-range)#switchport mode access
SW3(config-if-range)#switchport access vlan 50
SW3(config)#interface vlan 50
SW3(config-if)#ip address 172.16.50.254 255.255.255.0
SW3(config-if)#ipv6 address fe80::66 link-local
SW3(config-if)#ipv6 address 2001:db8:0:50::/64
SW3#write
## VLAN 60

SW3(config)#vlan 60
SW3(config-vlan)#name ROSA
SW3(config)#interface range gigabitEthernet 1/0/11-20
SW3(config-if-range)#switchport mode access
SW3(config-if-range)#switchport access vlan 60
SW3(config)#interface vlan 60
SW3(config-if)#ip address 172.16.60.254 255.255.255.0
SW3(config-if)#ipv6 address fe80::67 link-local
SW3(config-if)#ipv6 address 2001:db8:0:60::/64
SW3#write

## SW4

Switch>enable
Switch#configure terminal
Switch(config)#hostname SW4
Switch(config)#vlan 70
Switch(config-vlan)#name VERDE
Switch(config)#interface range fastEthernet 0/1-10
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 70
Switch(config)#vlan 80
Switch(config-vlan)#name NARANJA
Switch(config)#interface gigabitEthernet 0/2
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 80
Switch#write






# Configuración DHCP
## R1

User Access Verification

Password: 
Password: 
Password: 

R1>enable
Password: 
Password: 
R1#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#ip dhcp pool R1DHCP
R1(dhcp-config)#network 172.16.20.0 255.255.255.0
R1(dhcp-config)#default-router 172.16.20.254
R1(dhcp-config)#dns-server 172.16.10.1
R1(dhcp-config)#exit
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...







User Access Verification

Password: 

R1>enable
Password: 
Password: 
R1#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#router ospf 10
R1(config-router)#router-id 1.1.1.1
R1(config-router)#log-adjacency-changes
R1(config-router)#network 10.1.1.0 0.0.0.3 area 0
R1(config-router)#network 10.1.1.4 0.0.0.3 area 0
R1(config-router)#network 172.16.10.0 0.0.0.255 area 0
R1(config-router)#network 172.16.20.0 0.0.0.255 area 0
R1(config-router)#passive-interface gigabitEthernet 0/0/0.10
R1(config-router)#passive-interface gigabitEthernet 0/0/0.20
R1(config-router)#exit
R1(config)#ipv6 router ospf 10
R1(config-rtr)#router-id 1.1.1.1
R1(config-rtr)#log-adjacency-changes
R1(config-rtr)#exit
R1(config)#interface serial 0/1/0
R1(config-if)#ipv6 ospf 10 area 0
R1(config-if)#exit
R1(config)#interface serial 0/1/1
R1(config-if)#ipv6 ospf 10 area 0
R1(config-if)#exit
R1(config)#interface gigabitEthernet 0/0/0.10
R1(config-subif)#ipv6 ospf 10 area 0
R1(config-subif)#exit
R1(config)#interface gigabitEthernet 0/0/0.20
R1(config-subif)#ipv6 ospf 10 area 0
R1(config-subif)#exit
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
[OK]
R1#






User Access Verification

Password: 

R2>enable
Password: 
R2#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R2(config)#router ospf 10
R2(config-router)#router-id 2.2.2.2
R2(config-router)#log-adjacency-changes
R2(config-router)#network 10.1.1.4 0.0.0.3 area 0
R2(config-router)#network 10.1.1.8 0.0.0.3 area 0
00:28:39: %OSPF-5-ADJCHG: Process 10, Nbr 1.1.1.1 on Serial0/2/1 from LOADING to FULL, Loading Done

R2(config-router)#network 10.1.1.12 0.0.0.3 area 0
R2(config-router)#network 10.1.1.16 0.0.0.3 area 0
R2(config-router)#network 10.1.1.20 0.0.0.3 area 0
R2(config-router)#exit
R2(config)#ipv6 router ospf 10
R2(config-rtr)#router-id 2.2.2.2
R2(config-rtr)#log-adjacency-changes 
R2(config-rtr)#exit
R2(config)#interface serial 0/1/0
R2(config-if)#ipv6 ospf 10 area 0
R2(config-if)#exit
R2(config)#interface serial 0/1/1
R2(config-if)#ipv6 ospf 10 area 0
R2(config-if)#exit
R2(config)#interface serial 0/2/1
R2(config-if)#ipv6 ospf 10 area 0
R2(config-if)#exit
R2(config)#
00:29:55: %OSPFv3-5-ADJCHG: Process 10, Nbr 1.1.1.1 on Serial0/2/1 from LOADING to FULL, Loading Done
interface gigabitEthernet 0/0/0
R2(config-if)#ipv6 ospf 10 area 0
R2(config-if)#exit
R2(config)#interface gigabitEthernet 0/0/1
R2(config-if)#ipv6 ospf 10 area 0
R2(config-if)#exit
R2(config)#exit
R2#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
[OK]
R2#




R3>enable
Password: 
Password: 
R3#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R3(config)#router ospf 10
R3(config-router)#router-id 3.3.3.3
R3(config-router)#log-adjacency-changes
R3(config-router)#network 10.1.1.12 0.0.0.3 area 0
R3(config-router)#network 10.1.1.24 0.0.0.3 area 0
R3(config-router)#
00:31:15: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on Serial0/1/1 from LOADING to FULL, Loading Done
network 172.16.70.0 0.0.0.255 area 0
R3(config-router)#network 172.16.80.0 0.0.0.255 area 0
R3(config-router)#passive-interface gigabitEthernet 0/0/0.70
R3(config-router)#passive-interface gigabitEthernet 0/0/0.80
R3(config-router)#exit
R3(config)#ipv6 router ospf 10
R3(config-rtr)#router-id 3.3.3.3
R3(config-rtr)#log-adjacency-changes 
R3(config-rtr)#exit
R3(config)#interface serial 0/1/1
R3(config-if)#ipv6 ospf 10 area 0
R3(config-if)#exit
R3(config)#
00:32:08: %OSPFv3-5-ADJCHG: Process 10, Nbr 2.2.2.2 on Serial0/1/1 from LOADING to FULL, Loading Done
interface gigabitEthernet 0/0/0.70
R3(config-subif)#ipv6 ospf 10 area 0
R3(config-subif)#exit
R3(config)#interface gigabitEthernet 0/0/0.80
R3(config-subif)#ipv6 ospf 10 area 0
R3(config-subif)#exit
R3(config)#interface gigabitEthernet 0/0/1
R3(config-if)#ipv6 ospf 10 area 0
R3(config-if)#exit
R3(config)#exit
R3#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
[OK]




User Access Verification

Password: 

R4>enable
Password: 
Password: 
R4#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R4(config)#router ospf 10
R4(config-router)#router-id 4.4.4.4
R4(config-router)#log-adjacency-changes
R4(config-router)#network 10.1.1.0 0.0.0.3 area 0
R4(config-router)#
00:40:37: %OSPF-5-ADJCHG: Process 10, Nbr 1.1.1.1 on Serial0/1/0 from LOADING to FULL, Loading Done
network 10.1.1.8 0.0.0.3 area 0
R4(config-router)#
00:40:40: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on Serial0/2/0 from LOADING to FULL, Loading Done
network 11.1.1.0 0.0.0.3 area 0
R4(config-router)#default-information originate
R4(config-router)#exit
R4(config)#ipv6 router ospf 10
R4(config-rtr)#router-id 4.4.4.4
R4(config-rtr)#log-adjacency-changes
R4(config-rtr)#default-information originate
R4(config-rtr)#redistribute static
R4(config-rtr)#exit
R4(config)#interface serial 0/1/0
R4(config-if)#ipv6 ospf 10 area 0
R4(config-if)#exit
R4(config)#interface serial 0/1/1
R4(config-if)#
00:41:40: %OSPFv3-5-ADJCHG: Process 10, Nbr 1.1.1.1 on Serial0/1/0 from LOADING to FULL, Loading Done
ipv6 ospf 10 area 0
R4(config-if)#exit
R4(config)#interface serial 0/2/0
R4(config-if)#ipv6 ospf 10 area 0
R4(config-if)#exit
R4(config)#exit
R4#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
[OK]
R4#
00:42:05: %OSPFv3-5-ADJCHG: Process 10, Nbr 2.2.2.2 on Serial0/2/0 from LOADING to FULL, Loading Done






SW2>enable
Password: 
SW2#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
SW2(config)#router ospf 10
SW2(config-router)#router-id 5.5.5.5
SW2(config-router)#log-adjacency-changes
SW2(config-router)#network 10.1.1.16 0.0.0.3 area 0
SW2(config-router)#network 10.1.1.24 0.0.0.3 area 0
SW2(config-router)#network 172.16.30.0 0.0.0.255 area 0
00:43:36: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet1/0/23 from LOADING to FULL, Loading Done

SW2(config-router)#
00:43:39: %OSPF-5-ADJCHG: Process 10, Nbr 3.3.3.3 on GigabitEthernet1/0/24 from LOADING to FULL, Loading Done
network 172.16.40.0 0.0.0.255 area 0
SW2(config-router)#passive-interface vlan30
SW2(config-router)#passive-interface vlan40
SW2(config-router)#exit
SW2(config)#ipv6 router ospf 10
SW2(config-rtr)#router-id 5.5.5.5
SW2(config-rtr)#log-adjacency-changes 
SW2(config-rtr)#exit
SW2(config)#interface gigabitEthernet1/0/23
SW2(config-if)#ipv6 ospf 10 area 0
SW2(config-if)#eit
                ^
% Invalid input detected at '^' marker.
	
SW2(config-if)#exit
SW2(config)#interface gigabitEthernet1/0/24
SW2(config-if)#ipv6 ospf 10 area 0
SW2(config-if)#}
00:44:35: %OSPFv3-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet1/0/23 from LOADING to FULL, Loading Done
exit
               ^
% Invalid input detected at '^' marker.
	
SW2(config-if)#
00:44:45: %OSPFv3-5-ADJCHG: Process 10, Nbr 3.3.3.3 on GigabitEthernet1/0/24 from LOADING to FULL, Loading Done
exit
SW2(config)#interface vlan30
SW2(config-if)#ipv6 ospf 10 area 0
SW2(config-if)#exit
SW2(config)#interface vlan40
SW2(config-if)#ipv6 ospf 10 area 0
SW2(config-if)#exit
SW2(config)#exit
SW2#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
Compressed configuration from 7383 bytes to 3601 bytes[OK]
[OK]
SW2#







User Access Verification

Password: 

SW3>enable
Password: 
Password: 
SW3#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
SW3(config)#router ospf 10
SW3(config-router)#router-id 6.6.6.6
SW3(config-router)#log-adjacency-changes
SW3(config-router)#network 10.1.1.20 0.0.0.3 area 0
SW3(config-router)#network 172.16.50.0 0.0.0.255 area 0
SW3(config-router)#network 172.16.60.0 0.0.0.255 area 0
SW3(config-router)#
00:46:42: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet1/0/24 from LOADING to FULL, Loading Done
passive-interface vlan50
SW3(config-router)#passive-interface vlan60
SW3(config-router)#exit
SW3(config)#ipv6 router ospf 10
SW3(config-rtr)#router-id 6.6.6.6
SW3(config-rtr)#log-adjacency-changes
SW3(config-rtr)#exit
SW3(config)#interface gigabitEthernet1/0/24
SW3(config-if)#ipv6 ospf 10 area 0
SW3(config-if)#exit
SW3(config)#interface vlan50
SW3(config-if)#ipv6 ospf 10 area 0
00:47:33: %OSPFv3-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet1/0/24 from LOADING to FULL, Loading Done

SW3(config-if)#exit
SW3(config)#interface vlan60
SW3(config-if)#ipv6 ospf 10 area 0
SW3(config-if)#exit
SW3(config)#exit
SW3#
%SYS-5-CONFIG_I: Configured from console by console
write
Building configuration...
Compressed configuration from 7383 bytes to 3601 bytes[OK]
[OK]
