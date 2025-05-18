---
tags:
  - konfiguracja
---
Dokładne ustalenie czasu jest ważne w zarządzaniu sieciami, zatem warto jest mieć serwery zarządzające czasem żeby nie polegać na zegarze systemowym. Może do tego posłużyć **NTP** (*Network Time Protocol*). 

Zegar można ustawić manualnie, jak tutaj:

```
R1# clock set 16:01:00 sept 25 2020
*Sep 25 16:01:00.000: %SYS-6-CLOCKUPDATE: System clock has been updated from 13:09:49 UTC Fri Sep 25 2020 to 16:01:00 UTC Fri Sep 25 2020, configured from console by console.
Sep 25 16:01:00.001: %PKI-6-AUTHORITATIVE_CLOCK: The system clock has been set.
R1#
```

Ale w większych sieciach warto jest mieć zsynchronizowany czas. NTP pozwala ustalać czas na podstawie połączonego z nim serwera NTP. Ten serwer może być w sieci wewnętrznej lub publicznie dostępnym serwerem.

Sieci NTP są hierarchiczne, gdzie na szczycie hierarchii (w warstwie 0) są najbardziej zaufane (autorytatywne) źródła, a z każdym przeskokiem precyzja trochę maleje. Urządzenia *stratum 1* są połączone z tymi autorytatywnymi źródłami i są standardem. Wszystko niżej jest co raz mniej precyzyjne, poniżej 15 warstwy już mówimy o serwerze zdesynchronizowanym.  

##### Konfiguracja NTP

To, co jest źródłem czasu można sprawdzić poleceniem `show clock detail`. Domyślnie:

```
R1# show clock detail
20:55:10.207 UTC Fri Nov 15 2019
Time source is user configuration
```

Żeby zmienić źródło czasu na serwer NTP, należy użyć `ntp server [ip-addr]`

```
R1(config)# ntp server 209.165.200.225
R1(config)# end

R1# show clock detail
21:01:34.563 UTC Fri Nov 15 2019
Time source is NTP
```

Jak widać, źródło zostało zamienione na serwer NTP. **Taki router może stać się źródłem informacji NTP dla innych urządzeń w sieci. Wtedy, router jest urządzeniem *stratum* 1, a np. korzystający z jego usług switch jest urządzeniem *stratum* 2.** 