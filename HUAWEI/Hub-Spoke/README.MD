![](images/Hub-Spoke-Topolgy-01.png)

![Agg-SW01-HQ01 full config](configs/Agg-SW01-HQ01.ios)

```
sysname Agg-SW01-HQ01
#
device board 1 board-type CE-MPUB
#
vlan batch 110 120 130 140
#
dhcp enable
#
interface Vlanif110
 ip address 192.168.110.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
 dhcp select relay
 dhcp relay binding server ip 192.168.140.100
#
interface Vlanif120
 ip address 192.168.120.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
 dhcp select relay
 dhcp relay binding server ip 192.168.140.100
#
interface Vlanif130
 ip address 192.168.130.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
 dhcp select relay
 dhcp relay binding server ip 192.168.140.100
#
interface Vlanif140
 ip address 192.168.140.254 255.255.255.0
#
interface Eth-Trunk10
 port link-type trunk
 port trunk allow-pass vlan 140
 mode lacp-static
#
interface GE1/0/0
 undo portswitch
 undo shutdown
 ip address 10.0.0.1 255.255.255.254
 ospf network-type p2p
 ospf enable 1 area 0.0.0.0
#
interface GE1/0/1
 undo shutdown
 port default vlan 110
#
interface GE1/0/2
 undo shutdown
 port default vlan 120
#
interface GE1/0/3
 undo shutdown
 port default vlan 130
#
interface GE1/0/4
 undo shutdown
 eth-trunk 10
#
interface GE1/0/5
 undo shutdown
 eth-trunk 10
#
interface LoopBack0
 ip address 1.1.1.10 255.255.255.255
 ospf enable 1 area 0.0.0.0
#
ospf 1 router-id 1.1.1.10
 area 0.0.0.0
#
```

