### SW9
```
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname SW9
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
!
!
!
!
!
ip arp inspection vlan 10,20
!
!
!
ip dhcp snooping vlan 10,20
no ip dhcp snooping information option
ip dhcp snooping
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface GigabitEthernet0/0
 description *** to DHCP Server ***
 switchport trunk allowed vlan 10,20
 switchport trunk encapsulation dot1q
 switchport mode trunk
 ip arp inspection trust
 negotiation auto
 ip dhcp snooping trust
!
interface GigabitEthernet0/1
 description *** to SW10 ***
 switchport trunk allowed vlan 10,20
 switchport trunk encapsulation dot1q
 switchport mode trunk
 ip arp inspection trust
 negotiation auto
!
interface GigabitEthernet0/2
 description *** to Static Server ***
 switchport access vlan 10
 switchport mode access
 ip device tracking maximum 8
 ip arp inspection trust
 negotiation auto
 ip verify source tracking
!
interface GigabitEthernet0/3
 description *** to Clients ***
 switchport access vlan 10
 switchport mode access
 negotiation auto
!
interface GigabitEthernet1/0
 description *** to Clients ***
 switchport access vlan 20
 switchport mode access
 negotiation auto
!
interface GigabitEthernet1/1
 description *** to Clients ***
 switchport access vlan 10
 switchport mode access
 switchport port-security maximum 3
 switchport port-security violation restrict
 switchport port-security
 negotiation auto
!
interface GigabitEthernet1/2
 negotiation auto
!
interface GigabitEthernet1/3
 negotiation auto
!
ip forward-protocol nd
!
ip http server
ip http secure-server
!
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
ip source binding 5000.0003.0000 vlan 10 192.168.10.100 interface Gi0/2
!
!
!
!
control-plane
!
banner exec ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
banner incoming ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
banner login ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
!
line con 0
line aux 0
line vty 0 4
 login
!
!
end
```