---
tags:
  - konfiguracja
---
**CDP** (*Cisco Discovery Protocol*) pozwala na utworzenie mapy sieci poprzez ogłoszenia między urządzeniami. W tych ogłoszeniach widać interfejsy, typ urządzenia, jego nazwę. "Skacząc" sobie CDP po kolejnych urządzeniach i szukając kolejnych sąsiadów można powoli budować mapę całej sieci. Jest to pewne zagrożenie bezpieczeństwa, zatem CDP należy wyłączyć jeśli nie jest potrzebny.

##### Działanie

Protokół włącza się na całym urządzeniu poleceniem `R1/S1(config)# cdp run`, ale można go też włączyć (*enable-ować*) na wybranym interface:
```
R1/S1(config)# int g0/0/1
R1/S1(config-if)# cdp enable
```

Sąsiadów CDP można zobaczyć poleceniem `show cdp neighbors`.

```
R1# show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                  D - Remote, C - CVTA, M - Two-port Mac Relay
Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
S1               Gig 0/0/1           179         S I      WS-C3560- Fas 0/5
```

W tym przypadku sąsiadem naszego routera jest switch `S1`. Interfejs G0/0/1 routera łączy się z F0/5 switcha.  `Capability` potwierdza, że jest to rzeczywiście `S`witch, a także pokazana jest *platforma sprzętowa*. 

Szczegóły można zobaczyć dzięki `show cdp neighbors detail`, gdzie można zobaczyć też chociażby adresy IP, wersje, adres wsparcia technicznego, włączone protokoły...

```
R1# show cdp neighbors detail
-------------------------
Device ID: S1
Entry address(es):
  IP address: 192.168.1.2
Platform: cisco WS-C3560-24TS,  Capabilities: Switch IGMP
Interface: GigabitEthernet0/0/1,  Port ID (outgoing port): FastEthernet0/5
Holdtime : 136 sec
Version :
Cisco IOS Software, C3560 Software (C3560-LANBASEK9-M), Version 15.0(2)SE7, R
RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2014 by Cisco Systems, Inc.
Compiled Thu 23-Oct-14 14:49 by prod_rel_team
advertisement version: 2
Protocol Hello:  OUI=0x00000C, Protocol ID=0x0112; payload len=27,
value=00000000FFFFFFFF010221FF000000000000002291210380FF0000
VTP Management Domain: ''
Native VLAN: 1
Duplex: full
Management address(es):
  IP address: 192.168.1.2
Total cdp entries displayed : 1
```

Tak jak wspominałem, można w ten sposób "skakać" od urządzenia do urządzenia poprzez np. SSH i dalej sprawdzać kolejnych sąsiadów. 

```
S1# show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                  D - Remote, C - CVTA, M - Two-port Mac Relay
Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
S2               Fas 0/1           150              S I   WS-C2960- Fas 0/1
R1               Fas 0/5           179             R S I  ISR4331/K Gig 0/0/1
```

Na przykładzie widzimy `R1` - skoro `S1` jest sąsiadem `R1` to `R1` musi być sąsiadem `S1`, widzimy te same informacje ale "z drugiej strony", czyli jak inne urządzenia w sieci widzą ten router.

Dodatkowo, w tablicy sąsiadów pojawia się `S2`, czyli kolejny switch w sieci. Ten nie był podłączony do `R1`, ale do `S1` już tak. 