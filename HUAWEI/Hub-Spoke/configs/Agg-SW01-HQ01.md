### Agg-SW01-HQ01
```
#
sysname Agg-SW01-HQ01
#
device board 1 board-type CE-MPUB
#
vlan batch 110 120 130 140
#
dhcp enable
#
acl number 2210
 rule 10 permit source 192.168.210.0 0.0.0.255
#
acl number 2220
 rule 10 permit source 192.168.220.0 0.0.0.255
#
acl number 2230
 rule 10 permit source 192.168.230.0 0.0.0.255
#
aaa
 #
 authentication-scheme default
 #
 authorization-scheme default
 #
 accounting-scheme default
 #
 domain default
 #
 domain default_admin
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
interface MEth0/0/0
 undo shutdown
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
interface GE1/0/6
 undo shutdown
#
interface GE1/0/7
 undo shutdown
#
interface GE1/0/8
 undo shutdown
#
interface GE1/0/9
 undo shutdown
#
interface GE1/0/10
 undo shutdown
#
interface GE1/0/11
 undo shutdown
#
interface GE1/0/12
 undo shutdown
#
interface GE1/0/13
 undo shutdown
#
interface GE1/0/14
 undo shutdown
#
interface GE1/0/15
 undo shutdown
#
interface GE1/0/16
 undo shutdown
#
interface GE1/0/17
 undo shutdown
#
interface GE1/0/18
 undo shutdown
#
interface GE1/0/19
 undo shutdown
#
interface GE1/0/20
 shutdown
#
interface GE1/0/21
 shutdown
#
interface GE1/0/22
 shutdown
#
interface GE1/0/23
 shutdown
#
interface GE1/0/24
 shutdown
#
interface GE1/0/25
 shutdown
#
interface GE1/0/26
 shutdown
#
interface GE1/0/27
 shutdown
#
interface GE1/0/28
 shutdown
#
interface GE1/0/29
 shutdown
#
interface GE1/0/30
 shutdown
#
interface GE1/0/31
 shutdown
#
interface GE1/0/32
 shutdown
#
interface GE1/0/33
 shutdown
#
interface GE1/0/34
 shutdown
#
interface GE1/0/35
 shutdown
#
interface GE1/0/36
 shutdown
#
interface GE1/0/37
 shutdown
#
interface GE1/0/38
 shutdown
#
interface GE1/0/39
 shutdown
#
interface GE1/0/40
 shutdown
#
interface GE1/0/41
 shutdown
#
interface GE1/0/42
 shutdown
#
interface GE1/0/43
 shutdown
#
interface GE1/0/44
 shutdown
#
interface GE1/0/45
 shutdown
#
interface GE1/0/46
 shutdown
#
interface GE1/0/47
 shutdown
#
interface LoopBack0
 ip address 1.1.1.10 255.255.255.255
 ospf enable 1 area 0.0.0.0
#
interface NULL0
#
ospf 1 router-id 1.1.1.10
 area 0.0.0.0
#
ssh authorization-type default aaa
#
ssh server cipher aes256_gcm aes128_gcm aes256_ctr aes192_ctr aes128_ctr aes256_cbc aes128_cbc 3des_cbc
#
ssh server dh-exchange min-len 1024
#
ssh client cipher aes256_gcm aes128_gcm aes256_ctr aes192_ctr aes128_ctr aes256_cbc aes128_cbc 3des_cbc
#
user-interface con 0
#
vm-manager
#
return
```