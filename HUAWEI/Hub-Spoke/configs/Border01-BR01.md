### Border01-BR01
```
[V300R019C00SPC300]
#
 sysname Border01-BR01
#
stp disable
#
authentication-profile name default_authen_profile
authentication-profile name dot1x_authen_profile
authentication-profile name dot1xmac_authen_profile
authentication-profile name mac_authen_profile
authentication-profile name multi_authen_profile
authentication-profile name portal_authen_profile
#
dhcp enable
#
radius-server template default
#
pki realm default
#
ssl policy default_policy type server
 pki-realm default
 version tls1.2
 ciphersuite rsa_aes_128_cbc_sha rsa_aes_128_sha256 rsa_aes_256_sha256 ecdhe_rsa_aes128_gcm_sha256 ecdhe_rsa_aes256_gcm_sha384
#
acl number 2000
 rule 5 permit source 192.168.210.0 0.0.0.255
 rule 10 permit source 192.168.220.0 0.0.0.255
 rule 15 permit source 192.168.230.0 0.0.0.255
 rule 20 deny
#
ipsec proposal 10
 esp authentication-algorithm sha2-512
 esp encryption-algorithm aes-256
#
ike proposal default
 encryption-algorithm aes-256 aes-192 aes-128
 dh group14
 authentication-algorithm sha2-512 sha2-384 sha2-256
 authentication-method pre-share
 integrity-algorithm hmac-sha2-256
 prf hmac-sha2-256
ike proposal 10
 encryption-algorithm aes-256
 dh group14
 authentication-algorithm sha2-256
 authentication-method pre-share
 integrity-algorithm hmac-sha2-256
 prf hmac-sha2-256
#
ike peer HQ-01
 pre-shared-key cipher %^%#v|^!M-o)*FR@N-72R@RJXWs5#IDg5Ir/GJE^TJ&&%^%#
 ike-proposal 10
 local-address 2.58.17.1
 remote-address 14.1.2.1
 rsa encryption-padding oaep
 rsa signature-padding pss
 ikev2 authentication sign-hash sha2-256
#
ipsec profile HQ-01-PROF
 ike-peer HQ-01
 proposal 10
#
free-rule-template name default_free_rule
#
portal-access-profile name portal_access_profile
#
aaa
 authentication-scheme default
 authentication-scheme radius
  authentication-mode radius
 authorization-scheme default
 accounting-scheme default
 local-aaa-user password policy administrator
  undo password alert original
 local-aaa-user password policy access-user
 domain default
  authentication-scheme default
 domain default_admin
  authentication-scheme default
 undo user-password complexity-check
 undo local-user admin
 local-user super password irreversible-cipher $1a$3^@+N$E3OL$"0R*(}gOZ7{bSkF#daO9<Q`cG]W:~,sE:>=#];UX$
 local-user super privilege level 15
 local-user super service-type telnet terminal
#
firewall zone Local
#
interface GigabitEthernet0/0/0
 ip address 2.58.17.1 255.255.255.252
 nat outbound 2000
#
interface GigabitEthernet0/0/1
 ip address 10.0.1.0 255.255.255.254
 ospf network-type p2p
 ospf enable 1 area 0.0.0.0
#
interface GigabitEthernet0/0/2
#
interface GigabitEthernet0/0/3
#
interface GigabitEthernet0/0/4
#
interface GigabitEthernet0/0/5
#
interface GigabitEthernet0/0/6
 description VirtualPort
#
interface GigabitEthernet0/0/7
#
interface GigabitEthernet0/0/8
 description VirtualPort
#
interface NULL0
#
interface LoopBack0
 ip address 2.2.2.2 255.255.255.255
 ospf enable 1 area 0.0.0.0
#
interface Tunnel0/0/1
 ip address 172.16.10.2 255.255.255.252
 tunnel-protocol gre
 source 2.58.17.1
 destination 14.1.2.1
 ipsec profile HQ-01-PROF
#
bgp 65200
 peer 172.16.10.1 as-number 65100
 peer 172.16.10.1 connect-interface Tunnel0/0/1
 #
 ipv4-family unicast
  undo synchronization
  import-route ospf 1
  peer 172.16.10.1 enable
  peer 172.16.10.1 ip-prefix PL_ALLOWED_PREFIXES import
#
ospf 1 router-id 2.2.2.2
 default-route-advertise always
 area 0.0.0.0
#
 snmp-agent local-engineid 800007DB03E0FC000A0B0C
 snmp-agent trap enable
#
 ssh server permit interface GigabitEthernet0/0/0
#
 http secure-server ssl-policy default_policy
 http secure-server enable
 http server permit interface GigabitEthernet0/0/0
#
ip ip-prefix PL_ALLOWED_PREFIXES index 10 permit 192.168.0.0 16 greater-equal 16 less-equal 32
#
ip route-static 0.0.0.0 0.0.0.0 2.58.17.2
#
fib regularly-refresh disable
#
user-interface con 0
 authentication-mode aaa
user-interface vty 0
 authentication-mode aaa
 user privilege level 15
user-interface vty 1 4
#
dot1x-access-profile name dot1x_access_profile
#
mac-access-profile name mac_access_profile
#
ops
#
autostart
#
secelog
#
 ms-channel

#
return
```