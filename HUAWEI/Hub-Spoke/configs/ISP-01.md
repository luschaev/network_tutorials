### ISP-01
```
[V300R019C00SPC300]
#
 sysname ISP-01
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
ike proposal default
 encryption-algorithm aes-256 aes-192 aes-128
 dh group14
 authentication-algorithm sha2-512 sha2-384 sha2-256
 authentication-method pre-share
 integrity-algorithm hmac-sha2-256
 prf hmac-sha2-256
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
 local-user super password irreversible-cipher $1a$Q@;lC#7_~'$h_;m'I42j@6tPsFp3S\>&38LYC4^`J@'uk"I>'%4$
 local-user super privilege level 15
 local-user super service-type telnet terminal
#
firewall zone Local
#
interface GigabitEthernet0/0/0
 ip address 14.1.2.2 255.255.255.252
#
interface GigabitEthernet0/0/1
 ip address 2.58.17.2 255.255.255.252
#
interface GigabitEthernet0/0/2
 ip address 195.147.98.2 255.255.255.252
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
 ip address 8.8.8.8 255.255.255.255
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