---
tags:
  - konfiguracja
---
Statyczny [[NAT]] polega na tłumaczeniu adresy [[Prywatne adresy IPv4|prywatnego]] na publiczny w stosunku 1:1 - jeden adres prywatny = jeden adres publiczny. Jest przydatny w serwerach WWW i innych urządzeniach o stałym adresie, a także do wygodnego dostępu zdalnego. Można zrobić tak, że ustawiamy statyczny NAT na serwer a [[Dynamiczny NAT|dynamiczny]] na wszystko inne w sieci.

![[Pasted image 20250513162411.png]]

##### Konfiguracja NAT statycznego opera się na:
1. Stworzeniu odwzorowania pomiędzy wewnętrznym adresem lokalnym a wewnętrznym adresem globalnym
   >`R2(config)# ip nat inside source static 192.168.10.254 209.165.201.5`
   >- `192.168.10.254` to adres wewnętrzny lokalny
   >- `209.165.201.5` to adres wewnętrzny globalny
2. Określenie interfejsu wewnętrznego i zewnętrznego - który "styka" się z siecią LAN a który z Internetem. Interfejs musi być w tej samej sieci, co adres przed lub po tłumaczeniu.
   >```
   >R2(config)# interface serial 0/1/0
R2(config-if)# ip address 192.168.1.2 255.255.255.252
R2(config-if)# ip nat inside
R2(config-if)# interface serial 0/1/1
R2(config-if)# ip address 209.165.200.1 255.255.255.252
R2(config-if)# ip nat outside
>```