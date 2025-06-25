### Agg-SW01-BR02
```
#
sysname Agg-SW01-BR02
#
device board 1 board-type CE-MPUB
#
vlan batch 10 20 30
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
isis 1
 network-entity 49.0001.0000.0000.0002.00
#
interface Vlanif10
 ip address 192.168.10.254 255.255.255.0
 isis enable 1
 isis circuit-type p2p
#
interface Vlanif20
 ip address 192.168.20.254 255.255.255.0
 isis enable 1
 isis circuit-type p2p
#
interface Vlanif30
 ip address 192.168.30.254 255.255.255.0
#
interface MEth0/0/0
 undo shutdown
#
interface GE1/0/0
 undo portswitch
 undo shutdown
 ip address 10.0.2.2 255.255.255.254
 isis enable 1
 isis circuit-type p2p
#
interface GE1/0/1
 undo portswitch
 undo shutdown
 ip address 10.0.2.0 255.255.255.254
 isis enable 1
 isis circuit-type p2p
#
interface GE1/0/2
 undo shutdown
 port default vlan 20
#
interface GE1/0/3
 undo shutdown
 port default vlan 10
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
 ip address 3.3.3.10 255.255.255.255
 isis enable 1
#
interface NULL0
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