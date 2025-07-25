### Agg-SW01-BR01
```
#
sysname Agg-SW01-BR01
#
device board 1 board-type CE-MPUB
#
vlan batch 210 220 230
#
dhcp enable
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
interface Vlanif210
 ip address 192.168.210.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
 dhcp select relay
#
interface Vlanif220
 ip address 192.168.220.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
#
interface Vlanif230
 ip address 192.168.230.254 255.255.255.0
 ospf enable 1 area 0.0.0.0
#
interface MEth0/0/0
 undo shutdown
#
interface GE1/0/0
 undo portswitch
 undo shutdown
 ip address 10.0.1.1 255.255.255.254
 ospf network-type p2p
 ospf enable 1 area 0.0.0.0
#
interface GE1/0/1
 undo shutdown
 port default vlan 210
#
interface GE1/0/2
 undo shutdown
 port default vlan 220
#
interface GE1/0/3
 undo shutdown
 port default vlan 230
#
interface GE1/0/4
 undo shutdown
#
interface GE1/0/5
 undo shutdown
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
 ip address 2.2.2.10 255.255.255.255
 ospf enable 1 area 0.0.0.0
#
interface NULL0
#
ospf 1 router-id 2.2.2.10
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