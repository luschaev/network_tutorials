# Hub and Spoke Topology Huawei AR1000v + CE6800

![](images/Hub-Spoke-Topolgy-01.png)

#### [Border01-HQ01 full config](configs/Border01-HQ01.md)
<details>
    <summary>display version</summary>
    
    <Border01-HQ01>display vers
    Huawei Versatile Routing Platform Software
    VRP (R) software, Version 5.170 (AR1000V V300R019C00SPC300)
    Copyright (C) 2011-2019 HUAWEI TECH CO., LTD
    Huawei AR1000V Router uptime is 0 week, 0 day, 3 hours, 1 minute
</details>

<details>
    <summary>display ip int b</summary>

    <Border01-HQ01>display ip int b
    *down: administratively down
    ^down: standby
    (l): loopback
    (s): spoofing
    (E): E-Trunk down
    The number of interface that is UP in Physical is 13
    The number of interface that is DOWN in Physical is 0
    The number of interface that is UP in Protocol is 6
    The number of interface that is DOWN in Protocol is 7

    Interface                         IP Address/Mask      Physical   Protocol
    GigabitEthernet0/0/0              14.1.2.1/30          up         up
    GigabitEthernet0/0/1              10.0.0.0/31          up         up
    GigabitEthernet0/0/2              unassigned           up         down
    GigabitEthernet0/0/3              unassigned           up         down
    GigabitEthernet0/0/4              unassigned           up         down
    GigabitEthernet0/0/5              unassigned           up         down
    GigabitEthernet0/0/6              unassigned           up         down
    GigabitEthernet0/0/7              unassigned           up         down
    GigabitEthernet0/0/8              unassigned           up         down
    LoopBack0                         1.1.1.1/32           up         up(s)
    NULL0                             unassigned           up         up(s)
    Tunnel0/0/1                       172.16.10.1/30       up         up
    Tunnel0/0/2                       172.16.20.1/30       up         up
</details>

<details>
    <summary>display ip routing-table protocol ospf</summary>

    <Border01-HQ01>display ip routing-table protocol ospf
    Route Flags: R - relay, D - download to fib, T - to vpn-instance
    ------------------------------------------------------------------------------
    Public routing table : OSPF
            Destinations : 4        Routes : 4

    OSPF routing table status : <Active>
            Destinations : 4        Routes : 4

    Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

        1.1.1.10/32  OSPF    10   1           D   10.0.0.1        GigabitEthernet0/0/1
    192.168.110.0/24  OSPF    10   2           D   10.0.0.1        GigabitEthernet0/0/1
    192.168.120.0/24  OSPF    10   2           D   10.0.0.1        GigabitEthernet0/0/1
    192.168.130.0/24  OSPF    10   2           D   10.0.0.1        GigabitEthernet0/0/1

    OSPF routing table status : <Inactive>
            Destinations : 0        Routes : 0
</details>

<details>
    <summary>display bgp peer</summary>

    <Border01-HQ01>display bgp peer

    Status codes: * - Dynamic

    BGP local router ID : 14.1.2.1
    Local AS number : 65100
    Total number of peers : 2                Peers in established state : 2
    Total number of dynamic peers : 0

    Peer            V          AS  MsgRcvd  MsgSent  OutQ  Up/Down       State PrefRcv

    172.16.10.2     4       65200      194      197     0 03:08:36 Established       3
    172.16.20.2     4       65300      194      196     0 03:07:48 Established       2
</details>

<details>
    <summary>display ip routing-table protocol bgp</summary>

    <Border01-HQ01>display ip routing-table protocol bgp
    Route Flags: R - relay, D - download to fib, T - to vpn-instance
    ------------------------------------------------------------------------------
    Public routing table : BGP
            Destinations : 5        Routes : 5

    BGP routing table status : <Active>
            Destinations : 5        Routes : 5

    Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

    192.168.10.0/24  EBGP    255  20         RD   172.16.20.2     Tunnel0/0/2
    192.168.20.0/24  EBGP    255  20         RD   172.16.20.2     Tunnel0/0/2
    192.168.210.0/24  EBGP    255  2          RD   172.16.10.2     Tunnel0/0/1
    192.168.220.0/24  EBGP    255  2          RD   172.16.10.2     Tunnel0/0/1
    192.168.230.0/24  EBGP    255  2          RD   172.16.10.2     Tunnel0/0/1

    BGP routing table status : <Inactive>
            Destinations : 0        Routes : 0

</details>

<details>
    <summary>display ipsec sa brief</summary>

    <Border01-HQ01>display ipsec sa b

    IPSec SA information:
    Src address                             Dst address                             SPI
    VPN                                     Protocol                                Algorithm
    --------------------------------------------------------------------------------------------------------------------------
    14.1.2.1                                195.147.98.1                            11898564
                                            ESP                                     E:AES-256 A:SHA2_512_256
    195.147.98.1                            14.1.2.1                                2909459
                                            ESP                                     E:AES-256 A:SHA2_512_256
    14.1.2.1                                2.58.17.1                               240680
                                            ESP                                     E:AES-256 A:SHA2_512_256
    2.58.17.1                               14.1.2.1                                14985427
                                            ESP                                     E:AES-256 A:SHA2_512_256

    Number of IPSec SA : 4
    --------------------------------------------------------------------------------------------------------------------------
</details>

<details>
    <summary>display ike sa</summary>

    <Border01-HQ01>
    Conn-ID    Peer                                          VPN              Flag(s)               Phase  RemoteType  RemoteID
    ------------------------------------------------------------------------------------------------------------------------------------
    16         2.58.17.1/500                                                  RD|A                  v2:2   IP          2.58.17.1
    4          2.58.17.1/500                                                  RD|A                  v2:1   IP          2.58.17.1
    17         195.147.98.1/500                                               RD|ST|A               v2:2   IP          195.147.98.1
    6          195.147.98.1/500                                               RD|ST|A               v2:1   IP          195.147.98.1

    Number of IKE SA : 4
    ------------------------------------------------------------------------------------------------------------------------------------

    Flag Description:
    RD--READY   ST--STAYALIVE   RL--REPLACED   FD--FADING   TO--TIMEOUT
    HRT--HEARTBEAT   LKG--LAST KNOWN GOOD SEQ NO.   BCK--BACKED UP
    M--ACTIVE   S--STANDBY   A--ALONE  NEG--NEGOTIATING
</details>

#### [Agg-SW01-HQ01 full config](configs/Agg-SW01-HQ01.md)

```
<Agg-SW01-HQ01>display version
Huawei Versatile Routing Platform Software
VRP (R) software, Version 8.180 (CE6800 V200R005C10SPC607B607)
Copyright (C) 2012-2018 Huawei Technologies Co., Ltd.
HUAWEI CE6800 uptime is 0 day, 3 hours, 15 minutes
SVRP Platform Version 1.0
```

```
<Agg-SW01-HQ01>display ip int b
*down: administratively down
!down: FIB overload down
^down: standby
(l): loopback
(s): spoofing
(d): Dampening Suppressed
The number of interface that is UP in Physical is 7
The number of interface that is DOWN in Physical is 1
The number of interface that is UP in Protocol is 6
The number of interface that is DOWN in Protocol is 2
Interface                   IP Address/Mask    Physical Protocol VPN
GE1/0/0                     10.0.0.1/31        up       up       --
LoopBack0                   1.1.1.10/32        up       up(s)    --
MEth0/0/0                   unassigned         up       down     --
NULL0                       unassigned         up       up(s)    --
Vlanif110                   192.168.110.254/24 up       up       --
Vlanif120                   192.168.120.254/24 up       up       --
Vlanif130                   192.168.130.254/24 up       up       --
Vlanif140                   192.168.140.254/24 down     down     --
```

```
<Agg-SW01-HQ01>display ospf peer
OSPF Process 1 with Router ID 1.1.1.10
 Area 0.0.0.0 interface 10.0.0.1 (GE1/0/0)'s neighbors
  Router ID: 1.1.1.1            Address : 10.0.0.0
  State    : Full               Mode    : Nbr is Slave       Priority: 1
  DR       : None               BDR     : None               MTU     : 0
  Dead timer due (in seconds) : 30
  Retrans timer interval      : 5
  Neighbor up time            : 02h45m47s
  Neighbor up time stamp      : 2025-06-25 10:26:59
  Authentication Sequence     : 0
```

```
<Agg-SW01-HQ01>display ip routing-table protocol ospf
Proto: Protocol        Pre: Preference
Route Flags: R - relay, D - download to fib, T - to vpn-instance, B - black hole route
------------------------------------------------------------------------------
_public_ Routing Table : OSPF
         Destinations : 7        Routes : 7

OSPF routing table status : <Active>
         Destinations : 2        Routes : 2

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

        0.0.0.0/0   O_ASE   150  1             D   10.0.0.0        GE1/0/0
        1.1.1.1/32  OSPF    10   1             D   10.0.0.0        GE1/0/0

OSPF routing table status : <Inactive>
         Destinations : 5        Routes : 5

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

       1.1.1.10/32  OSPF    10   0                 1.1.1.10        LoopBack0
       10.0.0.0/31  OSPF    10   1                 10.0.0.1        GE1/0/0
  192.168.110.0/24  OSPF    10   1                 192.168.110.254 Vlanif110
  192.168.120.0/24  OSPF    10   1                 192.168.120.254 Vlanif120
  192.168.130.0/24  OSPF    10   1                 192.168.130.254 Vlanif130
```
```
<Agg-SW01-HQ01>display eth-trunk
Eth-Trunk10's state information is:
Local:
LAG ID: 10                      Working Mode: Static
Preempt Delay: Disabled         Hash Arithmetic: According to flow
System Priority: 32768          System ID: 708c-9b8c-d9c0
Least Active-linknumber: 1      Max Active-linknumber: 32
Operating Status: up            Number Of Up Ports In Trunk: 2
Timeout Period: Slow
--------------------------------------------------------------------------------
ActorPortName          Status   PortType PortPri PortNo PortKey PortState Weight
GE1/0/4                Selected 100M     32768   1      2593    10111100  1
GE1/0/5                Selected 100M     32768   2      2593    10111100  1

Partner:
--------------------------------------------------------------------------------
ActorPortName          SysPri   SystemID        PortPri PortNo PortKey PortState
GE1/0/4                32768    001e-49c3-7400  32768   1      1       10111100
GE1/0/5                32768    001e-49c3-7400  32768   1      1       10111100
```

#### Cisco EtherChannel status

```
Router#sh etherchannel summary
Flags:  D - down        P/bndl - bundled in port-channel
        I - stand-alone s/susp - suspended
        H - Hot-standby (LACP only)
        R - Layer3      S - Layer2
        U - in use      f - failed to allocate aggregator

        M - not in use, minimum links not met
        u - unsuitable for bundling
        w - waiting to be aggregated
        d - default port


Number of channel-groups in use: 1
Number of aggregators:           1

Group  Port-channel  Protocol    Ports
------+-------------+-----------+-----------------------------------------------
1       Po1(RU)         LACP     Gi1(bndl) Gi2(bndl)

RU - L3 port-channel UP State
SU - L2 port-channel UP state
P/bndl -  Bundled
S/susp  - Suspended
```

#### [Border01-BR01 full config](configs/Border01-BR01.md)

```
<Border01-BR01>display vers
Huawei Versatile Routing Platform Software
VRP (R) software, Version 5.170 (AR1000V V300R019C00SPC300)
Copyright (C) 2011-2019 HUAWEI TECH CO., LTD
Huawei AR1000V Router uptime is 0 week, 0 day, 3 hours, 20 minutes
```

```
<Border01-BR01>display ip int b
*down: administratively down
^down: standby
(l): loopback
(s): spoofing
(E): E-Trunk down
The number of interface that is UP in Physical is 12
The number of interface that is DOWN in Physical is 0
The number of interface that is UP in Protocol is 5
The number of interface that is DOWN in Protocol is 7

Interface                         IP Address/Mask      Physical   Protocol
GigabitEthernet0/0/0              2.58.17.1/30         up         up
GigabitEthernet0/0/1              10.0.1.0/31          up         up
GigabitEthernet0/0/2              unassigned           up         down
GigabitEthernet0/0/3              unassigned           up         down
GigabitEthernet0/0/4              unassigned           up         down
GigabitEthernet0/0/5              unassigned           up         down
GigabitEthernet0/0/6              unassigned           up         down
GigabitEthernet0/0/7              unassigned           up         down
GigabitEthernet0/0/8              unassigned           up         down
LoopBack0                         2.2.2.2/32           up         up(s)
NULL0                             unassigned           up         up(s)
Tunnel0/0/1                       172.16.10.2/30       up         up
```

```
<Border01-BR01>display ip routing-table protocol ospf
Route Flags: R - relay, D - download to fib, T - to vpn-instance
------------------------------------------------------------------------------
Public routing table : OSPF
         Destinations : 4        Routes : 4

OSPF routing table status : <Active>
         Destinations : 4        Routes : 4

Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

       2.2.2.10/32  OSPF    10   1           D   10.0.1.1        GigabitEthernet0/0/1
  192.168.210.0/24  OSPF    10   2           D   10.0.1.1        GigabitEthernet0/0/1
  192.168.220.0/24  OSPF    10   2           D   10.0.1.1        GigabitEthernet0/0/1
  192.168.230.0/24  OSPF    10   2           D   10.0.1.1        GigabitEthernet0/0/1

OSPF routing table status : <Inactive>
         Destinations : 0        Routes : 0
```

```
<Border01-BR01>display bgp peer

 Status codes: * - Dynamic

 BGP local router ID : 2.58.17.1
 Local AS number : 65200
 Total number of peers : 1                Peers in established state : 1
 Total number of dynamic peers : 0

  Peer            V          AS  MsgRcvd  MsgSent  OutQ  Up/Down       State PrefRcv

  172.16.10.1     4       65100      212      209     0 03:24:00 Established       5
```

```
<Border01-BR01>display ip routing-table protocol bgp
Route Flags: R - relay, D - download to fib, T - to vpn-instance
------------------------------------------------------------------------------
Public routing table : BGP
         Destinations : 5        Routes : 5

BGP routing table status : <Active>
         Destinations : 5        Routes : 5

Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

   192.168.10.0/24  EBGP    255  0          RD   172.16.10.1     Tunnel0/0/1
   192.168.20.0/24  EBGP    255  0          RD   172.16.10.1     Tunnel0/0/1
  192.168.110.0/24  EBGP    255  2          RD   172.16.10.1     Tunnel0/0/1
  192.168.120.0/24  EBGP    255  2          RD   172.16.10.1     Tunnel0/0/1
  192.168.130.0/24  EBGP    255  2          RD   172.16.10.1     Tunnel0/0/1

BGP routing table status : <Inactive>
         Destinations : 0        Routes : 0
```

```
<Border01-BR01>display ipsec sa b

IPSec SA information:
   Src address                             Dst address                             SPI
   VPN                                     Protocol                                Algorithm
 --------------------------------------------------------------------------------------------------------------------------
   14.1.2.1                                2.58.17.1                               240680
                                           ESP                                     E:AES-256 A:SHA2_512_256
   2.58.17.1                               14.1.2.1                                14985427
                                           ESP                                     E:AES-256 A:SHA2_512_256

  Number of IPSec SA : 2
 --------------------------------------------------------------------------------------------------------------------------
```

```
<Border01-BR01>display ike sa
 Conn-ID    Peer                                          VPN              Flag(s)               Phase  RemoteType  RemoteID
------------------------------------------------------------------------------------------------------------------------------------
 9          14.1.2.1/500                                                   RD|A                  v2:2   IP          14.1.2.1
 1          14.1.2.1/500                                                   RD|ST|A               v2:1   IP          14.1.2.1

  Number of IKE SA : 2
------------------------------------------------------------------------------------------------------------------------------------

 Flag Description:
 RD--READY   ST--STAYALIVE   RL--REPLACED   FD--FADING   TO--TIMEOUT
 HRT--HEARTBEAT   LKG--LAST KNOWN GOOD SEQ NO.   BCK--BACKED UP
 M--ACTIVE   S--STANDBY   A--ALONE  NEG--NEGOTIATING
```

#### [Agg-SW01-BR01 full config](configs/Agg-SW01-BR01.md)

```
<Agg-SW01-BR01>display vers
Huawei Versatile Routing Platform Software
VRP (R) software, Version 8.180 (CE6800 V200R005C10SPC607B607)
Copyright (C) 2012-2018 Huawei Technologies Co., Ltd.
HUAWEI CE6800 uptime is 0 day, 3 hours, 42 minutes
SVRP Platform Version 1.0
```

```
<Agg-SW01-BR01>display ip int b
*down: administratively down
!down: FIB overload down
^down: standby
(l): loopback
(s): spoofing
(d): Dampening Suppressed
The number of interface that is UP in Physical is 7
The number of interface that is DOWN in Physical is 0
The number of interface that is UP in Protocol is 6
The number of interface that is DOWN in Protocol is 1
Interface                   IP Address/Mask    Physical Protocol VPN
GE1/0/0                     10.0.1.1/31        up       up       --
LoopBack0                   2.2.2.10/32        up       up(s)    --
MEth0/0/0                   unassigned         up       down     --
NULL0                       unassigned         up       up(s)    --
Vlanif210                   192.168.210.254/24 up       up       --
Vlanif220                   192.168.220.254/24 up       up       --
Vlanif230                   192.168.230.254/24 up       up       --
```

```
<Agg-SW01-BR01>display ospf peer
OSPF Process 1 with Router ID 2.2.2.10
 Area 0.0.0.0 interface 10.0.1.1 (GE1/0/0)'s neighbors
  Router ID: 2.2.2.2            Address : 10.0.1.0
  State    : Full               Mode    : Nbr is Slave       Priority: 1
  DR       : None               BDR     : None               MTU     : 0
  Dead timer due (in seconds) : 36
  Retrans timer interval      : 5
  Neighbor up time            : 03h43m27s
  Neighbor up time stamp      : 2025-06-25 10:27:06
  Authentication Sequence     : 0
```

```
<Agg-SW01-BR01>display ip routing-table protocol ospf
Proto: Protocol        Pre: Preference
Route Flags: R - relay, D - download to fib, T - to vpn-instance, B - black hole route
------------------------------------------------------------------------------
_public_ Routing Table : OSPF
         Destinations : 7        Routes : 7

OSPF routing table status : <Active>
         Destinations : 2        Routes : 2

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

        0.0.0.0/0   O_ASE   150  1             D   10.0.1.0        GE1/0/0
        2.2.2.2/32  OSPF    10   1             D   10.0.1.0        GE1/0/0

OSPF routing table status : <Inactive>
         Destinations : 5        Routes : 5

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

       2.2.2.10/32  OSPF    10   0                 2.2.2.10        LoopBack0
       10.0.1.0/31  OSPF    10   1                 10.0.1.1        GE1/0/0
  192.168.210.0/24  OSPF    10   1                 192.168.210.254 Vlanif210
  192.168.220.0/24  OSPF    10   1                 192.168.220.254 Vlanif220
  192.168.230.0/24  OSPF    10   1                 192.168.230.254 Vlanif230
```

#### [Border01-BR02 full config](configs/Border01-BR02.md)

```
<Border01-BR02>display vers
Huawei Versatile Routing Platform Software
VRP (R) software, Version 5.170 (AR1000V V300R019C00SPC300)
Copyright (C) 2011-2019 HUAWEI TECH CO., LTD
Huawei AR1000V Router uptime is 0 week, 0 day, 3 hours, 31 minutes
```

```
<Border01-BR02>display ip int b
*down: administratively down
^down: standby
(l): loopback
(s): spoofing
(E): E-Trunk down
The number of interface that is UP in Physical is 12
The number of interface that is DOWN in Physical is 0
The number of interface that is UP in Protocol is 6
The number of interface that is DOWN in Protocol is 6

Interface                         IP Address/Mask      Physical   Protocol
GigabitEthernet0/0/0              195.147.98.1/30      up         up
GigabitEthernet0/0/1              10.0.2.3/31          up         up
GigabitEthernet0/0/2              10.0.2.1/31          up         up
GigabitEthernet0/0/3              unassigned           up         down
GigabitEthernet0/0/4              unassigned           up         down
GigabitEthernet0/0/5              unassigned           up         down
GigabitEthernet0/0/6              unassigned           up         down
GigabitEthernet0/0/7              unassigned           up         down
GigabitEthernet0/0/8              unassigned           up         down
LoopBack0                         3.3.3.3/32           up         up(s)
NULL0                             unassigned           up         up(s)
Tunnel0/0/1                       172.16.20.2/30       up         up
```

```
<Border01-BR02>display ip routing-table protocol isis
Route Flags: R - relay, D - download to fib, T - to vpn-instance
------------------------------------------------------------------------------
Public routing table : ISIS
         Destinations : 3        Routes : 6

ISIS routing table status : <Active>
         Destinations : 3        Routes : 6

Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

       3.3.3.10/32  ISIS-L1 15   10          D   10.0.2.2        GigabitEthernet0/0/1
                    ISIS-L1 15   10          D   10.0.2.0        GigabitEthernet0/0/2
   192.168.10.0/24  ISIS-L1 15   20          D   10.0.2.2        GigabitEthernet0/0/1
                    ISIS-L1 15   20          D   10.0.2.0        GigabitEthernet0/0/2
   192.168.20.0/24  ISIS-L1 15   20          D   10.0.2.2        GigabitEthernet0/0/1
                    ISIS-L1 15   20          D   10.0.2.0        GigabitEthernet0/0/2

ISIS routing table status : <Inactive>
         Destinations : 0        Routes : 0
```

```
<Border01-BR02>display bgp peer

 Status codes: * - Dynamic

 BGP local router ID : 195.147.98.1
 Local AS number : 65300
 Total number of peers : 1                Peers in established state : 1
 Total number of dynamic peers : 0

  Peer            V          AS  MsgRcvd  MsgSent  OutQ  Up/Down       State PrefRcv

  172.16.20.1     4       65100      218      217     0 03:30:33 Established       6
```

```
<Border01-BR02>display ip routing-table protocol bgp
Route Flags: R - relay, D - download to fib, T - to vpn-instance
------------------------------------------------------------------------------
Public routing table : BGP
         Destinations : 6        Routes : 6

BGP routing table status : <Active>
         Destinations : 6        Routes : 6

Destination/Mask    Proto   Pre  Cost      Flags NextHop         Interface

  192.168.110.0/24  EBGP    255  2          RD   172.16.20.1     Tunnel0/0/1
  192.168.120.0/24  EBGP    255  2          RD   172.16.20.1     Tunnel0/0/1
  192.168.130.0/24  EBGP    255  2          RD   172.16.20.1     Tunnel0/0/1
  192.168.210.0/24  EBGP    255  0          RD   172.16.20.1     Tunnel0/0/1
  192.168.220.0/24  EBGP    255  0          RD   172.16.20.1     Tunnel0/0/1
  192.168.230.0/24  EBGP    255  0          RD   172.16.20.1     Tunnel0/0/1

BGP routing table status : <Inactive>
         Destinations : 0        Routes : 0
```

```
<Border01-BR02>display ipsec sa b

IPSec SA information:
   Src address                             Dst address                             SPI
   VPN                                     Protocol                                Algorithm
 --------------------------------------------------------------------------------------------------------------------------
   14.1.2.1                                195.147.98.1                            11898564
                                           ESP                                     E:AES-256 A:SHA2_512_256
   195.147.98.1                            14.1.2.1                                2909459
                                           ESP                                     E:AES-256 A:SHA2_512_256

  Number of IPSec SA : 2
 --------------------------------------------------------------------------------------------------------------------------
```

```
<Border01-BR02>display ike sa
 Conn-ID    Peer                                          VPN              Flag(s)               Phase  RemoteType  RemoteID
------------------------------------------------------------------------------------------------------------------------------------
 8          14.1.2.1/500                                                   RD|A                  v2:2   IP          14.1.2.1
 3          14.1.2.1/500                                                   RD|A                  v2:1   IP          14.1.2.1

  Number of IKE SA : 2
------------------------------------------------------------------------------------------------------------------------------------
```

#### [Agg-SW01-BR02 full config](configs/Agg-SW01-BR02.md)

```
<Agg-SW01-BR02>display version
Huawei Versatile Routing Platform Software
VRP (R) software, Version 8.180 (CE6800 V200R005C10SPC607B607)
Copyright (C) 2012-2018 Huawei Technologies Co., Ltd.
HUAWEI CE6800 uptime is 0 day, 3 hours, 49 minutes
SVRP Platform Version 1.0
```

```
<Agg-SW01-BR02>display ip int b | i up
*down: administratively down
!down: FIB overload down
^down: standby
(l): loopback
(s): spoofing
(d): Dampening Suppressed
The number of interface that is UP in Physical is 7
The number of interface that is DOWN in Physical is 1
The number of interface that is UP in Protocol is 6
The number of interface that is DOWN in Protocol is 2
Interface                   IP Address/Mask    Physical Protocol VPN
GE1/0/0                     10.0.2.2/31        up       up       --
GE1/0/1                     10.0.2.0/31        up       up       --
LoopBack0                   3.3.3.10/32        up       up(s)    --
MEth0/0/0                   unassigned         up       down     --
NULL0                       unassigned         up       up(s)    --
Vlanif10                    192.168.10.254/24  up       up       --
Vlanif20                    192.168.20.254/24  up       up       --
```

```
<Agg-SW01-BR02>display isis peer

Peer Information for ISIS(1)
--------------------------------------------------------------------------------

  System ID     Interface       Circuit ID        State HoldTime(s) Type     PRI
--------------------------------------------------------------------------------
0000.0000.0001  GE1/0/0         0000000001         Up            24 L1L2      --
0000.0000.0001  GE1/0/1         0000000002         Up            24 L1L2      --

Total Peer(s): 2
```

```
<Agg-SW01-BR02>display ip routing-table protocol isis
Proto: Protocol        Pre: Preference
Route Flags: R - relay, D - download to fib, T - to vpn-instance, B - black hole route
------------------------------------------------------------------------------
_public_ Routing Table : IS-IS
         Destinations : 7        Routes : 9

IS-IS routing table status : <Active>
         Destinations : 2        Routes : 4

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

        0.0.0.0/0   ISIS-L2 15   10            D   10.0.2.3        GE1/0/0
                    ISIS-L2 15   10            D   10.0.2.1        GE1/0/1
        3.3.3.3/32  ISIS-L1 15   10            D   10.0.2.3        GE1/0/0
                    ISIS-L1 15   10            D   10.0.2.1        GE1/0/1

IS-IS routing table status : <Inactive>
         Destinations : 5        Routes : 5

Destination/Mask    Proto   Pre  Cost        Flags NextHop         Interface

       3.3.3.10/32  ISIS-L1 15   0                 3.3.3.10        LoopBack0
       10.0.2.0/31  ISIS-L1 15   0                 10.0.2.0        GE1/0/1
       10.0.2.2/31  ISIS-L1 15   0                 10.0.2.2        GE1/0/0
   192.168.10.0/24  ISIS-L1 15   0                 192.168.10.254  Vlanif10
   192.168.20.0/24  ISIS-L1 15   0                 192.168.20.254  Vlanif20
```










