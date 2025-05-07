---
tags:
  - konfiguracja
---
Z protokołu [[OSPF]] mogą korzystać nie tylko sieci wielodostępowe, ale też sieci punkt-punkt. Żeby to skonfigurować, należy w konfiguracji routera określić podsieci, które mają być rozgłaszane przez OSPF. Interfejsy routera "mieszczące" się w zakresie ogłaszanej podsieci w **poleceniu network** są wskazane do wysyłania i odbierania pakietów OSPF.

[[Konfiguracja OSPF]] odbywa się normalnie, należy jednak jasno i wyraźnie zaznaczyć procesowi OSPF, że interfejs należy do sieci point-to-point, żeby ten nie próbował liczyć [[Router desygnowany|DR i BDR]], ponieważ nie są one konieczne. Można to zrobić poleceniem:

```
R1(config)# interface GigabitEthernet 0/0/0
R1(config-if)# ip ospf network point-to-point
```

